---
title: "Cannot find a package"
date: 2016-02-25
forum: Ubuntu Development Version
---

### Post by archa2 on 2016-02-25
I am trying to install the 'xrdp' and 'xfce4' package using apt-get .
When I do it from my VM, I am successful and can install both the packages.
 But when I try to install in a container, it fails with the Unable to find package```
[INDENT]root@715ee8a963f0:/# apt-get install xrdp
Reading package lists... Done
Building dependency tree... Done
E: Unable to locate package xrdp
[/INDENT]

```Similarly for xfce4, get a similar exception
```
[INDENT]root@715ee8a963f0:/# apt-get install xfce4
Reading package lists... Done
Building dependency tree... Done
E: Unable to locate package xfce4
[/INDENT]

```
Also noticed that when I run apt-cache search xrdp or apt-cache search xfce4 from VM, I get a big list, but inside the container there is no result got
```
[INDENT]root@715ee8a963f0:/# apt-cache search xrdp
root@715ee8a963f0:/# apt-cache search xfce4
root@715ee8a963f0:/#
[/INDENT]

```
I have the sources.list populated and updated before i run these commands 
echo "deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) wily restricted multiverse universe"  >> /etc/apt/sources.list
apt-get update || apt-get upgrade
Am i missing on something? Please help
[INDENT]
[/INDENT]

---

### Post by cmcanulty on 2016-02-25
I would go with this pages info. Works much better than the stock version

[http://scarygliders.net/x11rdp-o-matic-information/]("http://scarygliders.net/x11rdp-o-matic-information/")

---

### Post by dino99 on 2016-02-25
you need to set your user session; never install as "root"

---

### Post by grahammechanical on 2016-02-25
> But when I try to install _in a container_, it fails with the Unable to find package

Does the container have access to the internet? The "unable to find package" message can mean the package is not in the repositories; It can mean the URL to the repository is wrong or the repository is off-line. It can mean we are not connected to the internet.

Eliminate the obvious.

Regards.

---

