---
title: "Trouble installing windows xp on gazv4"
date: 2008-09-17
forum: System76 Support
---

### Post by bretthall on 2008-09-17
This weekend I was trying to convert my gazv4 to dual boot windows (need it for work and vmware isn't cutting it) and when I try to run the windows installer I get a blue screen. the installer starts up, loads all the drivers and then gets to the point where it says "setup is starting windows" and then I get a blue screen with a stop code of 0x0000007E (0xC0000005, ...) in pci.sys. Has anyone else seen this and have a fix? All the info I can find on this problem points at SATA drives being the problem, but the gazv4 has an IDE drive. I can't find any details on the hardware for the gazv4 so I don't know where to look for firmware updates and the like.

---

### Post by thomasaaron on 2008-09-17
Could you please post the entire error message you are getting?

Is it, by chance, this one:

> A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps:

Check to be sure you have adequate disk space. If a driver is identified in the Stop message, disable the driver or check with the manufacturer for driver updates. Try chaging video adapters.

Check with your hardware vendor for any BIOS updates. Disable BIOS memory options such as caching or shadowing. If you need to use Safe Mode to remove or disable components, restart your computer, press F8 to select Advanced Startup Options, and then select Safe Mode.

Technical Information:

*** STOP: 0x0000007E (0xC0000005, 0xF85F9AD9, 0xF898B7A4, 0xF898B4A4)  

If so, do you have adequate disk space? The disk space you reserved with you vmware xp install may be causing you to have less space than you think.

---

### Post by bretthall on 2008-09-17
That looks like it. I have the last three numbers in parentheses written down at home so I can't verify them until tonight. Currently my entire hard-drive has one LVM partition on it. Since LVM partitions can't be easily resized my plan was to repartition the drive in the windows installer so that it was half NTFS and then reinstall ubuntu on the other half after I had windows going. Should I first remove the LVM partition using parted and then install windows?

---

### Post by thomasaaron on 2008-09-17
Ah, you have the old LVM partitioning scheme. We don't use that anymore because we were unable to resize it. I'm relatively sure the Windows disk can't re-size it either.

That's probably the issue.

You may need to re-install. You can do Windows first and then Ubuntu and everything should work like a charm.

---

### Post by bretthall on 2008-09-18
I booted from an Ubuntu live CD and used gparted to blow away all the partitions on my disk (boot and LVM). I'm still getting the the blue screen when installing windows. The message is the same as from your earlier post except for the "Technical information" at the bottom of the screen which is:

```

*** STOP: 0x0000007E (0xC0000005, 0xF748E0BF, 0xF78DA208, 0xF78D9F08)

***   pci.sys - Address F748E0BF base at F7487000, DateStamp 3b7d855c

```

I did see a post elsewhere suggesting that removing a memory stick mught help. I have 2GB in my laptop, do you think that removing one of the sticks would help?

---

### Post by thomasaaron on 2008-09-18
> do you think that removing one of the sticks would help?

I'm not sure. It couldn't hurt to try it though.

When you try to install Windows, have a look at the partitions. Are there any there that you can delete?
(Clarification: Maybe there's something there that is confusing Windows.)

---

### Post by bretthall on 2008-09-18
OK, figured out the problem. I was using a WIN XP Pro disk that is pre SP1. Apparently windows can't deal with some piece of hardware on the Gazv4 without SP1. I found a SP2 install disk at work and now it's working fine.

---

