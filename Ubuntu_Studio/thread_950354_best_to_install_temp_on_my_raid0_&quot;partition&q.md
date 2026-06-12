---
title: "best to install /temp on my raid0 &quot;partition&quot; for video editing; space limit. for /?"
date: 2008-10-17
forum: Ubuntu Studio
---

### Post by streamsanddragonflies on 2008-10-17
I only have experience in audio editing/recording and want to learn basic video editing. I have to (re-)install Hardy U. Studio LTS and find that raid0 could be usefull for me.

I have 11 GiGs space left on fast enough SCSI (XP is still needed), plan on installing / there. A generous friend just gave me a 36 GIG 10k Ultrastar IBM SCSI (2001), that operates at slightly lower access/specs, which I wanted to keep 2 GIG for swap, and ~ 8 GIG for /home. I wanted to use 25 GIGS from the IBM SCSI and another 25 GIGS from an extended partition on my recent 500 GIG IDE drive. These partitions I will use as raid0, which I can create with ubuntu alternate install DVD. Note: I boot from a separate primary partition on the same 500 GIG drive, the remainder of this IDE drive is for other OS and storage partitions, and extra swap.

I heard that /temp files can swell depending on project, and if I don't want to create a LVD within my raid partition, can I send my rendered video files to a link from within the /temp partition and play them from same partition. Then later on, send final results to my other non- raid partitions on IDE, while I start to work on a new edit. Or do I have the whole process wrong!? For Ubuntu install, I must pick what to mount my raid0 partition as, right? I figure that /temp is good choice for video edits/writes...


Does cinelerra work with temp files and then writes to the data target partition or does the video file get processed straight to a data partition?


Here is an excerpt from the Cinelerra doc.:


"Cinelerra is demanding on all PC subsystems, as reading, decoding and playing video can be quite taxing. Thus, performance and usability of Cinelerra are directly proportional to the video format (SVCD/DV/HDV/HD/etc) used and the CPU and I/O bus speeds and video and memory bus architecture of your hardware. Therefore, it stands to reason that a less powerful system will be sufficient for users working with audio only or lower resolution video formats. However, that same system may slow down considerably when playing back a higher resolution format, such as DV video. Effects and several tracks of audio will compound these problems. Given these constraints, here are some suggestions for running Cinelerra:

* CPU speed
At least 500 MHz CPU speed, anything less would be useless. Dual-core and SMP processors greatly improve Cinelerra speed.
* Memory
When working with video, a large amount of free memory available can help speed up operations by avoiding unnecessary disk swaps and keeping material ready accessible. Have at least 256 Megabytes of memory. To really use Cinelerra for higher resolution video formats and larger projects, greater than 1 Gb memory space is suggested.
* Storage
Video editing can be quite I/O intensive. Storage requirements are based on your particular video editing needs. If you expect to produce long pieces in uncompressed or larger resolution formats, you should have large (>200 Gb) and fast (<10ms) disk drives. For example, DV uses about 3.5 Megs per second, or 12 Gigs per hour. For smaller projects you might get away with 1 Gb. RAID0 (stripe set), RAID1+0 (striped/mirrored) or RAID5 (stripe set with parity) will also speed playback
* Video adapters
Since version 2.1, Cinelerra benefits from OpenGL hardware acceleration. Make sure the video card you use supports OpenGL 2.0 in order to benefit from that acceleration. Nvidia series 7 (ie. 7600GS) are known to work well. Unfortunately, ATI's Linux drivers do not support a complete implementation of OpenGL 2.0. If you are going to send a composite signal directly to a TV or video recorder, make sure your video card supports it.
* Multiple monitors
You can use XFree86's Xinerama features to work on multiple monitor heads. This feature can be a very effective way of increasing productivity."

My video card does not even support open GL 2.0, only GL 1.0, so that means this will slow things down at the outset! My 2 2.4 GIG CPUs are ok, 1 GIG memory just ok. My nv quadro4 900XGL videocard enables 2 monitors at least! I have a 2002 HP workstation, with no more room or budget for extra drives or hardware...

Any ideas on better setup for video editing, will be much appreciated!
If anyone knows of any more linux video production (forum or other) links (besides Ubuntu), I'd appreciate..





:guitar:

---

### Post by streamsanddragonflies on 2008-10-18
Really hoping to do install this weekend- anyone with an idea?
Thanks

---

### Post by Queen555 on 2009-10-08
**rizvii** may not have other drives available, but I also prefer three drives, boot, edit and storage. But you could use the 160GB drive for encoding, even to and from the same drive. Encoding is not hard drive intensive, just CPU intensive, and most any drive can keep up, even for input/output at the same time. That setup may slow some editing operations, but still much better than just having a single drive in the computer. :) 
 
The problem with using the boot drive is that the OS accesses it so much that it can slow some operations. Because of that, I don't use mine except for the OS, program storage and some archival data storage. It's also best to keep any hard drive less than 80% full, 70% is even better. That way there is room to defrag when you need to and the drive should be able to operate at optimum speed most of the time. 
 
I'm using a 60GB SSD (Solid State Drive) for boot on one of my computers and have it about 40% full. And that's not easy with Vista. :( I had to move the paging file and other temp files to other drives. And I try to keep programs from wanting to use it. A SSD drive needs more headroom than a mechanical drive and 50% freespace is about as low as you want to go. It doesn't use defragging, but it does alternate the internal RAM locations. (And it's very fast. :D )================================================
[Tummy Tuck Recovery](http://tummytuckguide.com/tummytuckrecovery.php) [phuket resort hotel](http://www.bestatthailandholidays.co.uk/pages/phuket/)

---

