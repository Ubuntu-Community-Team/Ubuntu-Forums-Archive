---
title: "Ubuntu LTS-14.04 guest in VM - mount vboxsf errors.. Unknown filesystem type"
date: 2014-09-02
forum: Virtualisation
---

### Post by spicycold on 2014-09-02
Facing above mentioned issue in Ubuntu LTS 14.04 version running as Guest in Virtual Box VM (on Windows7). This works fine in Ubuntu desktop 12.0x fine.  
In 12.0x I do see vboxsf kernel modules, but not in LTS 14.04. Tried to apt-get for the package but it can't fine one. 

Anybody faced this and solved the issue?  

-SC

---

### Post by ibjsb4 on 2014-09-03
I run vBox using an ubuntu host, not so sure about windows host setup, but ..

You say that you cannot find the package.  Are you talking about virtualbox-guest-dkms?

A general fix I assume will work in windows:
```
sudo /etc/init.d/vboxdrv setup
```
I have a mix of 12.04 and 14.04 guest using vBox 4.3.14.  Is that the version your running?

---

