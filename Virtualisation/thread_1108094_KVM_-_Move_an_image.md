---
title: "KVM - Move an image"
date: 2009-03-27
forum: Virtualisation
---

### Post by Rocket2DMn on 2009-03-27
Hey all, quick question for you.

I started fiddling around with KVM last night and have been making some good progress.  However, the first machine I successfully created ended up having its image in my home directory, and I want it to be in a subfolder.  I can move the image manually and boot it up using the kvm command, but virt-manager doesn't recognize the move.  I guess the change needs to be registered within the URI qemu:///system ?

Is there a configuration file somewhere I need to edit, or a command I need to run so that the system knows that the disk image has moved?  Thanks!

---

### Post by Rocket2DMn on 2009-03-28
Ok, so I finally figured this out despite not finding any documentation on it.  Here is how in case somebody else needs this.

The machine is called "hardy", so I had to change the xml file in "/etc/libvirt/qemu/":
```
gksudo gedit /etc/libvirt/qemu/hardy.xml
```

I changed the line
```
      <source file='/home/connor/hardy.qcow2'/>
```
to
```
      <source file='/home/connor/ubuntu-kvm/hardy.qcow2'/>
```
so that libvirt looks in the ubuntu-kvm subfolder of my home directory for the file.

Then I moved the image itself:
```
mv ~/hardy.qcow2 ~/ubuntu-kvm/
```
Then restarted libvirt
```
sudo /etc/init.d/libvirt-bin restart
```

I was then able to access the hardy VM from virt-manager after moving the disk image.

Edit: some notes here - [https://help.ubuntu.com/community/KVM/Managing](https://help.ubuntu.com/community/KVM/Managing) - under "Define, undefine, start, shutdown, destroy VMs".  It looks like you should be able to run virsh and simply use the "define" option to have it re-read the xml.

---

### Post by Slezhuk on 2012-09-10
It works, thanks!
p.s virsh define /etc/libvirt/qemu/domain.conf works too- no need for rebooting entire libvirt.

---

