---
title: "Ubuntu server 18.04: Where could I found information about /etc/cloud directory?"
date: 2018-05-22
forum: Server Platforms
---

### Post by itprof on 2018-05-22
Hi, 

I've just installed the new server version and I found that it comes with a **/etc/cloud** directory. I can't find any information about that in the server manual either on Internet. What is it the purpose of this directory and how can you  use the templates/config files that it has inside? 

Is there any information about this topic on Ubuntu Official site?

If I have a standalone server, do I need this? If I modify Netplan files, do I have to modify the similar files on /etc/cloud?

Thanks.

---

### Post by LHammonds on 2018-05-22
Sounds like you installed from the "live" ISO which is considered "default."  The cloud files are not part of the "alternative" install.

I make use of LVM partitions and as such, I have to use the "alternative" ISO image.  There are some differences between the end-results of the servers depending on what ISO image you use to install (beyond what is mentioned in the release notes).  We are trying to document a list of [known differences](https://ubuntuforums.org/showthread.php?t=2390785) here.

You can check what software is installed having the name "cloud" in it with this command:

```
apt search cloud | grep installed
```

Here are the results from that command on a server installed using the alternative ISO image (along with the descriptions added):

```

cloud-guest-utils/bionic,bionic,now 0.30-0ubuntu5 all [installed]
  cloud guest utilities

cloud-initramfs-copymods/bionic,bionic,now 0.40ubuntu1 all [installed]
  copy initramfs modules into root filesystem for later use

cloud-initramfs-dyn-netconf/bionic,bionic,now 0.40ubuntu1 all [installed]
  write a network interface file in /run for BOOTIF

netplan.io/bionic,now 0.36.1 amd64 [installed]
  YAML network configuration abstraction for various backends

nplan/bionic,bionic,now 0.36.1 all [installed]
  YAML network configuration abstraction - transitional package

pollinate/bionic,bionic,now 4.31-0ubuntu1 all [installed]
  seed the pseudo random number generator

```

LHammonds

---

### Post by itprof on 2018-05-22
Thank you for your answer LHammonds. Maybe I should reinstall the system with an alternative ISO.

---

### Post by LHammonds on 2018-05-23
> **itprof said:**
> Thank you for your answer LHammonds. Maybe I should reinstall the system with an alternative ISO.
If you installed using the "live" ISO, then you probably have a single partition and I would not recommend that for ANY server regardless of the operating system installed.  If a process starts to fill up /var, that also means it is filling up all your available space including your root (/) and when that happens, the server will freak out and it won't be pretty.

Check my signature for Ubuntu Server and my notes about separating the partitions and controlling the growth by separating the partitions and allowing automated expansion using LVM.

LHammonds

---

