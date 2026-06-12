---
title: "The end?"
date: 2008-03-16
forum: Testimonials &amp; Experiences
---

### Post by Jay Jay on 2008-03-16
Wasn't sure if this belongs in General help or Testimonials & Experiences as it covers both categories. 

This is my story...

I started off with 5.10 and at first the learning curve sent me running back to Windows, but my time, perserverance and persistence paid off and I made the transition from being a daunted novice to a fairly confident Ubuntu user. For the most part the Ubuntu distros have put the fun back into computing for me and there's definitely more power and scope on offer than anything the people at Redmond ever delivered. :) However as I began to make heavy usage of my laptop,[ hardware problems]("http://ubuntuforums.org/showthread.php?t=721000") emerged. 

As It stands now, for my [video issues]("http://ubuntuforums.org/showthread.php?t=713168") alone I have gone through at least 7 different forums (two of which were specialist ATI boards and no-one replied), searched online at length for clues and leads and experimented with trial and error in the hope I'd succeed. I tried Knoppix and Fedora but encountered the same problems that plague me in Ubuntu. It was suggested to me that Solaris might be worth checking out, but the hardware support is even worse. From these experiences I'm seriously doubting if my machine will ever work properly outside of the Windows realm.

Right now I've had to fall back onto my Win2K partition for wireless connectivity and decent graphics performance, which is really demoralising. Where do I go from here? Returning to Windows would be a last resort and a waste of all my efforts in switching to open source.

---

### Post by freebios on 2008-03-16
hardy heron will be released next month the live dvd is supposed to have excellent hardware support and more linux drivers because it is a LTS release.  you can give it a shot.  I hope it solves your problems.

---

### Post by jrusso2 on 2008-03-16
Some of the best Linux hardware support I have seen was in the Mandriva 2008 one cd.

---

### Post by 3rdalbum on 2008-03-17
ATI? Say no more. ATI has always had bad drivers. Rather than admit "Okay, I don't understand how to write drivers that don't make the kernel and Xorg flaky", ATI (and Nvidia, to a lesser extent) write their own that cause terrible troubles. Unfortunately these are closed-source, so Ubuntu and the kernel developers can't do much.

---

### Post by Jay Jay on 2008-03-17
Thanks for the feedback. I have a few questions, the first is that given the predicament with ATI and their Linux driver support - should I wait for the release of Hardy Heron, as freebios recommended or is  the situation unlikely to change for the foreseeable future?

---

### Post by 3rdalbum on 2008-03-18
> **Jay Jay said:**
> Thanks for the feedback. I have a few questions, the first is that given the predicament with ATI and their Linux driver support - should I wait for the release of Hardy Heron, as freebios recommended or is  the situation unlikely to change for the foreseeable future?

I can't see the ATI code, so I don't know if the drivers will work better with Ubuntu 8.04. But give it a try.

---

### Post by rustybronco on 2008-03-18
> **freebios said:**
> hardy heron will be released next month the live dvd is supposed to have excellent hardware support and more linux drivers because it is a LTS release.  you can give it a shot.  I hope it solves your problems.it wouldn't hurt to try it as a live cd, possibly dual boot it?

> **jrusso2 said:**
> Some of the best Linux hardware support I have seen was in the Mandriva 2008 one cd.the only distro  that I could get my radeon 7000ve working ootb with a wide screen was 
mandriva.

> **Jay Jay said:**
> Thanks for the feedback. I have a few questions, the first is that given the predicament with ATI and their Linux driver support - should I wait for the release of Hardy Heron, as freebios recommended or is  the situation unlikely to change for the foreseeable future?again what will it hurt to try it now (which I would not normally recommend doing). for the most part it's stable and I use it day to day.

---

### Post by Jay Jay on 2008-03-19
Ok, I'll download the ISO and see how things work out, on a side note I checked out the Mandriva site and my rig is well below the minimum CPU requirement of 1Ghz - ah well...

A question regarding the 8.04 DVD - my laptop doesn't have a built in CD/DVD drive, however I do have an external USB DVD/RW. Would it be possible for me to install 8.04 from a DOS boot floppy containing USB drivers, or is there another way?

I'm open to suggestion :)

---

### Post by freebeer on 2008-03-19
Does your BIOS support booting from a USB device?  If it does, then that's the way to go, I would think.

---

### Post by Jay Jay on 2008-03-19
No, unfortunately there is no provision in the BIOS to boot from USB, nor is an update available to add that option. Any other ways I could do this? What would be ideal is if I could start the Installation from within either Ubuntu or Windows 2000 where my DVD/RW drive can be seen...

---

### Post by freebeer on 2008-03-19
Bummer.

How about a network install?  Is that a viable option?  I don't know what involved with a network install, but I know that it's doable.

---

### Post by Jay Jay on 2008-03-20
An excellent idea - [two machines, a crossover cable and some settings on the server box]("http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows") but I've found an even easier way. You mount the ISO from within Ubuntu, copy over a couple of files, edit Grub and then the DVD can be installed - without the need for a CD/DVD drive or a 2nd machine as a server for the network installation :)

Here's the best two guides I came across, one for [Fedora]("http://bobpeers.com/linux/hard_drive_install.php") (which I imagine could be adapted easily to work with other distros) and another for [Ubuntu]("https://help.ubuntu.com/community/Installation/FromLinux").

---

