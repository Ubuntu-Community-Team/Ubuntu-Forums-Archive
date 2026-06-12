---
title: "Windows 7 Gaming with Ubuntu"
date: 2012-05-02
forum: Virtualisation
---

### Post by lawsofgod on 2012-05-02
So I am a gamer, I understand that VirtualBox (VB) supports 3d acceleration at least experimentally, however my experience has not been very positive. However, this experience has been on my OLD laptop, so I was not overly surprised when it didn't work.

I'm prepping to reload my desktop which is currently W7, its a much more burly machine than my laptop, a Phenome Black 9950, 6Gig ram Geforce 480 and several TB of HDD space. 

What I am trying to decide is how to setup the OS's. On my laptop I currently have ubuntu 12.04 host and XP VB guest running in seamless mode. This works great, I love the shared desktop and the flexibility it provides me. However, if I can't make full use of my Geforce 480 for the VM to play games on then this setup will not work for my desktop. So what I am considering is running windows 7 host with 12.04 as a virtual guest after the reload. Perhaps partition my drives so I can run as parallel drives instead of using a .VHD hard drive. If seamless mode will work with this setup I think it may very well be ideal for my needs. 

I am not a big fan of WINE, I can usually get things to work, but the slow-downs/glitches etc inherent in using such an environment will not satisfy me when it comes to gaming so that is pretty much out.

I was hoping for something more like Parallels for Mac and Windows but AFAIK, Parallels only works for Mac hosts, perhaps I am wrong? If I am wrong will this solution prevent the performance issues I have run into with VB and WINE?
What do you think the best option/config would be?

---

### Post by lukeiamyourfather on 2012-05-02
If you want to game with Windows the best option is to dual boot. While VirtualBox and other virtualization softwares have 3D acceleration they have many caveats and limitations. For example DirectX 10 and DirectX 11 are not supported which many modern games require.

---

### Post by lawsofgod on 2012-05-02
I was hoping to avoid a purely dual boot. There are few things that I do with Ubuntu that require excessive graphics capabilities. I am concerned that running in a virtual environment might cause the Ubuntu side of the system to lag however. Also I am uncertain how running off a parallel drive setup vs a .vhd or associated format.

---

### Post by lukeiamyourfather on 2012-05-03
> **lawsofgod said:**
> I was hoping to avoid a purely dual boot. There are few things that I do with Ubuntu that require excessive graphics capabilities. I am concerned that running in a virtual environment might cause the Ubuntu side of the system to lag however. Also I am uncertain how running off a parallel drive setup vs a .vhd or associated format.

If you dual boot a virtual hard disk is not an option. You'd need to setup two or more partitions or hard disks. The exception would be Wubi but I wouldn't recommend that to anyone other than to try out Ubuntu to see if they like it.

---

### Post by Dedoimedo on 2012-05-03
I would second dual boot here.
Dedoimedo

---

### Post by muteXe on 2012-05-04
> **lawsofgod said:**
> So I am a gamer, 

to me that screams dual-boot as well.

---

### Post by lawsofgod on 2012-05-05
Well I will do some experimenting and let you guys know how it goes when I finish. The first thing I'm going to try is two partitions windows and Ubuntu, I will install Windows on one partition then use virtual box and parallel hard drive mode to put Ubuntu on the other. We will find out if seamless mod works well enough to satisfy me.

---

