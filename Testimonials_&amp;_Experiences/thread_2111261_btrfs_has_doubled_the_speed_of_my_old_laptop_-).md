---
title: "btrfs has doubled the speed of my old laptop :-)"
date: 2013-02-01
forum: Testimonials &amp; Experiences
---

### Post by 7bit on 2013-02-01
Hardware: Thinkpad T40, 40GB Harddrive (really slow, ~25MB/s), 500MB RAM, 1.5GHz Pentium-M (single core).

OS: Xubuntu 12.04

Before: Ext4, 98% full, extremely slow, not much fun working with this laptop anymore. I made a complete backup of all partitions using tar onto an external drive (took 2 hours)


There are many benchmarks of file systems around using specialized tools but I thought all I am interested in is whether this will actually make any *noticable* difference when actually *using* it. So I just tried it myself.



### Test 1 (ext4):

boot live distribution from usb drive and change the partition layout (I wanted to do this anyways, so this was the opportunity to finally do it): 
sda1: 500MB swap (at beginning of disk, the outermost cylinders where it it is fastest)
sda2: 500MB ext2 (/boot near beginning because old BIOS)
sda3: 38GB ext4  (/)
then I restored the backup, edited fstab, updated grub, rebooted.

** Results:
* boot took 35 seconds (instead of 55)
* drop caches and start eclipse¹:  1:58
* drop caches and start chromium²: 1:19

¹) eclipse with 3 java projects open, waited until entire workspace was rebuilt after start.
²) started with no open tab, only the speed dial, waited until all thumbnails appeared and HD activity stopped.



### Test 2 (btrfs):

boot live distribution from usb, delete sda3, create it newly as btrfs and formatted with default options. 

* remount sda3 with **compress** option (**this is not the default!**) before beginning restore, restore same backup of / from previous test (took twice as long as restoring to ext4), edited fstab (don't forget compress option), updated grub, messed up grub configuration badly, finally able to repair it, reboot.

** Results:
* boot took 55 seconds again (?)
* drop caches and start eclipse:  1:15 (instead of 1.58)
* drop caches and start chromium: 0:36 (instead of 1.19)
* / is now 67% used (instead of 98%)
* It almost feels like an entire new laptop now :-)


Now I just hope it won't do any bad things to my data because it is still said to be "beta". I guess I'm going to make backups more regularly now (which is always a good idea anyways).

---

### Post by Paddy Landau on 2013-02-01
That's interesting. I rather suspect that it is faster mainly because you have freed space by using compression. I bet that if you were to repeat the test but without compression, it would be slow again.

> **7bit said:**
> … drop caches…
How do you drop the caches?

---

### Post by tgalati4 on 2013-02-01
How much of the speed increase is due to btrfs versus simply rewriting your disk?  At 98% capacity, you may have had significant fragmentation.  Rewriting your partitions would restripe the data (essentially performing a defragmentation) which would result in speed improvements.

I have a Thinkpad T43p and I pulled out the old 80GB drive and replaced it with a 320GB drive with a significant increase in speed.  The newer drives have larger buffers and faster controllers, so they really fly on older machines.

Let us know how well btrfs works over the next year and report back with any problems.  Also, don't let your disk fill up greater than 90%.  Linux needs room to breathe.

---

### Post by 7bit on 2013-02-01
> **Paddy Landau said:**
> That's interesting. I rather suspect that it is faster mainly because you have freed space by using compression. I bet that if you were to repeat the test but without compression, it would be slow again.


Yes, I believe most of it comes from compression. It also has to be noted that *writing* files seems slower now, at least when writing many files in a short time this is noticeable, it was very obvious during restoring the backup, the CPU was at 100% all the time and it took roughly twice as much time.

My harddrive is *extremely* slow, it has ~30MB/s throughput on the outer cylinders and only ~20MB/s at the inner cylinders. Compared to a modern HD this is ridiculously slow, some would consider something that slow almost unusable nowadays. If decompressing the compressed data can happen faster than the HD is able to read then this is likely the main reason for the performance gain.


> How do you drop the caches?

sudo sysctl vm.drop_caches=3

---

### Post by 7bit on 2013-02-01
> **tgalati4 said:**
> Rewriting your partitions would restripe the data (essentially performing a defragmentation) which would result in speed improvements.

I already felt an improvement during the first test (restore backup to ext4) compared to how it was before, this was certainly due to rewriting all the files unfragmented. My interpretation of the additional speed improvement with btrfs is that it is due to the compression, it seems my CPU is fast enough to decompress much faster than my slow HD would ever be able to read from the disk and when starting these huge applications it is mostly only reading and not writing. Maybe it is really only the sheer slowness of my HD that makes the difference so obvious.

---

### Post by Paddy Landau on 2013-02-01
> **7bit said:**
> sudo sysctl vm.drop_caches=3
Thank you.

---

### Post by tgalati4 on 2013-02-01
I don't recall the exact speed of my 320GB black drive;it was between 65 and 77MB/sec which is about as fast as my desktop 75GB Raptors.

---

### Post by frankennetbook on 2013-02-02
Being fairly new to Ubuntu, and still learning linux language I can't provide much for an educated addition to this thread but... 

I installed Ubuntu 12.04 on my acer netbook and while it ran WinXP I had trouble streaming live video.  It really only worked when it was plugged in. But since switching to Ubuntu I've had no issues and can stream without issue!  Makes me very happy!

---

### Post by 7bit on 2013-02-03
> **tgalati4 said:**
> 
Let us know how well btrfs works over the next year and report back with any problems.

I'm not sure if I will keep it forever now, I will observe the behavior very closely and I am prepared to change the file system again if any serious problems occur.

There is one thing I noticed (It is mentioned in the btrfs wiki and I was aware of it but I wanted to test the impact of this myself), it is the handling of things like virtual disk images (especially virtualbox and truecrypt volumes). A 4GB Windows XP installation in virtualbox compresses nicely (only 2GB used) but performs very badly when compression and COW is in effect. It rapidly fragments and a lot of btrfs kernel threads are hogging the disk and consuming CPU like crazy all the time when this virtual machine is running. Fortunately I don't use it very often, maybe I should activate nodatacow for this disk image or move it to an ext4 partition.

And there is one even more important effect that results from this but is not immediately obvious: **Users of truecrypt who make use of truecrypt's hidden volumes feature (or other comparable disk encryption software with similar features) should under no circumstances put their container files on a btrfs volume! It totally ruins plausible deniability of the existence of the hidden volume!** Initially after converting to btrfs the entire file will have only few extents (easily visible with the filefrag tool) but as soon as you mount the (hidden) volume and do any write operations it immediately fragments heavily at exactly the file offsets where the files inside the volume are located and for hidden volumes this means it is immediately visible from the outside(!) that the parts toward the *end* of the volume were actively used while the parts at the beginning of the file were never touched. This means from looking at the unmounted volume container from the outside with filefrag alone it can be proven that there *must* exist a recently used hidden volume near the end of the container, all deniability is totally gone! Therefore: Never store encrypted volumes on btrfs, use simpler file systems for that.

---

