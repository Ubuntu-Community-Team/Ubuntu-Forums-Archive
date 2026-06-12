---
title: "Accessing internal hard drives in VirtualBox Ubuntu 9.10"
date: 2009-11-19
forum: Virtualisation
---

### Post by jw8212 on 2009-11-19
Okay, so I installed Sun VirtualBox in Vista and installed Ubuntu 9.10 inside VirtualBox. It runs decent (though I could use something bigger than an 800x600 screen res, but I digress), but there is one major problem: I can't access my internal hard drives.

My computer came with a pre-partitioned C and D drive with Vista (naturally) installed on the C drive. I have previously installed 9.04 using wubi onto my D drive and when I boot into it, I can't access my D drive, but my C drive works just like my external hard drive. However, when I go into the VirtualBox, neither my C nor my D drives show. If there is any way I can find them or mount them or access either of them, I would be extremely grateful for the advice. I don't know too much about the VirtualBox, so I may have overlooked an option or something, but I'm really not sure.

---

### Post by Markkreuzz on 2009-11-20
During the Virtual Drive creation you should have specified the whole disk for creating a raw HD image like so 

```
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk -rawdisk /dev/sda
```

where /dev/sda is disk you want access to. "-partitions" option specifies the partitions you want access to as well.

You can also do something like this:

```
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk -rawdisk /dev/sda -partitions 1,5 
```

where 1,5 specifies partitions 1 and 5 on your physical disk.

to know which partition # is which do this

```
VBoxManage internalcommands listpartitions -rawdisk /dev/sda
```

Last option is to create images from each of the partitions and add them each to the Virtual Media Manager then add it your Virtual Machine...

Hope that helps.


hope that helps.

---

