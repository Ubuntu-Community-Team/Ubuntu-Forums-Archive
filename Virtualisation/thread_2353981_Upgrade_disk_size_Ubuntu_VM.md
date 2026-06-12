---
title: "Upgrade disk size Ubuntu VM"
date: 2017-02-27
forum: Virtualisation
---

### Post by jimmy2017 on 2017-02-27
Gents,

I would like to increase the disk size of a Ubuntu VM device. 
In VM Edit Settings it's increased to 40GB, and stays the value accepted.
But when I see inside the OS I get other results, see photo.


Does anyone know what's going wrong why the 40GB doesn't get deployed on the OS itself?

---

### Post by TheFu on 2017-02-27
Welcome to the forums.

What is an "Ubuntu VM device?"  That is very vague.
Which hypervisor? 
Did you use vboxmanage or qemu-img to increase the size?
Is the storage sparce or fully preallocated or passed thru as a LV?

Can't really help without details.

Please don't post images when text copy/paste would work better.  Be kind to people with limited bandwidth.

---

### Post by ajgreeny on 2017-02-27
I assume you now have a partition in your virtual disk that does not totally fill the disk, which is quite normal after increasing the Virtual Machine size, as that VM is just a disk, not the partition.

You will now need to insert, for example, a live Lubuntu or Gparted iso as an IDE CDrom drive using the VBox manager window.
[LIST=1]
[*]Go to your VBoxmanager window, ie the window with the list of your VMs in left hand pane, and select your Ubuntu VM.
[*]Go to Settings ->Storage and click on the small CD icon by **Controller : IDE**
[*]In the dialogue that pops up go to **Choose disk** and navigate to your live iso file of Lubuntu/Gparted/Other and add that iso file as a new CD disk.
[*]Boot your Ubuntu VM but immediately hit F12 to choose the live CD as boot device, and the system should boot to the live desktop from which you can open gparted to enlarge the Ubuntu partition to fill the available space.
[*]Shutdown the live OS now running, and reverse the addition of that live iso CD if you wish.
[*]Boot to Ubuntu VM and you should now see it has filled the available disk space.
[/LIST]
Good luck! It has worked for me in the past with no problems.

---

