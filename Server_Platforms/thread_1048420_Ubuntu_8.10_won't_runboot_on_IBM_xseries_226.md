---
title: "Ubuntu 8.10 won't run/boot on IBM xseries 226"
date: 2009-01-23
forum: Server Platforms
---

### Post by mohitchawla on 2009-01-23
Well its the first time I am working on a server machine and was excited but anyway...a strange problem. Not sure where the issue lies.

The machine is IBM xseries 226, with a SCSI hard disk. 
The installation goes fine...I do a clean install, no other OS. But then I get dropped to the initramfs shell after getting the /dev/123 UUID device doesn't exist error. (The one with the ALERT !! /dev/689ehyf2c89qy2blahblah doesn't exist). Could it be a SCSI related problem (I have absolutely no idea) ?

By the way, I installed FreeBSD later without issues and it ran fine...so wonder where the problem lies. Should I rather try 7.10 ?

---

### Post by redroad55 on 2009-01-23
8.04 lts alternate install is your best bet if there is a driver issue you will be able to see ( scsi controller ) ... Check Ibm support for bios update but do nothing until you are comfortable with their instructions ..also check driver updates .. Identify hard drive and search there for any firmware updates for hard drive .. post your progress here .. best to you ..Ibm has great support you are in luck there ..

---

### Post by redroad55 on 2009-01-23
Also check bios settings do you see drive there .. scsi controoller if you have one must see drive .. Lots of documentation for your machine with Ibm your machine is similar to the intellistation Zpro so some of that imfo will be relevant also .. check bios settings documentation .. post back

---

