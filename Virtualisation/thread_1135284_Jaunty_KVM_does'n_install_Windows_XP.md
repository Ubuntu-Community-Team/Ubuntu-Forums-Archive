---
title: "Jaunty KVM does'n install Windows XP"
date: 2009-04-24
forum: Virtualisation
---

### Post by hmgp on 2009-04-24
Hello. I'm a bit lost, because I already tried several How-to's that I've found here on the forum an also out there on the Internet.

My objective is to install Windows XP on a KVM virtual Machine having Ubuntu 9.04 (Jaunty) has a host. I tried the method of creating the vm by command line until format is done, and then using virt-manager and all the ohter I've found here. I tried different types of disk image (qcow, qcow2, vmdk, raw, ... ) and my problem persists, when Windows install formats the "hard drive" then copies the files on to it, then reboots and ... nothing stays a black screen ...

Anyone has something for me to try? 

Thank you.

---

### Post by she11c0de on 2009-04-25
I have same problem, and i also try Windows XP with SP2/SP3, but nothing help.
my hardware is Dell D630.

Before upgrade to 9.04, i had install and run Windows XP on ubuntu 8.04/8.10 with KVM, it's work very good.

---

### Post by clhsharky on 2009-04-25
Same problem here all so!
Installing (ubuntu-virt-mgmt) in 9.4 fixed it for me.

Good Luck

---

### Post by she11c0de on 2009-04-26
I had install ubuntu-virt-mgmt and try again, but the problem still exist :(

---

### Post by she11c0de on 2009-04-26
I resolve this problem, when i use 9.04 default version kvm-84, the Windows XP working is OK. after i upgrade to kvm-85 then not working, maybe it's kvm-85 some bugs.

[http://bbs.archlinux.org/viewtopic.php?pid=536830](http://bbs.archlinux.org/viewtopic.php?pid=536830)

---

### Post by hmgp on 2009-04-27
Hi there. Thank you for all your ideas. I managed to test both "Installing (ubuntu-virt-mgmt)" and "default version kvm-84", but the problem remains exactly the same... I will keep trying to discover what it is... and if someone else remembers anything don't forget to share.

---

### Post by clhsharky on 2009-04-28
Hi back to ya all

What kernel are you running? I have 2.6.28.11 in 9.04 and all packages from Ubuntu with xp doing fine.I all so tested on 2nd machine with success again. 8.04 has worked for me but 8.10 has given me issues with windows.

---

### Post by wickerman1413 on 2009-05-03
> **hmgp said:**
> Hello. I'm a bit lost, because I already tried several How-to's that I've found here on the forum an also out there on the Internet.

My objective is to install Windows XP on a KVM virtual Machine having Ubuntu 9.04 (Jaunty) has a host. I tried the method of creating the vm by command line until format is done, and then using virt-manager and all the ohter I've found here. I tried different types of disk image (qcow, qcow2, vmdk, raw, ... ) and my problem persists, when Windows install formats the "hard drive" then copies the files on to it, then reboots and ... nothing stays a black screen ...

Anyone has something for me to try? 

Thank you.

This sounds like the same issue I came across in 8.10. Effectively when the VM rebooted after the format of the virtual disk the CD drive (or ISO image) wasnt defined so it didnt continue the install.

There is some workarounds defined here:
[https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/105195](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/105195)

I just shutdown the virtual machine and edited /etc/libvirt/qemu/wxp.xml to define the CD by hand, then ran virsh, define wxp.xml and start the VM. Strange that this hasnt been resolved yet.

---

### Post by hmgp on 2009-05-05
I there. I'm using 9.04 upgraded from 8.10. Maybe that's a problem since I see lot's of questions from upgrades and not from fresh install. But it's a working machine and with little time to spare to do a clean install, so I will try to give wickerman's ideas some time and let's see if I can go from there. If not I will have to manage a clean install.

Thank you very much for your help!

---

