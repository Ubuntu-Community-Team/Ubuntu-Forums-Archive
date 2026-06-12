---
title: "Subdividing RAID Array into Partitions"
date: 2014-03-02
forum: Server Platforms
---

### Post by m-dw on 2014-03-02
I think these might be basic/idiot questions - if they are, let me know and I'll do more research.  I've been using a consumer NAS as a home server and am about to embark on building a small server to replace it (the NAS will become a backup target).

The NAS is configured as a single volume spanned across 4 disks.  My server will have similar hardware (4 disks) but will have more storage.  I've decided on RAID10 as it seems to provide the resilience I need without the overhead of parity calculations.

1) Is it possible to subdivide the logical disk into partitions like you might put /home on a separate partition on a big single hard disk in a desktop PC?
2) Is there any real advantage to doing so?  I was thinking of putting a MySQL database on one partition and general  data storage on another, and maybe storage for a mail server on a third, but will there be any benefits to doing that?  One big partition makes for greater flexibility (just keep adding stuff until it's full).

I remember talking to a "linux guru" at work (about 10 years ago) who favoured leaving some of the disk unused so you could format it and allocate it to different partitions as necessary, but that advice is old (and possibly referring to LVM).  This will be a home server, mainly serving files to my PC, IMAP and webmail to several devices and streaming media (audio, video, photos) to devices on the network.  The database will be there to support the media server(s).  I am the only user at the moment, though it might extend to a second user at some point.

Many thanks

---

### Post by rubylaser on 2014-03-02
These partitions would all be on the same underlying RAID array, so you would see no performance benefit chopping them up.  One other thing to note is that if you use mdadm for your RAID10 array, you can not expand the array in the future.  If you plan on using ZFS on Linux, adding another mirror vdev to the pool in the future isn't difficult at all to do.

As a sidenote, for home use, I almost always prefer RAID6 over RAID10.  You are guaranteed to survive two disk failures and on decent hardware, you can still get very good transfer speeds and with mdadm, you can add disks in the future.  If you are thinking about ZFS, then going the RAID10 route probably makes more sense, because you can add more mirrors down the line to add storage vs. a raidz or raidz2, you would need to add a matching vdev to maintain good performance (i.e. if you had a 6 disk raidz2, you would want to add a second, six disk raidz2 vdev to expand the pool. This can obviously be very cost prohibitive).

---

### Post by m-dw on 2014-03-03
Thanks for the reply - it confirmed my suspicions, so I'll go the one big disk route.

> **rubylaser said:**
> ... I almost always prefer RAID6 over RAID10.  You are guaranteed to survive two disk failures and on decent hardware, you can still get very good transfer speeds ... 

Thanks very much for this.  I'll have another look at RAID6.  My concern was that as this is going to be a low power device (dual core Atom D525) that the overhead of the parity updates may impact the performance of the server doing other stuff (e.g. transcoding internet audio).  You can see the impact that a RAID5-alike has on my ReadyNAS NV+ (but then again that's got a tiny sparc CPU)

I'm not sure space is an issue, as I'm currently using only a small fraction of a 3Gbyte array, but you never know.

---

### Post by lukeiamyourfather on 2014-03-07
> **m-dw said:**
> 
Thanks very much for this.  I'll have another look at RAID6.  My concern was that as this is going to be a low power device (dual core Atom D525) that the overhead of the parity updates may impact the performance of the server doing other stuff (e.g. transcoding internet audio).  You can see the impact that a RAID5-alike has on my ReadyNAS NV+ (but then again that's got a tiny sparc CPU)


It might be worth rethinking the hardware if you plan to do stuff like transcode audio as well as serve files. I'd pick RAID Z2 because you can lose ***any*** two disks. With RAID 10 only one disk can fail from either mirror. If you haven't purchased the hardware yet there are processors that offer much better performance but are still relatively low power, like the Core i3-4130T (35 watts). Almost three times as much power draw but about eight times the performance of the Atom D525.

Regardless of the hardware you pick and the array configuration it'll still work. So good luck with whatever you end up with. :D

---

### Post by m-dw on 2014-03-07
> **lukeiamyourfather said:**
> It might be worth rethinking the hardware if you plan to do stuff like transcode audio as well as serve files....

I've already got the hardware, after much research to give me the best overall solution, although I acknowledge it isn't the most zippy of CPUs.  Overall system cost was an issues as well.  Having said that the transcoding is mainly 128k AAC+ and 1Mbit/s OggFLAC radio streams to PCM/WAV and the NV+ (280MHz Sparc) will manage that to 4 synchronised streamers, so I'm not too worried (I'm still using an AMD64 3200+ in my desktop which will be 10 years old this year to rip CDs).

Just waiting for the case to arrive, and for 14.04 LTS to be released, which gives me plenty more time to fret over which RAID config to use :lolflag:

---

