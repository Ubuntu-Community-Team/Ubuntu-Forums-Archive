---
title: "i have to go back to windows...."
date: 2009-04-25
forum: The Cafe
---

### Post by JakeHinojosa on 2009-04-25
since my usb internet adapter thing only works on windows. my laptop cant use wired internet and my wireless card is not working. so i have to use windows..... until i get the gazelle ultra computer from system76.com :)
but let me ask this, how do i remove ubuntu?

edit: the gazelle ultra computer runs ubuntu.

---

### Post by Eviltechie on 2009-04-25
You could install windows over it. But if you have a dual boot, just resize the windows partition to overtake the linux one.

---

### Post by JakeHinojosa on 2009-04-25
> **Eviltechie said:**
> You could install windows over it. But if you have a dual boot, just resize the windows partition to overtake the linux one.

i need it fully removed because i need to sell my computer to buy a new one. people will want the computer with windows on it. not ubuntu.

---

### Post by gletob on 2009-04-25
Oh come on are you sure you've tried your best?

To remove Ubuntu:
download a partitioner live cd. (gparted)
Put in your windows cd.
Get to a command promot.
type "FIXMBR" (no quotes)
boot into gparted and delete ubuntu partitions and resize windows partition.
Reboot

---

### Post by lisati on 2009-04-25
If you're selling your machine, it might be safer (and easier) just to restore your Windows from the recovery partition or recovery DVD.

---

### Post by mamamia88 on 2009-04-25
you could boot grub live cd delete all partitions and create 1 big ntfs partition with freed space and install windows on it.  easiest way i think

---

### Post by Wiebelhaus on 2009-04-25
No worries , good luck! but I must mind you to guard your "prison wallet" from the capitalists!

Cheers!

---

### Post by LookTJ on 2009-04-25
Step 1: use DBAN to wipe the hard drive: 3 passes to be safe

Step 2: install Windows

Step 3: configure and install drivers

Step 4: sell the computer



This is my suggestion. :) Good luck!

---

### Post by Mehall on 2009-04-25
> **Taylor said:**
> Step 1: use DBAN to wipe the hard drive: 3 passes to be safe

Step 2: install Windows

Step 3: configure and install drivers

Step 4: sell the computer



This is my suggestion. :) Good luck!

if you're only gonna 3 pass it, "sudo dd if=/dev/urandom of=/dev/hda" is just as good (or /dev/null instead of /dev/urandom if you're feeling lazy)

---

### Post by dragos240 on 2009-04-25
Sad to see someone leave, it happens occasionally. Have fun!

---

### Post by LookTJ on 2009-04-25
> **Mehall said:**
> if you're only gonna 3 pass it, "sudo dd if=/dev/urandom of=/dev/hda" is just as good (or /dev/null instead of /dev/urandom if you're feeling lazy)
:) I wanted him to safeguard his data so that others will not recover it. But yeah, that's another way to overwrite blocks.

---

### Post by Mehall on 2009-04-25
> **Taylor said:**
> :) I wanted him to safeguard his data so that others will not recover it. But yeah, that's another way to overwrite blocks.

3 pass is not much better than a simple dd, but even a simple dd (even using /dev/null ) is strong enough for any commercial data recovery experts to refuse to even try most of the time. Unless the NSA is after you (in which case, you want to put DBAN on continuous repeat ;) then a simple dd will suffice.

---

### Post by gymophett on 2009-04-25
What type of USB Wireless adapter to you have? There may be a fix. I'll try and help.

---

### Post by Wiebelhaus on 2009-04-25
> **Mehall said:**
> 3 pass is not much better than a simple dd, but even a simple dd (even using /dev/null ) is strong enough for any commercial data recovery experts to refuse to even try most of the time. Unless the NSA is after you (in which case, you want to put DBAN on continuous repeat ;) then a simple dd will suffice.

No reason to split hairs over some stolen mp3's and adult content , format the drive and it's gone , let's be realistic here , we aren't talking to Warren Buffet or Trump or Bill Clinton , if your not important or rich then a simple format or partition deletion will suffice , don't cha think?

---

### Post by LookTJ on 2009-04-25
> **Mehall said:**
> 3 pass is not much better than a simple dd, but even a simple dd (even using /dev/null ) is strong enough for any commercial data recovery experts to refuse to even try most of the time. Unless the NSA is after you (in which case, you want to put DBAN on continuous repeat ;) then a simple dd will suffice.
Thanks for this little advice.  I'll keep it for the future.

---

### Post by JakeHinojosa on 2009-04-25
> **dragos240 said:**
> Sad to see someone leave, it happens occasionally. Have fun!

im coming back when i buy a new computer.

---

### Post by Mehall on 2009-04-25
> **sx66gns said:**
> No reason to split hairs over some stolen mp3's and adult content , format the drive and it's gone , let's be realistic here , we aren't talking to Warren Buffet or Trump or Bill Clinton , if your not important or rich then a simple format or partition deletion will suffice , don't cha think?

Actually, I could recover from that.

It would take effort, but the only tool I would need is the BackTrack Live CD.

If it's not overwritten, then it's not gone. Deleting a partition doesn't overwrite all the blocks, nor does a simple format. Nor does a "full" format as Windows would do it. You need to dd or DBAN it if you want it gone, even just from freely available tools.

---

### Post by JakeHinojosa on 2009-04-25
and i dont have any blank CDs or usb flash drives or anything. all i have is a windows XP cd. but i tried to boot from it but it didnt work.

---

### Post by Methuselah on 2009-04-25
Sometimes you can get USB wireless adapters to work in Ubuntu using the windows drivers and ndiswrapper.
That's what I did with my 2wire adapter.

---

### Post by JakeHinojosa on 2009-04-25
> **Methuselah said:**
> Sometimes you can get USB wireless adapters to work in Ubuntu using the windows drivers and ndiswrapper.
That's what I did with my 2wire adapter.

huh?

---

### Post by sailthesea on 2009-04-25
JakeHinojosa
 I Think your thread has been a bit hijacked 
But if you have your XP disc and have removed any files you don't want others to see then you should be able to reboot press F12 and reinstall XP removing all trace of ubuntu

---

### Post by JakeHinojosa on 2009-04-25
> **Methuselah said:**
> Sometimes you can get USB wireless adapters to work in Ubuntu using the windows drivers and ndiswrapper.
That's what I did with my 2wire adapter.

how do i use ndiswrapper?

---

### Post by JakeHinojosa on 2009-04-25
> **sailthesea said:**
> remove any files you don't want others to see then you should be able to reboot press F12 and reinstall XP removing all trace of ubuntu

...

---

### Post by Methuselah on 2009-04-26
> **JakeHinojosa said:**
> how do i use ndiswrapper?


Here is an example:
[http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html](http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html)

---

