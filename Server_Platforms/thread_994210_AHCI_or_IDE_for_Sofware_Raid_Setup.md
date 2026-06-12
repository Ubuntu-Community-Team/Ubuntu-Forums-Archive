---
title: "AHCI or IDE for Sofware Raid Setup?"
date: 2008-11-26
forum: Server Platforms
---

### Post by sam702 on 2008-11-26
Hi everyone.

I'm confused regarding the AHCI, IDE and RAID storage drive configuration in the bios setting.  

I have an ASUS P5Q-EM.  I'm building a headless fileserver using Ibex and Samba.  I'm doing software raid 1 using two physical drives for the operating system and raid 5 using three physical drives for data storage.

In the bios, there is an option for AHCI, IDE, and Raid.  All of my drives are SATA II (3G/s).  I know Raid is for the onboard raid setup.  Based on my other reading, software raid is better.

Which option would work best for the Ibex/Samba filesever, AHCI or IDE?

Thanks.  Happy Thanksgiving!

---

### Post by Krupski on 2008-11-26
> **sam702 said:**
> Hi everyone.

I'm confused regarding the AHCI, IDE and RAID storage drive configuration in the bios setting.  

I have an ASUS P5Q-EM.  I'm building a headless fileserver using Ibex and Samba.  I'm doing software raid 1 using two physical drives for the operating system and raid 5 using three physical drives for data storage.

In the bios, there is an option for AHCI, IDE, and Raid.  All of my drives are SATA II (3G/s).  I know Raid is for the onboard raid setup.  Based on my other reading, software raid is better.

Which option would work best for the Ibex/Samba filesever, AHCI or IDE?

Thanks.  Happy Thanksgiving!

AHCI - no question about it.

AHCI supports native command queuing, hot plugging... all the newest features.

IDE mode is a translated, legacy mode that is much slower and doesn't have all the features.

Linux fully supports AHCI, so use it!

---

### Post by cariboo on 2008-11-26
You should have a look at the fakeraid howto, I found it really easy to setup my raid array. it is available here:

```
https://help.ubuntu.com/community/FakeRaidHowto
```

I see it has been updated in the last couple of weeks.

Jim

---

### Post by sam702 on 2008-11-26
Thank all.  

I did enable the AHCI and have the RAID 1 setup for the OS portion.  I will buy the harddrives for the RAID 5 after Thanksgiving to see if I can get any deals.

The next step is testing disk failure and restore process.  And automated external backup.

Thanks again.  Happy a wonderful Thanksgiving!

---

### Post by Krupski on 2008-11-27
> **cariboo907 said:**
> You should have a look at the fakeraid howto, I found it really easy to setup my raid array. it is available here:

```
https://help.ubuntu.com/community/FakeRaidHowto
```

I see it has been updated in the last couple of weeks.

Jim

I really am bothered by the term "fake raid".

ALL RAID is software. If you have a "RAID controller card", it is a multiple port disk controller with RAID software in it's BIOS.

If you use something like MDADM in Linux, you are using RAID software to talk to multiple disk controller ports.

Absolutely no difference.

The ONLY time one should be concerned is if they are dual booting Linux and a different OS (like Windows).

A RAID system in Linux setup using MDADM will not, obviously, be seen by Windows.

However, a RAID card with RAID software in it's BIOS will be seen identically by any OS and will boot Linux, Windows or anything else equally well.

-- Roger

---

### Post by cariboo on 2008-11-27
Quoted from the FakeRaid Howto

> In the last few years, a number of hardware products have come onto the market claiming to be IDE or SATA RAID controllers. These have shown up in a number of desktop/workstation motherboards. Virtually none of these are true hardware RAID controllers. Instead, they are simply multi-channel disk controllers combined with special BIOS configuration options and software drivers to assist the OS in performing RAID operations. This gives the appearance of a hardware RAID, because the RAID configuration is done using a BIOS setup screen, and the operating system can be booted from the RAID. 

I don't know if this is true for all onboard raid controllers, but I have seen it with several IDE raid controllers back when onboard raid first became available.

Personally I don't care what it is called as long as it works. My setup uses dmraid to administer the array.

Jim

---

### Post by psusi on 2008-11-29
> **Krupski said:**
> I really am bothered by the term "fake raid".

ALL RAID is software. If you have a "RAID controller card", it is a multiple port disk controller with RAID software in it's BIOS.

No, all raid is not like that.  Real hardware raid is done in dedicated hardware that handles routing the data to the correct disk, computing the checksums, etc, and usually has on board ram for cache that is usually backed up with a small battery in case the power fails.  What you describe is fake hardware raid, so called exactly because it doesn't do the raid in hardware, but isn't conventional software raid either.

> **Krupski said:**
> 
If you use something like MDADM in Linux, you are using RAID software to talk to multiple disk controller ports.

Absolutely no difference.

The ONLY time one should be concerned is if they are dual booting Linux and a different OS (like Windows).

A RAID system in Linux setup using MDADM will not, obviously, be seen by Windows.

There are two key differences between software raid and fakeraid.  You mention the one being the ability to dual boot with windows.  The other is the ability to boot from the raid at all.  Pure software raid can't be booted directly from since the bios doesn't know how to access it, which is why you have to make a normal /boot partition outside of the raid array when you use mdadm ( except for raid1 since it just looks like two normal disks to the bios that happen to contain exactly the same data ).

> **Krupski said:**
> However, a RAID card with RAID software in it's BIOS will be seen identically by any OS and will boot Linux, Windows or anything else equally well.


Not quite.  Windows does not see the card at all until you install the driver provided by the manufacturer that handles the raiding internally and presents what looks like a single disk to the OS.  Linux sees the controller for what it is: a regular multi channel ACHI controller that has multiple physical disks attached.  To access it as a raid in Linux you need special software.  With other operating systems, like bsd or something, you are out of luck.

---

### Post by Krupski on 2008-11-29
> **psusi said:**
> Not quite.  Windows does not see the card at all until you install the driver provided by the manufacturer that handles the raiding internally and presents what looks like a single disk to the OS.  Linux sees the controller for what it is: a regular multi channel ACHI controller that has multiple physical disks attached.  To access it as a raid in Linux you need special software.  With other operating systems, like bsd or something, you are out of luck.

Usually, a RAID card has a BIOS on board and the standard INT-13 interface (slow) is used to start the boot process. Once the OS is loaded, it's native drivers take over and the card performs at maximum speed.

A hardware RAID card would be rather useless if it didn't do this, as it would be a Catch-22 (can't load the driver until the driver is loaded).  :)

---

### Post by psusi on 2008-11-30
> **Krupski said:**
> Usually, a RAID card has a BIOS on board and the standard INT-13 interface (slow) is used to start the boot process. Once the OS is loaded, it's native drivers take over and the card performs at maximum speed.

A hardware RAID card would be rather useless if it didn't do this, as it would be a Catch-22 (can't load the driver until the driver is loaded).  :)

This is true, but what does it have to do with what I said?

---

