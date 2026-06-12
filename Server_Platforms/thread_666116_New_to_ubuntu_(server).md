---
title: "New to ubuntu (server)"
date: 2008-01-13
forum: Server Platforms
---

### Post by michaelAMSI on 2008-01-13
Played with ubuntu but couldn't get it to do what I wanted so downloaded and installed server (with graphical interface).
  
I have an Intel DG33TL, Core2duo E6550 cpu, 2 Gb RAM, 3 Seagate 250 Gb HDs.  

Want to set it up as a "data server" to which I can back up files from each of my other 12 XP/Vista PCs in the office.  I want them each to have a folder with their name.  Passworded?  OK but not necessary as security is not a big issue at this point but maybe later.

I would like to have one large data partition and a smaller OS partition.

I would like the drives in a raid level 10(1st choice) or 5(2nd choice) or 0 (mirror).  The motherboard has raid capabilities but don't know how to get it all set up.  

Appreciate your help.  Please make instructions detailed as I am new to Linux (learning but new).

Thanks
Michael:confused:

---

### Post by chrisgibbs on 2008-01-13
Hi,

Since I'm not familiar with this motherboard, i'm going to assume that it is a type where the 'HW' RAID is actually software and Ubuntu will need some tweaking before an OS can be setup on it.

Will you be installing the OS into the RAID? 

If you are installing into the RAID then I would suggest you have a look at 

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)
(I have not tried this, but from the quick read I had looks decent enough)

OR

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
(This I have tried - but it may not be what you are looking for.)


If you are not going to setup the OS in the RAID, then I would suggest using software RAID as I had (and still having) huge problems getting my Ubuntu 7.10 Desktop to boot correctly after my 2x320Gb Raid 0 drivers and dmraid was setup. See thread

[http://ubuntuforums.org/showthread.php?t=661618](http://ubuntuforums.org/showthread.php?t=661618)

Cheers,

---

