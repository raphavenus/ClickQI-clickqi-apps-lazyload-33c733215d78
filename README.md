# **Lazyload**

Lazyload allows an asynchronous loading of images from the shelf and banners independent of frameworks.

## **Instalation**

```bash
$ npm install git+https://git-clickqi:bfKGnknsGDkKdPu58sRp@bitbucket.org/ClickQI/clickqi-apps-lazyload.git --save
```

or

```bash
$ yarn add git+https://git-clickqi:bfKGnknsGDkKdPu58sRp@bitbucket.org/ClickQI/clickqi-apps-lazyload.git
```

## **Basic Usage**

### **HTML Structure**

To use in Shelves (an example):

```html
<div class="shelf-images">
    <div class="mult-images">
        <p class="image-main">
            <noscript data-lazy-img="true">
                $product.GetImageTag(290, 290)
            </noscript>
        </p>
        <p class="image-over">
            <noscript data-lazy-img="true">
                $product.GetImageTag(290, 290, 'ImageOver')
            </noscript>
        </p>
    </div>
</div>
```

To use in banners (an example using VTEX):

```html
<noscript data-viewport-desktop="true">
    <vtex:contentPlaceHolder id="Banner Example" />
</noscript>
```

### **Javascript Instantiation**

To use the Lazyload plugin you must instantiate it in the running project.

```js
import { LazyLoad } from "@ClickQi/clickqi-apps-lazyload";
```

### **Invoke the Plugin**

After the package was imported invoke the plugin.

Using it for shelves:

```js
LazyLoad({
    placeholder: "image converted in base64"
});
```

Using it for banners:

```js
if (window.innerWidth > 767) {
    LazyLoad({
        attribute: "viewport-desktop",
        querySelectorType: ".box-banner",
        placeholder: "image converted in base64"
    });
} else {
    LazyLoad({
        attribute: "viewport-mobile",
        querySelectorType: ".box-banner",
        placeholder: "image converted in base64"
    });
}
```

### **Options**

| Property            | Value Type | Description                                                                                                      |
| ------------------- | ---------- | ---------------------------------------------------------------------------------------------------------------- |
| `attribute`         | String     | Set the NoScript that contains the image. Default is `lazy-img`.                                                 |
| `events`            | Array      | Set the events to listen. Default is `resize`, `scroll` and `touched`.                                           |
| `interval`          | Number     | Set the interval of time to verify the elements. Default is `500`.                                               |
| `querySelectorType` | String     | Set the label to be checked into the script and be unpacked. Default is `img`.                                   |
| `placeholder`       | String     | Set an image to use while the target image is being charged. It is suggested to use image converted to `base64`. |

## **Remove package**

```bash
$ npm uninstall @ClickQi/clickqi-apps-lazyload
```

or

```bash
$ yarn remove @ClickQi/clickqi-apps-lazyload
```
