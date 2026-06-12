---
title: "Can I RAID with an external hard drive?"
date: 2011-01-18
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-18
Hey everyone,
I'll be setting up my first server tomorrow. I say that a little too confidently, as it will probably take me a week. At any rate... I would really like to use RAID 1. The problem is, my server only has one wired 250 GB hard drive. I don't want to buy another wired drive right away but I happen to have a 250 GB external hard drive. Can I just plug that into the USB and use RAID 1 with one wired HDD and one external?

***IMPORTANT NOTE*** (maybe): My server DOES NOT have a RAID controller. I will be using fakeRAID software. I don't know if this matters. 

Thanks for your help!

---

### Post by trundlenut on 2011-01-19
I would suspect that may well make things hard for you, escpecially when you come to install the OS.

On the raid side of things you are going to be using software raid, rather than fakeraid - IIRC fakeraid is a mixture of hardware and software.

How about dismantling the usb drive and putting the disk in the machine, do you know if they are IDE or SATA drives?

---

