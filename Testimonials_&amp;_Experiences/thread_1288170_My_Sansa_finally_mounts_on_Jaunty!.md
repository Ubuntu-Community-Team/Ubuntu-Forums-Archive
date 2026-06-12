---
title: "My Sansa finally mounts on Jaunty!"
date: 2009-10-11
forum: Testimonials &amp; Experiences
---

### Post by Vostrocity on 2009-10-11
I've had both my Sansa (mp3 player) and Ubuntu for a while, but for some reason I never tried connecting them until Jaunty. Well when I finally decided to one day, nothing happened. Ubuntu didn't recognize the Sansa at all. I did some research and apparently it was a well-known issue that Jaunty broke Sansa mounting (previous Ubuntu versions were fine). There were a few workarounds for it. I tried them but none worked (possibly due to my poor ability to use the Terminal). Remember this happened a whole 6 months ago, when Jaunty first came out. So about every other month after that, I would get so frustrated with having to reboot to to Windows that I would decide to try to fix the problem again. And nothing ever came of it. Finally today, it worked! Apparently MTP was the missing piece of the puzzle. Sansas are dual-mode USB devices (meaning they have an on-screen option to switch between MTP and MSC). I've always used MSC, just because it seemed the logical choice being that MSC is standard USB while MTP is a Windows-based protocol. I was wrong, setting my Sansa to MTP enabled one of the patches I used earlier and now my Sansa happily connects to Ubuntu. Ironically, Jaunty's life is just about over, I hope Karmic doesn't create the issue all over again. :)


EDIT: Bonus! Ubuntu even gives me custom icon that is the exact model of my Sansa.

I'm not asking any responses (though feel free), that was just a random rant/rave that I had to put on paper (read: text box).

---

### Post by 3rdalbum on 2009-10-11
Gnome developers like to break non-iPod MP3 players every couple of releases. They did it in Hardy and they did it in Jaunty.

For little-known reasons, some versions of Gnome seem to think "If a device supports UMS and MTP, use MTP", and whenever this happens, MTP is also broken in that release.

---

### Post by armandh on 2009-10-11
thank you for pointing the way for other ipod users
you have probably saved someone a month of frustration

---

### Post by HappyFeet on 2009-10-11
> **Vostrocity said:**
> Ironically, Jaunty's life is just about over, I hope Karmic doesn't create the issue all over again. :)


Why is jaunty's life over? It is supported for 18 months, and you can use it for years if you like. No one forces you to "upgrade".

---

### Post by Tamlynmac on 2009-10-11
> HappyFeet
Why is jaunty's life over? It is supported for 18 months, and you can use it for years if you like. No one forces you to "upgrade".

I'm also amazed by those that assume because a new version is released that all other versions are "over". For example, there are still those using 8.04 as it was an LTS release. Likely, other previous versions are still out there.

Odd to think Jaunty is over, just because Karmic is released. Reminding people of the fact that no one forces them to upgrade, is a good idea. Are you preparing for the inevitable? :)

---

### Post by sgosnell on 2009-10-11
Maybe it's just me, but I've never had any problem with my Sansa.  My Fuze can be set to automatically use either MTP or MSC, and I just plug it in and it works.  I have an old clip model somewhere, maybe I'll try to find it and see if it works with Jaunty.

---

### Post by aysiu on 2009-10-12
I've been using a Sansa Clip with MSC and have had no mounting problems with any of the past five Ubuntu releases (including Jaunty).

---

### Post by darrenn on 2009-10-12
My sansa has always worked perfectly with ubuntu. Yeah it sucks when a piece of hardware doesn't work.

---

### Post by waspbr on 2009-10-12
same here, my sansa clip has always worked well on jaunty, in the preferences you can set the sansa to automatically switch between the two modes. 

I just had a little bit of an issue with karmic when it was alpha but now it mounts just fine.

---

### Post by Vostrocity on 2009-10-12
> **HappyFeet said:**
> Why is jaunty's life over? It is supported for 18 months, and you can use it for years if you like. No one forces you to "upgrade".
I'm not cutting-edge at all, but when a new stable version of something comes out I always upgrade. I don't know many people who use a non-current release unless it's a LTS.

> **waspbr said:**
> same here, my sansa clip has always worked well on jaunty, in the preferences you can set the sansa to automatically switch between the two modes. 

I just had a little bit of an issue with karmic when it was alpha but now it mounts just fine.
I have a Sansa e200, which doesn't have an auto mode (made if I do a firmware upgrade?).

---

### Post by sgosnell on 2009-10-12
You need to do the firmware upgrades regardless of the model, I think.  My Clip wouldn't connect until I did an upgrade, and the latest upgrades for the Clip and Fuze provide a lot of functionality.  IMO any time your mp3 player won't connect, check for a firmware upgrade.

---

