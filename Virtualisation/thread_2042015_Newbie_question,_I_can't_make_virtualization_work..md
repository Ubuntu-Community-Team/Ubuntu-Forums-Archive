---
title: "Newbie question, I can't make virtualization work."
date: 2012-08-13
forum: Virtualisation
---

### Post by Jeska on 2012-08-13
Hi there, I'm a newbie to linux, and I'm trying to figure out a way to get vectorworks(CAD software) to run on my new ubuntu 12.04 installation. 

I had limited success getting it to run on wine, and then I went to a LUG meeting, where the helpful people there pointed out that my computer is capable of hardware virtualization. 

We set it all up, and got these messages:


Unable to connect to libvirt:

Failed to connect socket to '/var/run/libvirt/libvirt-sock': Permission denied

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - You are member of the 'libvirtd' group

The wiz who was helping me did some magical stuff to make these messages go away, and we proceeded to install another version of 12.04, just to see if we could make it work.  

As soon as I got home, I rebooted to play with my virtual version of 12.04 and see about installing XP 64bit.  

Sadly, the messages came back again, and there's nothing showing up as installed in my virtual machine manager. 

Any advice? Aside from waiting till the next meeting : )

Oh, this is me: 
HP Pavilion Dv7-6199us
Key Features and Benefits:
Intel Core i7-2670QM processor
2.20GHz
8GB DDR3 SDRAM system memory (expandable to 16GB)
1TB SATA hard drive
Blu-ray player and SuperMulti DVD Burner
802.11b/g/n Wireless LAN
Radeon HD 6770M switchable graphics with 2048MB GDDR5

Thanks!

---

### Post by Aubergines on 2012-08-14
check that you're in the libvirtd group, in a terminal type:

```
getent group libvirtd
```

you should see your login name, if not add yourself with

```
sudo usermod -a -G libvirtd <login_name>
```

One thing though, I've not kept up to date with KVM virtualisation but surely something like vmware player or even virtualbox would be better since I'd guess you'd want guest 3d acceleration for CAD software. I've never used any CAD software myself but I always thought it was pretty hardware intensive so running it under virtualisation might be slow.

---

### Post by slooksterpsv on 2012-08-14
Personally, I'd say you may want to look into VMWare, it seems to have a bit of Graphical support (if your system supports IOMMU). Otherwise, I personally enjoy VirtualBox (granted I dislike Oracle, but that's a different story).

---

### Post by Bucky Ball on 2012-08-14
Virtualbox easy. Simple GUI.

As mentioned, as is CAD you want to devote plenty of RAM to the guest (XP). What happens, in Virtualbox anyway as I know nothing of KVM, is that the physical RAM is shared between guest and host: 2Gb for guest, 2Gb for host, if you had 4Gb altogether, or however you want to allocate the RAM you have.

---

