# feedify

Feedify is a plug-and-play(esque) client-side Instagram feed for Shopify-developed themes. Quoick loading and comes with 4 presets, as well as several other customizable options to let the widget fit the look and feel of a merchant's theme. 

Feedify uses instafeed.js, and fetches users' access tokens using an OAuth2 authentication directly from Instagram. (Presently, using Pixel Union's token generator (http://instagram.pixelunion.net/) until a development account gets approved for Shopify. )

**To install**

Download all files; upload *instafeed.js*, *instafeed.min.js* and *feedify.scss.liquid* to the assets folder of the merchant's theme. 

Upload the *feedify.liquid* file to the snippets folder.

Take the *setting_schema_addition.json* and append the content to the theme's *settings_schema.json*, as the last set of options (before the closing ] )

In the theme.liquid, find the CSS includes section of the header; add 
` {{ 'feedify.scss.css' | asset_url | stylesheet_tag }}`.

Locate the ` {{content_for_header}} `; below this, paste:

```
  {% if settings.feedify_enable %}
  {{ 'instafeed.js' | asset_url | script_tag }} 
  {{ 'instafeed.min.js' | asset_url | script_tag }}
  {% endif %} 
```
  
Finally, you can add this to the theme where you wish to place the feed (either in the *index.liquid* or in the *theme.liquid*, depending on how you want the feed to display): 

```
{% if settings.feedify_enable %}
    {% include 'feedify' %}
{% endif %}
``` 

Note that you don't need to wrap this include in `<div>` tags as they're contained in the snippet. 

**Save all changes.** 

Open the storefront editor, and head to the Instagram widget section.

[![alt](https://screenshot.click/10-41-i91lq-rz65y.png)](https://screenshot.click/10-41-i91lq-rz65y.png)

When you generate an access token, it will come in the format `123456789.1234ab5.123qwe456rty789uio0132w5475fy712`; this entire string is the access token; additionally, the first 9 digits (everything before the first . ) is the user id. 
[![alt](348559287.1677ed0.b281428a19854f20bc331413c326d34a)](348559287.1677ed0.b281428a19854f20bc331413c326d34a)

You will require both for this to function.

Once those are added, save your changes; and now you can toggle on the *show Instagram feed?* setting, and explore the presets and display options!



