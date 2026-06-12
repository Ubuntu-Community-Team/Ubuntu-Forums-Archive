---
title: "Usb pendrive and kvm"
date: 2008-07-28
forum: Virtualisation
---

### Post by cyrocr on 2008-07-28
Hello all,

A just installed kvm and started a windows xp guest onto it. Everything works fine except usb devices. How can i use an usb pendrive on the virtual machine? I have created the virtual machine with virt-manager and had no chance to configure usb devices. When i plug the pendrive on hardy it is automatically loaded and i can see the files on linux, but nothing happens on the kvm virtual machine. Reading thru the internet i have commented out the /proc/bus/usb section on the /etc/init.d/mountdevsubfs.sh file, but still nothing happens on the virtual machine when i plug the usb stick.

Thanks very much for any help.

---

### Post by DagMan on 2008-07-29
I find a good workaround when it just a storage device, is to make a shared folder from the virtual machine to somewhere in your home folder, and to make a symlink from the shared folder to the usb mount point.  I've had that work in virtualbox.  I don't know if it will help in your situation though.

---

