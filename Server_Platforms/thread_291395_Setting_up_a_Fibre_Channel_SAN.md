---
title: "Setting up a Fibre Channel SAN"
date: 2006-11-02
forum: Server Platforms
---

### Post by dallingham on 2006-11-02
I need to set up a Fibre Channel SAN under Ubuntu. I have a 1.5TB Fibre Channel RAID array that about 8 machines need to connect to. Performance is key, so we need direct connect instead of NFS mounting.

I realize that I'm going to need a SAN aware filesystem. GFS seems to be the likely candidate. However, I can't seem to find any instructions on how to setup GFS. In fact the attempting to install the redhat-cluster-suite (under 6.10) provides the following errors:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clvm
Recommended packages:
  system-config-cluster
The following NEW packages will be installed:
  clvm redhat-cluster-suite
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/199kB of archives.
After unpacking 541kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package clvm.
(Reading database ... 100526 files and directories currently installed.)
Unpacking clvm (from .../clvm_2.02.06-2ubuntu3_amd64.deb) ...
Selecting previously deselected package redhat-cluster-suite.
Unpacking redhat-cluster-suite (from .../redhat-cluster-suite_2.20061002-0ubuntu2_all.deb) ...
Setting up clvm (2.02.06-2ubuntu3) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help or advice would be greatly appreciated.

---

### Post by dannyboy79 on 2006-11-02
well I am no expert but I can tell you that you should read your syslog just like it says. Also, it appears that everything installed correctly it's just that when Starting Cluster LVM Daemon clvmd could not connect to cluster manager didn't work then the next step in the setup couldn't continue. Have you tried to gogle how to setup clvm?

---

### Post by dallingham on 2006-11-02
Nothing related appears in the syslog. The software obviously can't talk to the cluster manager, because I haven't set one up yet. I'm assuming that I have to install the clustering software before I can set up a clustering manager. However, the clustering software seems to want a clustering manager to already exist before it will install. A bit of a catch-22.

---

### Post by fnjordy on 2006-11-03
You can install multiple packages at once:

$ sudo apt-get install package-one package-two ...

---

### Post by dannyboy79 on 2006-11-03
> **fnjordy said:**
> You can install multiple packages at once:

$ sudo apt-get install package-one package-two ...

i am not sure what your point is here, as you can see by the command that ran, "The following NEW packages will be installed:
clvm redhat-cluster-suite" it was trying to install both packages. The problem is that when the first one was installed it didn't set itself up  correctly so then the following package failed because it was dependent upon the first being installed and CONFIGURED.

---

