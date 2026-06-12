---
title: "URL Icon"
date: 2010-12-17
forum: The Cafe
---

### Post by shadowfax1 on 2010-12-17
Just finished a website and looking to install a url address bar icon.  In windows you need a small program that's a .exe.  Anyone know of a linux program that does the same thing or can it be setup in 'wordpress'

---

### Post by Spice Weasel on 2010-12-17
Stick the icon you want to use in the root directory of your website and call it "favicon".

---

### Post by ki4jgt on 2010-12-17
> 
First, change the name of the favicon to "favicon.ico".
Insert the following HTML tag inside the <head> ... </head> section of your web page:
<link rel="shortcut icon" href="favicon.ico">

If you have downloaded an animated favicon, insert this:
<link rel="shortcut icon" href="favicon.ico">	

<link rel="icon" href="NAME OF THE ANIMATED FAVICON.gif" type="image/gif">	

Thats it!


[http://www.faviconsr.us/howto.php](http://www.faviconsr.us/howto.php)

---

### Post by Spice Weasel on 2010-12-17
It can be done that way... or you can do it the lazy way and let the web browser find out where the icon is.

---

### Post by ki4jgt on 2010-12-17
LOL, I've done it both ways :-) just letting the op know all available methods :-) I was wondering why that way was invented. I was assuming all browsers didn't support favicons or something like that was up. But didn't know for sure.

---

### Post by koenn on 2010-12-17
[http://en.wikipedia.org/wiki/Favicon](http://en.wikipedia.org/wiki/Favicon)

It started with as a Micosoft thing : "drop an .ico in the webfolder root and Interet Explorer will use it as an icon when you add the site to your 'Favorites' "

---

### Post by Quadunit404 on 2010-12-17
1. Make a small 16x16 icon related to your site. Save it as favicon.ico (can also be favicon.gif or favicon.png, but favicon.ico is pretty much universal and supported by all browsers)
2. Upload it to your site. This can be done by dropping it in the root folder of your site (or the root folder of a sub-domain of your site e.g. forum.mysite.com) or through a CMS admin page (I know that Drupal allows this)
3. Add this to your index.php or <insert language here>:
[HTML]<link rel="shortcut icon" href="/favicon.ico">[/HTML] (this isn't necessary if using a CMS as it automatically adds this to your index.whatever)
4. Save it.
5. Make sure that a browser is capable of finding the favicon by visiting your site in one.
6. If it does display the favicon, done!

---

### Post by shadowfax1 on 2010-12-17
Tried uploading a .png renaming it to favicon.ico but it doesn't upload in that format for me to insert <head>favicon.ico</head>

---

### Post by Spice Weasel on 2010-12-17
favicon.png will work too.

---

### Post by CharlesA on 2010-12-17
You have to tell the browser what to do with it.

[http://www.w3.org/2005/10/howto-favicon](http://www.w3.org/2005/10/howto-favicon)

---

### Post by MrGXZ on 2011-01-15
> **shadowfax1 said:**
> Tried uploading a .png renaming it to favicon.ico but it doesn't upload in that format for me to insert <head>favicon.ico</head>

Try converting it to ICO using something like [http://www.pngtoico.com](http://www.pngtoico.com) or downloading an application that converts it to the ICO format. ;)

---

