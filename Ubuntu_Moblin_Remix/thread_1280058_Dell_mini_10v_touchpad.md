---
title: "Dell mini 10v touchpad"
date: 2009-10-01
forum: Ubuntu Moblin Remix
---

### Post by jeromek on 2009-10-01
Hi all,

I've put the ubuntu moblin developer remix on my mini 10v, and (almost) everything is working very nicely. I'm having major problems with the touchpad though. The touchpad is extremely annoying, as the cursor keeps jumping when you try to click on the button.

This is a well known problem with the mini 10v, and seems to have been solved for 9.04 in general. However, I can't seem to get it to work on the moblin remix. Has anyone else had this problem? Better yet, has anyone solved this problem?

For reference, I've tried the following walk through:

[http://ubuntuforums.org/showthread.php?t=1270382](http://ubuntuforums.org/showthread.php?t=1270382)

Enabling the ppa doesn't seem to make any difference: apt-get seems to be convinced it already has the most recent version.

I've also tried disabling the bottom quarter of the touchpad, to no avail:

[http://ubuntuforums.org/showthread.php?p=7990445](http://ubuntuforums.org/showthread.php?p=7990445)

Any help appreciated!

---

### Post by benny215 on 2009-10-02
I'm suffering from the same problem. The thing is pretty much unusable without an external mouse because that touch pad gets so frustrating. If you figure something out please let me know.

---

### Post by bfiller on 2009-10-05
Are you running Karmic Ubuntu Moblin Remix (from cdimages.ubuntu.com/ubuntu-karmic-remix) or Dell's Jaunty based Moblin image from Dell's website? The Dell version should already have the touchpad fixes. If you are running the karmic version you'll need to install a patched **xserver-xorg-input-synaptics **I can provide for you that hasn't made it's way into Karmic yet.

---

### Post by jeromek on 2009-10-05
I'm running the Dell version of Jaunty. I think you're right and the patches have been applied, but the touchpad is still pretty cruddy. I downloaded the source for xserver-xorg-input-synaptics with apt-get, built the .deb package and got

xserver-xorg-input-synaptics_0.99.3-2ubuntu5_i386.deb

I intended to apply Alberto's patches to the source but it seems that they have been applied already from what I can tell. Maybe the setup I have is a massive improvement over the unpatched driver; it's still pretty bad though.

Are there any disadvantages to mobving over to the karmic version? I.e., will I have to spend ages getting other bits of hardware working?

Thanks for the help!

---

### Post by linuxcentre on 2009-10-18
I did some work on getting this right for Karmic. The parameter names in the synaptic driver changed from the Jaunty ppa version when it got released in Karmic. See this page on the tweaks I used to get it really quite usable: [http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook](http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook)

---

### Post by bfiller on 2009-10-18
Alberto recently made some touchpad fixes for the 10v in karmic which he backported to jaunty (xserver-xorg-input-synaptic_1.1.2-1ubuntu7~karmic1), which should help alot. I uploaded his jaunty backport to the moblin ppa:

[https://edge.launchpad.net/~moblin/+archive/ppa](https://edge.launchpad.net/~moblin/+archive/ppa)

You should be able to install it from this ppa once it's finished building. Also I've found it helps a lot if you go to the Applications->Settings->Mouse and on the "touchpad" tab select "Enable mouse clicks with touchpad". This makes is much easier to click without having to tap the lower buttons. Hope this helps.

---

### Post by jeromek on 2009-10-19
Yes! This is big, big improvement! Thanks very much for the help, much appreciated.

There was one weird thing, though. When I installed the packages from bfiller's ppa, I restarted the x server, and things were immediately much better. When I rebooted, however, the trackpad didn't work at all, I had to use the mouse to get the pointer moving. I reverted the package with 

```
sudo apt-get install xserver-xorg-input-synaptics=0.99.3-2ubuntu5
```which got the mouse pad working again, albeit in it's immensely irritating mode. In the interest of sending a decent bug report I installed the version from the ppa again, but it worked fine this time. After several reboots, it still seems to work. Weird. Anyway, I'm delighted to be able to use my 10v with moblin without going mad, so cheers!

Thanks too to linuxcentre, I was trying to figure out how to get the shm config working, your wiki is a handy resource.

---

### Post by Tweeks_tx on 2009-10-29
So has anyone had problems with the Dell mini 10v's left-right click (for pasting)?

This seems mechanically impossible.. or in the very least difficult from what I've seen.

Tweeks

---

### Post by safi78 on 2009-11-11
> **linuxcentre said:**
> I did some work on getting this right for Karmic. The parameter names in the synaptic driver changed from the Jaunty ppa version when it got released in Karmic. See this page on the tweaks I used to get it really quite usable: [http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook](http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook)
Just to let you know, this worked perfectly for me!

Many thanks :)

---

