---
title: "Can't install on Fake-raid or IBM Software Raid"
date: 2014-03-18
forum: Server Platforms
---

### Post by Adryb75 on 2014-03-18
Hello to all
I'm not an expert on linux but I'm really desperate ](*,)! Within  seven days I try to perform this type of installation of Ubuntu Server  12.4.x on a server **IBM x3100 M4**  **RAID1** but I have  encountered many problems in spite of having followed several guides and  post ( also in Portuguese) on both official and unofficial forums .
I'm at the end ... :cry:

I've tried using the UEFI enabled...it's failed
I've tried using the built-in fake-raid...it's  failed
I've tried setting the disk controller in AHCI and using the Linux software raid...it's  failed
Finally I tried UEFI is disabled and setting the disk controller board using the IDE and Linux software raid...it's  failed
The main problem is that when restart does not boot and stops in a mystery bash shell "**grub > **" .

I  feel really defeated because even with all the information that I found  on the internet do not agree on how to proceed with the installation . Those who talk about bootgrub out Raid or 2 pair to the disks on raid1 .
The same server with a only disk and partition automatic I have installed and configured in 3 hours.

I ask desperately for help as soon as possible to anyone who can give it to me .

I would like to install in RAID1 two 500GB SATA drives with this server 12.4.x

Help me

Thanks advance
Adry

---

### Post by TheFu on 2014-03-18
If there isn't a native Linux RAID driver for the RAID controller card, then you'll need to use JBOD and Linux software RAID - not "IBM RAID".
This [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) was found, but hasn't been for any release since 12.04.

I've never attempted to use FakeRAID. Only real RAID with supported hardware and drivers OR built-in Linux RAID using mdadm.

I haven't a clue about "IBM Software RAID", sorry.

---

### Post by Adryb75 on 2014-03-19
> **TheFu said:**
> If there isn't a native Linux RAID driver for the RAID controller card, then you'll need to use JBOD and Linux software RAID - not "IBM RAID".
This [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) was found, but hasn't been for any release since 12.04.

I've never attempted to use FakeRAID. Only real RAID with supported hardware and drivers OR built-in Linux RAID using mdadm.

I haven't a clue about "IBM Software RAID", sorry.

Thank you for your response. 
Explain. IBM Raid is actually a fake-raid LSI Logic MegaRAID SAS 8480 controller integrated into the MB server. 
The link already know it and it is very dated compared to the current version 12.4. 

I look forward to other solutions. 
thanks

---

### Post by TheFu on 2014-03-19
Scroll to the bottom of htat link - there is a section for 12.04. You can always use it as JBOD and use mdadm.

---

