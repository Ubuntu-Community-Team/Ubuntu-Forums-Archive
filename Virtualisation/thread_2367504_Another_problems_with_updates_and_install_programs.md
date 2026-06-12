---
title: "Another problems with updates and install programs [Lubuntu 16.04]"
date: 2017-07-31
forum: Virtualisation
---

### Post by sed_faster on 2017-07-31
Hi folks,

I was install virtualbox on my Lubuntu 16.04 when I receive this error:
```

eno@pcwork:~$ sudo apt-get update
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
eno@pcwork:~$ sudo apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-dkms is already the newest version (5.0.40-dfsg-0ubuntu1.16.04.1).
The following packages were automatically installed and are no longer required:
  libllvm3.8 libmircommon5 ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up dkms (2.2.0.3-2ubuntu11.3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package dkms (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on dkms (>= 2.1.0.0); however:
  Package dkms is not configured yet.

dpkg: error processing package virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on virtualbox-dkms (>= 5.0.40-dfsg-0ubuntu1.16.04.1) | virtualbox-source (>= 5.0.40-dfsg-0ubuntu1.16.04.1) | virtualbox-modules; however:
  Package virtualbox-dkms is not configured yet.
  Package virtualbox-source is not installed.
  Package virtualbox-modules is not installed.
  Package virtualbox-dkms which provides virtualbox-modules is not configured yet.

dpkg: error processing package virtualbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 5.0.40-dfsg-0ubuntu1.16.04.1); however:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                            No apport report written because MaxReports is reached already


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dkms
 virtualbox-dkms
 virtualbox
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I try execute the virtual machine appear this message box: [http://imgur.com/a/vDR9H](http://imgur.com/a/vDR9H)
How can I handle this situation?

Thanks

[UPDATE]
I don't know but I think I have problem with apt-get update! :( The system is new, I installed recently.

---

### Post by slickymaster on 2017-07-31
*Thread moved to **Virtualisation**.*

---

### Post by slickymaster on 2017-07-31
Do you have software center, synaptic or update manager, running? In all cases log out and back in and see if that does it.

---

### Post by sed_faster on 2017-07-31
I run 
```

sudo dpkg --configure -a

```
and resolve the problem. But before I needed restart the system.

Why the ubuntu it is looking like windows??? Why I need restart the system all the times I have problems with system?

---

### Post by lammert-nijhof on 2017-07-31
I remember that Lubuntu does not have all needed packages installed by default. You have a list of 4 packages, that are missing, install those first and then re-install Virtualbox. 

However Lubuntu is not very suited for using Virtualbox as host. All periodical processes in the Guest OSes will run lousy, music will stutter and the system monitor / task manager graphs will stop for many seconds and only move again, if you e.g. move the mouse. If you want to use Virtualbox, it is better to use Ubuntu itself as host. Installation is also easier.

Peppermint has the same problem and even Ubuntu Server (without kvm?) has it in a mild form. I did not try other distros.

---

