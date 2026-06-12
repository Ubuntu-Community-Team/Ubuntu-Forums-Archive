---
title: "Bsod"
date: 2007-10-13
forum: Windows
---

### Post by jpittack on 2007-10-13
A note on my most recent experience with windows.  I was installing windows xp pro on a kinda old dell.  This is the third time I have reinstalled it.  My brother likes to dabble in spyware or something, because it just breaks without warning.

Anyways, I am installing it and I go make myself something to eat.  I come back and wham!  Blue Screen of Death.  While I was installing it!  This happen to anyone?

:lolflag:

P.S.  Second install was a failure.  A bunch of .sys files were not working out or something.  I am trying the third install now.  If I don't use the cd (as in any other Windows cd doesn't not help) then I get a error message and am told to reboot.

---

### Post by Imsati on 2007-10-13
> **jpittack said:**
> A note on my most recent experience with windows.  I was installing windows xp pro on a kinda old dell.  This is the third time I have reinstalled it.  My brother likes to dabble in spyware or something, because it just breaks without warning.

Anyways, I am installing it and I go make myself something to eat.  I come back and wham!  Blue Screen of Death.  While I was installing it!  This happen to anyone?

:lolflag:

P.S.  Second install was a failure.  A bunch of .sys files were not working out or something.  I am trying the third install now.  If I don't use the cd (as in any other Windows cd doesn't not help) then I get a error message and am told to reboot.

Yes, I've gotten a BSoD diring an install before, but it was a random occurance and happened years ago. I know it happened with 98SE, but can't recall if I've ever seen it on an XP install though.

When you say second and third install attempts, did you go back and start everything from the beginning? Meaning have the CD load temp files, accept the License Agreement, and go through formatting? With some systems, even though you select 'Boot from CD', you have to watch the bootup process. Sometimes, you'll need to physically press a key to boot at the beginning of the CD; just letting it boot will cause it to start at it's last known position. Not the case with all BIOSes (BIOSi? BIOS's?) but good to know about just in case yours is like that.

---

### Post by jpittack on 2007-10-13
I do need to press a button to boot from CD.  and my third install was a faulire.  If i try to put Ubuntu on the machine, I get a message saying that I need to restart because NT's bootloader is screwed up.  Windows can't install, Ubuntu is being prevented from installing.  I guess my brother is getting a new computer for Christmas.  Or maybe he should go get a job and buy his own.

---

### Post by Dr. C on 2007-10-13
Can you wipe the hard drive and install Ubuntu?

---

### Post by jpittack on 2007-10-13
I haven't really tried wiping the hard drive.  I format it everytime using the windows cd.  I could use gparted to delete the partition and then use the Ubuntu cd.  At the moment, Ubuntu (text-based) doesn't even work.  I will give this a try though.  I found that the cd is defective beyond belief.

---

### Post by Imsati on 2007-10-13
I'd agree then with the suggestion to wipe the HDD and start fresh. XP first, then Ubuntu to avoid MBR pains. If you have files on the HDD, you should still be able to hook it up to another computer (just set the jumper to cable select or slave) and copy the files over.

---

### Post by voided3 on 2007-10-13
Use the windows disk to delete the existing partition(s) and quick format it, then boot the Ubuntu installer and use gparted. I had to do this once before if I recall correctly....

---

