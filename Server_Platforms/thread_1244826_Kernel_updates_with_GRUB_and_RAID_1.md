---
title: "Kernel updates with GRUB and RAID 1"
date: 2009-08-19
forum: Server Platforms
---

### Post by wsmoser2004 on 2009-08-19
I just recently set up a server with Ubuntu 8.04, and as part of the process, I needed to configure software RAID 1 on the server's two drives.  Since I actually had the server already up and running, I followed instructions here: [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch]("http://http://www.howtoforge.com/software-raid1-grub-boot-debian-etch").  Even though they are for Debian, they worked great and I'm up and running with RAID 1.

Now I have a question about kernel upgrades.  Will I have to edit menu.lst and/or reinstall GRUB to one or both of the drives every time I do a kernel upgrade?  I can't seem to find any concrete answers about whether this will be a problem, though from what I've been reading I suspect it will.  Is there any sort of configuration I can do to make GRUB automatically install itself to both drives?

If that's the case, will GRUB 2 - the default for new Karmic installs - fix the problem so I don't have to do that after every upgrade?

---

### Post by wsmoser2004 on 2009-08-20
Well, I think I answered my own question (hate it when I do that).  

I did an upgrade today, and in the middle GRUB (actually update-grub, I think) asked me whether or not I wanted to update the configuration file menu.lst.  Since I had already backed it up, I elected to overwrite it with the "package maintainer's version."  Then, when the upgrade was complete, I modified the new menu.lst so that it would point to (hd0,0) and (hd1,0).

I didn't seem to need to reinstall grub.  Just in case, I fired up grub and did a 
```

find /boot/grub/stage1

```

When it returned
```

hd(0,0)
hd(1,0)

```

I felt pretty safe that GRUB was still there, and viola, on a reboot everything was fine.

---

