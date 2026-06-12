---
title: "Is Unity 8 still very unstable? I would like to try it out."
date: 2016-08-24
forum: Ubuntu, Linux and OS Chat
---

### Post by fromwin2lin on 2016-08-24
Is Unity 8 still very unstable? I would like to try it out.

Thanks,

fromwintolin

---

### Post by grahammechanical on 2016-08-24
It depends on what you mean by unstable. I have unity 8 installed on xenial & yakkety and it is stable. There is the background wallpaper. There is the top panel but without any indicators. The launcher is missing. The Scopes scope window does not have a background. The mouse is stuck centre screen. Yes, I would say that a frozen desktop is stable. 

Best results come with Intel graphics. It still does not work with proprietary video drivers. I have been doing regular updates on both these installs and yesterday I got to a working Unity 8 desktop on one of the machines.

It had detected that the WiFI was active in Unity 7 which it did not do the last time I successfully loaded Unity 8. I could not install any apps. It would not let me activate my Ubuntu One account which is necessary both to install apps and update apps. But I was able to change the desktop wallpaper. Browser loaded but when I tried to resize Browser it froze the desktop. And now when I load Unity 8 it loads to a frozen desktop. Which has been my experience with Unity 8 for many weeks.

I suggest waiting until October. Unity 8 is supposed to be on the 16.10 ISO image. It will not be the default desktop. Unity 7 will still be the default but the 16.10 ISO is supposed to install Unity 8 as an alternative desktop and so do away with the need to install a PPA and unity8 session.

In my opinion Unity 8 is still a long way from being a like for like replacement for Unity 7. It is still very much a phone/tablet UI. We will definitely need Libertine to use the existing deb packaged applications. 

Regards

---

### Post by simonsaysthis on 2016-08-25
Hmmm that's a bit disappointing to hear. This has been in development for so long. I was hoping at least by the time 16.10 gets released Mir would be rock solid.

---

### Post by grahammechanical on 2016-08-25
My post was about Unity 8 session installed onto Ubuntu + Unity 7

During the Wily (15.10) development cycle I installed something called personal_x86.img. That was Snappy Ubuntu Desktop Next. It is also known as Snappy Personal.

It was Snappy Ubuntu core + Mir + Unity 8 and it worked fine. It was being built on Wily code and the transactional updates worked even the rollback feature when a system update did not succeed. It updated daily. Unity 8 worked but again was very limited as to what could be done with it. And there were no applications to install because all the apps in the app store were click apps and not snap apps.

Sadly, development did not continue into the Xenial development cycle. As a proof of concept it succeeded. I do not fault Mir. It ran very well on my Nvidia GT 220 with Nouveau. 

Regards

---

### Post by ventrical on 2016-08-26
> **simonsaysthis said:**
> Hmmm that's a bit disappointing to hear. This has been in development for so long. I was hoping at least by the time 16.10 gets released Mir would be rock solid.

Unity8 is working fairly well but needs a final race down the stretch to mid-October  to be functioning in a way that could be called rock solid.  I have it working both on xenial and yakkety installs.  There have been many fixes to libertine which will allow you  to run debian/classic apps in containers.

Here is an example of one link in Development Version forums you can check out: [https://ubuntuforums.org/showthread.php?t=2332558](https://ubuntuforums.org/showthread.php?t=2332558)

However .. I have found a way to run apps like Firefox as a standalone in Xorg in a TTY so containers are not an absolute if one wants to run a minimal  system.

Regards..

---

### Post by cariboo on 2016-08-26
I'm posting from Unity8 right now, many things don't work, libertine, store and other functions, but so far I haven't run into any problems. I'm even running the web browser app in full screen mode. :). The system I'm running it on is a fairly recent Toshiba laptop with a 4-core atom cpu 4GiB ram and a Bay trail chipset.

**Edit:** Added a couple of screenshots, one of Unity8 running, and the other, the crash notifications I got after logging back into Unity7.

---

### Post by ventrical on 2016-08-29
As I had stated in another thread the libertine crashes are false flags. Even now it will report crashes and offer to 'dismiss' (choose yes) but the debian app is installed and can still be run from the x11-apps app in the scopes window.   What is broken is the instructional development 'set'  in the unity8 graphical user interface but these are more cosmetic bugs which , imo , are serious bugs enough but does not affect the core workings of libertine and x11-apps.

The libertine/x11-apps using lxc containers provides us with a unique desktop experience and I am assuming that this will converge somehow with snap apps - meaning to say that we can run snap apps in containers. (they can be safely updated in each separate container.)

 Another benefit with libertine/x11 is that  each container that we build is uniquely protected yet has share access with the unity8 file system meaning to say that you can run separate  instances of firefox from separate containers. You can also add xterm to each container and each instance of xterm from separate containers is autonomous from the other. So we don't have to use startx in a tty. I think this is a rather enthusiastic concept for desktop convergence which I hope will pan out for the benefits of all.

Regards..

---

### Post by mc4man on 2016-08-29
> **fromwin2lin said:**
> Is Unity 8 still very unstable? I would like to try it out.

Thanks,

fromwintolin
It is absolutely unstable/volatile . There is little to do in it but with what's there some things work, some don't. Some things work one minute but not the next. Some things work for some but not others. Some things work ok, some things work but very poorly.
Doesn't mean you can't try it for a few minutes or so...

---

