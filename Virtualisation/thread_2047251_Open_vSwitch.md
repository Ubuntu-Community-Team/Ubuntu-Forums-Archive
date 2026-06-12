---
title: "Open vSwitch"
date: 2012-08-24
forum: Virtualisation
---

### Post by Maose on 2012-08-24
Hi,
I´m a Network Engineer and Freelancer and I`m a newbie on both sides, Ubuntu and Open vSwitch. My intention is to get a deeper experience in network virtualization and therefore I want to install Open vSwitch on my Ubuntu 12.04 host. I followed the installation description from this link [http://blog.allanglesit.com/2012/03/linux-kvm-ubuntu-12-04-with-openvswitch/](http://blog.allanglesit.com/2012/03/linux-kvm-ubuntu-12-04-with-openvswitch/) but I don´t get running the brcompat modul.
The module seems to be available, but it´s not loaded.

```
$ ls -l /lib/modules/$(uname -r)/kernel
total 5636
drwxr-xr-x 3 root root 4096 Aug 22 22:49 arch
-rw-r--r-- 1 root root 503300 Aug 22 23:01 brcompat_mod.ko
drwxr-xr-x 3 root root 4096 Aug 22 22:49 crypto
drwxr-xr-x 63 root root 4096 Aug 22 22:49 drivers
drwxr-xr-x 53 root root 4096 Aug 22 22:49 fs
drwxr-xr-x 6 root root 4096 Aug 22 22:49 lib
drwxr-xr-x 46 root root 4096 Aug 22 22:49 net
-rw-r--r-- 1 root root 5232461 Aug 22 23:01 openvswitch_mod.ko
drwxr-xr-x 12 root root 4096 Aug 22 22:49 sound
drwxr-xr-x 5 root root 4096 Aug 22 22:49 ubuntu
```

```

$ lsmod | grep brcom
$ 

```

Everything else seems to be ok.

```
$ service openvswitch-switch status
ovsdb-server is running with pid 1170
ovs-vswitchd is running with pid 1182
```

[FONT=Arial][SIZE=3][/SIZE][/FONT]
Can anybody help in this case?


Kind regards

Markus Ose

---

### Post by yitzhakbg on 2012-09-12
I don't know if you got it solved by now.
In any case, here are useful links, some of which recommend staying away from brcompat:
[http://blog.flameeyes.eu/tag/lxc](http://blog.flameeyes.eu/tag/lxc)
[http://networkstatic.net/2012/04/installing-and-configuring-openvswitch-on-ubuntu-12-04-precise-pangolin/](http://networkstatic.net/2012/04/installing-and-configuring-openvswitch-on-ubuntu-12-04-precise-pangolin/)
[http://s3hh.wordpress.com/2012/05/28/connecting-containers-on-several-hosts-with-open-vswitch/](http://s3hh.wordpress.com/2012/05/28/connecting-containers-on-several-hosts-with-open-vswitch/)

---

### Post by Maose on 2012-09-21
yitzhakbg, thank you for your help, but I could solve the problem by myself. After checking the configuration again and again I could find ou that it was a simple typing error. In /etc/default/openvswitch-switch I forgot to delete the hash-tag at the beginning of the line BRCOMPAT=yes and so the module wasn´t installed automatically.

---

