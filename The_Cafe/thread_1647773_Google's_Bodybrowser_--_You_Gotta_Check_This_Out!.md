---
title: "Google's Bodybrowser -- You Gotta Check This Out!"
date: 2010-12-17
forum: The Cafe
---

### Post by laceration on 2010-12-17
If anyone doubts that Google is at the absolute bleeding edge in computing...check out the bodybrowser.
This is a groundbreaking and very significant web application.  It's at [http://bodybrowser.googlelabs.com](http://bodybrowser.googlelabs.com).  This is best described as a google map for the human body.  I feel like I have just doubled my knowledge of human anatomy in the last hour.  I just tweaked my back from skiing and biking a lot in the last few days, looks like its the iliolumbar ligament, who knew?  

Intel graphics probably won't handle this and you need a next generation web browser to run this as it works by WebGL and the HTML5 Canvas element.  All the major browsers will be supporting this except for IE!  If you have a daily build ppa for chromium or firefox it'll work. You have to start at the cli.  I started Chromium like this:

$ chromium-browser --enable-webgl

I hope Google ports Maps to this technology, we can already see how Youtube is moving away from the resource hogging and program crashing Flash.  It does seem like Flash is opening up their specifications and adding hardware acceleration, so maybe there is some hope there even, but probably too little too late.  And MS isn't in on the consortium behind this(google, apple, ff + opera are).
This all suggests to me that IE and Flash are over!  Good Riddance!

And in the face of so much Smart Phone hype these days this is something that is great on my 42" monitor.

