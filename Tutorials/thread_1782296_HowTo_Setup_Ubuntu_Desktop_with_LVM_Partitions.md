---
title: "HowTo: Setup Ubuntu Desktop with LVM Partitions"
date: 2011-06-14
forum: Tutorials
---

### Post by ruffEdgz on 2011-06-14
The information in this thread has been moved to [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062142#post12062142](http://ubuntuforums.org/showthread.php?p=12062142#post12062142)

Thread closed.


This tutorial will help anyone who wishs to setup their desktop using logical volumes on a fresh install of Ubuntu Desktop only. You can use the Ubuntu Alternate image to complete this as well but you will need to set it up in a TUI (Text based-User-Interface).

**What is LVM?**
---
LVM stands for Logical Volume Manager (or Logical Volume Management). Instead of using all physical volumes for your system (hard to change, static), take one (or many) disk(s) and have that drive logically divided for expandability, better monitoring and all around better disk management on your computer. If you wish to learn more, please refer to the links below:

[http://www.redhat.com/magazine/009jul05/features/lvm2/](http://www.redhat.com/magazine/009jul05/features/lvm2/)
[http://sourceware.org/lvm2/](http://sourceware.org/lvm2/)
---

**Versions tested on:**
---
Ubuntu 10.04
Ubuntu 10.10
Ubuntu 11.04 
Ubuntu 11.10
Ubuntu 12.04 (current)
---

**Preparation:**
---
*Ubuntu Desktop ISO* ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download))
*CD* or *USB*
*A Computer*
*Hands*
---

**Table of Contents**
---
1. How to burn an ISO
2. Start up Ubuntu Live
3. Install lvm2
4. Setup hard drive partions
5. pvcreate, vgcreate, lvcreate, mkfs
6. Ubuntu Installation
7. Install lvm2 onto your new Ubuntu Install
---

**1. How to burn an ISO**
There are many guides on how to get your Ubuntu ISO going and it doesn't matter if you use a CD or a USB, either one will work.

CD Install - [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
USB Install - [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

**2. Start up Ubuntu Live**
Once you have your Ubuntu Live CD or USB ready, start up that computer/laptop, go into your BIOS (usually its F2 but this link can help if it doesn't work: [http://www.cyberwalker.com/article/28](http://www.cyberwalker.com/article/28)) and make sure your 'Boot Sequence' is set to CDROM or USB (if its supported). Save your BIOS setting and watch Ubuntu startup in front of your eyes. Later, you should see two options of "Try Ubuntu" and "Install Ubuntu" (11.04). Select "Try Ubuntu" and let it load into the Ubuntu 11.04.

**3. Install lvm2**
Now that Ubuntu is booted up, now we will need a terminal by selecting the following:

Applications >> Accessories >> Terminal

Once the terminal in front of you, run the following command:

```
sudo apt-get -y install lvm2
```

This command will install lvm2 onto your Live CD session only but will help with the rest of this tutorial.

**4. Setup hard drive partions**
Keep the terminal open as we will be creating partitions using the command fdisk. In the example below, I will be setting up my desktop using the /dev/sda patition (to find yours, do the command 'sudo fdisk -l' and make sure you know much your storage is on the machine so you can figure out what physical device you want to use):

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x568311d6.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): n 
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-5221, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-5221, default 5221): +1G

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (133-5221, default 133): 
Using default value 133
Last cylinder, +cylinders or +size{K,M,G} (133-5221, default 5221): 
Using default value 5221

Command (m for help): t
Partition number (1-4): 2
Hex code (type L to list codes): 8e

Changed system type of partition 2 to 8e (Linux LVM)

Command (m for help): p

Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x568311d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         132     1060258+  83  Linux
/dev/sda2             133        5221    40877392+  8e  Linux LVM

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

The reason for this setup is explained below:

_/dev/sda1_ -- This partition has been created for /boot of the installation. It always a good thing to make your /boot the first partion of any Linux system

_/dev/sda2_ -- This is the LVM physical parition that will be used to create the rest of the system before installation.

**NOTE**: In the following setup, I will be using a LVM swap partition instead of making it through fdisk. Having swap as a LVM partition might cause overhead. You can make a new partition before you make your LVM partition as a swap partition. Make sure you know how much you need since you will not be able to increase the swap size easily. The table id for swap is 82 (Linux swap / Solaris).

**5. pvcreate, vgcreate, lvcreate, mkfs**
This part will help setup your logical volumes for your desktop. In this example, there will be three different logical volumes using one volume group and one physical volume:

Create the physical volume:
```

sudo pvcreate /dev/sda2
                  ^
                  PV

```
This gives the LVM an understand of what physical volumes it has to offer for volume groups and logical volumes during your setup.

Create a group using our newly create physical volume:
```

sudo vgcreate sysvg /dev/sda2
                ^       ^
               name     PV

```
This part creates a new volume group which is tided to a physical volume. A physical disk can not be can not be used on multiple violume groups (unless you partition that disk before hand like we did above). The name of this volume group is 'sysvg' but you can name it whatever you wish.

Create the swap logical volume using the newly create sysvg group:
```

sudo lvcreate -L 1G -n lvswap sysvg
                ^        ^      ^
             size(GB)   name    VG

```
I need a swap for the system so 1GB will do in this case (you can change the size to whatever you want). The name can be whatever you want it to be but I like to keep a naming scheme when creating VG's and LV's. Then assign it to a VG group that you made from before and you will have your first LV done.

Create the root logical volume using the newly create sysvg group:
```

sudo lvcreate -L 20G -n lvroot sysvg
                ^        ^      ^
             size(GB)   name    VG

```
Again, like the swap but this will be used for my root file system. The size and name is up to you and make sure you point it to your VG that was created above.

Create the home logical volume using the newly create sysvg group:
```

sudo lvcreate -l 100%FREE -n lvhome sysvg
                ^            ^      ^
             extents(%)     name    VG

```
Without getting into a lot of details, this will create a logical volume called 'home' using 100% of whats left on my VG. The percentage and name is up to you and make sure you point it to your VG that was created above. You do not need to use the rest of your disk space on home or any of the above created. 

**NOTE - Please use any of the above commands if you want to make a seperate LV for tmp, var, etc...**

View the create logical volumes:
```
sudo lvdisplay
```
You don't need to do this but its always nice to see the work as a whole.

Display only your free space on your volume group:
```
sudo vgdisplay | grep -i free
```
This is just important if you didn't use the rest of the disk on a LV. This will show how much you have to expand current LV's or create new ones at a later date.

Build linux file systems for all newly created logical volumes:
```

sudo mkfs.ext4 /dev/mapper/sysvg-lvroot
sudo mkfs.ext4 /dev/mapper/sysvg-lvhome
sudo mkswap -f /dev/mapper/sysvg-lvswap

```
This will help the installation process know that each LV is selectable and usable as a partition point.

**6. Ubuntu Installation**
Now its time to get your computer setup. Double click on "Install Ubuntu 11.04" icon on the desktop and get where picture 1.0 is below:

picture 1.0
[IMG]http://ubuntuforums.org/picture.php?albumid=2326&pictureid=7953[/IMG]

On the "Preparing to install Ubuntu" screen, you can select both "Download updates while installing" and "Install this third-party software" (this is optional). Now move to picture 1.1 for the next part:

picture 1.1
[IMG]http://ubuntuforums.org/picture.php?albumid=2326&pictureid=7954[/IMG]

On the "Allocate drive space" screen, make sure you select 'Something else' before pressing the 'Forward' button. After you press the 'Forward' button, go to picture 1.3 for what you should see when manually setting up your partitions:

picture 1.3
[IMG]http://ubuntuforums.org/picture.php?albumid=2326&pictureid=7955[/IMG]

The "Allocated drive space" should look different now showing you a list of your logical volumes and the /dev/sda partitions near the bottom. Scroll down the list to the bottom and highlight /dev/sda1 and press the "Change..." button. See picture 1.4 on what the change window should look like for /dev/sda1:

picture 1.4
[IMG]http://ubuntuforums.org/picture.php?albumid=2326&pictureid=7949[/IMG]

The partition /dev/sda1 will be the /boot partition for your system and you can select whatever file system you wish (I would advise on ext4 or better). Now lets scroll up to the top and highlight the /dev/mapper/sysvg-lvhome partition that has the "ext4" next to it. Press the "Change..." button and see picture 1.5 for what this partition should look like:

picture 1.5
[IMG]http://ubuntuforums.org/picture.php?albumid=2326&pictureid=7950[/IMG]

This will be the /home directory for my system using ext4. Again, the file system is your choice and doesn't need to be ext4. Do this same process for /dev/mapper/sysvg-root and /dev/mapper/sysvg-lvswap by highlighting them and pressing the "Change..." button. See pictures 1.6 and 1.7 for what you should setup for both:

picture 1.6
[IMG]http://ubuntuforums.org/picture.php?albumid=2326&pictureid=7951[/IMG]

picture 1.7
[IMG]http://ubuntuforums.org/picture.php?albumid=2326&pictureid=7952[/IMG]

If you are all setup for your system to have all proper logical volumes, you press the "Install Now" button to start the installation process. This installation will ask for you additional information like your timezone, username, etc... please fill that in with what you want for your system. Once you are done, you can sit back and wait for the whole thing to comeplete. Once the installation process is complete, you will see picture 1.8 in front of you:

picture 1.8
[IMG]http://ubuntuforums.org/picture.php?albumid=2326&pictureid=7956[/IMG]

Make sure you **DO NOT PRESS** "Restart Now". You want to press the "Continue Testing" so you can continue to step 7.

**7. Install lvm2 onto your new Ubuntu Install**
Your system is almost ready to use LVM2 but the only problem is LVM2 isn't a package that is installed by default (oh noes!!). To fix that we need to install it onto your newly setup Ubuntu instance. The commands below will help do this.

Mount your system into /mnt/:
```

sudo mount /dev/mapper/sysvg-lvroot /mnt
sudo mount /dev/mapper/sysvg-lvhome /mnt/home/
sudo mount /dev/sda1 /mnt/boot

```

We need to first mount your root file system to /mnt. Mounting your home file system probably isn't necessary but doesn't hurt to do. We do need your boot file system mounted to /mnt/boot to have this work so make sure you have at least your root and boot file systems mounted.

Change your root to /mnt/
```
sudo chroot /mnt
```

This command allows you to change your root file system so you can manage that new file system. Doing this will make any installations and changes perminant onto your changed root filesystem. Now that we are on your Ubuntu instance, you will noticed that you are now root and the symbole after 'root@ubuntu:' has changed to a #. That is a good thing as we are not on the live CD's root file system but on your instance of Ubuntu. We will need to run the following command to allow your file system to boot into your LVM create partitions.

**---OPTIONAL---**

Load LVM modules on startup

If you want some additional functionality once your system is setup, ***MarioSchmidtSoftware*** suggests running these commands below before you install the package lvm2 (not needed but wouldn't hurt if you plan on using LVM for more then just the basics):
```

echo "dm-mod" >> /etc/modules
echo "dm-snapshot" >> /etc/modules
echo "dm-mirror" >> /etc/modules
echo "dm-mod" >> /etc/initramfs-tools/modules
echo "dm-snapshot" >> /etc/initramfs-tools/modules
echo "dm-mirror" >> /etc/initramfs-tools/modules

``` 

**---OPTIONAL---**

Install LVM2 onto your chroot file system:
```

root@ubuntu:/# apt-get -y install lvm2

```
Just like in step 3, we install lvm2 onto your instance of Ubuntu instead of the live instance. I want to point out some of the output that is import to why you need to install lvm2 onto your instance of Ubuntu:
```

update-initramfs: deferring update (trigger activated)
Setting up lvm2 (2.02.66-4ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic

```
If you see this during your installation of lvm2, this means, in a nutshell, your initrd image will now be able to use LVM based partitions at startup. If lvm2 was not installed on your computer and you started to start it up, you computer would complain about not being able to find /dev/mapper/sysvg-lvroot and so on...

Your computer is now setup with Ubuntu and logical volumes by using the Ubuntu Desktop image.

**References:**
---
[http://www.redhat.com/magazine/009jul05/features/lvm2/](http://www.redhat.com/magazine/009jul05/features/lvm2/)
[http://sourceware.org/lvm2/](http://sourceware.org/lvm2/)
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.cyberwalker.com/article/28](http://www.cyberwalker.com/article/28)
[http://man.he.net/man8/initramfs-tools](http://man.he.net/man8/initramfs-tools)
---

---

### Post by DirtyPC on 2011-06-15
detailed and alot of effort. Great job.

---

### Post by ruffEdgz on 2011-10-13
**Update**

Ran my tutorial on 11.10 without any problems. Updated the first post to reflect that it works also in 11.10.

Please reply back to this post if you have any additional questions about this tutorial.

---

### Post by pcas on 2011-10-14
Hi,

First step in "7. Install lvm2 onto your new Ubuntu Install" should be to setup the device-mapper entries in /dev

optional: discover the available volume groups
```

vgscan
```

change the active volume group (creates entries in /dev/mapper)
```

vgchange -a y sysvg
```

Now it's possible to mount the devices in /mnt (at least on my PXE booted Asus eee pc-901 while installing 11.04)

Thanks for a detailed tutorial,
/Pablo

---

### Post by ruffEdgz on 2011-10-14
> **pcas said:**
> Hi,

First step in "7. Install lvm2 onto your new Ubuntu Install" should be to setup the device-mapper entries in /dev

optional: discover the available volume groups
```

vgscan
```

change the active volume group (creates entries in /dev/mapper)
```

vgchange -a y sysvg
```

Now it's possible to mount the devices in /mnt (at least on my PXE booted Asus eee pc-901 while installing 11.04)

Thanks for a detailed tutorial,
/Pablo

Hey Pablo,

Thanks for the update on my tutorial.

You are correct about the activation of the volume group only when you already have volume group(s) setup on a machine. That part is a bit different since the steps for have Ubuntu recognize the LV would be:
[LIST=1]
[*]install lvm2
[*]pvscan (make sure your system can see the physical volumes)
[*]vgchange -a y (activate all the volume groups you have)
[*]lvdisplay (see all the logical volumes ready for use)
[/LIST]
In my steps, I'm advising those who never setup a machine with logical volumes, this is how you do it from scratch.

I will append to the end of this tutorial the way you probably did it with already existing logical volumes/volume groups/ physical volumes and how you can setup a machine without removing the older LVM configurations.

Cheers!

---

### Post by pcas on 2011-10-15
Aha, then maybe I understand now why I had to perform the vgchange. 

I actually followed your tutorial to create the lvm setup, I did not have lvm on this machine before. But I rebooted the system during step 7 as a last resort, because I could not re-install lvm2 on the chrooted filesystem in step 7 (I lost wifi connnectivity, probably due to user error :) ). The reboot forced me to then rediscover the volume group...

I of course had to reboot into the liveCD, or actually the netbooted/PXE liveCD that I was running during the installation as the new installation could not be booted due to missing lvm drivers (as you have decribed above)

/Pablo

---

### Post by T.J. Crowder on 2011-10-19
@ruffEdgz: **_Thank you_** for this thorough, clear, and above all *correct* how-to!! Worked perfectly! Very much appreciated. It's *so* rare to find a write-up where there isn't *something* wrong, a command missing a hyphen, a step missed out, etc., etc. Brilliant stuff!

@pcas: Thank you for the bit about [FONT="Courier New"]vgscan[/FONT], that was very helpful when I ended up doing repeated installs on the same box.
--
T.J. Crowder
tj / crowder software / com
Independent Software Engineer

---

### Post by MarioSchmidtSoftware on 2012-05-17
Works like a charm! Thank you for that guide.

I would like to make two suggestions for that How-To.

First of all, I think we should not build a swap drive over LVM. It's possible but a overhead, because who will ever have to extend or snapshot a swap drive. So it's better placed native on /dev/sda3.

Second, I would suggest adding LVM-kernel-modules right after you change-root. If we do it before "apt-get install lvm2" in the chroot-environment, the modules will automatically be build into the initramfs and the kernel! That allows us additional scenarios like booting from a snapshot-root-system.

```
echo "dm-mod" >> /etc/modules
echo "dm-snapshot" >> /etc/modules
echo "dm-mirror" >> /etc/modules
echo "dm-mod" >> /etc/initramfs-tools/modules
echo "dm-snapshot" >> /etc/initramfs-tools/modules
echo "dm-mirror" >> /etc/initramfs-tools/modules

```Right before:

```

apt-get install lvm2

```

---

### Post by ruffEdgz on 2012-06-13
> **MarioSchmidtSoftware said:**
> Works like a charm! Thank you for that guide.

I would like to make two suggestions for that How-To.

First of all, I think we should not build a swap drive over LVM. It's possible but a overhead, because who will ever have to extend or snapshot a swap drive. So it's better placed native on /dev/sda3.


I agree about the possible overhead and the reason why I suggested it was for possible extending of the swap if you don't know much you needed (mostly for laptop usage). I will update that part to make sure the swap isn't managed by LVM but just a separate partition and let people know that its possible to make swap into a LVM managed partition but could cause overhead.

> **MarioSchmidtSoftware said:**
> 
Second, I would suggest adding LVM-kernel-modules right after you change-root. If we do it before "apt-get install lvm2" in the chroot-environment, the modules will automatically be build into the initramfs and the kernel! That allows us additional scenarios like booting from a snapshot-root-system.

```
echo "dm-mod" >> /etc/modules
echo "dm-snapshot" >> /etc/modules
echo "dm-mirror" >> /etc/modules
echo "dm-mod" >> /etc/initramfs-tools/modules
echo "dm-snapshot" >> /etc/initramfs-tools/modules
echo "dm-mirror" >> /etc/initramfs-tools/modules

```Right before:

```

apt-get install lvm2

```

I never thought about that part for the additional modules for LVM to get additional functionality. Will update the post with this part but will make it optional since it isn't totally needed . I do like the option though since being able to boot up to a snapshot would be nice ;)

Cheers!

---

### Post by held7over on 2012-06-14
Ubuntu 12.04  

How can I wipe my entire drive, so I can start over clean?

Ah. Guys. Upon reboot after installing as described here, all I have is a blinking cursor. It's my fault. 

I thought I had wiped the drive with gparted, but evidently not, as a prior attempt to get the layout I wanted using Ubuntu 12.04's Guided LVM install evidently wasn't wiped at all. -Hence, the black screen and blinking cursor in the upper left hand corner of the screen upon boot, after following these instructions.  (If I had realized LVM still existed, I would have used the "vgchange -a y sysvg" fix before trying to mount /mnt.

Subsequent attempts to overwrite with a normal install of 12.04 or wipe the drive with gparted seem to have failed, as the layout I created using this guide, still exists! Which would be great if I could use!

Help! How do I fix this or wipe the drive clean?  :)

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12062142#post12062142](http://ubuntuforums.org/showthread.php?p=12062142#post12062142)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

