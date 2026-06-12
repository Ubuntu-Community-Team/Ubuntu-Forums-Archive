---
title: "Ubuntu Desktop vs Ubuntu Server: RAID"
date: 2011-02-08
forum: Server Platforms
---

### Post by Pevichaey5 on 2011-02-08
Hey

I've recently got hold of a 1U rack server, so I pretty much want to upgrade my home lan and like a central backup server

Now I've done this before on Windows Server 2003, however I want to slowly move away from being a Microsoft person and get more into the open source material

I believe the RAId on these disks in RAID 1 but what would you recommend I load with? Ubuntu Server (I'll learn some CLI Fu) or Ubuntu Desktop bearing in mind it is RAId so I'm not sure how that will cope

Thanks

---

### Post by liquidxit2 on 2011-02-08
I personally would recommend ubuntu server. While it runs light on CLI only, you can load gnome to get your GUI fix and then turn off gnome with: ctrl - alt - f1. Should make the server run a bit leaner from that point and you could always reload the GUI with ctrl - alt - f2. Somebody please correct me if Im wrong on the commands. I personally LOVE the CLI for linux as it takes me back to the DOS days, but sometimes I want a GUI to mess around in. But for ultimate lean and mean and security CLI is the way to go.

---

### Post by Pevichaey5 on 2011-02-08
What about RAID though? I had some issues yesterday with an ex RAID drive and the partition manager about as Windows left behind something to do with RAID on the disks causes Ubuntu to not see a partition?

How will it cope with a hardware RAID 1 configuration?

---

### Post by Joe of loath on 2011-02-08
You can't install Ubuntu desktop on RAID, the installer doesn't have support for it.

Ubuntu server shouldn't have a problem, however.

---

### Post by uRock on 2011-02-08
Moved to Server Platforms.

---

### Post by liquidxit2 on 2011-02-08
The only raid help i can give is that ubuntu server has native software raid support so I would think its just a matter of whether or not a driver is available for your hardware raid. I would think that wouldnt be an issue either as driver support is pretty solid.

---

### Post by arrrghhh on 2011-02-08
Honestly there's not a huge difference between server and desktop platforms - you can run all the same services, etc from Ubuntu Desktop that you can from Server.

The Server distro is just optimized to be lean&mean as stated above.  Less packages to update, less security holes...

At any rate, RAID array should be no different in Desktop than Server.

With that said, I don't think it's advised to have the boot disk be in an array - AFAIK it's recommended to use a different disk to boot from, and use the RAID array for storage.  Someone more knowledgeable, feel free to correct me if I'm wrong, I'm not a RAID expert ;).

---

