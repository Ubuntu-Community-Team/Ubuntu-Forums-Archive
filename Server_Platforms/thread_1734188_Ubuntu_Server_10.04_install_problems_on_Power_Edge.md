---
title: "Ubuntu Server 10.04 install problems on Power Edge 1850"
date: 2011-04-20
forum: Server Platforms
---

### Post by tmlemm on 2011-04-20
Hi everyone,
Im having a bit of an issue installing Ubuntu Server 10.04 on a Dell Power Edge 1850. I am running RAID1 via the onboard PERC4 controller that is set to emulate MASS storage. I am able to boot from the disk and run through the initial setup, however, when I give it the go ahead to start the partitioning it hangs up on 33%. It does this on both the Guided full disk and guided full disk LVM.

I have run a check on the disk as well as memory.

Any ideas?

---

### Post by tlan on 2011-04-20
that array controller might not be supported in ubuntu 10.04

have you tried using 10.10 or debian 6

this will probably not make a difference but in the bios there is a setting that states what OS is being installed. make sure that's correct. linux other

---

### Post by usatonycuba on 2011-04-20
> **tmlemm said:**
> Hi everyone,
Im having a bit of an issue installing Ubuntu Server 10.04 on a Dell Power Edge 1850. I am running RAID1 via the onboard PERC4 controller that is set to emulate MASS storage..

> **tlan said:**
> that array controller might not be supported in ubuntu 10.04..
[Ubuntu-certified hardware Models]("http://www.ubuntu.com/certification/catalog/component/pci:244E:8086/models")

---

### Post by tmlemm on 2011-04-20
I see that the PE1850 is not listed but neither is half the hardware I run Ubuntu on. I have seen Ubuntu Server running on PE1850s before so was thinking that I might be doing something wrong.

---

### Post by usatonycuba on 2011-04-20
> **tmlemm said:**
> I see that the PE1850 is not listed but neither is half the hardware I run Ubuntu on. I have seen Ubuntu Server running on PE1850s before so was thinking that I might be doing something wrong.

Then?... Thread have been title as [COLOR="Black"]**Ubuntu Server 10.04 install problems on Power Edge 1850**[/COLOR] ?

 IMHO,  you better post then.. the configuration of your hardware, where you run Ubuntu on it .. and what is the problem .. I think it would be easier ..

---

### Post by tmlemm on 2011-04-21
> **usatonycuba said:**
> Then?... Thread have been title as [COLOR=Black]**Ubuntu Server 10.04 install problems on Power Edge 1850**[/COLOR] ?

 IMHO,  you better post then.. the configuration of your hardware, where you run Ubuntu on it .. and what is the problem .. I think it would be easier ..

Got it had nothing to do with compatibility. Bad sector on one of the drives...

---

### Post by usatonycuba on 2011-04-21
> **tmlemm said:**
> i see that the pe1850 is not listed but neither is half the hardware i run ubuntu on. I have seen ubuntu server running on pe1850s before so was thinking that i might be doing something wrong.
> **usatonycuba said:**
> then?... Thread have been title as [color="black"]**ubuntu server 10.04 install problems on power edge 1850**[/color] ?
Imho,  you better post then.. The configuration of your hardware, where you run ubuntu on it .. And what is the problem .. I think it would be easier ..
> **tmlemm said:**
> got it had nothing to do with compatibility. Bad sector on one of the drives...

Never mind, the point was.... if you try to get help installing **Ubuntu Server 10.04** on a **Power Edge 1850** as you stated on this Thread TITLE, everyone who reads the thread, will try to offer solutions according to the General Contract Conditions of the specific and exact match of that Operating Systems and Computer Hardware that you specify in the Thread TITLE above.

Anyway, if I'm in the middle of a problem with ***Bad sector on one of the drives...***...I probably would make a full  wipe-up..with the option of - repair damaged sectors on the disk..which repairs the damage most of the time.. IMHO

---

