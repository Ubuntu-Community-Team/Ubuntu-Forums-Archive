---
title: "How to resize a partition / , others Gparted method."
date: 2015-11-27
forum: Tutorials
---

### Post by Portaro on 2015-11-27
[B]Atention:
[/B]&#8594;the following steps dont work in **LVM** partition tables.
&#8594;fdisk command dont work with devices with more of 2TB.
&#8594;all steps is done on a system that have a single / ; /home and a part of disk that is used like a device inside of disk (the first partition out of extended partition at left)
&#8594;is a modal case , an example to try explain the work when your system needs space on the / (the most important partition of GNU/Linux because the three  of all start here.
Thanks to TheFU to **advice me about LVM and fdisk**.

Use the steps with visit a guides of partition tables , of gparted [http://gparted.org/faq.php](http://gparted.org/faq.php) ; parted [http://www.gnu.org/software/parted/#downloading](http://www.gnu.org/software/parted/#downloading) and [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)


Today and once more time I need to resize a partition in the case my / partition that have also /boot /var etc.

I remember that in this days I read a question about resize partions writed by an user, and I think that I can share how to partition with Gparted method because I need to do this for my mahcine today so is a hot content .

So start with the job -

First of all - Atention !!! If you need resize partition always remember to do a backup of data of content if your content is important to you because any resize requires a previous delete of a partition, and also remembers that any resize of a partition requires a free space to increase the target partition to left or right of disk /old deleted partitions .

In my case I use a Flavitu Linux ISO to do unetbootin boot usb and boot machine on a live session with it ,  this give to me the opportunity to resize / mnt/ and edit disk partition of the real disk of machine. Flavitu dont have installed , by default, the Gparted tool so I need to connect the live mode to internet and then update the repos and install gparted - sudo apt-get install gparted.

Now start the real steps:

First I open Gparted ->

[IMG]http://s25.postimg.org/rmw50xpvx/2015_11_27_100058_1280x1024_scrot.png[/IMG]


Delete the left partition (that in past is used like a usb to put files that I need to move of my /home when I need space) and I also delete Swap partition the first partition inside the extended partition [blue], so the partition target to resize is my /dev/sda that also is my / and this mean that when the job start the Grub config lost the correct initial sector of system boot (init) and also means that my swap UUID is also lost by system (so in the final steps we will see how to update grub and reconfigure the UUID of Swap.

In my case I'll do a Swap partition but in the recent times the community suggest that this is no longer need , to new machines , is only real effective if your machine have a poor amount of dedicated RAM.

The Guide to following to work with Gparted is - [http://gparted.org/faq.php](http://gparted.org/faq.php)
[http://gparted.org/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem](http://gparted.org/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem)  - for this tutorial take a special look on :

 "Fixing GRUB boot problem" 

When I delete all partitions at left I can resize my extended partition first  and then resize my /dev/sda5 to this new left space , at this step I only need to put atention to leave the Swap space to the swap partition tha is created on the final.

[IMG]http://s25.postimg.org/g1qk6ytsd/2015_11_27_102418_1280x1024_scrot.png[/IMG]




Also You read in the first lines of post , I have a partition out of extended partition and I will maintain some of the space to have a part of disk to use like a USB to temporal moving files of /home if I have problems with free space on my /home, so all I need is create a partition(ext4) to this space that I dont need to use on /dev/sda5 or other.

[IMG]http://s25.postimg.org/5u80uk7kd/2015_11_27_104001_1280x1024_scrot.png[/IMG]

Ok All partitions is created and I have 20 GB more on my/dev/sda to use .

Now take a look with fdisk

> $ sudo fdisk -l 



Remember ! 

I lost my initial sector of /dev/sda5
I lost my swap UUID

And I need to solve this so ....

I'll do the steps of Gparted Guide :

> $ sudo mkdir /tmp/portaro/ (in the official guide is sudo mkdir /tmp/mydir -> repalce /mydir with portaro in my case this is optional you can do the name that you want to the path)


Step = mount
> $sudo mount /dev/sda5 /tmp/portaro

Step = prepare to work with a root environment 
> $sudo mount --bind /dev /tmp/portaro/dev
$sudo mount --bind /proc /tmp/portaro/proc
$sudo mount --bind /sys /tmp/portaro/sys

Step=chroot active 
> $sudo chroot /tmp/portaro


As you probably know the update to a Grub is make with a pshisical target the entire /partition for example my / init is on /dev/sda5 however my /dev/sda5 is on /dev/sda and this is the target that I need send  to the Grub config and  can update the Grub without problems ->

> root@flavitu:/# grub-install /dev/sda

Ok at this point we need all partitions work  , We can finally reboot the machine to boot to the machine disk and system with the new partitions and with a good grub config!

**When we boot to system machine we can take a look on our new swap** (remember I lost my swap because I delete and resize this partition also)

First of all - commands ->
 
> $sudo swapon -a 
$sudo swapon -s

If appear an erro like -> swapon: cannot find the device for... ; we need to find UUID of swap and put this on our /etc/fstab -> 

[IMG]http://s25.postimg.org/8texhoh1r/2015_11_27_114747_1280x1024_scrot.png[/IMG]

Take a look on our new UUID Swap with the command **blkid**

> $ sudo blkid

[IMG]http://s25.postimg.org/eyb18qyj3/2015_11_27_115614_1280x1024_scrot.png[/IMG]

And **put this on the UUID for swap on the fstab config file **->

[IMG]http://s25.postimg.org/e7ib2yw5r/2015_11_27_115139_1280x1024_scrot.png[/IMG]

Now remember -> 

> $sudo swapon -a 
$sudo swapon -s

Nice!!! 

All is now well configured ...

And you have more space on the target partition , in my case I need to do a resize of my / partition to install more games on  my Ubuntu , **and dont have problems with space in future updates of programs or distro because I only have 0 bytes yesterday** at night and now I have more 20 GB, I think this can solve my problem :D


I hope this can help other users and turn easy the act of  resize partitions, all credits go for Gparted page and doucmentation!

Thanks.:D

---

### Post by TheFu on 2015-11-27
These instructions won't work for LVM or encrypted configurations. LVM can resize an LV on a running system in some situations, but not all.
A warning about those things really is needed at the top.

Also, *fdisk* may not work properly on GPT disks or disks over 2TB, so '**parted**' or **gparted** should be used instead.

As usual, there are many different ways to configure any Unix/Linux system. People tend to use the defaults, but our systems may not reflect what most users have.  This is all part of gaining greater knowledge. 

Flexibility leads to complexity and capability.

---

### Post by Portaro on 2015-11-27
Thanks for the advice, its important for me and for users.

Depend of each config of partitions on the pcs of users the way followed in the example is a case with   Disk space out of  system scpae + extended and inside / /home .

My intention is help that people lost some steps with different guides because this I focus the steps of GRUB and /Swap, but your advice is a very good point any info is welcome to help users I think.

Thanks for your contribution with LVM and fdisk (I dont have any idea about that fdisk dont work well with 2TB Disks)

:popcorn: You are always welcome , thanks.

---

