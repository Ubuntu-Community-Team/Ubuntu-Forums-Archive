---
title: "Best live CD to resize NTFS partitions"
date: 2005-09-27
forum: The Cafe
---

### Post by timelord726 on 2005-09-27
I finally convinced my mom to try Linux in a dual boot environment!  Woot!  :D

Anyway, her computer only has a CD-RW drive and so cannot read DVDs, and I am wondering what the best live CD would be to attempt to resize her NTFS partition so that the Ubuntu installer may do its work.

Thanks very much for any advice offered!

---

### Post by Ubunted on 2005-09-27
The Ubuntu installer itself does a pretty good job of it for me.

---

### Post by YourSurrogateGod on 2005-09-27
Is this actually possible without losing information on the NTFS partition granted that you can't write to an NTFS partition?

---

### Post by timelord726 on 2005-09-27
I've never known that the Ubuntu installer can resize NTFS partitions.  Is this new?  Or am I just ignorant of a feature that's been there for a while?

---

### Post by darkmatter on 2005-09-27
[QUOTE=YourSurrogateGod]Is this actually possible without losing information on the NTFS partition granted that you can't write to an NTFS partition?[/QUOTE]

Yes, it can be done without data loss, as long as a defrag (or several;) ) is done to the NTFS partition first.

If you a a defragmentation program that can run at boot time, even better, as it will not only defrag, but move the data as well, so there are no stray files.

---

### Post by BWF89 on 2005-09-27
Try the System Rescue CD:
[http://www.sysresccd.org/](http://www.sysresccd.org/)

It's basically a clone of Partition Magic 8.

---

### Post by timelord726 on 2005-09-27
Thanks for the advice, everyone.  I'll be sure to give a couple of these a whirl.  The sooner I can get my mom to try out Ubuntu and realize it's not as scary as it seems, the better.  :D

---

### Post by YourSurrogateGod on 2005-09-27
[QUOTE=darkmatter]Yes, it can be done without data loss, as long as a defrag (or several;) ) is done to the NTFS partition first.

If you a a defragmentation program that can run at boot time, even better, as it will not only defrag, but move the data as well, so there are no stray files.[/QUOTE]
News to me...

I figured that you couldn't do it since the it's impossible to write to an NTFS partition in a stable manner, as I've heard. Otherwise, I would have quessed that it would be possible to mount an NTFS partition for reading and writing in Ubuntu.

---

### Post by darkmatter on 2005-09-27
[QUOTE=YourSurrogateGod]News to me...

I figured that you couldn't do it since the it's impossible to write to an NTFS partition in a stable manner, as I've heard. Otherwise, I would have quessed that it would be possible to mount an NTFS partition for reading and writing in Ubuntu.[/QUOTE]

Ahhh...misunderstood your post. I was talking about the resize alone.

---

### Post by YourSurrogateGod on 2005-09-27
[QUOTE=darkmatter]Ahhh...misunderstood your post. I was talking about the resize alone.[/QUOTE]
*shrug* I didn't know that you could resize a partition without losing some data on it if you couldn't write to it...

---

### Post by darkmatter on 2005-09-27
Don't get me wrong. I'm not saying data CAN'T be lost, it's just not that likely to happen as long as everything is nice and tidy. You can write to NTFS, it's just that the results can be somewhat...unpredictable.

I've never had any problems resizing a well defragged partition, and have yet to experience data loss.

NTFS that hasn't been thouroughly defragged is another story however...

---

### Post by TrailerTrash on 2005-09-27
PCLinuxOS made it VERY EASY to resize NTFS partitions! Ive NEVER had any problems at all.

[IMG]http://img.photobucket.com/albums/v242/wam9468/snapshot5.png[/IMG]

[IMG]http://img.photobucket.com/albums/v242/wam9468/snapshot4.png[/IMG]

---

### Post by aysiu on 2005-09-27
[QUOTE=YourSurrogateGod]Is this actually possible without losing information on the NTFS partition granted that you can't write to an NTFS partition?[/QUOTE] Yes, if you follow the directions in [this tutorial](http://www3.telus.net/linux4u/ubuntu.html). Pay special attention to #3, though. You should always back up your data. You probably won't lose it, but you might.

Don't ride your motorcycle without a helmet.

---

### Post by Stealth on 2005-09-28
I've always used Qparted, which is on all the Knoppix CDs and on the SystemRescue CD mentioned earlier. I've had absolutely no probs using it. Seeing as how that's worked I've never actually bothered (or rather, attempted) to use Ubuntu's NTFS resizer...

---

### Post by az on 2005-09-28
[QUOTE=YourSurrogateGod]*shrug* I didn't know that you could resize a partition without losing some data on it if you couldn't write to it...[/QUOTE]

You can change the size of an NTFS partition without writing to it.

If you do not defragment it, the partitioner will just refuse to do anything.

So, it is very safe.  Any linux partitioning tool uses parted.  The ubuntu installer uses a very recent version of parted.  Nuff said.

I would not recommend using windows partitioning tools, since they do not always follow standards.

---

