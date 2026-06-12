---
title: "Blurry images"
date: 2020-02-19
forum: Ubuntu, Linux and OS Chat
---

### Post by phixate on 2020-02-19
I've been troubleshooting a problem I'm having with blurry images on my website. I'm running Ubuntu 16.04 on Apache with PHP. My website is Wordpress. When I upload pic to my website, whether inside or outside of Wordpress they look blurry. When I open them in Chrome locally they look sharp. I tried troubleshooting within Wordpress, disabling themes, messing with settings, trying different plugins, all kinds of stuff, and nothing worked. Then I tried uploading one of the images to my website root directory and it looked blurry there [https://whittsrentals.com/sandstone-620.png](https://whittsrentals.com/sandstone-620.png). How can an an image look blurry just sitting in my root directory, not being processed by anything in Wordpress? I'm wondering if Ubuntu or PHP or Apache has some software that will mess with your images. They are PNGs. The other weird thing is that they are displaying slightly larger than they should through my web server (they are supposed to be 620px wide). That is REALLY baffling me. This is one of the weirdest problems I've ever seen in web design and I can't figure out what it is. Any one have any suggestions?

Try this as an experiment: Save the image at the link I just posted to your desktop and open it. You will see it is slightly smaller and crisper than how it looks in the web browser.

---

### Post by phixate on 2020-02-19
OK, nevermind. It appears I tried everything BUT clearing my browser image cache. I feel really stupid now. It's always something stupid.

---

### Post by sdsurfer on 2020-02-19
Not always. :-D Welcome aboard and please mark your thread as solved. A couple ideas that may help in the future . . . .

> not being processed by anything in Wordpress

Wordpress doesn't mess with your images once they are set in a post. Once you upload them it creates copies at various sizes and resolutions using either the GD image extension or imageMagick, depending on how you have PHP and Wordpress configured (most often it's GD.) After that, it just SRC's the selected image files into pages as determined by the theme.

These sizes can be configured at a theme level and default to a set of sizes if the theme doesn't muck with them. It's not a dumb mistake to accidentally insert the wrong one into a theme or post. So if you accidentally insert a 320 wide image into a "featured image" that the theme sets for 620 wide, it will stretch it and make it look pixelated. That's a pretty common error.

> clearing my browser image cache

This is the bane of developers, caching. :-) Honestly I have found Chrome to be far more cache-greedy than Firefox, but although we as developers can tweak our cache settings or clear the cache, we have to consider that our users shouldn't be expected to do that.

The most straightforward answer is a "cachebuster." In it's most simple form, it means generating a unique identifier such as a timestamp and appending it to the image url. So I have 

image.png

and at some point I resize or otherwise change image.png, load the page, it appears unchanged because the browser says "hey, it hasn't really changed, I'm going to grab the cached copy." The fix is (pseudo code)

```

$rand = rand(); // say rand is 1234567
echo "<img src=\"image.png?$rand\">";

```

Browser says "image.png?1234567 is not the same as image.png" and downloads the fresh copy. The query string does not affect the image display.

Alternatively, some developers will set up a cachebuster who's value only changes when they change image sets, that is, hard code to "?today's date" then change the date when the image set changes. The idea is to go ahead and leverage caching to make your pages load faster, add a cachebuster only when you need it.

If you're not adept at coding themes, look for a cachebuster plugin or something, there should be one out there you can configure for specific resources: pages, images, download files, etc.

---

