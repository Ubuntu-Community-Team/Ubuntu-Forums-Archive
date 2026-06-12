---
title: "Help me install QEMU on Ubuntu server 16.04 LTS"
date: 2018-02-07
forum: Virtualisation
---

### Post by andrewfer000 on 2018-02-07
I would like to install QEMU/KVM on my server to run VMs but the install seems to be running into dependency issues here's the output... I allready tried apt-get install -f and totally cleaning and removing the software and re-installing it.

```
problems prevent configuration of qemu:
 qemu depends on qemu-system (>= 1:2.5+dfsg-5ubuntu10.20); however:
  Package qemu-system is not configured yet.

dpkg: error processing package qemu (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qemu-kvm:
 qemu-kvm depends on qemu-system-x86 (= 1:2.5+dfsg-5ubuntu10.20); however:
  Package qemu-system-x86 is not configured yet.

dpkg: error processing package qemu-kvm (--configure):
 dependency problems - leaving unconfigured
Setting up virtinst (1:1.3.2-3ubuntu1.16.04.4) ...
No apport report written because MaxReports is reached already
                                                              Setting up virt-manager (1:1.3.2-3ubuntu1.16.04.4) ...
Setting up virt-viewer (1.0-1) ...
update-alternatives: using /usr/bin/spice-xpi-client-remote-viewer to provide /usr/bin/spice-xpi-client (spice-xpi-client) in auto mode
Processing triggers for systemd (229-4ubuntu21.1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 qemu-system-common
 binfmt-support
 qemu-system-x86
 qemu-system-sparc
 qemu-system-ppc
 qemu-system-misc
 qemu-system-mips
 qemu-system-arm
 qemu-system
 qemu-user-binfmt
 libvirt-bin
 qemu
 qemu-kvm

```
 I suck at linux when it comes to dependency issues. can someone please give me a step by step by on how to fix.

---

### Post by andrewfer000 on 2018-02-07
Whoops sorry wrong fourm. sorry

---

### Post by wildmanne39 on 2018-02-07
*Thread moved to **Virtualisation, a more appropriate forum**.*

---

### Post by andrewfer000 on 2018-02-08
Thanks for moving it to the right place :D

---

