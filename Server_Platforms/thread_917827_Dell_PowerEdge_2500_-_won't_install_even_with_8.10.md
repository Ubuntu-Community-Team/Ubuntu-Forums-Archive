---
title: "Dell PowerEdge 2500 - won't install even with 8.10a5 :-("
date: 2008-09-12
forum: Server Platforms
---

### Post by oldsmobile_mike on 2008-09-12
I have an old Dell PowerEdge 2500 that I'm trying to get running with Ubuntu.  I've tried 7.10, 8.04, and even downloaded the latest release of 8.10 I could find, Alpha 5, and am having the exact problems detailed in these threads:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/148466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/148466)

[http://ubuntuforums.org/showthread.php?t=858377&highlight=poweredge+2500](http://ubuntuforums.org/showthread.php?t=858377&highlight=poweredge+2500)

[http://ubuntuforums.org/showthread.php?t=778496&highlight=poweredge+2500](http://ubuntuforums.org/showthread.php?t=778496&highlight=poweredge+2500)

...and many other threads.  It gets to a certain point in the install, usually not any further than 20%, then complains about not being able to read the disc.  Sorry to post another thread about this, but I figure if enough people post about it, maybe they'll do something about fixing it???  :-(

FYI, my Windows Server 2000 disc works fine, but stops at the point where I have to load the custom SCSI drivers (I don't have a driver disc for this machine).  Also, my BIOS is at the latest version (A07), and Perc3 updated to the latest firmware as of last night.

I'm going to try Debian, the Ubuntu Mini install, 6.10 and maybe Fedora tonight, in that order (I've heard that other people have had some success with those versions), and hopefully one of them will work, but it seems like this is a well-known problem from all the threads I found about it, so why isn't anything being done?  :-(

---

### Post by windependence on 2008-09-12
I gotta take a look at your threads but I have it running well on a 2550. I did have a problem with a Perc3 controller but I just removed it and figured I would tackle that later.

Let me read through your links and see if I remember having any of those problems and how I solved them.

-Tim

---

