---
title: "Issues with expanding partition in VM"
date: 2017-04-01
forum: Virtualisation
---

### Post by rpruett on 2017-04-01
So i have Ubuntu 16.04 running in a VM on my Microsoft Server 2016 Box. Originally, I set the VM to be 20gb and started experimenting. Now that I have the server up and running how I want it, I'm almost out of space and wanted to expand it. I expanded it to 40gb in HyperV, but didn't see the difference so I expanded it to 200gb. I now realize that not only do I have to expand it in HyperV, but I need to extend the partitions in Ubuntu as well. I've downloaded Gparted but had no luck, so then i tried a gparted live iso and didn't have any luck there.

I've looked through a lot of forums and either the scenarios aren't the same as what I'm seeing or the solution didn't seem to help.

Thoughts?:confused:

---

### Post by howefield on 2017-04-01
Thread moved to the  "*Virtualisation*" forum for a better fit.

---

### Post by ajgreeny on 2017-04-01
You can not simply install gparted into your virtual Ubuntu as the partitions have to be unmounted in order to work on them.

I do not know HyperV, but in VirtualBox, where I had the same problem as you, I needed to insert a live gparted iso (actually I used a live Lubuntu as I already had it) as an IDE CD disk to the Virtual Machine of the Windows OS that I needed to be larger.

I then booted that VM and pressed F12 which is the VBox key for the menu for the device to boot, and chose the live Lubuntu.  Once booted I could open gparted and use it to enlarge the Windows partition to the full size of the virtual disk.  

I note, however, that you have used LVM partitioning for your Ubuntu which I do not use nor know much about, but I do not think you can edit LVM partitions with gparted.
See [http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume) which may help you with this problem.
Good luck!

---

### Post by rpruett on 2017-04-01
I used a live iso for Ubuntu and then used gparted to "deactivate" the partition and then resized it. Looks like everything worked the same as it would even if it wasn't a VM so that's good to know, i'm just not sure why the live gparted ISO wasn't working? Oh well, this is solved.

---

### Post by Paddy Landau on 2017-04-03
It's good that you managed to solve the problem. GParted doesn't work well with LVM, which might explain why the GParted ISO didn't work.

---

