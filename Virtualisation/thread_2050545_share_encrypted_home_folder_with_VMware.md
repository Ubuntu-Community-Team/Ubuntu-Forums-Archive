---
title: "share encrypted home folder with VMware?"
date: 2012-08-31
forum: Virtualisation
---

### Post by RikoW on 2012-08-31
Dear all,

I'm in the process of setting up a new laptop using the option to encrypt my home directory.

The laptop will be the host of a Windows XP and a Windows7 virtual machine  running under VMware Workstation 8.0.4 / VMplayer 4.

I share my (Ubuntu) home directory with the VMs. Is that still possible if I have /home encrypted?

Thanks and cheers,
             Riko

---

### Post by 2F4U on 2012-08-31
It should work as long as you are logged on. The encrypted folder will be mounted on login and unmounted on logout.

[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

---

