---
title: "Virtualization of MS Office"
date: 2008-11-11
forum: Virtualisation
---

### Post by io5150 on 2008-11-11
Hello,

I have a couple of questions concerning virtualization.

First my system specs
IBM T30 - 1.6 MHz, 512 MB RAM, DVD, 40 GB hd
Dual Boot
   XP Pro 15 GB partition
   Ubuntu 8.10
     / = 7.4 GB
     /swap = 1 GB
     /home = 14 GB

Given my system specs, what is the best way to run MSO 2003 (Word, Excel, & Powerpoint) under Linux?  VMWare, VirtualBox, or WINE?  Is it possible to virtualize my XP partition under Linux - to save on disk space creating the virtual images?  

I am also wanting to run Quicken and DreamWeaver 4 under Ubuntu as well.

I am not a noob to PCs, but am total noob to virtualization.

Someone point me in the right direction.

Thanks,
David

---

### Post by 9999999999 on 2008-11-11
I use virtualBox and I really like it. I don't have any advice regarding performance because I've never used vmware or wine so I have nothing to compare to. 

I do know that it is possible to use virtualBox to run an Xp partition using the raw disk feature of virtualBox. The problem is that you most likely have to start with a fresh install of xp, I don't know how to do it with an existing setup. You can find a tutorial on the virtualBox support forums.

---

### Post by io5150 on 2008-11-12
Thanks,

I, as usual, jumped ahead of myself.  I didn't see the sticky at the top of the channel.  A lot of good info there.

I have seen linux desktop screen captures that have shortcuts to Word, IE, etc.  How are they setup?  Are the links launching the app in a VM (I am assuming so... MSO is not native to Linux)?  If so, how it that set up?  

I am working through setting up VirtualBox VM following the instructions in the sticky.

Thanks again,
David

---

### Post by killer_d76 on 2008-11-12
i have created a "How to" thread on installing MS Office 2007 using the latest wine here's the link 

> [http://ubuntuforums.org/showthread.php?t=922963](http://ubuntuforums.org/showthread.php?t=922963)

and this works well on 8.04 (Hardy).. haven't tried it on 8.10

right now **codeweaver** does the job for me of the same performance!.

---

### Post by shadanan on 2008-11-12
I have used both VirtualBox and VMWare. While both are free as in beer, VirtualBox has an open source community edition. More importantly, VirtualBox is available in the standard ubuntu repoistory. 

VMWare is a bit more polished than virtual box. For instance, sound in VMWare can be switched between linux and the virutal machine on the fly. In VirtualBox, you will have to shutdown the virtual machine in order to attach / detach the sound card.

Also, bridged networking in VMWare is automatically configured for you during installation. In VirtualBox, this has to be done manually.

On the other hand, VirtualBox's startup and shutdown time is incredibly fast. All in all, I prefer VirtualBox. It feels cleaner in the sense that it doesn't change your network settings by adding new interfaces and so on. It gives me more control and I really like the startup and shutdown time.

As for an icon, I don't think it is possible to create an Ubuntu desktop icon to Word that will launch the application in the virtual machine. You will likely have to do it from within VirtualBox. VirtualBox does however have a "seamless mode", but I have not had any success getting it to work.

Wine is another option, but I find that Windows apps don't work the way I expect them to in Wine. Your mileage may vary.

---

### Post by killer_d76 on 2008-11-13
> VMWare is a bit more polished than virtual box. For instance, sound in VMWare can be switched between linux and the virutal machine on the fly. In VirtualBox, you will have to shutdown the virtual machine in order to attach / detach the sound card.


got the latest VBox (PUEL) as well and seems to be working pretty fine.. with regard to sound, it works with Ubuntu at the same time now!..

---

