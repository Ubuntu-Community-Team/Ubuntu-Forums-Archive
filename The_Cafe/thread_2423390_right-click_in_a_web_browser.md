---
title: "right-click in a web browser"
date: 2019-07-22
forum: The Cafe
---

### Post by Skaperen on 2019-07-22
today, i found a [web site]("https://www.saywhatclub.org/") where right-click of every link was disabled.  any idea why anyone would do that?  it seems like a sick joke to me.   the pop-up message is framed like firefox is handling it. so it looks like a capability of firefox (i don't know about chrome, i avoid it).

*edit*:

just discovered that, in firefox, holding shift while doing right-click makes it work, anyway (i don't know about chrome, i avoid it).

---

### Post by #&amp;thj^% on 2019-07-22
most of the time one can overcome this with a setting:
```
about:config
```
now in the Search bar enter:
```
context
```
And change "dom.event.contextmenu.enabled" to "false"
I also avoid Chrome.
Sometimes it is to protect copying images or such that have copy right attached to it.

---

### Post by sevendogs1337 on 2019-07-22
Someone thought they'd pull a Javascript trick and disable right click. Stupid because they are probably thinking if you can't view the code on the page, that makes it more secure...

---

### Post by Skaperen on 2019-07-22
i use _right-click and "[FONT=courier new]Open Link in New Tab[/FONT]"_ out of habit. so it will use [FONT=century gothic]1fallen[/FONT]'s config fix to make it permanent in all my browsers.

---

### Post by sevendogs1337 on 2019-07-22
> **1fallen said:**
> 
Sometimes it is to protect copying images or such that have copy right attached to it.

Not possible: everything on a web age gets pulled to the browser, including images. Nothing on the web is safe if the web dev who built a given site only put in place client side controls. They can make images viewed on a page low res or with a watermark, but everything on a page is pulled to the client and is in cache.

The graphic owner would more than likely have to watermark an image with some sort of copy write if they didn't want people using it.

---

### Post by yetimon_64 on 2019-07-23
> **sevendogs1337 said:**
> Someone thought they'd pull a Javascript trick and disable right click. Stupid because they are probably thinking if you can't view the code on the page, that makes it more secure...
Yep, funny thing with using noscript is I had full right click menus on the site and such until I enabled their scripting; only then did the blocking happen. "noscript" sure makes a mess of that idea for them by default :P.

---

### Post by sevendogs1337 on 2019-07-23
Exactly - I visited OPs site and disabled Javascript via the dev panel in FF and viola, right click...client side only tricks are useless. I hack web sites for a living (pen tester) so there is pretty much nothing that can keep me from doing anything that is implemented client side.

---

### Post by #&amp;thj^% on 2019-07-23
> **sevendogs1337 said:**
> Not possible: everything on a web age gets pulled to the browser, including images. Nothing on the web is safe if the web dev who built a given site only put in place client side controls. They can make images viewed on a page low res or with a watermark, but everything on a page is pulled to the client and is in cache.

The graphic owner would more than likely have to watermark an image with some sort of copy write if they didn't want people using it.

I'm pretty sure you know what was meant, it's like locks, they only keep the honest folks out.;)

---

### Post by sevendogs1337 on 2019-07-23
I get it and yes, you are correct. I just wanted to make sure it was understood that anything on a web server that gets served can be pulled down and saved.

---

### Post by Skaperen on 2019-07-23
and anything a blu-ray shows on a TV with the wired up panel can be recorded.  every movie will show up online.  the honest folks won't download it.  OTOH, if the movie maker only markets it to Windows users...

---

### Post by kpatz on 2019-07-23
Disabling right click is just plain rude.  Anyone who does that is liable to see javascript disabled in my browser for their site.  Or I'll create a greasemonkey/tampermonkey script to restore the functionality.  Or I'll just boycott the site.

---

### Post by Skaperen on 2019-07-23
having the "feature" in an open source browser, at all, is what seems rude, to me.

---

### Post by sevendogs1337 on 2019-07-23
The browser is just rendering the Javascript as the web site designer intended. It's not a "feature" in the browser, this is how browsers work.

---

### Post by Skaperen on 2019-07-23
that's why i put quotes around the word.  OTOH, i would have made [FONT=courier new]dom.event.contextmenu.enabled[/FONT] default to true, if i were the developer (but, i'm not).

---

