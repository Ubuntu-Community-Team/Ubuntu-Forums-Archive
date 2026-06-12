---
title: "conversion"
date: 2011-03-27
forum: Virtualisation
---

### Post by niraj8554 on 2011-03-27
how to convert .vdi to hard disk partion

---

### Post by lmarmisa on 2011-03-27
I recommend to use Clonezilla Live:

[http://clonezilla.org/](http://clonezilla.org/)

Download the [ISO file of Clonezilla]("http://clonezilla.org/downloads/stable/iso-zip-files.php"). 

Select the bridged mode in the network interface of your virtual machine. Then start the virtual machine whose vdi file you want to backup from the Clonezilla iso file (virtual CD).

Make a full backup of your virtual disk (or partition) selecting the samba protocol for storing the backup files in a remote machine.

Finally restore that backup (using Clonezilla) in the destination hard drive of a physical computer.

---

