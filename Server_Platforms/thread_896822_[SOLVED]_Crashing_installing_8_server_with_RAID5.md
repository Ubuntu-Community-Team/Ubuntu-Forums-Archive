---
title: "[SOLVED] Crashing installing 8 server with RAID5"
date: 2008-08-21
forum: Server Platforms
---

### Post by Astro6312 on 2008-08-21
All,

I have a 3ware controller with 3x 1TB disk in RAID5.  This is shown as 1.81TB in the 3ware firmware and 2TB when partitioning in ubuntu server setup.  I setup 3 partition, / = 740Gig, /vmware = 1.2TB and SWAP of 60Gig.  All goes fine until the setup format the /.  It indicate 30% for some time and crash.

I have tried booting the live 8 CD and using Gparted. It crashes also on the second partition of 1.2 TB.

Any ideas what is going on.  I have updated the firmware of the 3ware 9550sx card.  This is a brand new server out of the box.

I have 3 other server configured like this one but with a bit older hardware. This is not a newbie question.

Also, it does not make sense that I see on one side 1.81 TB and the OS see 2TB.

Thanks for any hints.  I will report other attempts running now.

---

### Post by windependence on 2008-08-21
Check your BIOS and make sure there are no onboard RAID controllers enabled.

-Tim

---

### Post by Astro6312 on 2008-08-21
> **windependence said:**
> Check your BIOS and make sure there are no onboard RAID controllers enabled.

-Tim

Tim, I have disabled the internal RAID controller from start.

Any ideas if the size discrepancy between the 3ware 1.81 TB and 2 TB of ubuntu setup is a problem.  Also, Gparted from the Live CD of ubuntu 8 shows 1.82 TB.

Thanks,

---

### Post by windependence on 2008-08-21
The difference in size is most likey due to the way they calculate a megabyte. Since a true megabyte is 1024 kilobytes, if they use just 1000 instead of 1024 it will be different.

I have to think about what's goimg on with your board but I gotta believe it's some setting in the BIOS.

You could try something like partition magic to format or use utilities from a disk like Hiren's boot CD.

-Tim

---

### Post by Astro6312 on 2008-08-21
I did a quick test from Gparted on the live unbuntu 8 CD.  I created a 500Gig EXT3 partition on the RAID5.  Everything went ok.  I then did a check on that partition (e2fsck -f -y -v /dev/sda1) and the server rebooted by itself after a while.

I will try this again from a shell to see if I can catch a message before the reboot.

Very weird

---

### Post by Astro6312 on 2008-08-22
RESOLVED: 

I found the problem, nothing to do with RAID 5.  There was a watch dog timer enabled in BIOS.  After 5 minutes of formatting the big 1.8TB drive, the system was thinking the server was frozen and the WDT rebooted the server.

---

### Post by windependence on 2008-08-22
Great! I just KNEW it had to be a BIOS parameter. I'm glad you found that one because I have that very same setting on my boards. It's disabled though. 

-Tim

---

