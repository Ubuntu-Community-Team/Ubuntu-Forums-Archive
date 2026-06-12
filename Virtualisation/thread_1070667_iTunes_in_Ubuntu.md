---
title: "iTunes in Ubuntu"
date: 2009-02-15
forum: Virtualisation
---

### Post by woknam66 on 2009-02-15
Ok, first off, please don't give me any alternatives to iTunes, I like it's functionality and I mostly use it to download podcasts. Anyway, I've been looking around online to try to find a way to use iTunes in Ubuntu to sync my iPod with it, and I've mostly found that I need to use iTunes in a virtual machine like Virtualbox, but no guides on how to do this. Are there any?

---

### Post by overlord.gaurav on 2009-02-15
Probably [this]("http://ubuntuforums.org/showthread.php?t=970628") should help you out.

---

### Post by 5BallJuggler on 2009-02-15
You may struggle with this, this is what i did.

Got Virtualbox from the Package Manager.
Installed a Windows Version on it, mine has XP
Load iTunes onto this
then connected to my iTunes folder.

from here on in it should be easy, but this is where my problems started
I could not get Virtualbox to see my iPod due to a problem with the version in the package manager, something to do with the USB functionality.
so i got the latest version from the virtualbox web site, 
at this point i could see the iPod, but if i tried to connect to it, my Ubuntu machine would crash.

spent a couple of days trying to figure out what was going on, then decided to use gtkpod instead, you're right, the functionality is not as good, the interface is pretty poor to be honest, but it does work.

I suppose if it didn't i would have tried harder with the virtualbox method.

---

### Post by woknam66 on 2009-02-17
overlord.gaurav:Thanks, I'll try that.



5BallJuggler:
I can't use an alternative to iTunes because I need iTunes to download podcasts, and I have a iPod touch, so I need iTunes to get software updated for it too.



All:
Actually, I currently have a dual-boot system, so if there any way to virtualize my windows boot inside of my ubuntu boot? Because that would be awesome!

---

### Post by Mercury_Alpha on 2009-02-18
> **woknam66 said:**
> 
All:
Actually, I currently have a dual-boot system, so if there any way to virtualize my windows boot inside of my ubuntu boot? Because that would be awesome!

Well, you can see your current Windows partition from within Ubuntu, allowing you to copy/move your podcasts from the iTunes directory to your Linux partition. But with virtualization, what you're doing is installing an *additional* copy of Windows. This copy will operate from within Linux. [See here]("http://www.virtualbox.org/wiki/Screenshots") for a bunch of screenshots of what that looks like.

Virtualizing another OS can be tricky, but it's worth it if you need that second operating system. A lot handier than dual booting between the two. The thread that overlord.gaurav linked to explains how that all works.

---

### Post by woknam66 on 2009-02-18
Ok, thanks.

---

### Post by woknam66 on 2009-02-19
There was a rumor a while back that Apple might be making a version of iTunes for Linux, has anything ever actually come of this? Did Apple think about it, and then decide not to do it? Or was it always only a rumor?

---

### Post by woknam66 on 2009-02-22
Hello? Anyone?

---

### Post by JK3mp on 2009-02-22
> **woknam66 said:**
> There was a rumor a while back that Apple might be making a version of iTunes for Linux, has anything ever actually come of this? Did Apple think about it, and then decide not to do it? Or was it always only a rumor?
 

I thought i've heard that too but never anything released i don't beleive... maybe by someone who've cracked a version to work on Linux

---

### Post by woknam66 on 2009-02-22
Oh well

---

### Post by woknam66 on 2009-02-23
I'm about to do the thing that overlord.gaurav suggested (I didn't have time this past weekend), but before I do, I just want to make sure, iTunes won't work in Wine, right? Because Wine doesn't have USB support, right?

---

