---
title: "I don't believe this: Windows saves my Ubuntu installation"
date: 2006-04-13
forum: The Cafe
---

### Post by Derek Djons on 2006-04-13
Well, today was a normal day for me. From work I went straight home and booted Ubuntu Linux. I used the terminal to quickly update my installation* while reading the news and doing some artwork in Gimp.

* sudo apt-get update
   sudo apt-get upgrade
After a couple of hours and the completion of the updates I was done and needed to reboot to Windows for DreamWeaver.

As I rebooted and my notebook passed POST something else appeared instead of GRUB:

Grub can't be read, followed by a blinking cursor. I thought it might be something weird. So I unplugged the powercord and removed the batt. for three minutes. After I booted my notebook the same error came to me.

I had this joke once before. So I knew... I could easily overwrite my MBR with the Windows CD and be able to boot Windows (better than nothing). So I did that. I booted the Windows CD and got myself to the Rescue mode. There I used:

fixboot c:
- The MBR got overwritten and I rebooted my machine.

But instead of Windows booting, GRUB appeared with my Ubuntu installation, all previous Kernels and Windows XP in it.

I'm still confused about WTF happened and how fixboot can see or manage 3rd party MBR's. Well, I'm glad it works... it saves me hell of work finding out / reinstalling Ubuntu.

---

### Post by Monster_user on 2006-04-13
:o :confused: 

That is the first time I've heard that. That is something.

---

### Post by syg00 on 2006-04-13
Fixboot updates the boot sector record, _not_ the MBR.
Coincidence - M$oft has never shown any inclination in assisting the open source world.

---

### Post by prizrak on 2006-04-13
[QUOTE=syg00]Fixboot updates the boot sector record, _not_ the MBR.
Coincidence - M$oft has never shown any inclination in assisting the open source world.[/QUOTE]
So Windows is good for something sometimes by accident ;)

---

### Post by red_Marvin on 2006-04-13
Now keep quiet about this, or else windows fixxboot will start to rewrite mbr soon ;) ...

---

### Post by NeghVar on 2006-04-13
Extend, Embrace, Extinguish... I think they are extending their olive branch... qwuick, before they sharpen the other end lets beat em to it and sharpen our end into the tip of a spear...

---

### Post by rfruth on 2006-04-13
miracles never cease :confused:

---

### Post by Derek Djons on 2006-04-13
[QUOTE=syg00]Fixboot updates the boot sector record, _not_ the MBR.
Coincidence - M$oft has never shown any inclination in assisting the open source world.[/QUOTE]

Thank you for fishing out my error! syg00. There's indeed a big difference between the two.

---

### Post by John.Michael.Kane on 2006-04-13
I guess Good Stuff happens sometimes when you use MS...

---

### Post by Derek Djons on 2006-04-14
This morning I got the same error again. So something is definitelly wrong with my installation. Using fixboot c: didn't worked this time. I used fixmbr to boot Windows. Later on today I will be reinstall Ubuntu 6.06 Dapper Drake.

---

### Post by syg00 on 2006-04-14
Like I said, coincidence.

Backup anything you consider important.
**_NOW_**

---

### Post by BoyOfDestiny on 2006-04-14
[QUOTE=syg00]Like I said, coincidence.

Backup anything you consider important.
**_NOW_**[/QUOTE]

Agreed, also have you been running dapper? I think doing a dist-upgrade instead of upgrade is the way to go. Not sure if that'll prevent breakage, but my dappers have been running smoothly for months (32 and 64).

On a somewhat related note, and I think you'll get it a kick out of it:

*Some Mac users are reporting problems with Apple's Boot Camp, the software that lets Intel-based Macs run Windows. Ironically, some users have said been stuck with Windows, with their hardware left unable to reboot the Mac OS.*
[http://www.pcworld.com/news/article/0,aid,125393,00.asp](http://www.pcworld.com/news/article/0,aid,125393,00.asp)

---

### Post by ice60 on 2006-04-14
you can use gag if grub/mbr breaks. i've never used it but i heard about it on a podcast yesterday :D just put the iso on a disk
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

[img]http://gag.sourceforge.net/gagn3.gif[/img]

---

### Post by bonzodog on 2006-04-14
GAG doesn't support Ext3 or ReiserFS partitions though, and to use it, you have to create an ext2 /boot partition.

---

### Post by NeghVar on 2006-04-14
Ahh... so we are reaching the extinguish faze already?

---

### Post by Derek Djons on 2006-04-14
[QUOTE=NeghVar]Ahh... so we are reaching the extinguish faze already?[/QUOTE]
LOL... it sure as hell sound like it.

[QUOTE=syg00]Like I said, coincidence.

Backup anything you consider important.
NOW[/QUOTE]
I'm glad I learned from previous mistakes... data is not a problem. Got it stashed and ready for redeployment :)

---

