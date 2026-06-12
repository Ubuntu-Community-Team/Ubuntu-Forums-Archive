---
title: "Slow Virtualbox"
date: 2014-05-01
forum: Virtualisation
---

### Post by LastDino on 2014-05-01
Well, now that I'm on stable LTS OS, I would rather not dual boot or anything. So, I gave Virtualbox a extensive run.
Info:
My original system:
P4 3.0GHz
4GB RAM
On board GPU.

Usually what I give to VB:
Execution cap 100%
RAM 2GB
Video memory 128 (enable 2d acceleration)

To just give it a go on Xubuntu host, I tried Fedora Xfce as guest, and it ran extremely slow compared to what XP guest ran on Ubuntu 13.10 host. 
Weren't windows OS suppose to be more resource consuming one? I'm bit lost here as to what other changes do I need to do, so any suggestions are appreciated :3
Any suggestions regarding what guest's might run best with this configuration/settings, if I need to tweak anything and anything else I might need to install to make VB's life easier, are welcomed as well.

I wouldn't mind trying different Virtual software if it is faster either, so please don't hold your hand back there.;)

---

### Post by SeijiSensei on 2014-05-01
Did you install the Extension Pack?  That can make a difference with video performance in some cases.

Take a look at swap usage on both the host and guest.  Are either of them using a lot of swap?  If so, you might want to reallocate memory between the host and guest.

---

### Post by The Cog on 2014-05-01
I discovered the other day that enabling the CPU's virtualisation extensions in the BIOS make huge difference to how fast a VB guest runs. And I couldn't enable more than one cpu in VB until I enabled support.

---

### Post by jon43 on 2014-05-01
Is the P4 single or dual core? 

I've never even attempted to run a VB configuraiton on a single-core machine. Not to say it can't be done, but I certainly would assume there would be lots of lag with any OS...

---

### Post by jdeca57 on 2014-05-01
A reasonable Ubuntu guest (using a browser and libreoffice and some programs) doesn't use more than 1 GB so the problem isn't memory. You might tweak the chipset: sometimes that can make a difference: ICH9 can be faster. In essence, I didn't find that 3D acceleration makes a difference, but that may be hardware dependent.
But perhaps the problem is the guest: Fedora isn't exactly the leanest. Xubuntu and Lubuntu are other candidates. And don't forget: an OS like XP that is over 10 years old shouldn't be compared with modern OS.

---

### Post by LastDino on 2014-05-02
> **SeijiSensei said:**
> Did you install the Extension Pack?  That can make a difference with video performance in some cases.

Take a look at swap usage on both the host and guest.  Are either of them using a lot of swap?  If so, you might want to reallocate memory between the host and guest.
Yes, ''guest extension pack'' is installed. And yes, there was noticeable difference between mouse handling of the guest than it was before. But guest OS itself is acting quite slow.  

Amount of SWAP used was around 48 MB. And it was by host, I assume it is because I gave considerable amount to VB and host started to ''finally'' use that swap area.
> **The Cog said:**
> I discovered the other day that enabling the CPU's virtualisation extensions in the BIOS make huge difference to how fast a VB guest runs. And I couldn't enable more than one cpu in VB until I enabled support.
I didn't knew that, I'll try and see if it makes any difference on my machine. Thanks!
> **jon43 said:**
> Is the P4 single or dual core? 

I've never even attempted to run a VB configuraiton on a single-core machine. Not to say it can't be done, but I certainly would assume there would be lots of lag with any OS...
It is single, but my system usage have never exceeded 75-90% with even VB working. I was using the same settings and everything even on my 13.10 to run XP and there wasn't any noticeable lag tbh.

> **jdeca57 said:**
> A reasonable Ubuntu guest (using a browser and libreoffice and some programs) doesn't use more than 1 GB so the problem isn't memory. You might tweak the chipset: sometimes that can make a difference: ICH9 can be faster. In essence, I didn't find that 3D acceleration makes a difference, but that may be hardware dependent.
But perhaps the problem is the guest: Fedora isn't exactly the leanest. Xubuntu and Lubuntu are other candidates. And don't forget: an OS like XP that is over **10 years old shouldn't be compared with modern OS.**
Yes, indeed. I never give 3D acceleration. Mostly because I've my doubts my system being able to handle that level of graphics. But I'll have a look at ICH9. Thanks!

@Bolded: Good point! I'll try out  running Lubuntu and if it came down it maybe some other distro similar to it in weight.

Another thing I've been wondering is how to increase disk (HD not CD/DVD)  read /write speed of guest OS. I've done some research and it turns out that you can do that by using RAID or something but that sounds going way too far for miserly home testing VB. Are there any other ways to do that, I'm assuming it matters?

---

### Post by SeijiSensei on 2014-05-02
RAID is generally slower at writes, since it writes the same information across multiple devices, and for some RAID flavors calculates and writes a checksum as well.  Of the RAID flavors that provide true redundancy, RAID1 is generally faster at reads than a single disk since the information can be pulled from both copies at the same times.  

RAID0 ("striping") is also [faster]("http://www.overclock.net/t/1259951/raid0-and-data-transfer-rates") than a single disk, but it provides no redundancy.  It's not a solution I would choose since I'm generally more concerned with reliability than performance.

I'd be surprised if the disk performance by the guest is notably degraded.  Sure the data has to travel through the interface with the host, but that all happens in the CPU and memory.  Since disk performance is largely a function of the physical device itself, I would think the guest probably has about the same read/write speeds as the host.

---

### Post by LastDino on 2014-05-02
> **SeijiSensei said:**
> RAID is generally slower at writes, since it writes the same information across multiple devices, and for some RAID flavors calculates and writes a checksum as well.  Of the RAID flavors that provide true redundancy, RAID1 is generally faster at reads than a single disk since the information can be pulled from both copies at the same times.  

RAID0 ("striping") is also [faster]("http://www.overclock.net/t/1259951/raid0-and-data-transfer-rates") than a single disk, but it provides no redundancy.  It's not a solution I would choose since I'm generally more concerned with reliability than performance.

I'd be surprised if the disk performance by the guest is notably degraded.  Sure the data has to travel through the interface with the host, but that all happens in the CPU and memory.  Since disk performance is largely a function of the physical device itself, I would think the guest probably has about the same read/write speeds as the host.

That is some valuable information, I learned something new. Thank you very much ^^

So, all in all, the issue has more to do with me using latest guest OS and my original machine lacking horse power to do so. And it's turning out to be the only real hindrance here. 

I'll mark the thread as solved but any one who has some input to give, please do so ;)

---

### Post by TheFu on 2014-05-03
Virtualizing on any CPU less than a Core2Duo is unpleasant.  However, I do get good VM performance out of a new Haskel Celeron Chromebook ($199).
[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) explains how.

---

### Post by LastDino on 2014-05-03
> **TheFu said:**
> Virtualizing on any CPU less than a Core2Duo is unpleasant.  However, I do get good VM performance out of a new Haskel Celeron Chromebook ($199).
[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) explains how.


Wow! Nice share. It had all settings in details. I'll test them out when I'm on my test run. Thank you very much! :3

---

