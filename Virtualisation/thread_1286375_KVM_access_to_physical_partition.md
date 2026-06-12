---
title: "KVM access to physical partition"
date: 2009-10-08
forum: Virtualisation
---

### Post by marzvix on 2009-10-08
Anybody know how to access physical partition (and boot from it) on kvm.

My ubuntu is a new Karmic Koala.
Intended partion /dev/sda3 

My kvm is working fine with a raw image and a I can read my usb, cdrom and boot from it. Sound, mouse, video, network is workin fine with windows and another ubuntu.

But I cannot configure my /dev/sda3 to be accessed directly

I've tried many combination like 

kvm -disk file=file,scsi 

and edited an qcow2 like this way:

scsi0: /dev/sda

Nothing worked.

Thanks for any direction

---

### Post by bodhi.zazen on 2009-10-09
How are you running KVM ?

virt-manager , kvm, or virsh ?

With KVM , assuming you are wanting access to /dev/sda3 , and assuming your user is in the kvm group ...

```
sudo chown root.kvm /dev/sda3
sudo chmod 770 /dev/sda3
```

Then start kvm :

```
kvm -hda /dev/sda3
```

plus any additional options you want.

---

### Post by marzvix on 2009-10-09
Now it is working.

I've tried /dev/sda3 but it seems not fine so I've replaced with /dev/sda and now it's going on.

My comand line is

kvm -localtime -cpu coreduo -daemonize -soundhw ac97 -m 1024 -usb -usbdevice "$Pen8G" -hda /dev/sda

Abou my virtualization engine... I really don't know wich is running. (srry)

I perceived a problem: the system - winxp - installed in that partition is terribly slow compared with another winxp installed in a raw file. Same version, same sp3 ... I cannont figure out why. Do you ?

Another point observed: my sound works in debian better than in ubuntu. Weird but it is true.

I 've installed a nvdia driver in ubuntu and after tryied start that partition with grub (yes, in the same /dev/sda where my system is installed), my ubuntu was damaged. 

Anyway, I will keep trying to have three partitions working with any booted system which is my real intent.

Thanks a lot for your reply.

---

