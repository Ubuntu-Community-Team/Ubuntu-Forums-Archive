---
title: "xen-create-image fails on 7.10"
date: 2008-01-09
forum: Virtualisation
---

### Post by scpetand on 2008-01-09
Hi

I'm new into Ubunto but I have some experience of Suse so maybe I'm running into a beginners problem here.

I want to use Ubuntu as Dom0 and run several  xen virtualized hosts on it.

I install the necessery xen packages by:
apt-get install ubuntu-xen-server
and of course
apt-get update 
apt-get upgrade

If I have understood it correctly the easiest way of creating a gutsy DomU  is using xen-tools. First I edit  /etc/xen-tools/xen-tools.conf:
install-method = debootstrap
dist   = gutsy
mirror = [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu)

and then runs command:
xen-create-image --hostname=vmubuntu1 --dhcp

and the DomU installation fails.
/var/log/xen-tools/vmubuntu1.log gives
W: Failure trying to run: chroot /tmp/8ShTZIiFna mount -t proc proc /proc
It seems like it is a debootstrap bug [https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589](https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589)

Is the debootstrap bug causing my problem?
When will it be fixed?
If I want to do this manually instead is there any guidline, I haven't found any?

Regards
Peter Andersson

---

