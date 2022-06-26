# Favicon Tags
Simple PHP library to help developers 🐘 do better on-page Favicon optimization
Before starting, I suggest preparing your cup of coffee and cigarettes. To make your work more enjoyable. 😊


## Installation:

### Composer Installation
```bash
composer require officialxviid/favicon
```

### Manual Installation
Should you choose not to use Composer to install, you can clone or download this repo and then enable it by editing **Config/Autoload.php** and adding the **OfficialXVIID\Favicon** namespace to the **$psr4** array. For example, if you copied it into **app/ThirdParty**:
```php
    $psr4 = [
        'Config'                => APPPATH . 'Config',
        APP_NAMESPACE           => APPPATH,
        'OfficialXVIID\Favicon' => APPPATH .'ThirdParty/OfficialXVIID/favicon/src',
    ];
```


## Usage:
Check this simple examples. (of course the composer autoload.php file is required)

### Controller
Since this favicon will be used on all pages, let's assume your central controller is in **BaseController.php**
```php
<?php
use OfficialXVIID\Favicon\FaviconTags;

class BaseController {
    /**
     * Send Data To View
     */
    protected $dataPage;
    
    /**
     * Construct (Magic Method)
     */
    public function __construct(){
      // Add this line
      $this->set_favicon();
    }
    
    /**
     * Set Favicon
     * (Add this function)
     */
     protected function set_favicon(){
      // Your image (png)
      $favicontags = new FaviconTags();
      $favicontags->setFavicon();
      
      $this->dataPage['my_favicon'] = $favicontags->ico('/assets/favicon/favicon.ico')
                                                  ->fav180('/assets/favicon/favicon-180x180.png')
                                                  ->fav32('/assets/favicon/favicon-32x32.png')
                                                  ->fav16('/assets/favicon/favicon-16x16.png')
                                                  ->favManifest('/assets/favicon/site.webmanifest')
                                                  ->favMask('/assets/favicon/safari-pinned-tab.svg')
                                                  ->favMstile('/assets/favicon/mstile-144x144.png')
     }
}
```

### Views
We assume we will put this favicon in **app/Views/templates/header.php**
```php
<head>
  // Add This line
  <?= $my_favicon; ?>
</head>
```

### Result
```html
<link rel="shortcut icon" href="/assets/favicon/favicon.ico">
<link rel="apple-touch-icon" sizes="180x180" href="/assets/favicon/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="/assets/favicon/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/assets/favicon/favicon-16x16.png">
<link rel="manifest" href="/assets/favicon/site.webmanifest">
<link rel="mask-icon" href="/assets/favicon/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="msapplication-TileImage" content="/assets/favicon/mstile-144x144.png">
<meta name="theme-color" content="#ffffff">
```


## Coming Soon:
We will expand this library by adding a generator in it. So, just 1 file (Ex: SVG) all will be resolved.


## References:
- [Define a favicon to show in search results (https://developers.google.com/search/docs/advanced/appearance/favicon-in-search)](https://developers.google.com/search/docs/advanced/appearance/favicon-in-search)
- [cpswsg/Favicon MetaTags (https://gist.github.com/cpswsg/5843674)](https://gist.github.com/cpswsg/5843674)
- [HTML Favicon (https://www.w3schools.com/html/html_favicon.asp)](https://www.w3schools.com/html/html_favicon.asp)

## Contact
- [Twitter (https://twitter.com/officialxviid)](https://twitter.com/officialxviid)
- [Instagram (https://instagram.com/officialxviid)](https://instagram.com/officialxviid)
- [Site (https://xviid.net)](https://xviid.net)
- [Email (support@xviid.net)](mailto:support@xviid.net)


## Donate:
- [Paypal](https://paypal.me/xviid)


## License
[MIT](https://github.com/officialxviid/favicon/blob/main/LICENSE) Copyright (c) 2022 Official XVIID
