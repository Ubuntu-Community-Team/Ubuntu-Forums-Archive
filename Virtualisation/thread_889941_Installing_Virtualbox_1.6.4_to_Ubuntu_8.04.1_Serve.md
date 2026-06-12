---
title: "Installing Virtualbox 1.6.4 to Ubuntu 8.04.1 Server"
date: 2008-08-14
forum: Virtualisation
---

### Post by thegnark on 2008-08-14
I'm trying to install VirtualBox 1.6.4 onto Ubuntu Server Hardy 8.04.1, but am running into a bit of difficulty with dependencies due to its expectation of X being installed. I've already installed all the necessary build packages.

My intent it to run this headless, so even if I have to install the libraries, but don't start up X, that's fine by me. Any recommendations for packages to install to satisfy these libraries, or workaround to not need them?


```
sudo dpkg -i virtualbox_1.6.4-33808_Ubuntu_hardy_amd64.deb
Selecting previously deselected package virtualbox.
(Reading database ... 32191 files and directories currently installed.)
Unpacking virtualbox (from virtualbox_1.6.4-33808_Ubuntu_hardy_amd64.deb) ...
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libglib2.0-0 (>= 2.12.0); however:
  Package libglib2.0-0 is not installed.
 virtualbox depends on libidl0; however:
  Package libidl0 is not installed.
 virtualbox depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not installed.
 virtualbox depends on libsdl1.2debian (>= 1.2.10-1); however:
  Package libsdl1.2debian is not installed.
 virtualbox depends on libx11-6; however:
  Package libx11-6 is not installed.
 virtualbox depends on libxcursor1 (>> 1.1.2); however:
  Package libxcursor1 is not installed.
 virtualbox depends on libxml2 (>= 2.6.27); however:
  Package libxml2 is not installed.
 virtualbox depends on libxslt1.1 (>= 1.1.20); however:
  Package libxslt1.1 is not installed.
 virtualbox depends on libxt6; however:
  Package libxt6 is not installed.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox
```

---

### Post by mrsteveman1 on 2008-08-14
Doesn't virtualbox only come with a GUI installer, or were you going to configure it and run VMs some other way? By installer, i mean installing guests etc.

As long as you install the stuff it complains about you should be fine, i have the same trouble with installing truecrypt 5/6 on a headless server, it expects all these libraries and in fact relies on them being linked in at run time, even though it functions fine in bash without x11 even running.

Those specific errors are due to dpkg dependencies so you should be able to get those installed easily by name, but with TC it would also complain at runtime because it needed some libraries that the package didn't have listed as a dependency so i had to install those manually, and sometimes the libraries it complains about aren't named the same as the package you need, but you should be able to do some searching with apt-cache search [libraryname] if you have problems

---

### Post by thegnark on 2008-08-14
i guess i'm a little confused as to why it didn't prompt me to install the dependencies as normal

Edit: and no... you can completely manager virtualbox via VBoxManage, a command-line utility

---

### Post by mrsteveman1 on 2008-08-14
I don't think dpkg could resolve dependencies and download them from a repo. The repos are an apt thing, which is technically separate from dpkg and .debs.

---

### Post by thegnark on 2008-08-14
ahhh right your are... *shames self for overlooking simple things*

in any respect, "sudo apt-get install -f" resolved all the dependencies

---

### Post by mrsteveman1 on 2008-08-14
:D

How do you like Vbox? Does it work as well as VMware Server or ESXi ?

---

### Post by thegnark on 2008-08-15
It works as well as any other VM software I'ev played with (Virtual PC, VMWare)... specifically I loved the VRDP feature... but I've only run it on a Windows host... mostly I was just limited by Window's ability to create 1 bridge per physical interface, which doesn't scale wwell when you need multiple VMs.

---

