---
title: "My fresh Ubuntu install will use Ext3 - NOT Ext4"
date: 2010-10-11
forum: The Cafe
---

### Post by irrdev on 2010-10-11
Ext4 may tout features like delalloc and better journaling, but so far none of these have translated into speed improvements. I really don't care if my Ext3 hard drive is slightly more fragmented if it is still faster than the Ext4 unfragmented hard drive. That's not to say that Ext4's features have a lot of potential, but the current Ext4 implementation leaves a lot to be desired.

Take a look at [Phoronix's latest benchmarks for Ubuntu 10.10]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1010_benchmarks&num=1") and compare the benchmarks for IO-intensive tasks for 9.10 (using Ext3) to the performance of 10.04 and now 10.10, both of which by default use Ext4. I used Ext4 on 10.04, but with my new fresh install, I'm now switching back to Ext3. I am left wondering why Ext4 has been adopted as the default in the first place; it simply doesn't feel ready for prime-time yet, with such a huge speed regression. On several occasions when transferring DVD rips and performing backups, the speed difference has been noticeable. I'm curious, but how many other users have experienced the same problems and/or are still using Ext3 for 10.10?

---

### Post by NightwishFan on 2010-10-11
I would certainly use ext3 on a server. I might take a look at xfs as well. The only performance downside I noticed in ext4 is with dpkg (installing and removing debian packages) they used to install like 3-4 packages per second with libraries and small doc packages, now its much slower (certainly not SLOW though).

---

### Post by t0p on 2010-10-11
> **irrdev said:**
> Ext4 may tout features like delalloc and better journaling, but so far none of these have translated into speed improvements. **I really don't care if my hard drive is slightly more fragmented if it is still slower than the unfragmented hard drive.** That's not to say that Ext4's features have a lot of potential, but the current Ext4 implementation leaves a lot to be desired.


I *think* you made a mistake there.  I *think* you meant to say

> 
I really don't care if my (ext4) hard drive is slightly **less** fragmented if it is still slower than the **undefragmented** (ext3) hard drive.

I apologize if I've got that wrong.

---

### Post by CraigPaleo on 2010-10-11
> **t0p said:**
> I *think* you made a mistake there.  I *think* you meant to say

I really don't care if my (ext4) hard drive is slightly **less** fragmented if it is still slower than the **undefragmented** (ext3) hard drive. 



I apologize if I've got that wrong.

He's using ext3 so I think he meant:
> I really don't care if my hard drive is slightly more fragmented if it is still **faster** than the unfragmented hard drive.

---

### Post by irrdev on 2010-10-11
Yes, CraigPoleo, you're right, and thanks t0p for spotting the confusing sentence structure. I guess that's what happens after being awake for almost 20 hours. ;)

---

### Post by Sporkman on 2010-10-11
Ext4 is just an incremental improvement over ext3. BTRFS is the next big FS.

---

### Post by cascade9 on 2010-10-11
> **irrdev said:**
> Take a look at [Phoronix's latest benchmarks for Ubuntu 10.10]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1010_benchmarks&num=1") and compare the benchmarks for IO-intensive tasks for 9.10 (using Ext3) to the performance of 10.04 and now 10.10, both of which by default use Ext4. I used Ext4 on 10.04, but with my new fresh install, I'm now switching back to Ext3. I am left wondering why Ext4 has been adopted as the default in the first place; it simply doesn't feel ready for prime-time yet, with such a huge speed regression. On several occasions when transferring DVD rips and performing backups, the speed difference has been noticeable. I'm curious, but how many other users have experienced the same problems and/or are still using Ext3 for 10.10?

20 hours awake eh? Explains why you missed this- 

> In Ubuntu 9.10 the key  information includes the Linux 2.6.31 kernel, GNOME 2.28.1, X.Org Server 1.6.4,  NVIDIA 185.18.36, GCC 4.4.1, and an EXT4 file-system. Ubuntu 10.04.1 LTS information  includes the Linux 2.6.32 kernel, GNOME 2.30.2, X.Org Server 1.7.6, NVIDIA 195.36.24,  xf86-video-intel 1.7.6, Mesa 7.7, GCC 4.4.3, and an EXT4 file-system. Lastly,  with Ubuntu 10.10 we have the Linux 2.6.35 kernel, GNOME 2.32.0, X.Org Server  1.9.0, NVIDIA 260.19.06, xf86-video-intel 2.12.0, Mesa 7.9, GCC 4.4.5, and an  EXT4 file-system.[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1010_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1010_benchmarks&num=1)

All the tests were done with EXT4, so I wouldnt blame EXT4 (yet anyway) for any performance regression. ;)

