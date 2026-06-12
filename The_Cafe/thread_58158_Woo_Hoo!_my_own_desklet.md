---
title: "Woo Hoo! my own desklet"
date: 2005-08-19
forum: The Cafe
---

### Post by xmastree on 2005-08-19
So, I was playing with desklets, and I installed that dinocam one. I looked at the source, and realised that it just displays a picture.
I have a webcam in my Internet cafe, so I changed a couple of things and I now have my own custom desklet! :cool:

Anyone care to take a look? It's [here](http://www.xmastree.34sp.com/ubuntu/CGInternetCam.tgz).

---

### Post by warp4ever on 2007-08-04
I came across your post a bit late :))
I'm curious how you managed the desklet

---

### Post by init1 on 2007-08-04
The page does not load.

---

### Post by popch on 2007-08-04
> **init1 said:**
> The page does not load.

after two years?

---

### Post by xmastree on 2007-08-04
blimey, that's a blast from the past...

Basically, IIRC, the dinocam desklet displayed an image. At the time (and no longer) I had an internet cafe, with a webcam (Remnants of it are [here](http://www.cginternet.net/zwebcam/webcam.html)).
I looked at the code for the desklet and altered the url of the picture to my own.

I think...

But it was long ago and far away...

[This]("http://www.cginternet.net/zwebcam/tech.html") is how I did the cam thing.

The desklet is now [here](http://www.cginternet.net/ubuntu/CGInternetCam.tgz) but it won't work since the url's have changed.

---

### Post by wersdaluv on 2007-08-04
:lolflag:

I did not realize how old this thread was until I read "after two years?"

---

### Post by warp4ever on 2007-08-11
[QUOTE=xmastree;3134043]blimey, that's a blast from the past...

Ubuntu is gaining users any minute, any day, any week, any month, any year, any two years.

Thanks, i'll figure if i can get it to work with one of the BBC cams.
The included Gdesklet Cam wouldn' t work with them.

---

### Post by xmastree on 2007-08-12
```
 <?xml version="1.0" encoding="UTF-8"?>

<display width="[COLOR="Red"]328[/COLOR]" height="[COLOR="Red"]248[/COLOR]" bg-color="#000050a0"
         window-flags="sticky, below">

  <meta author="Chris"
        category="fun/picture"
        description="CG Internet Webcam."
        name="CGInternet"
        version="1.0"/>

  <sensor id="cam" module="External,
                           echo [COLOR="Red"]http://www.cginternet.net/zwebcam/capture.jpg,
1000000[/COLOR]"/>

  <image anchor="center" x="50%" y="50%" watch="uri=cam:value"
         uri="[COLOR="Red"]http://www.cginternet.net/zwebcam/capture.jpg[/COLOR]"/>
  <label value="DinoCam" x="2%" y="2%" font="Sans italic 14" color="red"/>

</display>


```

If I remember correctly (and it was long ago and far away) you just need to edit the areas I've highlighted in red, mainly the image size, image url and the refresh rate, currently set at 1000000. I think that must be milliseconds.

Although having just tried it with the correct url, it doesn't work, :-k

What's the url of the image you want to display?

---

