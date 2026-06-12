---
title: "How to almost get Netflix Watch Instantly to work in Linux"
date: 2010-03-11
forum: The Cafe
---

### Post by samh785 on 2010-03-11
[http://linuxphilia.blogspot.com/2010/03/how-to-almost-get-netflix-watch.html](http://linuxphilia.blogspot.com/2010/03/how-to-almost-get-netflix-watch.html)

> I can make Netflix Watch Instantly work on my Linux media center.
  Almost. Yes, almost. No, I don't have it working. But I thought that with a little help from the community along with instructions on how I've gotten this far might help bring some support to the topic.
  **Here's how I did it.**
  
[LIST=1]
[*]Start with your favorite Linux distribution and [install the latest version of WINE.]("http://www.winehq.org/download/")  I have tried on version 1.1.40 with near success.
[*]Download the [latest version of Firefox for Windows]("http://www.mozilla.com/en-US/firefox/all.html") and install it into your WINE instance.
[*]Launch the WINE instance of Firefox and browse to [about:config]("http://about%3Cb%3E%3C/b%3E:config")
[*]Get past the warning screen, then right-click in the main region.  Click New &#8594; String.  You'll be given two dialogues:
[*]In the first dialogue, enter general.useragent.override
[*]In the second dialogue, enter Mozilla/5.0 (X11; U; Windows NT 6.0; en-US; rv:1.9.2) Gecko/20100115 Firefox/3.6
[*]Close Firefox and relaunch it.
[*]Browse to [netflix.com]("http://www.netflix.com/"), log in, and go to the watch instantly page. Magically, you'll be transported beyond the "OS not supported" page you're used to, and you'll be given the option to install the Silverlight plugin. Do so.
[/LIST]
  It's about here that you'll notice a crash. Firefox in WINE doesn't like it when the Silverlight plugin tries to install and fails. When you repeat step 8, you'll notice that you actually get to the page where the video ordinarily plays, but the image is scrambled and Firefox soon crashes.
  So here's the part where I ask for some support from the amazing Linux community. Does anybody have any suggestions as to where to go from here? I'm not sure what parts of the user agent string are being looked at, but it seems more like the Silverlight plugin for Firefox just doesn't work in WINE. How can we go about making Silverlight work?


---

### Post by inobe on 2010-03-11
i believe it's a .net thing and a little bit of RIA DRM, i don't think these hidden features do well emulated but then again i really don't know.

---

### Post by Bullwinkle_Moose on 2010-03-11
If you get this far in Wine, I wonder if you'd get any further in Codeweavers Crossover (see [http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/) ) - maybe you could contact them or look in their forums to see if they support Silverlight. As I understand it, Crossover is essentially just Wine with a lot of extras, unfortunately it's not free except on a trial basis

---

### Post by undecim on 2010-03-11
Would it maybe work with Moonlight + User Agent Switcher?

---

### Post by Pogeymanz on 2010-03-11
> **undecim said:**
> Would it maybe work with Moonlight + User Agent Switcher?

Nope. Moonlight does not support DRM.

---

### Post by LowSky on 2010-03-11
This is why we should support projects that work cross platform like Hulu Desktop and Boxee.

---

### Post by samh785 on 2010-03-11
> **LowSky said:**
> This is why we should support projects that work cross platform like Hulu Desktop and Boxee.
Very true. I was pleasantly surprised when hulu released their desktop application for linux, and it's exactly what we need to try to make happen on a larger scale.

---

### Post by yester64 on 2010-03-11
> **LowSky said:**
> This is why we should support projects that work cross platform like Hulu Desktop and Boxee.

For Hulu i would need Roku Box. I can not stream Hulu over the 360 so far.

I tried it with installing firefox under Wine and even if you install Silverlight (what a name) it does not work. Seems to not getting reconized even if its registered. Bad.

---

