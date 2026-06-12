---
title: "Clustered File System (GFS or OCFS2)"
date: 2008-11-26
forum: Server Platforms
---

### Post by cpriest on 2008-11-26
I've got an OCFS2 cluster setup with 6 nodes and am running into the same problems many others are.  About every 3 days the nodes lock up, currently we have to reboot all nodes to fix it.

In an attempt to get away from ocfs2 we have also tried setting up gfs2 but have run into major difficulties, does anyone have an Ubuntu install HOWTO for GFS2?

We're running in a VMware environment, if anyone has any tips for GFS2 or OCFS2 in that type of environment on ubuntu it would be a great help!

---

### Post by ALAA_AA on 2009-05-25
Hi,

I'm facing some problems making OCFS2 works. I thought asking you for help might be the only way for me to fix the my pb.
Did you find any howto for the OCFS2 on ubuntu ?? 
I'm trying to build a cluster of 3 ubuntu servers ( 2x8.04 , and 1x8.10) . i want them to share the same LUN ( external storage using SAN FC). i'm searching for a howto build a file system. OCFS2, GPFS, lustre , ....

for the moment, the connection works between the nodes and the storage:  i tried mounting lun's and it worked. I think that my multipath works fine for the qlogic HBA's, and i still need a file system.

I've tried to install lustre, i didn't succeed, nor for GPFS, nor for OCFS2.. 

Any idea about something that really works fine, without passing weeks reading autoconfiguration and autoinstallation scripts made for Redhat or suse and then translating them to ubuntu ?? Thank you for your help
P.S. i think that i've read all the forums, and whenever i find something, i test it carefully. but still nothing works. example :
[http://www.ubuntugeek.com/heartbeat2-xen-cluster-with-drbd8-and-ocfs2.html](http://www.ubuntugeek.com/heartbeat2-xen-cluster-with-drbd8-and-ocfs2.html)
[https://help.ubuntu.com/community/SettingUpGPFSHowTo](https://help.ubuntu.com/community/SettingUpGPFSHowTo)
...

Thank's a lot

Best Regards,
Alaa

---

### Post by cpriest on 2009-05-25
We are still using ocfs2 and its been very stable.  Our issue was actually being caused whenever a vm migrated in the cluster but ultimately was a problem with the Dell BIOS.  After updating the bios we had no further problems.

What problem are you running into?

Here are some links we found useful:
[http://www.ubuntugeek.com/heartbeat2-xen-cluster-with-drbd8-and-ocfs2.html](http://www.ubuntugeek.com/heartbeat2-xen-cluster-with-drbd8-and-ocfs2.html)
[http://oss.oracle.com/projects/ocfs2/dist/documentation/v1.4/ocfs2-1_4-usersguide.pdf](http://oss.oracle.com/projects/ocfs2/dist/documentation/v1.4/ocfs2-1_4-usersguide.pdf)
[http://oss.oracle.com/projects/ocfs2/dist/documentation/ocfs2_faq.html](http://oss.oracle.com/projects/ocfs2/dist/documentation/ocfs2_faq.html)

---

### Post by yvess on 2010-02-01
What is better (reliable, faster) for the storage of kvm virtualization host images 
GFS2 or OCFS2 (both on top over drbd8)?
Which one would you recommend for ubuntu 9.10?
Is there a trend for ubuntu in which direction the future goes?

---

### Post by yvess on 2010-02-02
does nobody use GFS2 or OCFS2?
other better alternatives?

---

### Post by yvess on 2010-08-24
Finally I went with ocfs2, gfs seemed to complicated to setup. Ocfs2 works flawless. I have no problem with it (running since half a year).

---

