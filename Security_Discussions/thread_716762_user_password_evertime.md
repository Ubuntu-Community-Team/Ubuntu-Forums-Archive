---
title: "user password evertime"
date: 2008-03-06
forum: Security Discussions
---

### Post by shamalawy on 2008-03-06
i have ubuntu and vista dual boot, i mainly use ubuntu but i'm obligated to use vista for work, anyway.. i have two NTFS drives, one which contains windows and the other is drive D: wich contains everything.. everytime i log into  ubuntu i, have to enter the user password to be able to access the driver and i'm kinda guy which gets bored easily.. how can i JUST ACCESS IT without needing to type the password.. oh, BTW.. the same thing is for the network icon, everytime i try to change a network manually it does the same thing... sorry for you time, i just wanted everything to be clear. thanks in advance

GO EAST GO WEST... UBUNTU IS THE BEST!

---

### Post by Rytron on 2008-03-06
as far as I know this is a feature if Ubuntu - for your own safety.

---

### Post by Lacasito on 2008-03-06
well, maybe you could change the options in fstab, for instance:

/dev/sdb1  /media/PORTATIL	vfat	auto,users,rw,umask=0000,iocharset=utf8	0	0

As you can see in this line of my fstab, I've got the options "users" and "rw" so that every user can mount the partition and read and write in it.

---

### Post by shamalawy on 2008-03-06
wow, although i have know idea what on earth  FSTAB is, but i'm happy with the quick response.. what commands exactly do i need to type if you could number the steps i would be greatfull

1. do this
2. do that

it makes it easy for my tiny little brain of mine to understand ;)

---

### Post by Biochem on 2008-03-06
FSTAB ( located /etc/fstab) is the file where the information necessary to mount your filesystem are located. 

The easiest way to do what you want is installing ntfs-config

sudo apt-get install ntfs-3g ntfs-config

It's a gui and should find it in application => system tools. then folloow the instruction they are really simple.

the other way is to edit it manually

gksu gedit /etc/fstab

then add the line

/dev/sda1 /mnt/Windows ntfs-3g defaults,umask=007 0 1

where /dev/sda1 is the device/partition (found with sudo fdisk -l)
and /mnt/Windows is the mount point (ie the folder where your partion is going to be mounted) 

For more information on available option: man fstab

---

### Post by shamalawy on 2008-03-07
thank you so much Biochem.. the apt-get command did it all..

---

