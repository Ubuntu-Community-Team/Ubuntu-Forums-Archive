---
title: "Paid support  question"
date: 2011-11-18
forum: The Cafe
---

### Post by Neill_R on 2011-11-18
Hi

Now sort of solved by purchase of another PC.

 
I have a system I can not get working in UBUNTU 10.04 and as yet have had no replies to my posts.
 
Asked for hardware details 
 
[http://ubuntuforums.org/showthread.php?p=11462034](http://ubuntuforums.org/showthread.php?p=11462034)
[http://ubuntuforums.org/showthread.php?t=1882448](http://ubuntuforums.org/showthread.php?t=1882448)
 
My system is UBUNTU 10.04 LTS. 
My Hardware is PACKARD BELL I-Media 1328/1 2GB RAM 500 GB HD. 
Monitors E171FPb and HP S2231a. 
In windows Xp the system works just fine albeit at 1024x768. 
The VGA outputs are from the SIS motherboard and a PCI Diamond Steath 64 card S3. 
In Linux I either have to boot into recovery console low resolution single screen on the S3 card
or switch cards in the xorg.conf file, so that after BIOS boot on S3 the SIS becomes the active screen
and the S3 becomes the extended desktop. 
I also have had to use the vesa driver not the s3 driver as determined by Xorg --configure. 
S3 drive fails EE RAMDAC probe failure.
I have been asking for help from the forum as to why my mouse movement will freeze the system but have not,
as yet had any replies. Google had given me lots to read but no clear insight into how or what to do to fix it.
 
 
I am wondering if £88 buys one real support. What is your opinion and or experience of their support.

---

### Post by Rubi1200 on 2011-11-18
Moved to the cafe; hopefully you will receive some useful answers.

---

### Post by szymon_g on 2011-11-18
it would be helpful if you would mention what kind of hardware you have got...

---

### Post by 3Miro on 2011-11-18
If it is a matter of setting up the system, then the support people should be able to help. If it is a matter of not having drivers, then they will not write drivers for you. For example, if you have an Intel Sandy Bridge integrated graphics, then those will not work with 10.04 regardless of whether or not you pay.

---

### Post by meh_phistopheles on 2011-11-18
so far it seems like your problem is poor communication. how is anyone supposed to fix your problem if you don't say what it is?

---

### Post by Neill_R on 2011-11-18
My system is UBUNTU 10.04 LTS. 
My Hardware is PACKARD BELL I-Media 1328/1 2GB RAM 500 GB HD. 
Monitors E171FPb and HP S2231a. 
In windows Xp the system works just fine albeit at 1024x768. 
The VGA outputs are from the SIS motherboard and a PCI Diamond Steath 64 card S3. 
In Linux I either have to boot into recovery console low resolution single screen on the S3 card or switch cards in the xorg.conf file, so that after BIOS boot on S3 the SIS becomes the active screen and the S3 becomes the extended desktop. 
I also have had to use the vesa driver not the s3 driver as determined by Xorg --configure. S3 drive fails EE RAMDAC probe failure.
 
I have been asking for help from the forum as to why my mouse movement will freeze the system but have not as yet had any replies. Google had given me lots to read but no clear insight into how or what to do to fix it.

---

### Post by 3rdalbum on 2011-11-18
Easy solution: Remove the SiS graphics or disable it. Buy a real graphics card - something really cheap from Nvidia, or a cheap current ATI card will solve all your problems.

A lot cheaper than 88 pounds, might I add.

---

### Post by Neill_R on 2011-11-19
Can't remove SIS it is Motherboard graphic the S3 is removable.  

Anyhow I hate to give up but i have got another card a  AGP dual port DVI and VGA card by buying a second hand PC all works and the monitors are detected too. Nvidia Geforce Fx 5700 @128MB. It also means I get to have 3GB RAM PC useful for running virtualbox 

But it is sad that I could not determine how to stop the mouse from freezing the system when nearly everthing else appeared that it would be working. Thinking in the spirit of Ubuntu that there are others that do not have options to get additional hardware.

---

### Post by cariboo on 2011-11-19
Back during the Lucid development cycle, there was talk about SIS creating a new driver, but nothing ever came of it, as far as I know. You may want to contact them about your problem, as paying Canonical for support on something they have no control over would be throwing good money away.

---

### Post by 3Miro on 2011-11-19
> **cariboo907 said:**
> Back during the Lucid development cycle, there was talk about SIS creating a new driver, but nothing ever came of it, as far as I know. You may want to contact them about your problem, as paying Canonical for support on something they have no control over would be throwing good money away.

+1. If it is an issue with bad driver, then Canonical cannot do anything about it.

---

