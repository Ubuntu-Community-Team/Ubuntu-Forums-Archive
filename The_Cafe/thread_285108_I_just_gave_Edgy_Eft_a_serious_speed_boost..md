---
title: "I just gave Edgy Eft a *serious* speed boost."
date: 2006-10-26
forum: The Cafe
---

### Post by Old Pink on 2006-10-26
OK, Edgy Eft comes with the 2.6.17 kernel, but 2.6.18.1 is already available. 

I thought hey, I've got nothing to loose and decided to compile my own kernel and upgrade. Not only did it shave 15 seconds from my boot time, it's made my entire system considerably faster. Oh, and my WiFi doesn't cut out every hour or so. :D 

Great stuff! 

If you've got the knowledge and the time, I seriously reccomend updating. :) 

- Matt

---

### Post by IYY on 2006-10-26
What are the disadvantages to updating to this kernel? Is it buggier? Will some software not work/have to be recompiled?

---

### Post by maniacmusician on 2006-10-26
I could attempt it, but it would be at risk of screwing up my system (havn't done it before). any idea when it will be released as an update? or will it not? we've gotten kernel upgrades before..

---

### Post by Old Pink on 2006-10-26
> **IYY said:**
> What are the disadvantages to updating to this kernel? Is it buggier? Will some software not work/have to be recompiled?

Everything seems to work fine for me, and I do have alot of applications.

_**Full changelogs:**_
**2.6.17 to 2.6.18: **[http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18](http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18)
**2.6.18 to 2.6.18.1:** [http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18.1](http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18.1)

> **maniacmusician said:**
> I could attempt it, but it would be at risk of screwing up my system (havn't done it before). any idea when it will be released as an update? or will it not? we've gotten kernel upgrades before..

I understand in Dapper there was a kernel update, and then in Dapper to Edgy there was a kernel update, but I have no idea if they plan to put any future updates into the repositories. :-k

I just thought "Why wait for them to give me it, when I can reach out and grab it myself?" ;)

---

### Post by hk_2999 on 2006-10-26
is it available already in the repos? i havent noticed.

---

### Post by Old Pink on 2006-10-26
> **hk_2999 said:**
> is it available already in the repos? i havent noticed.

No.... nobody said that? :confused:

---

### Post by PriceChild on 2006-10-26
This kernel was selected for edgy for a reason... many reasons infact.

Just because there's a higher verison number doesn't make it better in every aspect.

Distros are encouraged to pick a kernel for them and customise it completely to be perfect for them.

---

### Post by Old Pink on 2006-10-26
> **PriceChild said:**
> This kernel was selected for edgy for a reason... many reasons infact.

Just because there's a higher verison number doesn't make it better in every aspect.


I know, I understand all the negatives everyones talking about, but I just *had *to try the latest version, and can't see any reason for turning back. 

If a major reason crops up, it's so easy to just boot into the default Edgy kernel, I have absolutley nothing to lose, and without trying it I didn't know what I had to gain, so you see... no loss & possible gain = a must try for Old Pink. ;)

---

### Post by Xceptiona1 on 2006-10-26
How involved is it to update a kernel in Ubuntu? If you know a good walk-thru let me know. Thank you

---

### Post by Old Pink on 2006-10-26
> **Xceptiona1 said:**
> How involved is it to update a kernel in Ubuntu? If you know a good walk-thru let me know. Thank you

Just use this link and change all instances of "2.6.18" to "2.6.18.1"

[http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.18](http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.18)

---

