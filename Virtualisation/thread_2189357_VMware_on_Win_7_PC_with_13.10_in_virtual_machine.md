---
title: "VMware on Win 7 PC with 13.10 in virtual machine"
date: 2013-11-21
forum: Virtualisation
---

### Post by SuperFreak on 2013-11-21
I am quite new at using VM and I have just installed VMware (free version) on my Win 7 machine. My expectations are probably too big but I am hoping to use this to test 13.10 with XBMC hooked up to the TV,  because of the issues with HDMI and sound not working without some tinkering. That is my purpose before I go ahead and do a full install of 13.10 but I am finding the PC fairly slow in virtual mode. It is a Hewlett-Packard dv7-6113cl with a AMD Quad-Core A6-3400M 1.4GHz, 6 GB Ram and a AMD Radeon HD 6520G graphics card (memory is shared). Is this unrealistic and are there ways to make the PC run faster in virtual mode? My next step is to try the fixes for HD Radeon that will allow HDMI to provide sound to the TV.

---

### Post by electrohandyman501 on 2013-11-21
Why not just try 13.10 with a LiveCD or USB boot. Without an actual hard drive install, or VMware install.

---

### Post by drmrgd on 2013-11-22
An easy thing to check is that you have AMD-v hardware virtualization enabled.  I think that processor is new enough to be capable, but you can double check that you do in fact see the flags in the 'cpuinfo' output:

```

sudo grep --color svm /proc/cpuinfo

```

If you see a result, that should confirm your processor is capable.  

The other thing to check is that virtualization technology is enabled in your BIOS.  You may have to dig around the BIOS settings to find it, but there should be an entry to enable or disable this feature.  

Without that, it's possible to do what you want, but it will run really slowly.  I have roughly the same setup at work (although on an intel desktop), and it runs completely fine.

---

### Post by SuperFreak on 2013-11-22
> Why not just try 13.10 with a LiveCD or USB boot. Without an actual hard drive install, or VMware install. 
Tried that with persistence but I can't get the HDMI sound to work with the LIve USB 


@drmrgd Thanks I will try the command and check BIOS settings

---

### Post by SuperFreak on 2013-11-22
> **drmrgd said:**
> An easy thing to check is that you have AMD-v hardware virtualization enabled.  I think that processor is new enough to be capable, but you can double check that you do in fact see the flags in the 'cpuinfo' output:

```

sudo grep --color svm /proc/cpuinfo

```

If you see a result, that should confirm your processor is capable.  

The other thing to check is that virtualization technology is enabled in your BIOS.  You may have to dig around the BIOS settings to find it, but there should be an entry to enable or disable this feature.  

Without that, it's possible to do what you want, but it will run really slowly.  I have roughly the same setup at work (although on an intel desktop), and it runs completely fine.


Virtualization seems to be enabled under BIOS(SVM enabled) but the command you gave yielded no result unfortunately so maybe my cpu is underpowered for the task

---

### Post by drmrgd on 2013-11-22
> **SuperFreak said:**
> Virtualization seems to be enabled under BIOS(SVM enabled) but the command you gave yielded no result unfortunately so maybe my cpu is underpowered for the task

You might just double-check I gave you the right flags to use for that processor.  I have only used Intel processors and am not 100% familiar with the AMD version of those flags.  Your CPU is fairly newer, and I would be really surprised if it didn't have native support for virtualization, but I could be wrong.  Hopefully I didn't give you any bad info!

---

