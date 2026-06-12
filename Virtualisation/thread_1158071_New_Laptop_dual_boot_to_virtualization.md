---
title: "New Laptop dual boot to virtualization"
date: 2009-05-13
forum: Virtualisation
---

### Post by kpgalligan on 2009-05-13
Sorry if you've seen this question or its equivalent 1000 times.  I've found pieces of answers, but I'm guessing there are some definitive solutions, or close to it, and the stuff I've found didn't seem very clear.

I have a (relatively) new laptop.  It came with Vista.  I shrank that partition and installed ubuntu.  Ubuntu is my main OS, but I occasionally boot up windows for various things.

I'd like to boot up windows while still in Ubuntu.  Here are the various options that I've found.

- VMWare Converter.  Make a new VM, and use that.  This option seems like it would be my best, but it seems like there may be hardware/licensing issues.  I'm not too concerned about the legality, as it seems to me like more of a technicality than a real breach of the terms, and, you know, nobody's going to bother coming after me.  However, I imagine there might be issues with the license key and whatnot.  If not, this option would be fine.

- VMWare to native partition.  I'm not sure this is possible, and it seems like there would be plenty of issues even if it was.

- VMWare, install from backup disk.  I'm guessing this won't work, as most machines don't ship with a full version Vista disk (I'm not sure about mine.  HP pavilion dv5t, bought 5 months ago).

- VirtualBox to native windows partition.  Also full of issues, but there appears to be a page documenting it, so I'd guess after a bunch of wrestling, it would work.

- virtualBox with new install from backup disk (same issue as above).

The "easy" option would be to buy a new copy of Vista, but I don't need it that badly, and that would go against all of my principles.

What do most people do with a new laptop?

Thanks in advance.

---

### Post by uupreti on 2009-05-13
I have Hp pavilion laptop shipped with Windows vista. I shrank partition and separate 10 GB to install **Ubuntu 9.04**. Then I installed **vmware server 2.0.1** version and install windows xp as a guest OS under ubuntu. Everything is smooth like butter. Now with new vmware server 2.0.1, I can browse my OS from internet. Wow, that's great to browse your desktop over internet. No need of remote desktop or real vnc or no nothing. 

I'm loving ubuntu 9.04..

---

### Post by kpgalligan on 2009-05-13
Does that mean you had a copy of Windows XP available?  If possibly, I'd like to use what's already on the machine.  Installing a new OS might be OK, but I need to get a copy.

---

### Post by coolen on 2009-05-13
One of my friends works in a computer store. He says when someone wants to buy a replacement copy of Windows XP, they just hand them one for free.

As I understand it, when you bought the laptop, you bought a license. That product key on the bottom is your right to use Vista.

So, if you get your hands on a CD (of the same version, no sneaky upgrades) I think you can just type in your product key and it will work.

I think.

---

### Post by uupreti on 2009-05-13
> **kpgalligan said:**
> Does that mean you had a copy of Windows XP available?  If possibly, I'd like to use what's already on the machine.  Installing a new OS might be OK, but I need to get a copy.


Or you can make a copy of windows xp from your existing OS. They might have something called recovery manager from which you can make copy of your OS. As long as you don't care piracy, you can also download and use cracked Serial key if you want.. But without having any copy in disc, installing windows under ubuntu seems not possible I think..

---

### Post by Pnuts on 2009-05-13
The version of the OS that comes with your laptop is the OEM version. The other 2 types are Retail and Volume. Retail is purchasing the OS seperate, like in a box at Walmart, and volume is for corperations to purchase multiple copies and use a single key that works on all of them.

With Windows XP (Home or Pro) OEM version, Microsoft allows you to move that license from one PC to another so long as it is only installed on a single computer at a time.

With Windows Vista, MS changed the policy so that the OEM version is not transferable. It must remain on the original PC it was installed on.

In your case, you would still be installing Vista on the same machine, thus not violating your license, so long as the original installation is removed.

There should be a sticker of some sorts with your license key on the computer itself or with the documents that came with it. This key is a valid Vista key. If you can get ahold of a Vista installation disk, you can use that to install and it will accept your key.

After so long Vista will tell you the key is not valid even though it is. It will ask for a new key, or you have the option to call MS to activate it over the phone. The call is toll free and takes from 3-10 minutes. You will have to speak with someone, they will ask questions like is it installed on any other PC, etc. Answer truthfully and they will give you a code to activate it.

Any Vista disk will work as MS only released a single disk with all versions on it, the key you enter will determine what gets installed for the different versions. Ex: Home, Business, Ultimate, etc.

-Pnuts

---

### Post by animelov on 2009-05-13
One other point that I think the op tried to make (or in any case, I'm making now :) ).

I've just moved to Ubuntu after getting an extremely nasty virus on Windows.  I love Ubuntu, but obviously there are some things that just will not work or I haven't researched enough to make work (My Zune, for example).  I'm also a gamer, and I just don't think wine can hack what I want.  And finally, for a final bit of background information, I have a pair of 120gb hard drives to do this job (and licensing is not an issue).

Here's my question given the background above, can I dual boot Ubuntu/<flavor of Windows> and use the SAME instance of Windows as a VM.  In other words, I have two options

1)  Stripe the two hard drives and make ONE Windows OS.  This single OS is bootable via both VMWare and straight dual-boot
2)  Make two OSs, one for VMs (utilities for various devices not supported by Linux), another for straight booting (gaming).

Is option one possible, or do I need to go to option two?

And yes, I understand the risks of striping and not making a mirror, it's not my primary OS, remember? :D

---

### Post by Pnuts on 2009-05-14
I think I understand but to clarify

option 1: Dual boot Ubuntu and Windows on seperate partitions(assuming raid 0). While in Ubuntu, boot the windows partition as a VM? This is legal and does not violate licensing for windows. you will run into issues with the vm image and drivers though. you should probably research this before trying it or try it on a system on which you do not care about the data on.

option 2: Dual boot Ubuntu and Windows, while in Ubuntu have a VM with windows loaded on it. This violates the windows license agreement unless you have Vista Business, Vista Enterprise, Vista Ultimate. If you have either of these 3, you are allowed to run up to 4 VM's on the machine the license is assigned to. It is not allowed with XP.

-Pnuts

---

### Post by animelov on 2009-05-14
Does it violate the agreement if there are two separate XP licenses?  Like I said before, licensing is not an issue, I have unused licenses

In any case, I did think of the driver issue, and hoped it wouldn't be too much of an issue, but didn't know for sure.  I'll give it a shot a will post the results.

Next question, do I install Windows first, then convert to VM, or vice versa?

---

### Post by Pnuts on 2009-05-14
If you have multiple XP licenses, you should be fine. Just follow the 1 license per 1 installation and your good.

Im not sure exactly what order you should go in, but I think creating a VM and then trying to boot it normally might be easier to troubleshoot later as you know what drivers to find for your hardware. That might not be the case in the VM instance. In the end, either way you go, I think you will run into the same problems.

---

