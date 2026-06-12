---
title: "virtualbox mixup OSE and PUEL"
date: 2010-12-10
forum: Virtualisation
---

### Post by candtalan on 2010-12-10
using ubuntu 10.04 I was happily using virtualbox ose and learning how to run with iso files instead of always burning a cd, and then I tried using PUEL version after uninstalling OSE.

that seemed ok, but I like free versions and then wanted to revert to the OSE. So I now uninstalled the PUEL and re installed the OSE.
Problem seems to be that I do not seem to get back to the original conditions for OSE.

Maybe something has got compiled and is not so easy to revert?


Window- virtualbox error
=================================
Failed to open a session for the virtual machine lubuntu.
Virtual machine 'lubuntu' has terminated unexpectedly during startup.

details:
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {99404f50-dd10-40d3-889b-dd2f79f1e95e}
==============================


window- virtualbox error in supR3HardenedMainInitRuntime
==============================
RTR3Init failed with rc=-1912 (rc=-1912)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.
==============================

comment- when I install virtualbox-ose-dkms, which seems to be installed already anyway, and run
sudo modprobe vboxdrv
then the problem still remains.

Any ideas please? tia

---

