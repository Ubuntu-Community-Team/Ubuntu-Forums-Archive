---
title: "Well...i think i've finally done it"
date: 2007-01-04
forum: Windows
---

### Post by jdhore on 2007-01-04
well...for the past few days my Windows install has been giving me massive problems and i knew i was dual-booting the system with Edgy...so i decided to just basically say screw windows and now i think (if i could figure out how), i'm moving to Linux full-time...i really only have 3 questions for you all:

1. Is there an easy way to get NTFS-3G to work so i can start moving all my music, movies, etc. off my windows partition?
2. Can an application like Gparted (either the live CD or running it inside Linux) resize my EXT3 partition to make it take up most of the HD (once i delete the NTFS partition of course)?
3. I use this application: [http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/) to send files to people, my question is, is there a Linux alternative (that's as easy to use) or do you all think it can be run in Wine (or Crossover Office). EDIT: i just tested it with Wine...that option is out.?

Thanking you all in advance for your help...and i hope to be a full-time Linux user soon
JD

---

### Post by chrisccoulson on 2007-01-04
Hi! I recently moved away from Windows so I should be able to help you a little here:

1) If you are copying files from your Windows partition to your Linux partition, then do you really need NTFS write support? If not, you can mount the NTFS partition read-only without needing NTFS-3G.
2) I assume your NTFS partition is physically located before your Linux partition (which I assume is ext3?). If so, there is no easy way to resize your ext3 partition, as it is anchored at the start of the partition. The end of an ext3 partition can be resized to take up space after the end of the partition. I recently had a similar issue where I had my root partition at the end of my disk, and wanted to make it bigger. The way I did this was to delete and resize partitions before my ext3 filesystem in order to make some room, and then create a new partition in the free space. I then copied files across, deleted the old partition and then resized the new partition to fill the space. It worked for me, but you must make sure you've got a good backup of all your important data.
3) I'm not too sure about this one as I haven't done anything like this before.

Hope that helps

---

### Post by meng on 2007-01-04
1. If you're just copying, you don't need write support. Don't fool with ntfs-3g unless you need to. I've never used it, but I consider it "experimental"; others may disagree of course.
2. Download the latest GPartedLiveCD, I think it has support for moving ext3 partitions, not just resizing them. I've used it and had no problems (but beware because it is also considered "experimental" - I guess that makes me a bit of a hypocrite :D)
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
Don't ever repartition running inside your installed Linux, use a LiveCd instead.
3. I am sure there's an alternative, you may wish to start a new thread describing in more detail what you're trying to achieve. It may not necessarily be done in exactly the same way as you are doing now, so describe it in terms of goals rather than means. You may be pleasantly surprised and find that there's an easier and/or more secure way of doing it in Linux.

Good luck!!!

---

### Post by jdhore on 2007-01-04
> **chrisccoulson said:**
> Hi! I recently moved away from Windows so I should be able to help you a little here:

1) If you are copying files from your Windows partition to your Linux partition, then do you really need NTFS write support? If not, you can mount the NTFS partition read-only without needing NTFS-3G.
2) I assume your NTFS partition is physically located before your Linux partition (which I assume is ext3?). If so, there is no easy way to resize your ext3 partition, as it is anchored at the start of the partition. The end of an ext3 partition can be resized to take up space after the end of the partition. I recently had a similar issue where I had my root partition at the end of my disk, and wanted to make it bigger. The way I did this was to delete and resize partitions before my ext3 filesystem in order to make some room, and then create a new partition in the free space. I then copied files across, deleted the old partition and then resized the new partition to fill the space. It worked for me, but you must make sure you've got a good backup of all your important data.
3) I'm not too sure about this one as I haven't done anything like this before.

Hope that helps

1. I don't want to boot into the borked Windows install if i can help it...so i guess NTFS-3G is my best option (plus i have a external HD that's NTFS) :( oh, and yes my Linux partition is EXT3)

2. yeah, my NTFS partition is apparently partition 1...but in Windows, at least 80% of my space was taken up by torrents and Limewire downloads so i should just be able to say screw it, create a 2nd EXT3 partition in the space that the Windows partition was in and use that partition for all my torrents and Limewire stuff.

---

### Post by meng on 2007-01-04
> **jdhore said:**
> 1. I don't want to boot into the borked Windows install if i can help it...so i guess NTFS-3G is my best option (plus i have a external HD that's NTFS) :( oh, and yes my Linux partition is EXT3)
One of us is missing something here, and I think it's you not me :D
From Linux, you can READ or COPY files on an NTFS partition, with ntfs support (built-in). ntfs-3g support is only required if you want to WRITE to an NTFS partition.
As for #2, please read my comment again.

---

### Post by jdhore on 2007-01-04
> **meng said:**
> 1. If you're just copying, you don't need write support. Don't fool with ntfs-3g unless you need to. I've never used it, but I consider it "experimental"; others may disagree of course.
2. Download the latest GPartedLiveCD, I think it has support for moving ext3 partitions, not just resizing them. I've used it and had no problems (but beware because it is also considered "experimental" - I guess that makes me a bit of a hypocrite :D)
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
Don't ever repartition running inside your installed Linux, use a LiveCd instead.
3. I am sure there's an alternative, you may wish to start a new thread describing in more detail what you're trying to achieve. It may not necessarily be done in exactly the same way as you are doing now, so describe it in terms of goals rather than means. You may be pleasantly surprised and find that there's an easier and/or more secure way of doing it in Linux.

Good luck!!!

1. my biggest reasons for trying to use NTFS-3G were the fact that i have an external HD formatted as NTFS and i wanted to totally move stuff off the Windows partition just so i knew where i stand on what's moved, what's not and freespace and stuff.

2. Thanks

3. I posted here, i posted in Networking & Wireless, but no replies yet...anywhere else you think i should post that topic?

---

### Post by meng on 2007-01-04
1. Okay. Thanks for making that clear.
2. Hope it works for you.
3. Be patient, some threads take hours/days to get a response.

---

### Post by Dr. C on 2007-01-05
I would first try a search for NTFS in Synaptic. (System > Administration > Synaptic Package Manager ) Make sure you have all the repositories enabled including Universe and Multiverse. This is the first place I look when looking for software tools.  If you are running Ubuntu Edgy then the ntfs-3g driver can be installed directly from Synaptic.. There are also some useful tools to work with NTFS partitions present in both Dapper and Edgy 

There is  thread on NTFS-3G that explains how to install it for Dapper and also Edgy
[http://www.ubuntuforums.org/showthread.php?t=217009]("http://www.ubuntuforums.org/showthread.php?t=217009")

There is also helpful information at 

[http://www.linux-ntfs.org/]("http://www.linux-ntfs.org/")

I hope this helps.

---

### Post by Sef on 2007-01-05
Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").  It can read and write to NTFS.

---

