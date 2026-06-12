---
title: "dell powerconnect sc1425 wont detect raid 1 on install"
date: 2010-06-04
forum: Server Platforms
---

### Post by Veratyr9 on 2010-06-04
got a dell powerconnect sc1425 running 2 250gb sata drives configured as raid 1 on a CERC onboard raid controller.

boot up into 10.04 x64 server install, all goes well until after network discovery it goes to detect hard drives.

a message appears "one or more drives containing serial ata raid configurations have been found.  do you wish to activate these raid devices?" yes/no

whether or not i hit yes or no, the next screen doesnt have any drives listed, just configure iscsi, undo changes to partitions and finish/write changes to disk.

:confused: so where are these drives? do i have to load drivers like in winblows setup?

---

### Post by disabledaccount on 2010-06-04
> **Veratyr9 said:**
> got a dell powerconnect sc1425 running 2 250gb sata drives configured as raid 1 on a CERC onboard raid controller.

boot up into 10.04 x64 server install, all goes well until after network discovery it goes to detect hard drives.

a message appears "one or more drives containing serial ata raid configurations have been found.  do you wish to activate these raid devices?" yes/no

whether or not i hit yes or no, the next screen doesnt have any drives listed, just configure iscsi, undo changes to partitions and finish/write changes to disk.

:confused: so where are these drives? do i have to load drivers like in winblows setup?
Every OS needs drivers for particular hardware - are you surprised ?
Automated installers are working well for commonly used hw only - in all other (special) cases you need to do some steps by hand.
So, the first step is to enter terminal and get info about your controller -> lspci, view kernel log / messages. Thanks to that, you will know what you're dealing with...
Onboard raid controller is supposed to be fakeraid and thus mdadm is propably what you need to configure - optionally, disable Raid mode in bios and create array manually, using mdadm.

---

### Post by Veratyr9 on 2010-06-04
-.- looks like its fakeraid..... ugh the whole reason i bought this server (ebay) was to get an onboard hardware raid controller.  guess i read wrong or my sources weren't valid.

lspci shows: "raid bus controller: intel corporation 82801er (ich5r) sata controller (rev 2)"

thats fakeraid isnt it?

then in addition to the question of this thread, is fakeraid or setting up softraid within linux more reliable? or does that question belong in a thread itself?

alright, step #2?

---

### Post by disabledaccount on 2010-06-04
> **Veratyr9 said:**
> ...lspci shows: "raid bus controller: intel corporation 82801er (ich5r) sata controller (rev 2)"

thats fakeraid isnt it?

then in addition to the question of this thread, is fakeraid or setting up softraid within linux more reliable? or does that question belong in a thread itself?

alright, step #2?Yes, its fakeraid.
Is software raid reliable? Mdadm is reliable, bios-based fakeraids are not.
~ Simple example: you have broken SATA cable on one of the drives - "stupid" fakeraid will endlessly try to rebuild array (killing performance), and will not give true info about the cause. Using md you will get message about SATA link reset due to transmission errors and furthermore you can view SMART report, that will show C7 parameter rising (C7 = Ultra DMA CRC Error rate). Such important functionality is rarely implemented even in professional hardware raid controllers (not counting high-end products).
Furthermore #2: I have desktop OS installed on md Raid0 (2x500GB HDDs) and I have experience with SATA link problems, which leaded only to remounting filesystem as read-only - without any data loss ;)

back to thread: step#2
what can I say: read mdadm manual ;)
You can create array during OS installation (switching to terminal), but this sometimes lead to problems. Another way (which I prefer) is to boot system from livecd, setup md array, then run OS installator. You can create array using whole disk space, but this is not necessarily best way -> more reliable solution is to split each drive into /boot and /(root) partitions, then setup array for /(root) only. Two /boot partitions needs additional steps after kernel updates, but this gives possibility to boot from both drives, without problems.

---

