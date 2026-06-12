---
title: "Additional possiblities for Software RAID?"
date: 2007-03-27
forum: The Cafe
---

### Post by brickheadbs on 2007-03-27
I've been searching around for ways to reliably backup a partition to a second HDD and came up with an idea, but I can't figure out if it's possible or already exists.

I've found interesting info about Software RAID via Linux (I also found something about Windows Server 2003 doing this??). If I understand correctly, it doesn't require any hardware support.

If that is true, is there any reason you can't create RAID stripes/mirrors over partitions only. What I would like to do is have a RAID 1 style partition to protect data (the usual photos, documents, etc.) and a RAID 0 style partition to speed some things up, both on the same pair of drives. I'm just running a basic PC, not a server, so hot swapping and uptime aren't priorities. I know you couldn't boot from these "RAID partitions", but if it worked you could crash a hard drive, reinstall to your good one if it's not already the one you're booting from, and just make sure not to reformat that mirrored partition. You'd loose your RAID 0, but that's what zero is all about.

RISKS: Of course, you could obviously run the risk of formatting over your mirrored partition accidentally and still loosing your data (totally different subject, if you did format in Linux, can you recover any data? I (being the smart person I am I formatted the wrong drive under windows and still was able to recover with a data recovery program.) This would not be as safe as a real RAID 1, but it's way better than no backup (I've crashed 2 drives over the past 5 years)..

Still, it would be cool. File backup is a hot issue in that so few people do it. I suck at it. I've not found a backup program that I find easy to use and really works (recovery is dumb for most of them). I have found some automated backup programs searching with Synaptic package manager. If they are easy, they'll work OK. But RAID style would be way cooler.

Added to UBUNTU I would like to see super easy backup (that's easy to recover) and my RAID idea. If UBUNTU could do this relatively simply it would take one more step closer to blowing the big OS's out of the water.

---

### Post by saulgoode on 2007-03-27
What you propose is quite reasonable -- in fact, I have been running just such a setup on my Slackware box for a couple of years now. Software RAIDs are based on partitions and there are no restrictions on the distribution of the partitions across different disks (you could even have two RAIDed partitions on the same disk parallelled but you would be decreasing drive performance by doing so). You will want to keep the paired partitions on separate IDE controllers so that disk accesses do not "collide" (the bottleneck is the IDE controller, not the PCI bus -- fortunately, most PCs come with two controllers).

I am not sure of the details of doing it in Ubuntu, but in Slackware all that is necessary is to create an '/etc/raidtab' with the appropriate data, execute '/sbin/mkraid', and then modify your system startup script to execute '/sbin/raidstart'. 

For the setup you described, an '/etc/raidtab' might look like:

```
[I] raiddev /dev/md0
          raid-level      0
          nr-raid-disks   2
          persistent-superblock 1
          chunk-size     4
          device          /dev/hda2
          raid-disk       0
          device          /dev/hdc1
          raid-disk       1
  raiddev /dev/md1
          raid-level      1
          nr-raid-disks   2
          persistent-superblock 1
          chunk-size     4
          device          /dev/hda3
          raid-disk       0
          device          /dev/hdc2
          raid-disk       1
[/I]
```

---

### Post by brickheadbs on 2007-03-27
I'm definitely going to give it a try. It'll probably take me a few days to get around to it. I have 3 drives, 2 SATA, 1 ATA, all three 160GB Seagate. Any ideas for the best setup?

---

### Post by brickheadbs on 2007-04-10
So... I know this is ambitious for a novice Linux user but... Can't learn if you don't try.

Anyone want to help me out a little? I'm ready to try. As far as I can tell the info above is the only directions I've found after much Googling (just heard they run Linux, that's cool).

I found out that Intel is now offering hardware based Matrix Raid. It sounds great and I hope that it gets implemented into all mobos.

If Linux can do this without a special chipset it's something that needs publicity - there's a need or Intel wouldn't be doing it.

I'll try what saulgoode is saying, but can anyone walk me through this? I ought to be able to recruit someone else who's willing to try!

Come on! Let's go! (and all that kinda motivational stuff).

---

