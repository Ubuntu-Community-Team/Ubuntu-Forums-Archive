---
title: "How do I rum vmware-uninstall-tools.pl on Ubuntu?"
date: 2022-05-03
forum: Virtualisation
---

### Post by Complete on 2022-05-03
How do I rum vmware-uninstall-tools.pl on Ubuntu?

On a Windows 10 OS, I have been using VMware to set up a vitrual machine (because of some strange security concerns with the company, I can not use Hyper-V) and I am using Ubuntu as the OS for the virtual machine.

VMware requires that I run their file, "VMware Tools" and this is the result I get:

> The installation of VMware Tools 10.3.23 build-16594550 for Linux completed successfully, you can decide to remove this software from your system at any time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware tools for the first time, you need to configure it by involing the following command: "/usr/bin/vmware-config-tools.pl". Do you want this program to invoke the command for you now? [yes]

INPUT: [yes] default

sh: 1: /usr/bin/vmware-config-tools.pl: Permission denied Enjoy,

--the VMware Team

Despite this snaky tone, this is the actual message I get after running the vmware-tools file.

Then when I try running vmware-config-tools.pl, I get a "Permission denied" message. Please advise or ask any clarifying questions.

---

### Post by CharlesA on 2022-05-03
This is a duplicate of:
[https://ubuntuforums.org/showthread.php?t=2474605](https://ubuntuforums.org/showthread.php?t=2474605)

---

