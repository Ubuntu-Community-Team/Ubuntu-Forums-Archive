---
title: "VM Workstation 10 not starting any guests"
date: 2013-10-24
forum: Virtualisation
---

### Post by AussiePozzie on 2013-10-24
After upgrading to 3.8.0-32 kernel two days ago, Workstation failed to start guest, responded with this error:
> Unable to change virtual machine power state: Cannot find a valid peer process to connect to
Googling has given scant results, and none of them actually refere to this problem directly.

Installing 
> sudo apt-get install open-vm-tools open-vm-tools-dev open-vm-dkms open-vm-toolbox open-vm-tools-dev
made no difference, equally so 
> sudo vmware-modconfig --console --install-all
equally so, removing the VM and reinstalling it, made no difference either.

**Reverting to back to kernel 3.8.0-31 isn't possible for me, as driver upgrades depend on 3.8.0-32.**

I can remember having similar problems with Workstation 9 after kernel upgrades, that it wouldn't compile, but applying a patch solved that problem. From what I understand, this issue should have gotten fixed in Workstation 10

When installing Workstation 10 under 3.8.0-19, it worked fine.

On a parallel installation of 13.10 for testing purposes, the VM 10 installs fine and also starts the guest with no problem, but due other other issues, I can't yet run 13.10

Useful suggstions would be greatly appreciated.

---

### Post by centaur2 on 2013-11-16
I had the same problem (in Fedora 18) and found that I was hitting the maximum allowed open files.  Try increasing your settings in /etc/security/limits.conf , for example :

user        soft     nofile          65536
user        hard    nofile          65536

Then log out and log back in.

---

