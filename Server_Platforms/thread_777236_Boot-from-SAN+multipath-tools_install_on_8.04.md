---
title: "Boot-from-SAN+multipath-tools install on 8.04"
date: 2008-05-01
forum: Server Platforms
---

### Post by reedk on 2008-05-01
I'm having problems booting a server from my SAN with multipath-tools.
I have a server (32-bit x86) that was installed as Boot-from-SAN by attaching only a single path from one HBA to one SAN controller. After the install and reboot were complete, I installed multipath-tools and with the goal of attaching the rest of the redundant paths.
At the time, I also installed multipath-tools-boot as I will be booting in a multi-pathed config. However, when I boot fsck fails because "some other process" has control of the device - in short, I think during the bootstrap the system does not like the multiple paths.
I then removed multipath-tools-boot and tried to install multipath-tools-initramfs, but I can't:

> root@misanasw04:/etc# apt-get install multipath-tools-initramfs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  multipath-tools-initramfs: Depends: multipath-tools but it is not going to be installed
E: Broken packages

and with dpkg:

> root@misanasw04:/etc# dpkg -i --force-depends multipath-tools-initramfs
dpkg: error processing multipath-tools-initramfs (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 multipath-tools-initramfs


At the time I issue these commands, multipath-tools is already installed (without errors).

Should I be using multipath-tools-initramfs over multipath-tools-boot? If so, any ideas on how to get -initramfs to install?

---

