---
title: "Gnome Boxes Fails creating guest"
date: 2012-10-20
forum: Virtualisation
---

### Post by TheFuzz4 on 2012-10-20
Hey Everyone

When I try and build out a guest system with Gnome Boxes its failing.  I've replicated this now on 3 machines.  

Here is the error that I"m getting

(gnome-boxes:3397): Boxes-WARNING **: app.vala:266: Unable to open qemu+unix:///session: Failed to connect socket to '/run/user/user/libvirt/libvirt-sock': No such file or directory

(gnome-boxes:3397): Boxes-WARNING **: wizard.vala:358: Failed to create storage pool: invalid connection pointer in virStoragePoolDefineXML

I"m not sure if its missing something during the install or what.  Thank you all in advance for your help with this.

---

### Post by Spr34d on 2012-10-20
I have the same issue,  I can get a bit further if I run gnomes-boxes as root, but then I get a different error

(gnome-boxes:3524): Boxes-WARNING **: wizard.vala:205: Unable to start domain: unsupported configuration: spicevmc not supported in this QEMU binary


Edit: Been fumbling in the dark, and I've managed to get past the OP errors without running as root, but still get the above error, by making sure the libvirtd daemon is running (libvirtd -d) (also added my user to the libvirtd group but don't think was necessary)

To my clueless eyes this appears related to this bug  [https://bugs.launchpad.net/ubuntu/+source/qemu-kvm-spice/+bug/962376](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm-spice/+bug/962376)

Error also present in virt-manager which gnome-boxes shares a large amount with.

---

### Post by Spr34d on 2012-10-21
Well I got this working by doing the following

First made sure libvirt daemon is running
```
libvirtd -d
``` (use your favourite method to get this done at boot otherwise you will need to do it manually every reboot)

Then I followed #7 on this [virt-manager bug]("https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/975165") 

```
sudo apt-get install qemu-kvm-spice
cd /usr/bin/
sudo rm kvm
sudo ln -s qemu-system-x86_64-spice kvm
```
note:command 1 should be redundant, not sure if the symbolic link creation in command 4 did any good but I did it.

There were a couple of new errors but re?/installing kvm resolved them
```
sudo apt-get install kvm
```


All good to go.  I perceive it as a bit slower than a virtualbox guest with the same hardware allowances, but nice to have the option.

---