### Post by Brunellus on 2006-10-26
In fact, I mused on this 'beta fever' on [my blog](http://ouij.livejournal.com/182853.html)

---

### Post by japurcell on 2006-10-26
I just upgraded my kernel to 2.6.18 and some settings didn't carry over from my old kernel config.  Make sure you enable **IP tables** if you use firestarter, and also **VFAT filesystem **if you use an iPod.  Those were the only problems I had besides installing the new nvidia driver and losing the usplash.  The driver from thier site worked ok, but I can't get the usplash back.

Other than that, boot time and file access is a little faster.

---

### Post by Old Pink on 2006-10-26
> **japurcell said:**
> I just upgraded my kernel to 2.6.18 and some settings didn't carry over from my old kernel config.  Make sure you enable **IP tables** if you use firestarter, and also **VFAT filesystem **if you use an iPod.  Those were the only problems I had besides installing the new nvidia driver and losing the usplash.  The driver from thier site worked ok, but I can't get the usplash back.

Other than that, boot time and file access is a little faster.

usplash and iPod support stayed strong for me... didn't you import your old config file before compiling? :(

---

### Post by japurcell on 2006-10-26
Yea, I did this: 
sudo cp /boot/config-`uname -r` .config && sudo make xconfig

---

### Post by Old Pink on 2006-10-26
Strange... mine works perfectly fine. :D 

Which error do you get?

---

### Post by japurcell on 2006-10-26
When I dmesg, it couldn't locate the right character set to read the ipod.  It was working perfectly fine before I upgraded my kernel.  When I looked at my config, I realized VFAT wasn't enabled.  I'm gonna recompile when I get home.

---

### Post by chaosgeisterchen on 2006-10-26
Is there any HowTo for upgrading the Kernel to 2.6.18.1 ?

---

### Post by japurcell on 2006-10-26
I would go with this one [http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.18]("http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.18"). Should be the same for the most part.

---

### Post by Old Pink on 2006-10-26
> **japurcell said:**
> I would go with this one [http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.18](http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.18). Should be the same for the most part.

Just change every instance of "2.6.18" to "2.6.18.1" :)

---

### Post by chaosgeisterchen on 2006-10-26
> **japurcell said:**
> I would go with this one [http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.18]("http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.18"). Should be the same for the most part.

Thank you very much - the both of you :)

---

### Post by David Corrales on 2006-10-29
> **japurcell said:**
> I just upgraded my kernel to 2.6.18 and some settings didn't carry over from my old kernel config.  Make sure you enable **IP tables** if you use firestarter, and also **VFAT filesystem **if you use an iPod.  Those were the only problems I had besides installing the new nvidia driver and losing the usplash.  The driver from thier site worked ok, but I can't get the usplash back.

Other than that, boot time and file access is a little faster.

To get the usplash back do the following:
1) Edit the file /etc/mkinitramfs/modules and add:
capability
vesafb
fbcon
unix

2) Reconfigure the kernel: **sudo dpkg-reconfigure kernel-image-<version>**

By the way, I read this on another post so the credit's not mine lol.

---

### Post by mips on 2006-10-29
Some other things you can do for speed are:
prelink
preload
hdparm
profile

> **Old Pink said:**
> OK, Edgy Eft comes with the 2.6.17 kernel, but 2.6.18.1 is already available. 

I thought hey, I've got nothing to loose and decided to compile my own kernel and upgrade. Not only did it shave 15 seconds from my boot time, it's made my entire system considerably faster. Oh, and my WiFi doesn't cut out every hour or so. :D 

Great stuff! 

If you've got the knowledge and the time, I seriously reccomend updating. :) 

- Matt

---

### Post by shining on 2006-10-29
> **japurcell said:**
> Yea, I did this: 
sudo cp /boot/config-`uname -r` .config && sudo make xconfig

Maybe you could have tried oldconfig before xconfig. (I'm not sure this would change anything)

---

### Post by d3v1ant_0n3 on 2006-10-30
I compiled 2.6.18, an noticed a marginal speed boost(~4 secs on boot), but for some reason, mp3 playback in Amarok was very sketchy- tracks would hang every few seconds. 

Compiled 2.6.18.1, and I get a similar thing.

Gone back to 2.6.17

I don't really need those 4 seconds.

---

### Post by ~LoKe on 2006-10-30
I'll give it a shot because I love breakage.

---

### Post by kuja on 2006-10-30
> **maniacmusician said:**
> I could attempt it, but it would be at risk of screwing up my system (havn't done it before). any idea when it will be released as an update? or will it not? we've gotten kernel upgrades before..
More than likely not. We don't tend to get kernel upgrades except for the occasional security patch.

---

### Post by kuja on 2006-10-30
> **mips said:**
> Some other things you can do for speed are:
prelink
preload
hdparm
profile
Care to give some details? I'm familiar with prelinking giving a speed boost and use it on my brothers older, slower computer, and profiling gives a great start-up time boost, but what about preloading and hdparm (unless you're just talking about turning dma on)?

---

### Post by ~LoKe on 2006-10-30
Worked for me.  Thanks for the tip. ;)

---

