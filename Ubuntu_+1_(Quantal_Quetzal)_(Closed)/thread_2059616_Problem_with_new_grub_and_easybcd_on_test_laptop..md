---
title: "Problem with new grub and easybcd on test laptop."
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-09-18
This test lappy has win 7 and 12.10. It's been fine booting using easybcd into grub. (grub installed to sda4 partition0 

Latest update with new grub now drops to grub prompt.

I've updated to latest easybcd version and reinstalled the daily live today.

Same thing.

Any ideas how to debug this. 

I'm loathed to install grub to MBR as it might screw up the lappy completely.

---

### Post by dino99 on 2012-09-18
right now i'm mailing Colin for my own bug(s) :P
The latest Bug #1052480

but sorry i'm not playing with easybcd, what's better with it ?

---

### Post by philinux on 2012-09-18
> **dino99 said:**
> 

but sorry i'm not playing with easybcd, what's better with it ?

It's a windows app and it leaves the windows bootloader intact and chains to grub. Err well it did until latest grub.

---

### Post by sgage on 2012-09-18
> **philinux said:**
> This test lappy has win 7 and 12.10. It's been fine booting using easybcd into grub. (grub installed to sda4 partition0 

Latest update with new grub now drops to grub prompt.

I've updated to latest easybcd version and reinstalled the daily live today.

Same thing.

Any ideas how to debug this. 

I'm loathed to install grub to MBR as it might screw up the lappy completely.

I am seeing the same behavior. Try telling EasyBCD that the grub is "legacy grub", and explicitly tell it which partition it's on. That worked for me when I had grub on /dev/sda2, but not with grub on /dev/sda5 - just got a blinking cursor (not even the grub prompt).

I, too, prefer to have the Windows bootloader in the MBR - for one thing, Windows won't hibernate with grub in the MBR...

---

### Post by oldfred on 2012-09-18
Hibernation and dual booting can be risky. Even if two versions of Windows.

Any write into a hibernated Windows will be lost as the hibernated Windows will not see it. And if you edit and move a file that was in the hibernated system it corrupts the hibernation as it cannot then find it.

---

### Post by sgage on 2012-09-18
> **oldfred said:**
> Hibernation and dual booting can be risky. Even if two versions of Windows.

Any write into a hibernated Windows will be lost as the hibernated Windows will not see it. And if you edit and move a file that was in the hibernated system it corrupts the hibernation as it cannot then find it.

??? How do you write into a hibernated Windows? If it's hibernated, the computer is off. When you turn it off, it boots to the hibernated Windows.

---

### Post by philinux on 2012-09-18
> **sgage said:**
> I am seeing the same behavior. Try telling EasyBCD that the grub is "legacy grub", and explicitly tell it which partition it's on. That worked for me when I had grub on /dev/sda2, but not with grub on /dev/sda5 - just got a blinking cursor (not even the grub prompt).

I, too, prefer to have the Windows bootloader in the MBR - for one thing, Windows won't hibernate with grub in the MBR...

I'll give that a whirl later. :)

---

### Post by philinux on 2012-09-19
Sorted. Now I'm back to dual booting and testing 12.10 on this lappy.

Live usb of 12.04.1 used. On my dual boot root is on /dev/sda5

$ sudo mount /dev/sda5 /mnt
then
$ sudo grub-install -f --root-directory=/mnt/ /dev/sda

( -f is needed else it throws the blocklists error. )

I first tried the chroot method and it re-installed grub but would still not boot from easybcd. Since it would have installed the new grub version.

There must be something new in the 12.10 grub that easybcd cant work with.

No point bugging it either.

[edit] I raised a bug thread on easybcd's forum]

---

### Post by jerrylamos on 2012-09-19
> **philinux said:**
> I'm loathed to install grub to MBR as it might screw up the lappy completely. Yea, verily.  On this Acer Aspire 5253 Grub loves to screw up the Windows 7 dual boot.  Super Grub2 usually bails me out.

My dodge is to take a leftover 2.5" laptop HD - even if you don't have one laying around, they're cheap at the local used computer parts store - then put it in a cheap USB case - $10 from Tiger Direct etc.

Then put Ubuntu stuff on the USB hard drive, and REMEMBER, be careful to specify /dev/sdb on install....and set bios to boot off USB first if it is plugged in.

This way, Windows 7 hasn't been clobbered for the last couple development releases even through the usual very messy Ubiquity throes.

---

### Post by philinux on 2012-09-19
> **jerrylamos said:**
> Yea, verily.  On this Acer Aspire 5253 Grub loves to screw up the Windows 7 dual boot.  Super Grub2 usually bails me out.

My dodge is to take a leftover 2.5" laptop HD - even if you don't have one laying around, they're cheap at the local used computer parts store - then put it in a cheap USB case - $10 from Tiger Direct etc.

Then put Ubuntu stuff on the USB hard drive, and REMEMBER, be careful to specify /dev/sdb on install....and set bios to boot off USB first if it is plugged in.

This way, Windows 7 hasn't been clobbered for the last couple development releases even through the usual very messy Ubiquity throes.

Yep but I've fixed it now and easybcd is in charge again. Yeah :p

See post #8

---

### Post by sgage on 2012-09-19
> **philinux said:**
> Sorted. Now I'm back to dual booting and testing 12.10 on this lappy.

Live usb of 12.04.1 used. On my dual boot root is on /dev/sda5

$ sudo mount /dev/sda5 /mnt
then
$ sudo grub-install -f --root-directory=/mnt/ /dev/sda

( -f is needed else it throws the blocklists error. )

I first tried the chroot method and it re-installed grub but would still not boot from easybcd. Since it would have installed the new grub version.

There must be something new in the 12.10 grub that easybcd cant work with.

No point bugging it either.

[edit] I raised a bug thread on easybcd's forum]

Works for me, too, except I get a few 'file not found' errors before the grub menu comes up. But everything works fine...

---

### Post by funicorn on 2012-09-19
grub has upgraded to version 2.00, one largely different from 1.99. I think easybcd fails reasonably.

---

### Post by philinux on 2012-09-19
> **funicorn said:**
> grub has upgraded to version 2.00, one largely different from 1.99. I think easybcd fails reasonably.

I had a response to my easybcd bug thread.  A beta version is out. Will test this next week.

[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

---

### Post by philinux on 2012-09-20
Tested today.

Installed the new easybcd version 2.2 beta build 180.

Deleted linux entry first and the added a new one. This version allows the user to specify where grub2 is installed. In my case /dev/sda5.

Booted into 12.10 fine. Then I ran sudo grub-install -f /dev/sda5 to install the 12.10 version of grub.

Rebooted and all fine. :p

---

### Post by sgage on 2012-09-20
> **philinux said:**
> Tested today.

Installed the new easybcd version 2.2 beta build 180.

Deleted linux entry first and the added a new one. This version allows the user to specify where grub2 is installed. In my case /dev/sda5.

Booted into 12.10 fine. Then I ran sudo grub-install -f /dev/sda5 to install the 12.10 version of grub.

Rebooted and all fine. :p

Thanks for the word. I picked up the beta build, and it works fine...

---

