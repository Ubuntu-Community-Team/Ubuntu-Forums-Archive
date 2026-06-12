---
title: "Fault Tolerance/High Availability"
date: 2015-08-19
forum: Virtualisation
---

### Post by biosboy4 on 2015-08-19
Hello, I work for a data center where we use a whole lot of VMware's "Fault Tolerant" Solution. As a personal project, I want to piece together an alternative solution out of open source software. 

Here's my punchlist:

*Configure Ubuntu to be as slimmed down as possible so that I may call it "Just Enough OS"
*Install and configure Xen with XenMotion
*Prove that both the physical and virtual fail-overs work as intended
*Prove the automatic repair of failed virtual machines. 

I've already been reading up, I'm just wondering if you guys have any links/white pages that may be of assistance.

Thanks for listening,

---

### Post by dino99 on 2015-08-19
the mini.iso let you install what you only need

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by biosboy4 on 2015-08-19
Thanks Dino!

---

### Post by tgalati4 on 2015-08-19
Using OpenStack services (not necessarily slim):  [https://wiki.ubuntu.com/ServerTeam/OpenStackHA](https://wiki.ubuntu.com/ServerTeam/OpenStackHA)

V-Server uses a single kernel to run multiple (linux) VM's reducing overhead over Xen.  Don't know how well-supported it is under Ubuntu:  [http://linux-vserver.org/Welcome_to_Linux-VServer.org](http://linux-vserver.org/Welcome_to_Linux-VServer.org)

The XenMotion wiki page does not exist in Ubuntu's community documentation collection, so you may be the first.    The only mention of XenMotion is 2 years old:  [https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20(XenAPI)%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager](https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20(XenAPI)%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager)

Xen is a moving target so just when you get it figured out--it changes!

---

### Post by biosboy4 on 2015-08-24
How about using KVM with oVirt? Will that work for Live migration, high availability, etc? If so, can you guys point me towards some guides/whitepages for installing/configuring KVM and oVirt on Ubuntu?

---

### Post by TheFu on 2015-08-25
oVirt was RHEL-only last time I looked. [http://www.ovirt.org/Ovirt_build_on_debian/ubuntu](http://www.ovirt.org/Ovirt_build_on_debian/ubuntu) has instructions for manually making it work on Ubuntu - don't know if this works or not.  It is NOT "light."  It is another one of those redhat enterprise tools that they didn't find any language they didn't want to use - like FreeIPA (which took years to port to Debian/Ubuntu).  Both are highly impressive, provided you don't look under the covers at all the little duck feet kicking frantically. ;)

IMHO.

libvirt is the important part of oVirt. Both virt-manager and virsh use libvirt.  To automate a live migration, I'd probably use virsh for the scripting.  I've never needed it. Systems don't go down under KVM.  Like since 2010 - ZERO crashes - but we are small and monitor everything for the beginning of failures and pre-replace disks, controllers, HW.

We moved off Xen completely in 2011 (migrated to KVM) after 3 yrs of weirdness every few weeks. The exact same systems are running KVM all this time perfectly. I hear it works better on RPM-based distros. Obviously my experience with Xen is dated.

If I wanted HA - I'd setup clustering like physical servers. None of our systems have to be up all the time - 4 hrs of downtime is fine, though we've never had more than 3 hrs due to some complex software migrations.

---

