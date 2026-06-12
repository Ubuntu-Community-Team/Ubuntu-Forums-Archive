---
title: "Run existing XP media cntr ed. from Qemu in Ubuntu 7.10?"
date: 2008-02-13
forum: Virtualisation
---

### Post by tobydeemer on 2008-02-13
Hi all-

I know this is somewhat of a redundant topic, but... anyway. Here's my situation- I want to run my existing XP from Ubuntu in a virtual machine using Qemu. But I've read that you can't really do that because it's on the same physical drive that Ubuntu is also on, therefore they can't run at the same time. 

So is there a way to make an ISO disc of my XP install that I can use to load it into Qemu? That would be the ideal, I think. 

But if that's not possible, I have an XP professional ed install disc, but I don't have a serial # for it. Only have a serial # for Media Center ed. Can I use the XP pro disc with the Med Cent serial # ?

Any help would be greatly appreciated, and again, sorry for a tired-topic post....

-toby

---

### Post by chewearn on 2008-02-14
> **tobydeemer said:**
> Hi all-

I know this is somewhat of a redundant topic, but... anyway. Here's my situation- I want to run my existing XP from Ubuntu in a virtual machine using Qemu. But I've read that you can't really do that because it's on the same physical drive that Ubuntu is also on, therefore they can't run at the same time. 
I read somewhere this is possible using vmware (but I have no personal experience).

> So is there a way to make an ISO disc of my XP install that I can use to load it into Qemu? That would be the ideal, I think. 
There is something call "slipstreaming", which allows you to create a new WinXP installation from your old one, but incorporating all the patches and even some new applications into it.  It will not be exactly the same as your existing installation, but it will be a more updated version than the stock XP disc.

> But if that's not possible, I have an XP professional ed install disc, but I don't have a serial # for it. Only have a serial # for Media Center ed. Can I use the XP pro disc with the Med Cent serial # ?

If your installation disc is genuine, and you still have the product ID sticker, you can call Microsoft for activation after you install it.

---

### Post by tobydeemer on 2008-02-14
Cool. Thanks for the reply. Do you know anymore specifics about slipstreaming? Is there a particular program I need to get to do that?

I did try to load a new installation of the XP disc I have (it is genuine) but when it got all the files copied, I got an error saying "Windows could not start- \WINDOWS\inf\biosinfo.inf is missing or corrupt."

So.... erm... I dunno. 

I did get a live CD of damn small linux to run virtually though. But when I chose to install to HD (into the file that qemu created) and then tried to boot that, it said "Fatal error- non-bootable disc."

Grr.

---

### Post by chewearn on 2008-02-15
> **tobydeemer said:**
> Cool. Thanks for the reply. Do you know anymore specifics about slipstreaming? Is there a particular program I need to get to do that?

I actually has not done this myself, personally; I heard about it from DL.TV.  But it's easy to find out by google; e.g. a link found:
[http://www.helpwithwindows.com/WindowsXP/winxp-sp2-bootcd.html](http://www.helpwithwindows.com/WindowsXP/winxp-sp2-bootcd.html)

> I did try to load a new installation of the XP disc I have (it is genuine) but when it got all the files copied, I got an error saying "Windows could not start- \WINDOWS\inf\biosinfo.inf is missing or corrupt."

So.... erm... I dunno. 

Probably a defective disc; I imagine your disc is at least a few years old?

> I did get a live CD of damn small linux to run virtually though. But when I chose to install to HD (into the file that qemu created) and then tried to boot that, it said "Fatal error- non-bootable disc."

Grr.

Which howto are you following?  I generally have good working results with qemu (I actually use kvm); some links I followed:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
[http://kvm.qumranet.com/kvmwiki/HOWTO](http://kvm.qumranet.com/kvmwiki/HOWTO)
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

---

