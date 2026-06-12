---
title: "Ubuntu Server SATA server problems"
date: 2010-12-28
forum: Server Platforms
---

### Post by miles.dp on 2010-12-28
I have recently purchased this server:

[http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/15351-15351-4237916-4237918-4237917-4248009.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/15351-15351-4237916-4237918-4237917-4248009.html)

It uses SATA hard drives but ubuntu server installer is not able to find them. I have checked the bios and it is AHCI.

Any ideas on why it isn't being found?

Thanks,

- M

---

### Post by spynappels on 2010-12-28
Are these separate SATA drives or do you have them connected to a hardware RAID card? You may need to check the RAID card compatibility if you are using one.

---

### Post by mikeobeda on 2010-12-29
Are you able to complete the install at all?  If you're able to install to one drive, and then just can't see the others, try running:

sudo lshw -C disk

That will show you the hard drives your server sees.  if you can see the 
hard drives after issuing that command, then just take a look at this link
to see more on formatting it and creating a mount point:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

