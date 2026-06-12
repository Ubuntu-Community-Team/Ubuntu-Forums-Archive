---
title: "Diablo 2 on Linux 11.04"
date: 2011-05-24
forum: Wine
---

### Post by ShaftxCam on 2011-05-24
Ok, I'm completely lost..

I'm new to using Linux and can't seem to get wine to install Diablo 2 at all.. I've tried using PlayOnLinux, but all it does is tell me that the game is installed and I can't access it for some reason.. Idk?

I've made a drive in the winecfg labeled D: and set it for the cdrom.. (I'm really not too sure what to do lol sorry)
But I've been up and down these forums and can't seem to find answers to my specific problem :(

Any help would be great, thanks :D

---

### Post by Pierrick584 on 2011-05-24
Uh, well for my part, every blizzard game are always arleady installed and i only execute them, always out of the box, realy, if i understand your problem is the cd detection? i'd recommand install it in a virtualbox, patch it (in 1.13 you dont need cd anymore, so that'll def help you) and then try to run it on linux, and by the way... i'd strongly recommand to only run it in window mode "~/Diablo\ II.exe -w" cause resolution switching of game on linux bug often with these old game

---

### Post by ShaftxCam on 2011-05-25
> **Pierrick584 said:**
> Uh, well for my part, every blizzard game are always arleady installed and i only execute them, always out of the box, realy, if i understand your problem is the cd detection? i'd recommand install it in a virtualbox, patch it (in 1.13 you dont need cd anymore, so that'll def help you) and then try to run it on linux, and by the way... i'd strongly recommand to only run it in window mode "~/Diablo\ II.exe -w" cause resolution switching of game on linux bug often with these old game

Well, when I put the cd in to install it, the computer recognizes it, but when I try to run it with wine, it says it's non-executable. I go in and give it permissions to run, and still the same error messages. 
How do I install in a virtualbox? Sorry I really do like Linux, it's just, I don't know the ins and outs of it lol..

---

### Post by P-I H on 2011-05-26
I installed Diablo 2 and Diablo LOD from CD:s, both on a computer with Nvidia graphics and a computer with Radeon graphics. Both games worked with Nvidia, but only Diablo LOD with Radeon.

To enable the installation program to get the correct CD-labels I did the following:
Made a directory called /media/cdrw.
Open a terminal and make the command
**sudo mkdir /media/cdrw**
Made these two commands in the terminal to make a change in fstab to connect the directory to the cd-drive
**gksudo gedit /etc/fstab**
and added this line
**/dev/sr0 /media/cdrw udf,iso9660 users,noauto,rw 0 0**
Started Wine config and changed/added the path in D: to **/media/cdrw**
and used advanced to set D: to CD-ROM.

After this I logged out and logged in. To enable use of the changed fstab.

After these preparations I opened a terminal and made the commands cd .wine and  wine "d:\setup.exe" to start the installation.

Hope this works for you.

---

### Post by ShaftxCam on 2011-05-28
> **P-I H said:**
> I installed Diablo 2 and Diablo LOD from CD:s, both on a computer with Nvidia graphics and a computer with Radeon graphics. Both games worked with Nvidia, but only Diablo LOD with Radeon.

To enable the installation program to get the correct CD-labels I did the following:
Made a directory called /media/cdrw.
Open a terminal and make the command
**sudo mkdir /media/cdrw**
Made these two commands in the terminal to make a change in fstab to connect the directory to the cd-drive
**gksudo gedit /etc/fstab**
and added this line
**/dev/sr0 /media/cdrw udf,iso9660 users,noauto,rw 0 0**
Started Wine config and changed/added the path in D: to **/media/cdrw**
and used advanced to set D: to CD-ROM.

After this I logged out and logged in. To enable use of the changed fstab.

After these preparations I opened a terminal and made the commands cd .wine and  wine "d:\setup.exe" to start the installation.

Hope this works for you.

This is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ace54712-a249-4b55-bfa8-d3a9d9dba164 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e22355e0-5980-4f89-8bc1-08cfb1b1f645 none            swap    sw              0       0

Where do I put the **/dev/sr0 /media/cdrw udf,iso9660 users,noauto,rw 0 0 ** ?

---

### Post by P-I H on 2011-05-28
I just placed it as the last row.


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6e6f6eaf-d0f9-41ae-ad93-631ebc8a4054 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1f2779ad-81c8-43ac-b8db-72fe311419d1 none            swap    sw              0       0
192.168.0.150:/srv/Media /home/p-i/NASMedia nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.0.150:/srv/Anvandare/p-i/NASDokument /home/p-i/NASDokument nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.0.150:/srv/Anvandare/p-i/NASMail /home/p-i/NASMail nfs rsize=8192,wsize=8192,timeo=14,intr
/dev/sr0 /media/cdrw udf,iso9660 users,noauto,rw 0 0

---

### Post by ShaftxCam on 2011-05-29
Thanks P-I H :D I got it to start installing xD so for now this problem is solved :D :D :D

---

