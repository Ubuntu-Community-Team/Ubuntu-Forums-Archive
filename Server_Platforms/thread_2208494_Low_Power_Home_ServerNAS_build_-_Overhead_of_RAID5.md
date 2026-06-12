---
title: "Low Power Home Server/NAS build - Overhead of RAID5 on CPU"
date: 2014-02-28
forum: Server Platforms
---

### Post by m-dw on 2014-02-28
I'm planning to build a home server to replace my ReadyNAS NV+

I've found a fanless MiniITX mainboard based on the Intel Atom D525 1800GHz dual core processor with 6 built in SATA2 interfaces.  My plan is to use a 2.5" drive for the OS, and 4 x 3.5" drives for the data array, and was hoping to use Raid 5.

There is no on-board raid controller.  Will using a purely software based RAID setup put an undue load on the server?  There's a PCI and a mini PCI-E slot on the board, so am investigating offloading the RAID to a separate hardware device, but not sure how well a consumer oriented card will play with Linux .  Any thoughts/advice/tales of woe gratefully recieved.

I'm planning to use the server to

[LIST]
[*]Export NFS and SMB/CIFS to my home network
[*]Run Logitech Media Server streaming to several wireless and wired SqueezeBox devices
[LIST]
[*]Transcoding OggFLAC and AAC+, WMA and other radio streams formats to FLAC or PCM on the fly.
[*]Streaming FLAC natively to multiple devices.
[/LIST]

[*]Streaming video files to a smart TV (transcoding not required) over DNLA.
[*]Transcoding FLAC to something more portable automatically when putting it on a PMP.
[*]Host an IMAP mail server.
[*]Host a LAMP server (home/household use, no SSL)
[*]Potentially install a scanning proxy like Squid.
[*]Integrate on access virus scanning (with clamav) to SMB access, email, proxy functions.
[/LIST]

Will using the CPU to run a RAID array restrict how many of the above tasks the server can do simultaneously?

Research has now led me to believe that RAID 10 is the way to go for performance and reliability so that's what I'm going to do.

---

### Post by m-dw on 2014-02-28
Or... with a littlke more research I might get 4 x 2TB drives and make them a RAID 0+1 giving me a capacity increase, lower overhead and more resilience against failure.

---