---

### Post by irrdev on 2010-10-11
You have to look at relevant benchmarks. For example, the Bullet Physics Engine is CPU-intensive and I wouldn't expect to see a major difference based on disk-io performance. However, PostgreSQL and the Apache Benchmark are relevent because to to a Ext3/Ext4 comparison. The PostgreSQL benchmark in particular is eye-opening: Ubuntu 9.10 using Ext3 was ~10 times faster than Ubuntu 10.10 using Ext4. Apache was definitely better, but the speed regression was still noticeable.

---

### Post by irrdev on 2010-10-11
You have to look at relevant benchmarks. For example, the Bullet Physics Engine is CPU-intensive and I wouldn't expect to see a major difference based on disk-io performance. However, PostgreSQL and the Apache Benchmark are relevent because to to a Ext3/Ext4 comparison. The PostgreSQL benchmark in particular is eye-opening: Ubuntu 9.10 using Ext3 was ~10 times faster than Ubuntu 10.10 using Ext4. Apache was definitely better, but the speed regression was still noticeable.

---

### Post by juancarlospaco on 2010-10-11
BTRFS is present on the normal Maverick installer ATM using manual partitioning

---

### Post by CraigPaleo on 2010-10-11
> **irrdev said:**
> You have to look at relevant benchmarks. For example, the Bullet Physics Engine is CPU-intensive and I wouldn't expect to see a major difference based on disk-io performance. However, PostgreSQL and the Apache Benchmark are relevent because to to a Ext3/Ext4 comparison. The PostgreSQL benchmark in particular is eye-opening: Ubuntu 9.10 using Ext3 was ~10 times faster than Ubuntu 10.10 using Ext4. Apache was definitely better, but the speed regression was still noticeable.

What he's trying to point out is that they are all using ext4. 

> **In Ubuntu 9.10** the key information includes the Linux 2.6.31 kernel, GNOME 2.28.1, X.Org Server
1.6.4, NVIDIA 185.18.36, GCC 4.4.1, and an **EXT4 file-system**. 
**Ubuntu 10.04.1 LTS **information includes the Linux 2.6.32 kernel, GNOME 2.30.2, X.Org Server 1.7.6, NVIDIA 195.36.24, xf86-video-intel 1.7.6, Mesa 7.7, GCC 4.4.3, and an **EXT4 file-system.** Lastly, with **Ubuntu 10.10** we have the Linux 2.6.35 kernel, GNOME 2.32.0, X.Org Server 1.9.0, NVIDIA 260.19.06, xf86-video-intel 2.12.0, Mesa 7.9, GCC 4.4.5, and an **EXT4 file-system**.

I think you're misunderstanding this:

> The PostgreSQL database server takes a large performance hit between Ubuntu 9.10 and 10.04.1 LTS, which is due to EXT4 changes in the Linux 2.6.32 kernel as we confirmed

That's saying that there were changes in EXT 4 itself between 9.10 and 10.04 - not that 9.10 was using EXT 3. Does that make more sense now?

---

### Post by cascade9 on 2010-10-14
> **CraigPaleo said:**
> That's saying that there were changes in EXT 4 itself between 9.10 and 10.04 - not that 9.10 was using EXT 3. Does that make more sense now?

IMO, that says that there is some problem with PostgreSQL/EXT4/2.6.32 (and later) kernels, not really a EXT4 (alone) issue. 

I'm semiguessing though, some of those benchmarks are all over the place.....The IOZone test in particular doesnt make sense to me at this time :S

---

