---
title: "read-only file system"
date: 2009-05-14
forum: Server Platforms
---

### Post by brown705 on 2009-05-14
Disclaimer: I'm a newbie at Ubuntu and Linux in general.

I don't know what I have done here, but I installed Ubuntu Server 8.10 and started going through the install directions for Zenoss ([http://www.howtoforge.com/zenoss_network_monitor_ubuntu](http://www.howtoforge.com/zenoss_network_monitor_ubuntu)) and also followed along here ([http://myhowtosandprojects.blogspot.com/2009/04/installing-zenoss-on-ubuntu-810-hardy.html](http://myhowtosandprojects.blogspot.com/2009/04/installing-zenoss-on-ubuntu-810-hardy.html)).  

Anyway, went through some of the directions OK and I began downloading the .bin file for Zenoss Core 2.4.0 using "wget".  It was downloading alright, but did not complete (I got about 17 MB of about 95+ MB).

Now, I cannot remove the file (zenoss-stack-2.4.0-linux.bin), even using sudo or logged in as root.  When I try to to an "rm", it says "rm: cannot remove 'zenoss-stack-2.4.0-linux.bin': Read-only file system".  I've done chmod 755 and chmod 777 and tried to chown it as well.  I can't get this file removed.

I'm doing this through Putty if it makes a difference.

Please help.  Thanks.
Michael

---

### Post by a9k3d on 2009-05-14
Check the output of "mount". Example:
/dev/md0 on / type ext3 (rw,errors=remount-ro)

You may find your partition has remounted (ro), read only, because of an error. If so, type **dmesg | grep -i error | less** to check for what errors happened.

---

### Post by brown705 on 2009-05-15
> **a9k3d said:**
> Check the output of "mount". Example:
/dev/md0 on / type ext3 (rw,errors=remount-ro)

You may find your partition has remounted (ro), read only, because of an error. If so, type **dmesg | grep -i error | less** to check for what errors happened.

I'm not sure how to do what you said in the first part...can you tell me what to enter?  I typed the dmesg line you gave and got this "-bash: /usr/bin/less: Input/output error", but when I did it without the "| less" part it returned nothing.  When I run dmesg by itself, I see a bunch of these:

[176426.613861] sd 0:0:0:0: rejecting I/O to offline device
[176435.640025] AAC: Host adapter dead -3

Are they related?  I'm running on a Dell PowerEdge 2650 on two drives that are mirrored from the PERC.  Can you suggest any commands I can run to look deeper into this?

Thanks for the help.
Michael

---

