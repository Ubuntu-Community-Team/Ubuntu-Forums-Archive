---
title: "server 10.04 setup multiple drives"
date: 2011-02-21
forum: Server Platforms
---

### Post by mpratt on 2011-02-21
I had a box running ubuntu server, and I switched to fedora, try something different. so far I am not impressed and am thinking of coming back to ubuntu server. this is what I need to be able to do with it.
1. I have 3 drives 80GB, 120 GB and 40GB, I need to be able to create the filesystem fo that I can put the OS on the 80GB, and create a virtualmachine with VBox that will have at least 80GB capacity. plus just some other random installs. I do not want to fill up one drive with all this information, is there a way t0 set up in the server install, the ability to use all drives as 1, or if not the best alternative. I do not want to run out of space because I didn't realize that one hard drive was full and the other could have been used. I am a newbie, so if I need to do some manual partitioning I would need some instruction on how to do it without creating a unusable machine.
 
Thanks for the help!

---

### Post by YesWeCan on 2011-02-21
Hi there. The good and bad about linux is there are lots of ways to do the same thing, but it takes a while to figure out which is best.

An experienced user would probably merge all three drives during the installation using the alternative install CD, either by making a linear RAID or by making an LVM volume group. You could figure this out with enough will power.

But I am inclined, as you are a newbie, to suggest taking it in smaller steps. Just for example, you could:

1) Do a normal Ubuntu install on the 80GB disk, erasing and using the whole disk. Afterwards, format the other two disks and, using LVM, merge them into one physical volume. So you would have an 80GB disk for the OS and home and general stuff, and a 160GB disk for VirtualBox files.

2) Do a manual install but a simple one, making a 20GB partition on the 80GB disk for Ubuntu. Get it all working and afterwards use LVM to merge the remaining 60GB+120GB+40GB to make a 220GB volume. Then mount it as your home directory.

It really depends whether you want to get it basically working or whether you want to take the time to do something fancy. Decide what you want to do and I'm sure you'll get plenty of help in this forum.

---

### Post by rubylaser on 2011-02-22
These are good ideas.  One caveat with your final plan of merging all of the disks into one Logical Volume, is that in essence, you'll end up with a linear RAID.  Meaning, if you lose one disk, all of your data is hosed.  You'd obviously want to have a good backup strategy to protect yourself from this possibility.

---

### Post by mciverza on 2011-02-22
> **rubylaser said:**
> These are good ideas.  One caveat with your final plan of merging all of the disks into one Logical Volume, is that in essence, you'll end up with a linear RAID.  Meaning, if you lose one disk, all of your data is hosed.  You'd obviously want to have a good backup strategy to protect yourself from this possibility.

+1 
When talking servers. Always implement backups. Always. (Test that your backups actually work, ie you can extract their contents, otherwise your backup is useless.)

---

### Post by mpratt on 2011-02-26
> **YesWeCan said:**
> Hi there. The good and bad about linux is there are lots of ways to do the same thing, but it takes a while to figure out which is best.
 
An experienced user would probably merge all three drives during the installation using the alternative install CD, either by making a linear RAID or by making an LVM volume group. You could figure this out with enough will power.
 
But I am inclined, as you are a newbie, to suggest taking it in smaller steps. Just for example, you could:
 
1) Do a normal Ubuntu install on the 80GB disk, erasing and using the whole disk. Afterwards, format the other two disks and, using LVM, merge them into one physical volume. So you would have an 80GB disk for the OS and home and general stuff, and a 160GB disk for VirtualBox files.
 
2) Do a manual install but a simple one, making a 20GB partition on the 80GB disk for Ubuntu. Get it all working and afterwards use LVM to merge the remaining 60GB+120GB+40GB to make a 220GB volume. Then mount it as your home directory.
 
It really depends whether you want to get it basically working or whether you want to take the time to do something fancy. Decide what you want to do and I'm sure you'll get plenty of help in this forum.
 
 
I would like to set it up like you mentioned in your first suggestion, with the other 2 hard drives as storage, now I have already formatted the 80 GB drive to use lvm, is that going to cause a problem.If it does then thats not a big deal, just installed the system tonight and havent used it yet, can re-do it if nessisary. and how do I go about mering the other 2 hard drives into that 160GB lvm you mentioned. Like I mentioned before, I am completly new to this, I keep reading about using fdisk, but I don't know what to set up or how, and I don't want to mess up my system.
 
thanks

---

### Post by YesWeCan on 2011-02-27
No problem. In the next description the term "volume" means the same thing as "partition".
The general idea is that you have to create a "volume group" and add physical disks to it. Then add "logical volumes" to the group and format them and mount them in your file-system. It is sort of bureaucratic  but not too hard.
BTW you will be using LVM2.
Full documentation is here: [http://www.tldp.org/HOWTO/LVM-HOWTO/index.html](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html)

To merge the 120GB and 40GB drives using LVM, you need to:

1) Go to the System/Administration/Disk Utility application and reformat and create one big partition on each disk of type ext4. So if your disks happen to be /dev/sdb and /dev/sdc you should end up with partitions /dev/sdb1 and /dev/sdc1.

2) In a terminal type 'sudo lvm'. This starts the lvm2 application and you should see a prompt "lvm>". Then create LVM physical volume labels on each disk (use the correct disk names for your system):
lvm> **pvcreate /dev/sdb1**
lvm> **pvcreate /dev/sdc1**
Now you make a logical volume that comprises the two physical volumes
lvm> **vgcreate vgname /dev/sdb1 /dev/sdc1** 
Use the "vgname" of your choice. Eg: data or vbox or whatever you like.

So now you will have a single volume group that spans both disks. A Volume group is sort of like a blank disk. So you have to add volumes to it and then format these volumes.

lvm> **lvcreate -L 20g -n lvname vgname**
Will make a 20GB logical volume named "lvname" inside the "vgname" volume group.

You could then add another.
Or you might want to make one big volume the same size as the volume group:
First find out how big the volume group is
lvm> **vgdisplay**
You will see lots of info. One is "Free PE" and this value should be used. Suppose Free PE = 330902
lvm> **lvcreate -l 330902 -n lvname vgname**
Small l this time. Then do vgdisplay again to see there is no Free PE.
When you are done exit from LVM
lvm> **exit**

Now you have one or more logical volumes. A LV can be referenced at /dev/vgname/lvname

Each LV has to be formatted and mounted.
**sudo mkfs.ext4 /dev/vgname/lvname**

Make a mount point, any name you like and any place. I like /media because in 10.04 this creates an icon on my desktop.
[B]sudo mkdir /media/bigDisk
sudo chmod 777 /media/bigDisk
sudo mount /dev/vgname/lvname /media/bigDisk
[/B]
It should now appear on your desktop and/or your Places menu.

To make the LV mount automatically at boot you have to add a directive to the /etc/fstab file. Make a backup first.
[B]sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab[/B]
Add a line at the end:
**/dev/vgname/lvname /media/bigDisk ext4 defaults 0 0**

That's it.

---

