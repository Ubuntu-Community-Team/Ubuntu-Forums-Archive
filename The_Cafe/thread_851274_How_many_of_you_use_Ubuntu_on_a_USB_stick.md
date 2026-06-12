---
title: "How many of you use Ubuntu on a USB stick?"
date: 2008-07-06
forum: The Cafe
---

### Post by kernelhaxor on 2008-07-06
I mean to ask how many of you have Ubuntu installed on a USB drive and boot from it and use it.  
Would you like to buy one? I was thinking of opening an online store and selling flash drives with Ubuntu installed on it.  But not sure if there's sufficient demand for it.

---

### Post by smartboyathome on 2008-07-06
I, for some reason, can't get any distros to boot off of my 8GB usb stick, though it could have something to do with me trying to make the actual partition the OS is trying to boot off of the second one, so I could use the first partition with Windows.

---

### Post by RATM_Owns on 2008-07-06
I wish I had a big enough USB to.

---

### Post by spamzilla on 2008-07-06
> **smartboyathome said:**
> I, for some reason, can't get any distros to boot off of my 8GB usb stick, though it could have something to do with me trying to make the actual partition the OS is trying to boot off of the second one, so I could use the first partition with Windows.

I'm not sure if this is correct, but I instantly thought that only 1gb memory sticks are bootable.

---

### Post by wrtpeeps on 2008-07-06
> **spamzilla said:**
> I'm not sure if this is correct, but I instantly thought that only 1gb memory sticks are bootable.

I think you can boot any, as long as your pc supports booting from USB. :confused:

---

### Post by smartboyathome on 2008-07-06
My PC does support booting from USB, it boots from my external USB drive fine. Though maybe not live-based USB sticks. :(

---

### Post by agurk on 2008-07-06
It's in the pipes for Intrepid: [https://wiki.ubuntu.com/USBInstallationImages](https://wiki.ubuntu.com/USBInstallationImages)

---

### Post by Lord Xeb on 2008-07-06
I have Ubuntu on a stick, but I haven't really used it...

---

### Post by red_team316 on 2008-07-06
Awesome, there's always at least one thing that really excites me about the new version :) This has to be one of them. NTFS by default was my gem with Hardy.

---

### Post by lukjad on 2008-07-06
> **kernelhaxor said:**
> I mean to ask how many of you have Ubuntu installed on a USB drive and boot from it and use it.  
Would you like to buy one? I was thinking of opening an online store and selling flash drives with Ubuntu installed on it.  But not sure if there's sufficient demand for it.
Not I. And you would have to convince me that it was as fast or almost as fast as an install. I see no reason that I wouldn't want one, except this. If I am into Linux in a big enough way and I can get Ubuntu for $0 and a USB for $10, why would I go to you? If I am not into Linux, will I want to go to some guy and buy his magical USB sticks that make Windows all weird? Will I even know how to change the BIOS to boot USB drive? Will I have the courage? Will I know that it has to be booted and not just popped into the drive after Windows is there? You need a hook, an edge. If you could include a glossy book of instructions, detailing what to do, how to set it up, what is a repository (is that like a suppository?), etc. that would get my attention. I would buy a few for my friends so that they could try it out on there own. You could offer to have different looks, even create a custom look. Or just let them choose the look they like. If you plan to go down this route, may I suggest Scribus for the type setting and GIMP for the image processing? 
These are a few things to think about and this is only my opinion, ask others first, but, here's hopin'!

---

### Post by az on 2008-07-07
> **smartboyathome said:**
> I, for some reason, can't get any distros to boot off of my 8GB usb stick, though it could have something to do with me trying to make the actual partition the OS is trying to boot off of the second one, so I could use the first partition with Windows.

If you don't even have a partition table on your device but it only contains one partition, it should boot fine, so long as the filesystem on it is bootable (for example, has syslinux installed on it).

That's not your case.  If you do have a partition table and want to boot off it, you need an MBR on your device. 

sudo apt-get install mbr

sudo mbr-install /dev/sdX # Pick the correct device!

You need to flag the partition as bootable.  If no partition is bootable, the first one found will be used.  If you want to keep your first partition free so that it is seen in Windows, you can make the second partition bootable and use that for your live system.

See here for gory details:
[http://ubuntu-rescue-remix.org/node/21](http://ubuntu-rescue-remix.org/node/21)

---

### Post by KingTermite on 2008-07-07
I have one, though honestly rarely use it. I think its a great idea, though wouldn't likely pay for it unless it were roughly the same price as the thumb drive in the first place. That's more the geek motto though...wouldn't pay more for it when I can easily do it myself.

---

### Post by amar on 2008-07-07
I use USB because I was running out of CDs and thought it was a waste. also my new laptop doesn't have an optical drive. It would be nice if there was an offical way to make your live USB.

---

