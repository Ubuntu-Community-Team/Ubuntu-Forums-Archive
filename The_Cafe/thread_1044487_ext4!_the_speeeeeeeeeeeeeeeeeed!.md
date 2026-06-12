---
title: "ext4! the speeeeeeeeeeeeeeeeeed!"
date: 2009-01-19
forum: The Cafe
---

### Post by uberdonkey5 on 2009-01-19
Have you seen the performance of the ext4 file system?

[http://arstechnica.com/journals/linux.ars/2009/01/12/super-fast-ext4-filesystem-arrives-in-ubuntu-9-04](http://arstechnica.com/journals/linux.ars/2009/01/12/super-fast-ext4-filesystem-arrives-in-ubuntu-9-04)

Its head and shoulders above the competition. Wow, can't wait for jaunty now!!!

Anyone tested it themselves??? What do you think?

P.S. if you are interested for a comparison with windows NTFS-3G file system performs similarly to XFS. So basically when 9.04 comes out we will beat the competition :D

[http://www.csamuel.org/2007/04/25/comparing-ntfs-3g-to-zfs-fuse-for-fuse-performance](http://www.csamuel.org/2007/04/25/comparing-ntfs-3g-to-zfs-fuse-for-fuse-performance)

---

### Post by jimi_hendrix on 2009-01-19
when i installed jaunty i couldnt find out how to get ext4

---

### Post by gletob on 2009-01-19
Is there a way to convert my existing EXT3 file systems to EXT4?

---

### Post by mips on 2009-01-19
I would like to see benchmarks on a standard 3.5" 32MB cache 7200rpm drive which is more commonly found in home computers.

Benchmarks like these would be cool,
[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)
[http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

---

### Post by Simian Man on 2009-01-19
I have been using it with Fedora 10 since it came out and it does seem much faster.  I only really notice it when doing things like backing up large amounts of data.

---

### Post by Amazona aestiva on 2009-01-19
Sounds interesting, I can't wait! :)

---

### Post by odinfromvalhalla on 2009-01-19
I'm using Jaunty alpha 3 and i reformatted all my HDD to ext4 (both / and /home partitions)

Not sure about if it's ext4's fault but with Jaunty my notebook runs way better than before. I get to book login screen in ~18s (CPU T7500 @2.2Ghz and 4Gb Corsair).

And yes, you can see the speed when moving backups around.

---

### Post by adamlau on 2009-01-19
Tough to really know until additional benchmarks across multiple media types are produced by the community at large. Sure holds promise, I am certain more than a few of us are anxious to try it out :) .

---

### Post by blackened on 2009-01-19
Phoronix also has a writeup with some ssd benchmarks.

[http://http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1]("http://http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1")

---

### Post by cardinals_fan on 2009-01-19
> **mips said:**
> I would like to see benchmarks on a standard 3.5" 32MB cache 7200rpm drive which is more commonly found in home computers.

Benchmarks like these would be cool,
[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)
[http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)
+1

The SSD benchmarks are of limited interest to me.

---

### Post by |eafhound on 2009-01-19
[http://vizzzion.org/?id=reiser4](http://vizzzion.org/?id=reiser4)

conclusion.
Overall reiser4 seems to win it, although the results are not weighed. In most cases, reiser4 does a pretty good job. When it comes to copying lots of small files, reiser4 is very fast, especially compared to xfs, end even more to compared to jfs.

It seems that, apart from all other features, users of reiserfs 3 will gain lots of speed when upgrading to reiser4. Running the benchmarks on a spare disk was a very good idea. ;-)

---

### Post by jespdj on 2009-01-19
That diagram on [Ars Technica](http://arstechnica.com/journals/linux.ars/2009/01/12/super-fast-ext4-filesystem-arrives-in-ubuntu-9-04) looks impressive, but do not take this literally, without thinking.

Ext4 is **NOT** going to be more than twice as fast for any kind of disk operation. And note that the test by Phoronix was done with a solid state drive, and not with a traditional harddrive. The numbers for a traditional harddrive, which has very long seek times compared to an SSD, could be totally different than what this benchmark shows. The title of the Ars Technica article is misleading ("Super fast Ext4 filesystem...").

It's not realistic to expect that the filesystem will suddenly be more than twice as fast on any computer.

Some of the other diagrams from the benchmark show something completely different:

[img]http://www.phoronix.com/data/img/results/ubuntu_ext4/5.png[/img]

---

### Post by CarpKing on 2009-01-19
Will I see any benefit from this if I only use it for /?  I reinstall every release, but changing /home would be more trouble.

---

### Post by cdekter on 2009-01-19
> **CarpKing said:**
> Will I see any benefit from this if I only use it for /?  I reinstall every release, but changing /home would be more trouble.

I read somewhere that it's going to be possible to convert ext3 to ext4, rather than having to reformat.

---

### Post by andrewabc on 2009-01-20
> **cdekter said:**
> I read somewhere that it's going to be possible to convert ext3 to ext4, rather than having to reformat.

Yep it is possible. Not sure how, but everyone says it is possible. google it.

---

### Post by mips on 2009-01-20
> **cdekter said:**
> I read somewhere that it's going to be possible to convert ext3 to ext4, rather than having to reformat.

[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)
[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)
[http://www.ibm.com/developerworks/linux/library/l-ext4/index.html](http://www.ibm.com/developerworks/linux/library/l-ext4/index.html)

---

### Post by sofasurfer on 2009-01-20
So if Juanty uses ext 4, I guess I can not dual boot it with Intrepid (ext 3)?

---

### Post by smartboyathome on 2009-01-20
> **sofasurfer said:**
> So if Juanty uses ext 4, I guess I can not dual boot it with Intrepid (ext 3)?

You can, but EXT4 is not backwards compatible with EXT3. :(

---

### Post by sofasurfer on 2009-01-20
Please clarify your meaning..."EXT4 is not backwards compatible with EXT3".

---

### Post by smartboyathome on 2009-01-20
> **sofasurfer said:**
> Please clarify your meaning..."EXT4 is not backwards compatible with EXT3".

As in, EXT4 cannot be mounted as EXT3, and thus Intrepid won't be able to mount it unless you install the newer kernel and e2fsprogs from Jaunty.

---

### Post by sofasurfer on 2009-01-21
I think you're saying that Jaunty needs to run on EXT 4, but my question is, Will Intrepid run on ext 4.

---

### Post by JordyD on 2009-01-21
If anyone has read the actual article, there are actually times when EXT4 is worse than any of the others.

---

### Post by fwojciec on 2009-01-21
Subjectively, to me, it feels faster than reiserfs for general use.  And this is pretty good, because I used to consider reiserfs the fastest general-purpose filesystem in Linux (excluding experimental filesystems like reiser4, etc.).

---

### Post by Grant A. on 2009-01-21
I'm still waiting for VaporFS (BtrFS).

---

### Post by Changturkey on 2009-01-21
> **Grant A. said:**
> I'm still waiting for VaporFS (BtrFS).

How is it vaporware? It's being tested with the .29 kernel...

---

### Post by collinp on 2009-01-21
> **sofasurfer said:**
> I think you're saying that Jaunty needs to run on EXT 4, but my question is, Will Intrepid run on ext 4.


Intrepid cannot mount EXT4 w/o the kernel and e2fsprogs from the Jaunty repository, is what he ment.

---

### Post by Grant A. on 2009-01-21
> **Changturkey said:**
> How is it vaporware? It's being tested with the .29 kernel...

It was supposed to be completed by the end of 2008, it's only at an alpha stage...

---

### Post by mips on 2009-01-22
> **Grant A. said:**
> It was supposed to be completed by the end of 2008, it's only at an alpha stage...

That does not mean it is vaporware. Development was just slower than expected but the project is very much alive and active.

Wonder what people would call the HURD kernel seeing how many years that has been going on?

---

### Post by SupaSonic on 2009-01-22
I still use killer... i mean reiserfs for my / and ext3 for my /home. If it's easy enough to convert ext3 to ext4, i'll definitely give it a go.

---

### Post by hugmenot on 2009-01-22
I have a fairly crufty Ubuntu Jaunty install on my laptop and two twin harddisks that I mirror from time to time (due to ATA instability).

Now this time around I reformatted one of them to Ext4 and then rsynced the system over and my boot time to the fully loaded desktop on ext4 was cut in half (2 min vs 1 min). Before it was reiserfs.

Now of course a cleanly formatted partition is faster than a fragmented, fairly filled, old partition, and the drive models aren&#8217;t identical, but I was impressed nonetheless.

---

### Post by tr4nce on 2009-01-22
Installed Jaunty alpha in a ext4 partition the other day. Boy... it's freaking fast! I am wondering if there is any setback for this filesystem. Anyone?

---

