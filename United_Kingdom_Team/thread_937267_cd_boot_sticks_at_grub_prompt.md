---
title: "cd boot sticks at grub prompt"
date: 2008-10-03
forum: United Kingdom Team
---

### Post by wonkyuk on 2008-10-03
i created a virtual cdrom drive and was able to reboot on this drive but it stops at a grub prompt. what do it do to progress this into a ubuntu install?

---

### Post by wonkyuk on 2008-10-04
ok, after ffi8nally succeeding in creating a dvd of the image file i ran it on the machine and ran the installer creating a partition on an external drive and leaving the windows partition on the internal drive alone.after sucxcessful completion of the install i rebooted. 

now we have a real problem. not only does the system no longer offer me a choice of boot volume or os, but when it tries to boot ubuntu i get a grub prompt and an immediate error 21.

i can boot the machine off the dvd ok and run ubuntu but i do not know how i can any longer boot from my windows drive. if i unplug the external drive and take out the dvd it still will not boot from the internal drive and still gives me the grub prompt with error 21. why am i getting grub even when i only have the internal drive attached? ubuntu should not have touched that drive at all. all the  files and folders are still intact on th einternal drive but i can no longer boot from it.

this is a major ******* nightmare. i havr followed your instructions to the letter and yet i now have a fatally crippled system thatr can only boot up from a dvd!!!

so how do we fix this problem?

i need to be able to boot both ubuntu and windows from this machine.

---

### Post by cr0wn3r on 2008-10-06
Did you fix this?

I just messed up my Vista install trying to dualboot with Ubuntu, and managed at least to get Vista back by booting from the Windows DVD, finding the option to go to Console, and and typing "fixmbr" to fix the master boot record for windows.

C

---

### Post by wonkyuk on 2008-10-06
Nah. I mean, I fixed the mbr with mastergrubdisk. so i can still boot the machine's windows partition. but it will not boot from the usb drive containing the full ubuntu/linux/grub install. if i boot from ther ubuntu cdrom i can see all the files and the install worked perfectly. but for some reason the boot mechanism of the machine will not recognise the system on the usb drive. i have tried making it the first in the line to boot through the bios but no workie. all i get when i select ubuntu from the boot options is a grub prompt. not even an error 21 anymore. if i try to find anything such as menu'lst or stage1 grub, it looks on the floopy drive!?!?!?!?!? I mean i am including the drive and directory info in the grub query but nothing seems to make a diff.

i have it is a simple fix to get grub to look to the usb drive (sdb1 partition) and fire up ubuntu but I do not know how to do that and set it up as a workable script with the dual boot capability.

ubuntu would be a whole lot more ubiquitous if this kind of a problem didn't exist. but as long as there is no functioning itunes store or playback of itunes drm files, then everyone with an itunes account and itunes music files will have to keep a windows partition and system on it. that's a lot of people who will prolly never get past the dual boot problems of error 21 or error 15..

i would be willing to pay canonical to help me sort this out as this would allow me to eek a copuple more years out of these two old windows desktop machines....but no reply to my emails.

---

