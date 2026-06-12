---
title: "Ubuntu on Virtualbox bad performance"
date: 2015-05-20
forum: Virtualisation
---

### Post by cwblanch on 2015-05-20
Hey,

I have Ubuntu 14.04 installed in Virtualbox and the performance is just awful! I've raised the RAM the virtualbox can use, and the number of cores. But that's about all the basic stuff I've found through Google searching.

I'm not really experienced in using Virtual Machines so any tips for improving performance would be awesome.

Thanks!

---

### Post by ajgreeny on 2015-05-20
Raised the RAM to how much, and leaving how much for the host, as both need plenty of RAM to run properly?

On my Intel i5-3570K, 8GB RAM, Intel HD4000 IGU, I have Ubuntu 15.04 and the as yet unreleased 15.10 running on VBox, both 64bit, and both I have set to use 4GB ram (half my hosts total RAM), use all 4 cores of CPU, and have the maximum graphic memory of 128MB.  They both work fine and fast, and I can see no difference in their speed of performance compared with a real hardware installation.

Some people say that the unity desktop runs very badly in VBox but that has not been my experience, so I can not give you any further clues.

---

### Post by bapoumba on 2015-05-20
ajgreeny +1. I gave 2GB ram (out of 8) and 128MB video and use only one for the 4 cores. I am yet to install ubuntu 15.10, but ubuntu-mate 15.10 runs flawlessly here.
I did not think of the video on my very first install (an early 15.04), and even ubuntu-mate was barely usable. I do not recall how low it was, but is was very low by default. Going to the max 128MB made a real difference.

---

### Post by cwblanch on 2015-05-21
> **ajgreeny said:**
> Raised the RAM to how much, and leaving how much for the host, as both need plenty of RAM to run properly?

On my Intel i5-3570K, 8GB RAM, Intel HD4000 IGU, I have Ubuntu 15.04 and the as yet unreleased 15.10 running on VBox, both 64bit, and both I have set to use 4GB ram (half my hosts total RAM), use all 4 cores of CPU, and have the maximum graphic memory of 128MB.  They both work fine and fast, and I can see no difference in their speed of performance compared with a real hardware installation.

Some people say that the unity desktop runs very badly in VBox but that has not been my experience, so I can not give you any further clues.

I have an AMD A6 APU @ 2.7GHz with 4GB of ram
I've given the VBox 2 of 4GB of ram, 2 of 4 processors and 32MB of video memory, I don't think I've changed the video memory yet.
I'm not on the best computer, but I've left everything as default and had better performance on a worse laptop before so I'm not sure why its running so badly.

Should I increase the video memory for Unity?
I could try a Ubuntu MATE install to compare.

---

### Post by v3.xx on 2015-05-21
Do you have 3D acceleration enabled in vBox?  Its under Settings>display>video.  

Could there be a bios setting?

I do not run Unity, but I would say 3D needs the video ram.

---

### Post by SeijiSensei on 2015-05-22
Set the video memory to the maximum available, 128M or 256M depending on your configuration.  I always choose the maximum video memory since 128-256M is usually a small proportion of the total memory available.  On a 2 GB machine, 128M for video still leaves 1,920M for everything else.

Make sure you have swap, too. Run "top" in a terminal to see how much there is, and how much is in use.

---

### Post by ajgreeny on 2015-05-22
Make sute that you have the VBox guest additions installed as well; I am not sure if it will help with this specific problem but it is really necessary to make full use of VMs.

---

### Post by cwblanch on 2015-05-22
> **SeijiSensei said:**
> Set the video memory to the maximum available, 128M or 256M depending on your configuration.  I always choose the maximum video memory since 128-256M is usually a small proportion of the total memory available.  On a 2 GB machine, 128M for video still leaves 1,920M for everything else.

Make sure you have swap, too. Run "top" in a terminal to see how much there is, and how much is in use.

I do have enough swap, that's an awesome command, I've never actually run across it before and I'll have to remember it.

Also I did max the video memory that that helped a lot, but I think in the end I'm going to switch to Ubuntu Mate. It looks like I remember Ubuntu looking when I first started using it.

> **ajgreeny said:**
> Make sute that you have the VBox guest additions installed as well; I am not sure if it will help with this specific problem but it is really necessary to make full use of VMs.

I have Vbox guest additions installed. It seems like most VMs have resolution issues when you don't use the guest additions.

> **v3.xx said:**
> Do you have 3D acceleration enabled in vBox?  Its under Settings>display>video.  

Could there be a bios setting?

I do not run Unity, but I would say 3D needs the video ram.

I haven't tried 3D acceleration, but I've decided to switch to Ubuntu Mate.

Thanks everyone for the help!

---

