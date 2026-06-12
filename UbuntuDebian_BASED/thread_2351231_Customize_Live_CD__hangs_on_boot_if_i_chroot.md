---
title: "Customize Live CD  hangs on boot if i chroot"
date: 2017-02-01
forum: Ubuntu/Debian BASED
---

### Post by george.asenov on 2017-02-01
Hello, 

I'm customizing the following Live CD [http://repo.r1soft.com/bm/serverbackup-bootcd-agent-5.8.2.iso](http://repo.r1soft.com/bm/serverbackup-bootcd-agent-5.8.2.iso) (it is ubuntu based) . The CD boots without issues before customization.
At minimum I need to install two packages vlan and ifenslave. 
So I made virtual machine with the closest ubuntu version as possible to the version of the ubuntu on the live CD and with the same architecture. 
I'm following this tutorial for the customize process [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) except the customization part of it because I do not need them (the cd do not have Desktop only console).
Also skip the part "rm /sbin/initctl and dpkg-divert --rename --remove /sbin/initctl" because I it was failing in container check and on using the cd as repository. 

The cd kernel version is "3.13.0-37-generic" 
uname -r  on the host system (on which i edit the iso)"3.19.0-25-generic"

So the issue is if I chroot to the CD like in the tutorial install the two packages (i think the result is the same if I only chroot without doing anything) the CD get stuck on the step "Starting system logging daemon   [OK]" I only unpack the CD but do no not mount the dev/ sys/ and so on and not chroot but only add the .deb files of the packages in /root/ folder of the cd it boots normally. 


My conclusion is the chroot which for some reason is braking the CD. 
As i do not have experience with chroot probably there is something that isn't up to date (like the initctl) in the tutorial that I need to or not to do around the chroot. 
Please help because I made near 50 CD's without susses.

PP I'm trying to boot trough IPMI on supermicro server. So no issues with burning CD-s using only iso

---

### Post by howefield on 2017-02-01
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by george.asenov on 2017-02-06
So there isn't any one that can help with that liveCD?

---

### Post by george.asenov on 2017-02-06
So there isn't any one that can help with that liveCD?

---

