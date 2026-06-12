---
title: "Flash Issues"
date: 2012-07-27
forum: Ubuntu Studio
---

### Post by Alecossy on 2012-07-27
Hey all,
I keep experimenting laggy playback when using anything that is flash based. 
This happens in both firefox and chrome, mostly while switching from a youtube page to a plain html page and back ( videos get stuck) or while using facebook chat.
Any idea what might be causing the issue?
Alecossy

---

### Post by pqwoerituytrueiwoq on 2012-07-27
What hardware are you using?
have you tried [yuotube html5](http://www.youtube.com/html5/) video
you can use [flash video replacer](https://addons.mozilla.org/en-us/firefox/addon/flashvideoreplacer/) on youtube

---

### Post by Alecossy on 2012-07-31
Here's the result of lshw.
[http://pastebin.com/ZdUnsUQG](http://pastebin.com/ZdUnsUQG)
HTML 5 with firefox only work with certain videos, the plug-in you linked to me has been removed by the author.
Problem doesn't only happen in youtube, I also experience problems when using fb or watching videos from other sources (such as putlocker or sockshare).
Expecially when using full screen.

---

### Post by shimoda on 2013-03-28
In my case the problem is with jack & pulseaudio... Audio of youtube videos is choppy... I solved it using and old version of flash, but since yesterday firefox is blocking it... 
With flash 12 the solution is close jack and then open firefox/youtube, all works well... But not seems a very good solution.. I don't want to close jack every time I start internet browser :S

¿any ideas?

---

### Post by CraigPid on 2013-03-28
I think the flash plugin is just a bad program.Last time I checked the min.reqirements for it was a dual core 2.4 GHZ chip or something like this.It seems ridiculous to me, or they're just using that to drive computer sales. We still have a P4 1.6 GHZ set up to output onto a TV. I have to set the quality of the flash video to 240p to get smooth playback.Meanwhile if I downloaded the same video at 1080p it plays flawlessly in any player.Go figure.

---

### Post by zequence on 2013-04-04
Flash is pretty hardware intensive, so if your computer is old, that could very well be the problem. I'm thinking at least 5 years old, or more, but that's just an estimation.

Could also be that your graphic card drivers aren't coping well. Do you know what kind of graphic card you have?

This should show you which graphic card you have:
```
$ lspci | grep VGA
```

Intel only has one set of drivers. Free and open source ones, written by Intel. AMD and Nvidia have both free and proprietary drivers available. How well the free ones work, depends at least on which release you are on. Newer releases have better drivers.

---

