---
title: "Recommend a home server setup?"
date: 2006-05-05
forum: Server Platforms
---

### Post by juicybananahead on 2006-05-05
Hi everyone,

Alas, there are but a mere 3 GB of space left on my 300 GB hard disk! What to do, what to do?! Well, what I'm thinking of doing is taking the plunge and purchasing some hardware to set up a Ubuntu home server that can sit underneath the stairs and provide the following basic functions:

[LIST=1]
[*]Samba fileserving (LAN)
[*]Samba / CUPS printserving (LAN)
[*]SFTP serving (WAN)
[*]Apache webserving (WAN)
[/LIST]

I'd also like to implement software RAID 5 on this setup, using three 250 GB SATA hard drives and maybe boot from a small PATA drive that's not in the RAID. I suppose that means that I'll have to buy two SATA controller cards so that none of the drives in the RAID are slaves? Lastly, I'd like to have a gigabit ethernet port and a Firewire 800 (1394B) port but neither of these is essential, as I think that I  can get away with fast ethernet and USB 2.0.

To come to the point, before I run out and purchase a whole load of hardware I'd like to know if anybody could recommend a hardware setup that would suit my needs _without_ any Linux compatibility issues? What do I need in terms of processor speed and RAM (it's only going to be under a fairly light load, serving to less than ten clients at any one time)?

If you can't suggest a setup that would work for me, I'd still be very interested in hearing what your own setup is.

Thanks in advance,
// juicy

---

### Post by hw-tph on 2006-05-05
While it may seem stupid I'm going to say it anyway: Tried and true. Older hardware has had more time to get mature drivers. I use a Dell PowerEdge 1400SC server with dual 800MHz Pentium 3 processors and 512MB registered ECC RAM as a local server for my family and my neighbours. This hardware is incredible overkill. For a storage server with ten simultaneous clients a P4 at 1.4 or so GHz will do fine, and 256MB will be plenty.

You will mostly be doing disk intensive stuff. IDE and S-ATA disk rely on the CPU. If you have a SCSI system you can chuck any sort of slow CPU in there and be alright as long as you have a decent SCSI controller. SCSI is expensive though, and CPU cycles and IDE/ATA storage are both cheap. S-ATA will not give any noticeable performance bump over IDE/ATA disks when used over a network so stay with tried and true ATA. Get an older P4 (like 1.4GHz like I said) and a good IDE (RAID if you like) card, or perhaps even better an Athlon XP. You can get this kind of hardware real cheap as a lot of gamers need to upgrade to keep up with the latest games. nforce2 based motherboards are very good bang for the buck and well supported these days. Put pretty much any Athlon XP you can find cheap on it and 256 or even 512MB RAM on it and you have your hardware along with the RAID card.

Oh, and I would like to suggest you have a look at [lighttpd](http://www.lighttpd.net/) instead of Apache. It is very easy to configure (and chroot for security!) and is light on resources. I like it a lot.


Håkan

---

