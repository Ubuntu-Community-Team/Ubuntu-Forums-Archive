---
title: "Harddrive Partition problems"
date: 2007-03-04
forum: Windows
---

### Post by PhilDes14 on 2007-03-04
I am fairly new to Ubuntu and i am having some difficulty getting into my windows partition.  I have  followed several instructions, however it does not seem to be working.  If anyone can tell me how i can get my /fstab_backup instead of the mess i have now... i can give it another try.
thanks

---

### Post by raja on 2007-03-04
I am sorry, but I have difficulty understanding you question. It may be useful to phrase your question again. Assuming that you mean you have backed up your original fstab as fstab_backup and that you are unable to access your windows partition from linux and that you want to restore the backup file as the fstab, all you have to do is rename that file as fstab. From the terminal, you just type ```
sudo mv /etc/fstab_backup /etc/fstab
``` If this was not your question at all, I am sorry.

---

### Post by PhilDes14 on 2007-03-04
No...perfect answer
thanks a bunch you are good for being able to understand my nonsense.

---

### Post by PhilDes14 on 2007-03-04
Perhaps I can get assistance on another problem.  This is what my fdisk -l looks like.
[B]
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6519    52363836    7  HPFS/NTFS
/dev/hda2            6520        7260     5952082+  83  Linux
/dev/hda3            7261        7297      297202+   5  Extended
/dev/hda5            7261        7297      297171   82  Linux swap / Solaris[/B]

I know that my windows partition is /dev/hda1,  now look at my original /fstab.

[B]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4973044a-2825-4b28-a017-8e8bc838a148 /        ext3    defaults,errors=remount-ro 0  1
# /dev/hda5
UUID=c5a450a7-03ca-463f-893b-171c5c2a0c99 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[/B]

my hda1 does not appear on my /fstab.  
I followed the [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) directions correctly but how do I mount something that does not show up? I attempted to enter my type in the new **/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0** ...but that is pointless.  Has anyone encountered this before and can give me some help, or is it a critical error?

---

### Post by raja on 2007-03-05
Can you try ```

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows
``` and see if the drive gets mounted

---

### Post by corbeau on 2007-03-17
I do not think that this will be of any help but, it might help getting the topic moving forward.

Here is my own little story.
My computer dies with Linux MINIMEE on it. It was an old machine, I was spreading its life. My hard disks have all my stuff on it and they are formatted "Linux".
I buy a computer (HP Entertainment Center) HP Pavilion a1710n. Nice little home machine. 
It has got a Vista home edition on it. Pretty but I got contaminated by Linux a year ago and I like it. I want to have dual-boot. However I am dumb and illiterate. 

So, here is how it goes, I get a copy of Xandros. I use the Xandros 4.0 CD and redo the partitions on the drive with it. Download all sort of stuff to go on it. Spent two evenings doing that. I always reboot in Xandros, everything is fine.
So, now I want to do some stuff in Windows and try to boot in Vista....
Recovery program starts (no problem, I am diligent, I have burned my recovery disks). So....... the thing hangs, gets to the Microsoft logo, HDD light flashes a bit, stop, the little gif from MS spins (as if it had a heart beating) everything is fine and then, the screen goes off and I wait....wait a bit more, nothing.

I take my recovery CD, boot from it and get a message:
Last windows shut down, the system hanged, running diagnostic tools and then, same as above.

Not losing my senses, I wait a bit.... and gathering all my will, I press on the power switch for 5 seconds. Computer shuts down and then, with a second pressing on the same button, it boots again: same thing. Try without CD and,  after having chosen to boot in windows recovery partition, same as above.

OK, OK no problem, I have this PC-Doctor disk I burned as well so I run it and choose the option to run a test on the HDD. Takes an hour, I am hungry so I make myself a nice supper (pasta with a nice tomato and swiss cheese Rose sauce; Its my own and I have impress a few with it and sometimes, even myself). I had a good time. 

Get back to my nice little machine, nothing, my disk is fine. Great, I go back in Xandros after having had a chat with a friend and download Ubuntu 6.10 since it is supposed to deal better with new Vista partitionning parameters. I do the partition routine, Ubuntu does not want to touch the Windows partition (lock, frozen, I don't know). Nevertheless, I install Ubuntu onto the Xandros partition after having repartitionned it. 

I really like Ubuntu. I started to download all sort of stuff for it and, I'm in the learning curve. Let's say that I am at the bottom of a cliff. Nevertheless, I like the OS. 

However, Windows does not boot. It's not the end of the world but I still need it for work purposes now and then and I had problems with that in the last year. 

So, does someone know anything about that kind of problem ?

---