here's a vid of it for all those of you who can't mange getting a newer browser going, + don't worry this will be mainstream soon enough.
[http://www.youtube.com/watch?v=KidJ-2H0nyY](http://www.youtube.com/watch?v=KidJ-2H0nyY)

---

### Post by Mr. Picklesworth on 2010-12-17
It's much easier to enable webgl (and other goodies) nowadays in Chromium. Just about:flags, select it (and any other things you want to play with) and restart your browser.

---

### Post by JustinR on 2010-12-17
This isn't really bleeding edge. Its okay quality CGI. And it's not very informative - and only supports 3 browsers.

Unlike, for example, [The Human Body Book]("http://www.amazon.com/Human-Body-Book-DVD/dp/0756628652/ref=sr_1_1?ie=UTF8&qid=1292636114&sr=8-1"), which has nicer CGI (if you click on the picture of the book cover, you can look at the inside of the book), and explains everything in the human body in great detail. The book also includes an interactive DVD that does the same as the web application.

Don't get me wrong, I'm sure this will get popular, but there isn't much to it.

---

### Post by Lucradia on 2010-12-17
I'm sorry, but seeing as Firefox 3 doesn't support it, it is fail.

---

### Post by Mr. Picklesworth on 2010-12-17
> **Lucradia said:**
> I'm sorry, but seeing as Firefox 3 doesn't support it, it is fail.

Firefox 3 doesn't support a lot of new things. Like WebM video, HTML5 forms and CSS Transitions ;)
What you need is [Firefox 4]("http://www.mozilla.com/en-US/firefox/beta/").
Here's a nice list of [web technology changes]("http://www.mozilla.com/en-US/firefox/beta/technology/")

If you're wondering, [WebGL]("http://www.khronos.org/webgl/") is indeed a young specification on the way to being standardised. And it's amazing. And we should all be very happy for it because it's another step forwards for OpenGL in general, freeing us from the grip Microsoft's DirectX currently has. With stuff like WebGL and even OpenGL ES on the *iPhone*, we're getting closer and closer to the OpenGL API being actively preferred by developers. It is now something that people actually really should take the time to learn. It means much more portable code, which gives us better compatibility through Wine and a reasonable possibility of games and other graphics-heavy software being built for Linux.
And it means Microsoft has less control. DirectX is how they have locked developers (and, by extension, users) into their ecosystem.

---

### Post by Lucradia on 2010-12-18
> **Mr. Picklesworth said:**
> Firefox 3 doesn't support a lot of new things. Like WebM video, HTML5 forms and CSS Transitions ;)
What you need is [Firefox 4]("http://www.mozilla.com/en-US/firefox/beta/").
Here's a nice list of [web technology changes]("http://www.mozilla.com/en-US/firefox/beta/technology/")

If you're wondering, [WebGL]("http://www.khronos.org/webgl/") is indeed a young specification on the way to being standardised. And it's amazing. And we should all be very happy for it because it's another step forwards for OpenGL in general, freeing us from the grip Microsoft's DirectX currently has. With stuff like WebGL and even OpenGL ES on the *iPhone*, we're getting closer and closer to the OpenGL API being actively preferred by developers. It is now something that people actually really should take the time to learn. It means much more portable code, which gives us better compatibility through Wine and a reasonable possibility of games and other graphics-heavy software being built for Linux.
And it means Microsoft has less control. DirectX is how they have locked developers (and, by extension, users) into their ecosystem.

I'll wait until full release though. I don't like installing a beta browser, when the main one will be upgraded side by side when full release comes, but the beta one won't be.

---

### Post by chriswyatt on 2010-12-18
> **Lucradia said:**
> I'm sorry, but seeing as Firefox 3 doesn't support it, it is fail.

Logic fail.

---

### Post by Spice Weasel on 2010-12-18
> **Lucradia said:**
> I'll wait until full release though. I don't like installing a beta browser, when the main one will be upgraded side by side when full release comes, but the beta one won't be.

Why?

It's already faster and more stable than 3 was ever on my system, thanks to addons you can make it look exactly like 3.6, and all of the most popular addons are available.

ymmv.

---

### Post by flying sheep on 2010-12-18
why is everything on the &#8220;serious&#8221; internet compatible to the american-wasp-hypocrit morale?
in other words: what&#8217;s a body browser worth if you can&#8217;t disable the &#8220;cloths&#8221; layer?

---

### Post by juancarlospaco on 2010-12-18
**^  +1**

It seems adults are not ready yet.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-12-18
> **flying sheep said:**
> why is everything on the “serious” internet compatible to the american-wasp-hypocrit morale?
in other words: what’s a body browser worth if you can’t disable the “cloths” layer?

You're complaining because google doesn't serve you pornography?

That's what their search engine is for, silly. :D

---

### Post by gpgp on 2010-12-18
I got this working on my desktop with chromium. It will not run on my laptop and i suspect it is as the OP said because i have intel graphics chipset. Will this ever work with intel graphic chipsets ? Curious as to why or why not. I use the i915 driver.

Thank you

gpgp

I have mesa installed but no luck in minefeild or chromium.

Output of terminal when i go to google body browser in minefield:

```
Can't find symbol 'OSMesaCreateContextExt'
Can't find symbol 'OSMesaMakeCurrent'
Can't find symbol 'OSMesaPixelStore'
Can't find symbol 'OSMesaDestroyContext'
Can't find symbol 'OSMesaGetCurrentContext'
Can't find symbol 'OSMesaMakeCurrent'
Can't find symbol 'OSMesaGetProcAddress'
Couldn't find required entry points in OSMesa libary
Can't find symbol 'OSMesaCreateContextExt'
Can't find symbol 'OSMesaMakeCurrent'
Can't find symbol 'OSMesaPixelStore'
Can't find symbol 'OSMesaDestroyContext'
Can't find symbol 'OSMesaGetCurrentContext'
Can't find symbol 'OSMesaMakeCurrent'
Can't find symbol 'OSMesaGetProcAddress'
Couldn't find required entry points in OSMesa libary
```

My webgl setings in minefield :

webgl.enabled_for_all_sites;true
webgl.force_osmesa;true
webgl.mochitest_native_gl;false
webgl.osmesalib;/usr/lib/mesa/libGL.so.1.2  <-- changed by me
webgl.shader_validator;true
webgl.verbose;false

The path to mesa was changed by me, the default did not exist. 

thank you

gpgp

---

### Post by gpgp on 2010-12-18
So far i have been able to determine you need the libosmesa packages installed from the repos. i had mesa but not OSMesa 

I have reconfigured minefield after installing the libOSMesa packages with the path to libOSMesa16.so. I now do not get any errors when going to the body browser page. the left hand sliders are working but i have no image of the body. 

Any ideas ?

gpgp

---

### Post by laceration on 2010-12-18
> **Lucradia said:**
> I'm sorry, but seeing as Firefox 3 doesn't support it, it is fail.
Yeah, I don't like the alpha/beta ff, breaking all the addons that I use.  But you need not limit yourself to 1 browser.  I have Chromium installed too, the daily build PPA.  Anyways ff 4 is due within weeks.

@JustinR
Stick in the mud arguments.  Bodybrowser is not merely okay.  Don't mistake its elegance for simplicity.  Have you tried typing a body part in the search bar?  For more detail there is no accompanied text, but there is google search--you see what they're doing there?

---

### Post by BigSilly on 2010-12-18
Thanks for bringing this brilliant find to my attention. Bit gobsmacked at it to be honest. It ran fine on my Chromium on Ubuntu as the OP stated. :)

---

