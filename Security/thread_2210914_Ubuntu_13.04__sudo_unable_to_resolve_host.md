---
title: "Ubuntu 13.04  sudo unable to resolve host"
date: 2014-03-13
forum: Security
---

### Post by Halfe on 2014-03-13
Im running the Ubuntu distro for FreeNAS Jail. and trying to solve this problem.

> root@Ubuntu:/mnt/Downloads/CrashPlan/CrashPlan-install# sudo ./install.sh
sudo: unable to resolve host Ubuntu
sudo: ./install.sh: command not found


> root@Ubuntu:/mnt/Downloads/CrashPlan/CrashPlan-install# ls
CrashPlan_3.6.3.cpi  INSTALL           install.sh  [COLOR=#0000ff]scripts[/COLOR]
EULA.txt             install.defaults  README      uninstall.sh

and when i try using this link [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)
i get this 

> root@Ubuntu:/mnt/Downloads/CrashPlan/CrashPlan-install# gksu gedit /etc/hosts


(gksu:26221): Gtk-WARNING **: cannot open display:



how do i edit /etc/hosts without using gksu/gksudo


> root@Ubuntu:/mnt/Downloads/CrashPlan/CrashPlan-install# cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       ubuntu-i386


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


Everything is done via SSH.

---

### Post by Lars Noodén on 2014-03-13
> **Halfe said:**
> 
how do i edit /etc/hosts without using gksu/gksudo

gksudo and gedit for graphical environments.  

You could try [nano](http://manpages.ubuntu.com/manpages/saucy/en/man1/nano.1.html)

```

sudo nano -w /etc/hosts

```

---

### Post by Halfe on 2014-03-13
[http://askubuntu.com/questions/282350/bash-install-sh-permission-denied-installing-intel-fortran-2011](http://askubuntu.com/questions/282350/bash-install-sh-permission-denied-installing-intel-fortran-2011)

the > [COLOR=#000000]*sudo: ./install.sh: command not found*[/COLOR] i used the link above

---

### Post by Halfe on 2014-03-13
thanks for the help

---

