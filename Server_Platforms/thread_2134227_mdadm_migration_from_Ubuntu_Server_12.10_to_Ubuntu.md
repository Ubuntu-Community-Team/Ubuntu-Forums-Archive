---
title: "mdadm migration from Ubuntu Server 12.10 to Ubuntu Desktop 10.10"
date: 2013-04-10
forum: Server Platforms
---

### Post by grunge09 on 2013-04-10
I have a Ubuntu Server v12.10 running off an 8gb usb flash drive.  With a mdadm raid5 array of FOUR 2TB sata drives.  One is a spare.  When I installed Server off the CD it made the array drives /sda, /sdb, /sdd, /sde.  It left the sdc out for some reason.  Now on this system I am using motherboard stat ports.  

My other pc is ubuntu desktop v10.10.  I have a PCI-E Promise 8 port raid controller that I would be using it as passthru for the raid.  This machine however does NOT run off USB flash drive.  It has a 1tb sata drive as /sda.  

Does this throw a wrench in the works?  Can I still move the drives over to thenew pc and run:

sudo mdadm --assemble --scan

would that work or go "Tilt?"

-----------------ripped from another thread---------------------------------------------------------------

Normally All you would have to do, is install MDADM, then open a command prompt and type:

sudo mdadm --assemble --scan

DO NOT try to use the old mdadm.conf file or any of the old files....

That should automatically send MDADM to query the disks, identify them and assemble.

There is no risk in that command.

Hopefully your raid set will be recognized, mounted and you should have access to your files.

To save this, so you don't have to do again after reboot:

from command prompt do:
sudo su
sudo mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf

This should save the configuration detail into the mdadm.conf file.

---

### Post by darkod on 2013-04-10
Yeah, it should be fine. Most probably the desktop OS disk will remain sda (and the array had sda as member) but that doesn't matter because it should assemble them by UUID and not by sda, sdb, etc. So, in theory it should be fine.

It's also correct that once the array is assembled it's best to use the --detail --scan command to insert the ARRAY definition in mdadm.conf. I don't see the point of running the sudo su before that, probably an overview. Since you have sudo at the start of the --detail --scan command, that's enough.

However, all of this is under a big assumption: That your controller can do pass through of the disks. Under no curcumstances create an array on the controller with the disks. I'm sure you are aware of that. If it can really do pass through, you should be fine.

This is one of the big flexibilities of mdadm.

---

### Post by SaturnusDJ on 2013-04-10
The 'sudo su' is because after the > sign, the permission is lost. The second sudo is not needed.
To prevent clearing other configuration options in the mdadm.conf, I suggest using >> instead of >, so the data is added. Then modify the file manually. And don't forget to run initramfs -u afterwards.

There is one more thing. Mdadm version. I'm pretty sure 10.04 doesn't have a mdadm version build in for metadata/superblock >0.90 support. So maybe 10.10 doesn't have also. This is fixable of course. That is, if it's a problem at all.

---

### Post by darkod on 2013-04-10
Thanks, I missed that. I'm used to:
```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

That works with single command and doesn't need sudo su first.

---

