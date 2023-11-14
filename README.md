# multipass

A Multipass module for Hydrogen and other storefronts where [Multipassify](https://github.com/beaucoo/multipassify) is not compatible.  

Multipass login is for store owners who have a separate website and a Shopify store. It redirects users from the website to the Shopify store and seamlessly logs them in with the same email address they used to sign up for the original website. See [Shopify Multipass page](https://shopify.dev/docs/api/multipass) for more about Multipass.  

## Installation

```npm install @nobu-shopify/multipass```

## How to use this module

```
  // Import
  import { Multipass } from '@shopify-apac-ts/multipass';

  // Create an Multipass object with your Shopify store's Multipass secret
  const multipass = new Multipass(context.env.MULTIPASS_SECRET);

  // Set customer data; only email is mandatory
  const customerData = {
    email,
    tag_string: `line_id:${sub}, line_name:${name}`,
  };

  // Generate Multipass token
  const token = multipass.generateToken(customerData);

  // Multipass endpoint with token
  const store_url = `${context.env.ONLINESTORE_URL}account/login/multipass/${token}`;

  // Redirect to the Multipass endpoint
  return redirect(store_url);

```

## Disclaimer

- This repository and its contents are not an officially supported Shopify product.
- This code is fully unofficial and NOT guaranteed to pass the public app review for Shopify app store. The official requirements are described [here](https://shopify.dev/apps/store/requirements).
- You need to follow [Shopify API Licene and Terms of Use](https://www.shopify.com/legal/api-terms) even for custom app usage.
- This code is supposed to be used as tutorial mainly for demonstrating how to develop a Shopify app and does NOT guarantee that all security concerns are taken care of such as [this one](https://shopify.dev/docs/api/checkout-ui-extensions/unstable/configuration#network-access). If you use this code for production, all resposibilties are owned by you and you should check the license first.

## License

All solutions within this repository are provided under the MIT license. Please see the [LICENSE](/LICENSE) file for more detailed terms and conditions.