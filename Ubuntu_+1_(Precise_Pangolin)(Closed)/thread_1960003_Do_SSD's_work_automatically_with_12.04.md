---
title: "Do SSD's work automatically with 12.04?"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by williammanda on 2012-04-16
I was looking into buying a SSD but wondered if there would be any problems / special setup that I'm unaware of.

---

### Post by ajgreeny on 2012-04-16
It should just work, but you may want to remove the journalling from the ext4 filesystem to prolong the disk's life by reducing writes to disk, which you can do with tune2fs.
See man tune2fs for details; something like ```
sudo tune2fs 0 has_journal /dev/sdx#
``` I think.

---

### Post by pqwoerituytrueiwoq on 2012-04-16
> **ajgreeny said:**
> It should just work, but you may want to remove the journalling from the ext4 filesystem to prolong the disk's life by reducing writes to disk, which you can do with tune2fs.
See man tune2fs for details; something like ```
sudo tune2fs 0 has_journal /dev/sdx#
``` I think.
that any different than using noatime in fstab on the partition on the ssd?
does than enable trim aka discard in fstab?

if you have a lot of ram put /tmp on your ram you will squeeze more like out of a ssd that way especally if you do a lot of disk burning

---

### Post by SlugSlug on 2012-04-17
am pretty sure ssd's are lasting as long as mechanical drives these days, I did a fresh install onto SSD it aligned it correctly and I think it added the discard option for me to (tho i may have done that).

---

### Post by Kronalias on 2012-04-17
I think the command is missing a carat - 

Assuming the ext4 partition that we want to remove the journal from is /dev/sda1, you would issue the following command:
sudo tune2fs -O ^has_journal /dev/sda1
Then, it&#8217;s a really good idea to run a filesystem check:
sudo e2fsck -f /dev/sda1
I&#8217;ve read some reports of filesystems not mounting if the second step is not done, so don&#8217;t skip it &#8211; since you have a solid-state drive, a fsck runs extremely quickly.

Now restart the computer, booting from the solid-state drive containing the ext4 partition you just de-journaled.  Open a command prompt and run:
dmesg | grep EXT4
Don't worry about any re-mount messages you see - they're normal.
If all went well you will see the following message from the boot process:
EXT4-fs (sda1): mounted filesystem without journal
If you ever want to add the journal back on, just run the steps above, but remove the caret (^) from the tune2fs command.

The other thing you might think about is ditching the swap partition, or alternatively lowering the swappiness - see [this]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")

---

### Post by Bobhuber on 2012-04-17
> **williammanda said:**
> I was looking into buying a SSD but wondered if there would be any problems / special setup that I'm unaware of.
Should work just fine. Just make sure to format as ext4 using gparted (which will automatically align the partions correctly) and leave journaling enabled with noatime and discard specified in fstab.I also moved all my log files and /tmp and /Download directories to my second sata drive and use symlinks for these to save writes on the SSD.On a fast system the SSD is the final step to amazing speeds.

---

### Post by fooman on 2012-04-17
Afaik,  you have to add "discard" option manually (at least I did).

That and putting temp in ram were the only tweaks that I have added to my ocz 120gb ssd.

---

### Post by pqwoerituytrueiwoq on 2012-04-17
anyone know any details on this setting?
"Switching IO Schedulers" section of this guide:
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

---

### Post by oldfred on 2012-04-17
I added noatime & discard as mentioned above but also used gpt and kept root about 25% full as recommended by the Arch link. 

I also did not use swap on SSD (it found an old swap on rotating drive), and kept /home on SSD, but all data including some of the hidden folders is on my rotating drive and linked back to /home. So /home on SSD really only has user settings.

Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

I forgot to add discard right away.

Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

---

