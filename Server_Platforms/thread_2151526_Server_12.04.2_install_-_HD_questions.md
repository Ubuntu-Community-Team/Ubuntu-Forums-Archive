---
title: "Server 12.04.2 install - HD questions?"
date: 2013-06-04
forum: Server Platforms
---

### Post by perryrt on 2013-06-04
Folks - I'm in the process of upgrading my file-(and print-,audio-,video-,samba, etc) server at home. I HAD an low powered Atom machine with a single 1 TB drive from five years ago or so (I was just going to try it out for a couple of weeks, then upgrade to something real, but it just worked well, and I never changed it...) Anyway, the drive finally died, and I am in the process of building up a more modern setup.

One of the (thousands of) questions I have is on hard drives. My plan at the moment is to use:

1) a smaller but fast (120G SSD/SATA 3) drive for the OS, and
2) three largish but slower (2TB, SATA 2) drives in a RAID 5 configuration for file/media service.

I'm going to try the software (mdadm) RAID control first - if that doesn't work/give me the access speed for video streaming, I'll go with a HW raid controller at that point.

Anyway, for the moment, my questions are these:

Do you folks this this setup will reasonably work? Or am I coocoo for Cocopuffs? My needs are pretty basic - nothing "cutting edge", just basic performance. Toughest thing this thing would run into would be streaming a DVD-quality image.

(I'm showing my *nix ignorance here, though) How/where should I set the mount point of the RAID for maximum benefit? "/" "/home" and swap are planned to be on the SSD (solo drive).  Is there a "standard" place for mounting the RAID array, though? (/dev/RAID or something?) On my old system, I collected all my media stuff under a single "/sharing" directory, which worked well with Samba, but I've not done anything like this with multiple drives before.

Your help would be appreciated, thanks!

---

### Post by SaturnusDJ on 2013-06-05
Even a single HDD should be fast enough to stream a Blu-ray rip. If it doesn't work, something else is wrong. (Like network.)

Many people recommend to place the swap on something else than a SSD. They also suggest to put /var and some other folders somewhere else.

My opinion, a bit controversial, is to disable swap if the amount of RAM is sufficient. I use a SSD myself and touched nothing, except for enabling noatime as mount option. If you don't use noatime, relatime will most likely be chosen automatically. Even /home is on the SSD, that's because I created another path for big data and shared that. So that's like your /sharing directory. One of the two big benefits there is that the OS will still be able to log you in into your personal environment (with GUI) if the data HDD's are missing.
I don't believe keeping /var on the SSD will totally decrease the life time. And if it does within 5 years, I'll move the OS 4GB forward, because I'm only using the first 4GB of the 32GB SSD.

Concerning raid, mdadm will create a md device (/dev/md0) from multiple partitions. Because future replacement drives maybe be a bit smaller in size (vendor specific), it's recommended to use partition with size a bit smaller than max HDD size, as array members. You'll mount the md device to a folder you choose.

Is this a bit understandable? Otherwise just ask.

---

### Post by SeijiSensei on 2013-06-05
I think an SSD drive in a server is overkill.  Once the OS and daemon processes load, most everything is in memory, and the drive tends to be idle except for swapping and writing log entries to /var/log.

As for the RAID device, as SaturnusDJ says, you'll just end up with a single device like /dev/md0 which you can treat the same way as a single device.  If you go with the SSD drive, I'd put /var on the RAID device.  In fact you might consider creating two RAID devices, a small one like 50-100 GB to mount as /var, and the rest allocated to data storage.  I usually mount the RAID as /home.  Putting /var on the RAID ensures you'll have logs if something goes wrong.

---

### Post by perryrt on 2013-06-07
Ok, you've convinced me on the SSD (also, the price to volume size ratio is still a little high for me.) A fast (SATA III) conventional HD is on it's way to me. I can always get one later if I want to continue to fiddle with it. 

I'm going to put / and /home etc on the "primary drive".

And that makes sense about putting /var on a seperate RAID partition (or is it device in that context) and leaving myself some room just in case. The discs I'm getting are 2000GB, so I think I'll try a 50G device for /var, and a 1750G one for /shares

Thanks for the help, folks!

---

