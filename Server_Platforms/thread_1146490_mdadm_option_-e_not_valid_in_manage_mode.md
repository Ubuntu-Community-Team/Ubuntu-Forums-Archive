---
title: "mdadm: option -e not valid in manage mode"
date: 2009-05-02
forum: Server Platforms
---

### Post by dstien on 2009-05-02
It very well may be something simple, but I can't remove a device from my RAID1 (mirror).  When I try the following remove command, I get the following message:

```
cnadmin@Servidor:~$ sudo mdadm /dev/md0 -remove /dev/sdb1
sudo: unable to resolve host Servidor
mdadm: option -e not valid in manage mode
cnadmin@Servidor:~$ 

```

I guess I'm just not sure what manage mode is, and what I've done to initiate it, or how to remove the -e option.  I followed instructions [here]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") to set it up a while back.  I'm just now trying to start a disk rotation--each week swapping one of the 2 drives for a spare (that is kept in a safe) as a backup.

---

### Post by fjgaude on 2009-05-04
Stop the array, fault the drive, then remove it.

```
sudo mdadm /dev/md0 --fault --remove /dev/sdb1
```

Can't remember if you have to use two commands to do this.

---

### Post by dstien on 2009-05-05
> **fjgaude said:**
> Stop the array, fault the drive, then remove it.

```
sudo mdadm /dev/md0 --fault --remove /dev/sdb1
```

Can't remember if you have to use two commands to do this.

Okay, trying to understand the instructions and what they mean.  If I stop the array...then that won't cause any problems for the currently running system?  Which part of the code stops the array (md0)?  If the drive is marked as faulted, can I reattach it later?  And to reattach another device, would I use the command as follows?

```
sudo mdadm /dev/md0 --add /dev/sdb1
```

---

### Post by fjgaude on 2009-05-06
I can't say why that -e is coming up. But here's the commands to remove a drive from an array:

```
sudo mdadm /dev/md0 --fault /dev/sdb1
sudo mdadm /dev/md0 --remove /dev/sdb
```1

Now you should be able to physically remove the drive.

Lots of things to learn about software raid. Here's some links plus the man pages:

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)
[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks) 

```
man mdadm
```

Good luck!

---

### Post by m2acis on 2009-09-11
I think the complaint about "-e" option comes from the fact that you used "-remove" and not "--remove", mdadm interpreted it as "-r -e- -m -o -v -e". I'm not shure but I think this is related to GNU/Linux/whatever standarts for short and long command line options.

---

### Post by tgrimley on 2009-09-11
> **m2acis said:**
> I think the complaint about "-e" option comes from the fact that you used "-remove" and not "--remove", mdadm interpreted it as "-r -e- -m -o -v -e". I'm not shure but I think this is related to GNU/Linux/whatever standarts for short and long command line options.

Was going to say this.  99% sure this is why..

---

