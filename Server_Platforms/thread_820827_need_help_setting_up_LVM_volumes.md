---
title: "need help setting up LVM volumes"
date: 2008-06-06
forum: Server Platforms
---

### Post by phrozendice on 2008-06-06
Hello.

I am new to Ubuntu and LVM, I am having trouble trying to setup 2 LVM volumes with Ubuntu 7.0.4 Server 

During installation I created a small partition for the OS and swap (about 80GB) and then I created 2 Phisical Volumes for LVM of 500GB each.

After installation was completed I logged in to the server and I do df -h and I cant see the LVM volumes. Granted they are not mounted or anything but i am lost on what to do from here.

Any help is appreciated on detailed information on how to create these volumes so that the system looks something like this.

 / < OS > 80GB
 /storage1 < LVM volume1 > 500GB
 /storage2 < LVM volume2 > 500GB

i am familiar with fdisk but detailed information is greatly appreciated. Sorry for my bad english.

Thanks
JIm

---

### Post by RealPSL on 2008-06-06
Can you provide the output from the command ```
sudo vgdisplay -v
```. This will list all the logical volumes and the volume groups they belong to. Once we have this information we should be able to get your logical volumes mounted and usable.

---

### Post by phrozendice on 2008-06-07
root@lea1:~# vgdisplay -v
-bash: vgdisplay: command not found

So I guess i am missing this tool, I apologize but I am still very new to Ubuntu, I tried searching for this tool with apt-cache search but no luck

Is this tool part of another package? if so, can you tell me which one is it so i can install?

Thank you in advance!
Jim

---

### Post by phrozendice on 2008-06-07
Please disregard my previous post, i followed this procedure including the creation of the link:

[http://ubuntuforums.org/archive/index.php/t-462954.html](http://ubuntuforums.org/archive/index.php/t-462954.html)

Now, this is what i get:

vgdisplay -v
    Creating directory "/var/lock/lvm"
    Finding all volume groups
  No volume groups found

Could this be because i installed lvm2 instead of lvm? 

What would be the next step?

Thanks!
Jim

---

### Post by quelx on 2008-06-07
> root@lea1:~# vgdisplay -v
-bash: vgdisplay: command not found
Do you have lvm installed? ```
sudo apt-get install lvm2
```
Granted parts of this tutorial is for a gui, if you know fdisk (or have already created the proper partitions it should get you started.

[http://ubuntuforums.org/showthread.php?t=555638](http://ubuntuforums.org/showthread.php?t=555638)

---

### Post by koenn on 2008-06-07
> **phrozendice said:**
> 
Any help is appreciated on detailed information on how to create these volumes so that the system looks something like this.

 / < OS > 80GB
 /storage1 < LVM volume1 > 500GB
 /storage2 < LVM volume2 > 500GB



iirc, lvm physical volumes represent the actual disks or partitions you'll be using, so I assume you have 2 500GB disks. 

In that case, the setup you have in mind doesn't much make sense, you might as well just mount the disks.

What would make sense is to join both PV's in 1 Logical Group, where you can then create a logical volume (LV) of 1000 GB and mount that to /storage 
[ or split the LG in severl LV's without having to care where 1 disk ends and the other one begins]


Have a look at this :
[http://users.telenet.be/mydotcom/howto/linux/disks2.htm](http://users.telenet.be/mydotcom/howto/linux/disks2.htm)

---

