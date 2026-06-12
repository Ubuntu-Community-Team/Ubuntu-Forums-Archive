---
title: "ext4 bugs :("
date: 2009-12-30
forum: The Cafe
---

### Post by chris200x9 on 2009-12-30
I'm mainly here to vent, but what genius decided to include ext4 in the stable kernel? Almost everytime I hard reboot something gets corrupted! First my /etc/rc.conf and now my ~/.conkyrc grrr

---

### Post by Skripka on 2009-12-30
> **chris200x9 said:**
> I'm mainly here to vent, but what genius decided to include ext4 in the stable kernel? Almost everytime I hard reboot something gets corrupted! First my /etc/rc.conf and now my ~/.conkyrc grrr

Are you powering down your machine properly, and/or are your drives getting unmounted prior to shutdown/reboot.

---

### Post by chris200x9 on 2009-12-30
> **Skripka said:**
> Are you powering down your machine properly, and/or are your drives getting unmounted prior to shutdown/reboot.

no, hard reboot I know no filesystem should safe guard me against user error, but ext3 never had a problem. Sometimes things like shutting down improperly just happen, from my point of view this is a major regression.

---

### Post by Crunchy the Headcrab on 2009-12-30
> **chris200x9 said:**
> [SIZE=5][COLOR=Red]Almost everytime I hard reboot something gets corrupted! [/COLOR][/SIZE]First my /etc/rc.conf and now my ~/.conkyrc grrr

Um...okay.  I love EXT4.  I don't think you can blame the entirety of the OS's (or your hardware's) issues on a new file system.

---

### Post by RiceMonster on 2009-12-30
> **Crunchy the Headcrab said:**
> Um...okay.  I love EXT4

Works for you != works for him


That said, ext4 works just fine on both my computers. No problems here.

---

### Post by Skripka on 2009-12-30
Some light reading:

[http://www.h-online.com/open/news/item/Ext4-data-loss-explanations-and-workarounds-740671.html](http://www.h-online.com/open/news/item/Ext4-data-loss-explanations-and-workarounds-740671.html)

Also a brief bit is in the Arch Wiki on the topic, but applies to any *nix system using Ext4:

[http://wiki.archlinux.org/index.php/Ext4#Data_Corruption](http://wiki.archlinux.org/index.php/Ext4#Data_Corruption)

---

### Post by DasEi on 2009-12-30
can't confirm that also, ext4 worked nice here, even a brutal damaged partitiontable could be recovered by testdisk and I'm also a one who pulls
the plug of my pc-tv from bed, so cold down.
only thing I found with older ext-drivers for windows is that that corrupts the table / fsck for ubuntu , which did not in ext3
there are options o'cause to get more performance by caching writes in memoy, like sync or relatime in fstab

---

### Post by spongypants23 on 2009-12-30
See, now it's your own fault, not EXT4's. Reboot properly.

---

### Post by Skripka on 2009-12-30
> **DasEi said:**
> 
only thing I found with older ext-drivers for windows is that that corrupts the table / fsck for ubuntu , which did not in ext3

That would be because the Win Ext2 IFS driver does not support Ext4...

---

### Post by lovinglinux on 2009-12-31
I have been using ext4 since Jaunty and it is very reliable for me, even with several power outages, some hard boots and a few partition space redistributions.

---

### Post by HappyFeet on 2009-12-31
> **lovinglinux said:**
> I have been using ext4 since Jaunty and it is very reliable for me, even with several power outages, some hard boots and a few partition space redistributions.

Same here, no problems since jaunty beta. Ext4 bugs are rare.

EVERYONE, STOP USING IT. ONE PERSON IS HAVING A PROBLEM WITH IT!

---

### Post by Khakilang on 2009-12-31
Almost 2 month now and I don't have any issue with ext4. Is your hard disk new? Maybe aging hard disk could corrupt.

---

### Post by venator260 on 2009-12-31
I think that the answer for you is to stop using Ext4. It seem to me that Ext4 still has a few kinks in it, so if your data is worth more than the speed advantages that you get from Ext4, use something else, the options are out there.

---

### Post by handy on 2009-12-31
I guess the user will have to do a full system rebuild on the Ext4 partitions.  

I know you can't convert other file systems to Ext4, so I expect you can't convert to other file systems from Ext4?

Which is a real drag imho.

---

### Post by Methuselah on 2009-12-31
DO NOT HARD REBOOT!

This is very important!
If your desktop seems to hang try to kill X (right Alt + PrintSrc + k).
If you have to hard reboot on a regular bassis something is seriously wrong with your system.

---

### Post by handy on 2009-12-31
You should be able to turn of caching on the HDD, & providing there is enough RAM, 1GB is more than enough for me I don't even run /swap.  Then when the thing goes down cold what has it got to loose.

Or is it somehow more complicated than that these days?

---

### Post by Xbehave on 2009-12-31
I have rubbish hardware and often have to hard reboot due to hw errors, ext4 hasn't given me any problems but my hardware problem means nothing gets stopped mid write.

ext4 will hold stuff in ram for longer but you can prevent corruption by doing data journaling (it will reduce performance slightly but, it means nothing will get corrupted)

Why are you hard rebooting anyway?
If you can, try doing it safely
alt+prntscr+U
alt+prntscr+S
alt+prntscr+B

---

