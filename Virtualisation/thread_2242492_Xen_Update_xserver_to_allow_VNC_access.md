---
title: "Xen: Update xserver to allow VNC access"
date: 2014-09-02
forum: Virtualisation
---

### Post by trapperjohn on 2014-09-02
Hi,

I have a 14.04 Xubuntu Desktop running as domU on a 14.04 Ubuntu Server hypervisor. My intention was to use the Xen-integrated VNC server to access the GUI of this system - but unfortunately this is not possible using the current version of Ubuntu's xserver (it crashes instantly when moving the mouse). See

[https://bugs.launchpad.net/ubuntu-gnome/+bug/1312484](https://bugs.launchpad.net/ubuntu-gnome/+bug/1312484)
or
[https://bugzilla.redhat.com/show_bug.cgi?id=1085074](https://bugzilla.redhat.com/show_bug.cgi?id=1085074)

As the last entry suggests, this bug is fixed upstream and should be available in a new version of the X.org server. 

Are there any quick and easy possibilities to update the xserver-xorg package to a more recent version? E.g. a launchpad ppa or something which offers an easy upgrade? I really don't want to start building it from source...

Thanks!

---

### Post by chaoticryld on 2015-02-18
Bump! I have the same issue...

Can we please update the xserver package to include this bug fix? Thanks a lot!!

P.S. @trapperjohn: you can get around this issue for now by installing a VNC server in DomU and connecting a VNC client to <DomU IP>:5900. In my experience this approach is a lot slower though...

---

