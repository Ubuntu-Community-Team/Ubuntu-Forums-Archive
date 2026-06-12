---
title: "Ubuntu Snappy Personal Desktop"
date: 2015-07-09
forum: Ubuntu Development Version
---

### Post by pixelro on 2015-07-09
(needs ubuntu-device-flash from wily ...)
sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
kvm -m 2048 -vga qxl personal_x86.img 

done. 
source ogra [https://plus.google.com/u/0/+OliverGrawert/posts/Z8q7fDQac2r](https://plus.google.com/u/0/+OliverGrawert/posts/Z8q7fDQac2r)

[https://www.youtube.com/watch?v=P9WivxsXDDU](https://www.youtube.com/watch?v=P9WivxsXDDU)

---

### Post by ventrical on 2015-07-09
Thanks .. but not exactly the .iso we were expecting.

Regards..

it's taking a real long time to download all the particulars from the server. it must be swamped.

Regards..

here

```

ventrical@ventrical-luntiy-betatest:~$ sudo apt-get install ubuntu-device-flash
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-10 linux-headers-3.19.0-10-generic
  linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic
  linux-headers-3.19.0-16 linux-headers-3.19.0-16-generic
  linux-image-3.19.0-10-generic linux-image-3.19.0-15-generic
  linux-image-3.19.0-16-generic linux-image-extra-3.19.0-10-generic
  linux-image-extra-3.19.0-15-generic linux-image-extra-3.19.0-16-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify kpartx libxmltok1 qemu-user-static ubuntu-snappy-cli
Suggested packages:
  debian-keyring
The following NEW packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify kpartx libxmltok1 qemu-user-static ubuntu-device-flash
  ubuntu-snappy-cli
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6 MB of archives.
After this operation, 97.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ wily/main binfmt-support amd64 2.1.5-1 [49.5 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ wily/main libxmltok1 amd64 1.2-3build3 [54.1 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ wily/universe debsig-verify amd64 0.13 [30.0 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ wily/universe qemu-user-static amd64 1:2.3+dfsg-5ubuntu2 [7,215 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ wily/universe android-tools-adb amd64 4.2.2+git20130218-3ubuntu41 [67.1 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ wily/universe android-tools-fastboot amd64 4.2.2+git20130218-3ubuntu41 [47.5 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ wily/universe click-ubuntu-policy all 0.1 [3,796 B]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ wily/main kpartx amd64 0.5.0-7ubuntu1 [23.8 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ wily/universe ubuntu-snappy-cli amd64 1.5ubuntu1 [1,534 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ wily/universe ubuntu-device-flash amd64 0.26-0ubuntu1 [1,556 kB]
Fetched 10.6 MB in 43s (243 kB/s)                                              
Selecting previously unselected package binfmt-support.
(Reading database ... 295191 files and directories currently installed.)
Preparing to unpack .../binfmt-support_2.1.5-1_amd64.deb ...
Unpacking binfmt-support (2.1.5-1) ...
Selecting previously unselected package libxmltok1.
Preparing to unpack .../libxmltok1_1.2-3build3_amd64.deb ...
Unpacking libxmltok1 (1.2-3build3) ...
Selecting previously unselected package debsig-verify.
Preparing to unpack .../debsig-verify_0.13_amd64.deb ...
Unpacking debsig-verify (0.13) ...
Selecting previously unselected package qemu-user-static.
Preparing to unpack .../qemu-user-static_1%3a2.3+dfsg-5ubuntu2_amd64.deb ...
Unpacking qemu-user-static (1:2.3+dfsg-5ubuntu2) ...
Selecting previously unselected package android-tools-adb.
Preparing to unpack .../android-tools-adb_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package android-tools-fastboot.
Preparing to unpack .../android-tools-fastboot_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package click-ubuntu-policy.
Preparing to unpack .../click-ubuntu-policy_0.1_all.deb ...
Unpacking click-ubuntu-policy (0.1) ...
Selecting previously unselected package kpartx.
Preparing to unpack .../kpartx_0.5.0-7ubuntu1_amd64.deb ...
Unpacking kpartx (0.5.0-7ubuntu1) ...
Selecting previously unselected package ubuntu-snappy-cli.
Preparing to unpack .../ubuntu-snappy-cli_1.5ubuntu1_amd64.deb ...
Unpacking ubuntu-snappy-cli (1.5ubuntu1) ...
Selecting previously unselected package ubuntu-device-flash.
Preparing to unpack .../ubuntu-device-flash_0.26-0ubuntu1_amd64.deb ...
Unpacking ubuntu-device-flash (0.26-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (221-1ubuntu2) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up binfmt-support (2.1.5-1) ...
Setting up libxmltok1 (1.2-3build3) ...
Setting up debsig-verify (0.13) ...
Setting up qemu-user-static (1:2.3+dfsg-5ubuntu2) ...
Setting up android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Setting up android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Setting up click-ubuntu-policy (0.1) ...
Setting up kpartx (0.5.0-7ubuntu1) ...
Setting up ubuntu-snappy-cli (1.5ubuntu1) ...
Warning: The home directory /nonexistent you specified can not be accessed: No such file or directory
Adding system user `snappypkg' (UID 120) ...
Adding new group `snappypkg' (GID 132) ...
Adding new user `snappypkg' (UID 120) with group `snappypkg' ...
Not creating home directory `/nonexistent'.
Setting up ubuntu-device-flash (0.26-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (221-1ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
ventrical@ventrical-luntiy-betatest:~$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
Determining oem configuration
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 150.14 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 111.12 KB/s 
Done
Fetching information from server...
Downloading and setting up...Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 112.32 KB/s 
Done
New image complete
Summary:
 Output: personal_x86.img
 Architecture: amd64
 Channel: edge
 Version: 32
ventrical@ventrical-luntiy-betatest:~$ 



```

```

ventrical@ventrical-luntiy-betatest:~$ kvm -m 2048 -vga qxl personal_x86.img 
The program 'kvm' is currently not installed. You can install it by typing:
sudo apt-get install qemu-kvm
ventrical@ventrical-luntiy-betatest:~$ sudo apt-get install qemu-kvm
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-10 linux-headers-3.19.0-10-generic
  linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic
  linux-headers-3.19.0-16 linux-headers-3.19.0-16-generic
  linux-image-3.19.0-10-generic linux-image-3.19.0-15-generic
  linux-image-3.19.0-16-generic linux-image-extra-3.19.0-10-generic
  linux-image-extra-3.19.0-15-generic linux-image-extra-3.19.0-16-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ipxe-qemu libaio1 libfdt1 libsdl1.2debian libusbredirparser1 libxen-4.5
  qemu-system-common qemu-system-x86 qemu-utils seabios sharutils
Suggested packages:
  samba vde2 qemu-block-extra sgabios ovmf debootstrap bsd-mailx mailx
The following NEW packages will be installed:
  ipxe-qemu libaio1 libfdt1 libsdl1.2debian libusbredirparser1 libxen-4.5
  qemu-kvm qemu-system-common qemu-system-x86 qemu-utils seabios sharutils
0 upgraded, 12 newly installed, 0 to remove and 21 not upgraded.
Need to get 4,324 kB of archives.
After this operation, 22.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ wily/main libaio1 amd64 0.3.110-1 [6,454 B]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ wily/main libsdl1.2debian amd64 1.2.15-10ubuntu1 [162 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ wily/main qemu-system-common amd64 1:2.3+dfsg-5ubuntu2 [253 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ wily/main libfdt1 amd64 1.4.0+dfsg-1 [15.7 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ wily/main ipxe-qemu all 1.0.0+git-20141004.86285d1-1ubuntu3 [580 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ wily/main libusbredirparser1 amd64 0.7-1ubuntu2 [13.9 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ wily/main libxen-4.5 amd64 4.5.0-1ubuntu4 [322 kB]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ wily/main seabios all 1.8.1-2ubuntu1 [113 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ wily/main qemu-system-x86 amd64 1:2.3+dfsg-5ubuntu2 [2,208 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ wily/main qemu-kvm amd64 1:2.3+dfsg-5ubuntu2 [7,282 B]
Get:11 http://ca.archive.ubuntu.com/ubuntu/ wily/main qemu-utils amd64 1:2.3+dfsg-5ubuntu2 [494 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu/ wily/main sharutils amd64 1:4.15.1-1 [148 kB]
Fetched 4,324 kB in 18s (231 kB/s)                                             
Selecting previously unselected package libaio1:amd64.
(Reading database ... 295334 files and directories currently installed.)
Preparing to unpack .../libaio1_0.3.110-1_amd64.deb ...
Unpacking libaio1:amd64 (0.3.110-1) ...
Selecting previously unselected package libsdl1.2debian:amd64.
Preparing to unpack .../libsdl1.2debian_1.2.15-10ubuntu1_amd64.deb ...
Unpacking libsdl1.2debian:amd64 (1.2.15-10ubuntu1) ...
Selecting previously unselected package qemu-system-common.
Preparing to unpack .../qemu-system-common_1%3a2.3+dfsg-5ubuntu2_amd64.deb ...
Unpacking qemu-system-common (1:2.3+dfsg-5ubuntu2) ...
Selecting previously unselected package libfdt1:amd64.
Preparing to unpack .../libfdt1_1.4.0+dfsg-1_amd64.deb ...
Unpacking libfdt1:amd64 (1.4.0+dfsg-1) ...
Selecting previously unselected package ipxe-qemu.
Preparing to unpack .../ipxe-qemu_1.0.0+git-20141004.86285d1-1ubuntu3_all.deb ...
Unpacking ipxe-qemu (1.0.0+git-20141004.86285d1-1ubuntu3) ...
Selecting previously unselected package libusbredirparser1:amd64.
Preparing to unpack .../libusbredirparser1_0.7-1ubuntu2_amd64.deb ...
Unpacking libusbredirparser1:amd64 (0.7-1ubuntu2) ...
Selecting previously unselected package libxen-4.5:amd64.
Preparing to unpack .../libxen-4.5_4.5.0-1ubuntu4_amd64.deb ...
Unpacking libxen-4.5:amd64 (4.5.0-1ubuntu4) ...
Selecting previously unselected package seabios.
Preparing to unpack .../seabios_1.8.1-2ubuntu1_all.deb ...
Unpacking seabios (1.8.1-2ubuntu1) ...
Selecting previously unselected package qemu-system-x86.
Preparing to unpack .../qemu-system-x86_1%3a2.3+dfsg-5ubuntu2_amd64.deb ...
Unpacking qemu-system-x86 (1:2.3+dfsg-5ubuntu2) ...
Selecting previously unselected package qemu-kvm.
Preparing to unpack .../qemu-kvm_1%3a2.3+dfsg-5ubuntu2_amd64.deb ...
Unpacking qemu-kvm (1:2.3+dfsg-5ubuntu2) ...
Selecting previously unselected package qemu-utils.
Preparing to unpack .../qemu-utils_1%3a2.3+dfsg-5ubuntu2_amd64.deb ...
Unpacking qemu-utils (1:2.3+dfsg-5ubuntu2) ...
Selecting previously unselected package sharutils.
Preparing to unpack .../sharutils_1%3a4.15.1-1_amd64.deb ...
Unpacking sharutils (1:4.15.1-1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for doc-base (0.10.6) ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (221-1ubuntu2) ...
Processing triggers for install-info (6.0.0.dfsg.1-3) ...
Setting up libaio1:amd64 (0.3.110-1) ...
Setting up libsdl1.2debian:amd64 (1.2.15-10ubuntu1) ...
Setting up qemu-system-common (1:2.3+dfsg-5ubuntu2) ...
Setting up libfdt1:amd64 (1.4.0+dfsg-1) ...
Setting up ipxe-qemu (1.0.0+git-20141004.86285d1-1ubuntu3) ...
Setting up libusbredirparser1:amd64 (0.7-1ubuntu2) ...
Setting up libxen-4.5:amd64 (4.5.0-1ubuntu4) ...
Setting up seabios (1.8.1-2ubuntu1) ...
Setting up qemu-system-x86 (1:2.3+dfsg-5ubuntu2) ...
Setting up qemu-kvm (1:2.3+dfsg-5ubuntu2) ...
Setting up qemu-utils (1:2.3+dfsg-5ubuntu2) ...
Setting up sharutils (1:4.15.1-1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for systemd (221-1ubuntu2) ...
Processing triggers for ureadahead (0.100.0-19) ...
ventrical@ventrical-luntiy-betatest:~$ 

```

it sort of breaks unity desktop after you exit but it's a start ..

---

### Post by grahammechanical on 2015-07-09
Oliver Grawert is something or other to do with snappy development. He was prominent on the recent snappy openhouses session on Ubuntu On Air. We what do we do? Download ubuntu-device-flash? Then download the image?

> sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode

And then create it in kvm with

> kvm -m 2048 -vga qxl personal_x86.img 

Have missed anything? I will give it a try. I do not expect it to be much further along than desktop next. I do not expect the desktop applications to be available as snappy apps yet.

Thanks pixelro

Regards.


Regards.

---

### Post by ventrical on 2015-07-09
> **grahammechanical said:**
> 
Oliver Grawert is something or other to do with snappy development. He  was prominent on the recent snappy openhouses session on Ubuntu On Air.  We what do we do? Download ubuntu-device-flash? Then download the image?

> 
                                                         sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode                      



     
 
And then create it in kvm with
[QUOTE]
                                                         kvm -m 2048 -vga qxl personal_x86.img                      


     
 

[/QUOTE]

The commands download the image which expands to 9.8 GBs and it runs in the kvm but I am going to try it standalone also.

 I am not trying to be cheeky here but it is more or less pretty well where we left off with unity8 when we were experiment with mir ..etc.. but I do expect that this image can be run soon without kvm.

edit

it will remind you to install qemu.

```

sudo apt-get install qemu

```


Regards..

I used the gnome 'disks' utility in ubuntu-desktop wily to 'restore image' to a hard drive and I installed the harddrive on a desktop and it shows verbose script (same as in kvm) then boots right into unity8!!

Bravo canonical!

Regards..

edit :

The image is:

```

personal_x86.img

```

and you will find it in your /Home directory. 

Regards..

---

### Post by grahammechanical on 2015-07-10
> I am not trying to be cheeky here but it is more or less pretty well where we left off with unity8 when we were experiment with mir ..etc.. 

I do not want to be cheeky either, but I do agree with you.

I have learnt something in trying this image out. My machine does not have the memory to run a desktop in kvm. Snappy-core worked fine. I am more in favour of LXC and with lxc-desktop I could run a desktop on another tty and switch between the two without any detrimental effects. It is a pity that they are not using LXC here.

Nautilus gives a right click option for personal_x86.img of open with Disk Image Writer, which if I understand correctly will write the image to USB stick. It enters my head that those desktop-next pre-installed images once unzipped might gives us this same kind of image file.

Just to be clear, what did Disks>Restore image do? Did it run the image in a window on the desktop? I am not clear on what happens when we use Disks>Restore image. I have never risked doing it.

Regards.

---

### Post by ventrical on 2015-07-10
> **grahammechanical said:**
> [QUOTE]I am not trying to be cheeky here but it is more or less pretty well where we left off with unity8 when we were experiment with mir ..etc.. [/code]

I do not want to be cheeky either, but I do agree with you.

Just to be clear, what did Disks>Restore image do? Did it run the image in a window on the desktop? I am not clear on what happens when we use Disks>Restore image. I have never risked doing it.

Regards.

It basically 'copies' or installs the image <perosnal_x86.img> to the target device. I have done it using both USB stick and a USB  to SATA docking device. That means I can use 'disks' to 'restore image to a hard drive and then put that hard drive into a desktop machine and then boot it. It boots into system -a which is in grub menu. (they have been able to put grub in there so you can install other installs on hdd ..etc..  Sudodus's mkusb will do the same thing but because this image is so on the edge I recommend using disks for now.

1. The image  <personal_x86.img> is 9.8 GBs large. 
2. You will need a 16GB USB stick for this.
3. If you have USB hdd drive or USB to SATA hdd docking device you can <restore image> to that target, then install the hdd into most any given machine and it will boot to grub <system-a>, and then boot right into Unity8 logon. KVM is not required with this method.  Once booted into unity8 and logged on you can use  Ctrl+Alt+F1 to get to terminal and run snappy commands. To get back to unity8 session just hit Ctrl+Alt+F7.


Here is a really  streamlined and reliable way to make a bootable USB disk with an (*)ubuntu image.

                                                         

[LIST=1]
[*]Download the ISO 
[*]Insert your USB stick in the knowledge that it’s going to get wiped 
[*]Open the “Disks” application 
[*]Choose your USB stick and click on the cog icon on the righthand side 
[*]Choose “Restore Disk Image” 
[*]Browse to and select the ISO you downloaded in #1 
[*]Click “Start restoring” 
[*]Wait 
[*]Boot and select “Try Ubuntu….” 
[*]Done * 
[/LIST]
                      
     
 
edit : do not select  ISO but select <personal_x86.img> from /Home directory (is where you should find image.
edit : also note that if you use USB stick USB ver2.0 and boot from there  you will notice the white arrow of mir. It is a little slow to boot from USB stick so you have to wait for Unity8 login to come up .. so be patient :)

Regards..

Here are how to screenshots to build bootable USB. I used 32GB ver3.0 USB as example.

The image already has it's own little file and partition format so it will wipe USB stick. It boots just great on my Maxtor 250GB hdd.

> **grahammechanical said:**
> [QUOTE]

Nautilus gives a right click option for personal_x86.img of open with Disk Image Writer, which if I understand correctly will write the image to USB stick. It enters my head that those desktop-next pre-installed images once unzipped might gives us this same kind of image file.

Regards.
Yep.  

I haven't tried the Disk Image Writer option .. just to err on the side of caution I used the 'disks' option which was recommended when we had big problems with SDC in trusty and utopic.

regards..

---

### Post by grahammechanical on 2015-07-10
I have just found out that the Disk Image Writer option loads Disks which in turn will recognise a USB stick but it gives a warning that the image to be restored is smaller than the size of USB stick. Is this a problem? Any side affects apart from the full size of the USB not being available? Unlike with persistence.

Edit: I have just gone over your earlier posts. Will try it.

Edit 2: Well, it took some time to get the image on the USB stick and it does load to a login screen and a desktop and it is much faster than using a kvm on my machine, But, although it recognises the WiFi access points it does not provide a dialog by which to put in pass phrases and that stuff. Desktop Next could do that. So, Browser blinks out of existence. Because, I think it is not connecting to the Ubuntu start screen server. The app store will not open. So, I cannot install the terminal to run my eyes over the file system.

With the USB stick plugged into a desktop install it shows three partitions

system-a which has the sort of folders usually expected in a Ubuntu file system; system-b which is empty, except for lost&found folder; writable which has cache, system-data and user-data folders.

user-data has the same folders as system-a home folder. A user folder (ubuntu) and inside that Documents, Downloads, Music, Pictures, & Videos.

It has a grub.cfg but it is in system-a/oem/generic-amd64/1.4/ It has lots of references to snappy. I have yet to find any of the bin files for applications like Libreoffice.

Regards

---

### Post by ventrical on 2015-07-10
It's very , very edge! :)  I plan to just keep updating by going to terminal (Ctrl+Alt+F1) log in ubuntu/ubuntu and then:

```

sudo snappy update list

```

or

```

sudo snappy update -v

```
 You can get back to unity8 with Ctrl+Alt+F7

Regards..

---

### Post by grahammechanical on 2015-07-11
I have been wondering how to get an updated personal_x86.img. What we would call a daily image. I am going to try running this command again in a day or two and see if I can notice any difference that will prove it is an updated image file.

```
sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
```

I do not know of any other place to down load the image files from.

EDIT: I was able to update snappy personal on a USB stick with the command sudo snappy update. Applying the updates takes a long time. I think that it also tried to update the kernel and failed with an out of space message. But it did not break the installation. So, I guess that confirms the roll back feature when an update fails.

The Apps store will let me install apps. Well, it downloads them but does not actually install them. At least it let me enter my Ubuntu One account details and it accepted them. 

Regards.

---

### Post by ventrical on 2015-08-05
I am now in persistive live trusty iso and I am going to try a *install alongside* on the hdd that has personal_x86.img on it.

I am going to choose the below option.

Here is the result so far.

I tried to use all the free space to create a partition and Ubiquity just bowed out , off the screen, no warnings , no errors... nuthing. Must be persisitive drive problem. Thats SDC for ya. :) jk..

Will try another iso boot.

Did not work. It appears that when the snappy image is restored to an hdd is burns the whole disk to a point where gparted and Ubiquity start to act very erractically and one cannot install a traditional ubuntu install using ubiquity installer on the hdd that has personal_x86.img.

Regards..

---

### Post by grahammechanical on 2015-08-05
I think the issue is that using image restore with personal_x86.img is like restoring a cloned a drive. It cannot be done to a smaller drive but when done to a larger drive the excess space becomes unavailable in some way. This means that the "free space" is not the same free space that we see when we partition a drive. Have you tried using Gparted to turn that free space into a partition?

I am thinking of using the dd command to move the three partitions (system-a, system-d, & writable) one at a time off of the USB stick and on to 3 partitions on my second hard drive. And boot into personal from grub and Ubuntu on my first hard drive.

Regards.

---

### Post by ventrical on 2015-08-06
I updated my snappy personal img and it is now broken. Cannot even get grub or Ctrl+Alt+F1 terminal. It is a read only image and after I updated Grub  it gave me an error message:

Reading in blind mode:

 ... or to this effect.. then booted into a otherwise useless session of unity8

  I think we have to get a new image of the experimental <personal_x86.img> each time we want to test it or experiement with things.

Regards..

---

### Post by ventrical on 2015-08-06
loaded up the new image on hdd - personal_x86.img (60) and there is some better functionality. browser will work but will break if you try to use scopes to expand the window .. etc.. apps from the app store pretend they are installing .. but no . Unity8 still the course for snappy.

Regards..

---

### Post by grahammechanical on 2015-09-09
I have been regularly updating snappy personal on a USB stick but as of the last three days there are no updates. The update command just takes us back to the prompt.

2 days ago I downloaded what I thought was the latest image but it was actually built on 2015-09-02. So, it seems that there is a pause in building these images. They are built on wily code so perhaps they are not completing all the automatic tests. Or perhaps they are converting the app store from click to snap.

Anyway, Browser now connects to the World Wide Web using ethernet. Still cannot activate the WiFi connection although there is a WiFi driver working. App store still pretends to install apps. Take the mouse pointer to the left screen edge and there is this cascade effect of open application surfaces which allows the switching of full screen applications. A neat trick.

Oh, I have done some reading and I better understand how the roll back of a failed update will work. At the first install the system files and folders are in the system-a partition. The next update to snappy core will go into the system-b partition. If the update fails the OS will continue to load from system-a partition. If the update succeeds then the next restart will be from system-b partition and the next update to the core will go in system-a partition. Depending on whether the update succeeds or fails then a flag is set accordingly to direct which partition to load snappy core from.

Regards.



Regards.

---

### Post by ventrical on 2015-09-09
I am assuming that we can still get the new updated images by:

```

sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode

```

and then , if preferred..
```

kvm -m 2048 -vga qxl personal_x86.img
 
```

---

### Post by ventrical on 2015-09-09
@graham

I had subscribed to the snappy developers mailing list and they are still working on basic frameworks, user/password setups .. etc..

Here is example of whats happening..

> 
On 01/09/15 12:00, Stefan Knorr wrote:
> we are currently evaluating, if we can use Ubuntu Snappy Core as embedded OS for some of our products.
>
 Up to now, Snappy Core looks like a good fit. We feel very good about 
the security system and the snappy app model. But I have some questions,
 which I couldn't get answered by the existing documentation.
>
> 1) We use x86 based boards as embedded hardware, on which the standard kernel 
>     (generic-amd64/generic-i386) are working out of the box. Unfortunately we add some dedicate   
>     hardware to the embedded system, for which we provide a kernel module on DKMS basis.
>     But DKMS doesn't work under Snappy Core, so what I got from the documentation is, that somehow we 
>     have to provide a oem snap with the kernel. 
>     My question is, if we have to provide the whole kernel and 
>     all the modules or is it possible to define an OEM snap to add just a kernel module to the generic kernel?
 
You'll have three options:
 
 * build your own kernel with just the modules you want for your device
 
     - smaller kernel, fewer security issues
     - choose the kernel version you want and update when you want
     - but obviously don't get kernel updates magically
     - this is best for a very focused single-purpose device
 
 * add the module to the standard Ubuntu supported list
 
     - this makes those devices work for everybody
     - we'll do the maintenance when we do normal updates
     - but requires at least a conversation and planning
     - this is best for the community and for open devices
 
 * find a middle way, like DKMS-in-OEM-snap
 
     - this will likely be possible
     - it will invalidate security certifications (tainting the kernel)
     - it also runs the risk of failing on update (dkms build failures)
     - but probably work well enough as a PoC
 
 
> 2) My second question is related to the system/app update procedure. Our systems will probably have 
>      connection to the internet, but on some installations they will run in a dedicated network with no 
>      internet access. From what I got from the docu, the update has to be started from an console (ssh) with 
>     the snappy command, which checks the store for update and downloads the newest version.
>     Is it possible to omit the download and transfer the new packages by a control-instance to the Snappy 
>     Core system and then deploy the update from the than uploaded package ?
 
 
In due course there will both online and offline ways to update a snappy
device. We need to support completely-disconnected updates for things
like medical scanners which cannot be connected to the Internet ever!
And we need to do that with validated updates, which requires a bunch of
signatures to provide the integrity of the update to the system. None of
that will require SSH access.
 
 
> 3) Can the update also triggered by a app or framework? 
>      If yes, which security-policies would be than necessary?
 
It will be possible to create a framework which can trigger updates,
yes, which would be a good way to bind a snappy system into your own
infrastructure.
 
 
> 4) Can a app or framework change the local IP-settings (static/dhcp)?
>      If yes, which security-policies would be than necessary?
 
In principle yes, this is just configuration of the core OS. It will
need privileges, details to be worked out, but it's not a bad or scary
thing in and of itself. In general though we would expect the owner /
user of the device to set IP addresses.
 
Mark
 
 

..so it looks as if they are still trying the hammer the gold in the crucible so to speak but I expect 
that there will big big changes after the next toolchain is uploaded.

---

### Post by grahammechanical on 2015-09-09
I do not have the RAM to run in a KVM so I use image restore to put the image on a USB stick. And I can still download personal_x86.img with that command but after restoring to the USB and running "snappy list" the date of ubuntu-core is 2015-09-02.

Big changes a coming? Most surely. Edit: A day later and personal has been updated. Posting from it now. Build 88. But ubuntu-core part is still dated 2015-09-02

---

### Post by ventrical on 2015-09-11
latest is 88. here we go :)

```

[sudo] password for ventrical: 
Determining oem configuration
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 199.69 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 238.62 KB/s 
Done
Fetching information from server...
Downloading and setting up...
84.88 MB / 84.88 MB [====================================] 100.00 % 213.68 KB/s 
463.35 MB / 463.35 MB [==================================] 100.00 % 351.75 KB/s 
Installing generic-amd64
Starting download of generic-amd64
41.70 KB / 41.70 KB [=====================================] 100.00 % 98.80 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 201.50 KB/s 
Done
New image complete
Summary:
 Output: personal_x86.img
 Architecture: amd64
 Channel: edge
 Version: 88
ventrical@ventrical-luntiy-betatest:~$ 

```

---

### Post by ventrical on 2015-09-11
I am writing this message using the unity8 provided 'browser' (whatever that is) and snappy personal now has some actual functionality. The scroll on the mouse does not work and there are no current gestures to 'slide' the screen so I have to use the right side scroll slider that is provided, ebing ever so careful no to go to the right edge and bump it into that  'shuffle' stack screen mode. The browser is behaving in a way where you can tell that there is definite progress with mir  infrastructure and bindings - yes - a gigantic smart phone. But please note I am running this img 88 on a 9th generation intel xeon graphics card. I tried loading it in a kvm on another machine and it was slow as molasses from from a dedicated hhd install it is working  very well .. well enough that I feel enthused to actually write something about it :)regards..

---

### Post by ventrical on 2015-09-11
It works much better with nVidia graphics hardware and an older machine with Wolfdale Processor. Also remembers Tabs, history and bookmarks. None of the widgets on the 'indicator-keyboard' work. The window does pull down nicely but they are just there for show right now. The network/flighmode widget works but not wifi settings. I can close browser by pulling mouse over to left side of screen, hover over the browser icon, right click and then it gives option to 'quit' which actually works! regards..

---

### Post by ventrical on 2015-09-11
Youtube will not show videos . Also other news sites will not play videos or sound. The browser  start to get real slow after while .. almost like IE used to be. In some cases it appears to be innovative but in others  it is more like it is in it's infant stages and takes extreme patience to navigate through. regards..

---

### Post by grahammechanical on 2015-09-11
Yesterday I was able to update to version 88 although I did notice that ubuntu-core was dated from a few days earlier. So, the update did not update the core from what I had previously downloaded. It was still booting from partition system-a. It will switch partitions when ubuntu-core is updated.

Browser has improved a lot. I now use it most of the time as my desktop browser. Tab browsing; Book Marks and Top Sites sites are now more easily accessed and we can copy URLs from one tab to another. But it does not give a line break in a Ubuntu Forum post.

It is possible to re-size app windows by grabbing side and bottom edges at the middle and pulling. The new size is remembered when the app is next launched. On Ubuntu Personal that is.

The weird thing about Browser is that it does not seem to be HTML5 compatible. That is the message I get when I try to play a live Ubuntu On Air session and other sites but it will play recorded Youtube Ubuntu On Air videos. Desktop Browser that is. I will have to try it on Ubuntu Personal. Running Ubuntu Personal on a USB2 speed USB stick requires patience. Especially, as there is not an indicator light to show that read/writes to the stick are taking place.

I am not sure if we will ever get Ubuntu Personal as an ISO image. It requires 4 partitions not including swap. 1) a boot partition (either BIOS of EFI); 2) System-a (about 5 GB minimal); 3) system-b (about 5 GB minimal) and 4) Writable (what we would call /home). So, already the minimal install size has gone up by 5 GB.

Regards.

---

### Post by ventrical on 2015-09-11
> **grahammechanical said:**
> Yesterday I was able to update to version 88 although I did notice that ubuntu-core was dated from a few days earlier. So, the update did not update the core from what I had previously downloaded. It was still booting from partition system-a. It will switch partitions when ubuntu-core is updated. Yes thanks.
> 
Browser has improved a lot. I now use it most of the time as my desktop browser. Tab browsing; Book Marks and Top Sites sites are now more easily accessed and we can copy URLs from one tab to another. But it does not give a line break in a Ubuntu Forum post. Same here.
> 
It is possible to re-size app windows by grabbing side and bottom edges at the middle and pulling. The new size is remembered when the app is next launched. On Ubuntu Personal that is. Yes .. thanks. Each time I resize I have to quit from panel and then restart but it remembers
where I left off.


Thansk for the reply. I think I know where I went wrong. I am using USB ver 3. 32GB now and it updated the core as you said and it is much more stable now. I think I know what happened also to my hdd installs. I cannot use the USB docker unless I am going to boot with it so I have to hot-swap hdd to SATA and install the image from SATA to SATA. Regards..

---

### Post by ventrical on 2015-09-11
When I try to install an app it asks for Ubuntu One sign on. I use my SSO account sign on. The apps appear to load bu tthey do not. Is there a conflict here. I was able to install apps when first experiementing with unity8+mir using SSO.  regards..

---

### Post by ventrical on 2015-09-11
I was able to  install Snappy Personal  and update to (89) with no problem using the SATA to SATA option using the ubuntu-disks utility (restore image). So now I can experiement with this image on multiple desktops/pcs by just swapping the drive in and out.

---

### Post by ventrical on 2015-09-11
Received some e-mails from Canonical software engineers and they suggest to install WebDm and that maybe the apps from the app store might install but they are not really focused on that atm it appears.

regards..

---

### Post by grahammechanical on 2015-09-11
I think that WebDm is the method used for installing Snaps on Snappy Ubuntu Core. That is the one without a desktop environment and I do not think that it has the Click apps that should be installable from the phone app store. The apps available through WebDm are more likely to be the snappy apps for the Internet of Things type devices. I think that snappy-core has its own app store.

It is my guess that click apps are not compatible (yet) with Snappy.

So, you were able to image restore personal_x86 to a hard disk? Were you able to create partitions out of the unused space? Or did it turn a 150 GB hard disk (for example) into a 10 GB disk? 

Regards.

---

### Post by QDR06VV9 on 2015-09-11
Just about to give A similar review.
Kind of losing Interest though, Because I feel their interest is [COLOR=#545454][FONT=arial] nonchalant [/FONT][/COLOR].  (Nothing personal meant by this)

---

### Post by ventrical on 2015-09-11
> **grahammechanical said:**
> I think that WebDm is the method used for installing Snaps on Snappy Ubuntu Core. That is the one without a desktop environment and I do not think that it has the Click apps that should be installable from the phone app store. The apps available through WebDm are more likely to be the snappy apps for the Internet of Things type devices. I think that snappy-core has its own app store.

It is my guess that click apps are not compatible (yet) with Snappy.

So, you were able to image restore personal_x86 to a hard disk? Were you able to create partitions out of the unused space? Or did it turn a 150 GB hard disk (for example) into a 10 GB disk? 

Regards.

Correct. Just found out that personal_x86.img will not install webdm (but software engineers from Canonical suggest I do). You are correct about IoT. It is a headless server at this point and it is their main focus, not snappy persona,l but they tell me to 'hang in there - we're working on it'.

2. Yes .. I was able to success install to hdd. I have 150GBs free space left over. I did this once already using a USB docker and it failed. maybe with new method of direct SATA to SATA I will be able to do a conventional desktop install (like ubuntu-desktop) and use GRuB. I can just imagine the outcome :)

Regards..

---

### Post by ventrical on 2015-09-11
> **runrickus said:**
> Just about to give A similar review.
Kind of losing Interest though, Because I feel their interest is [COLOR=#545454][FONT=arial] nonchalant [/FONT][/COLOR].  (Nothing personal meant by this)

The snappy image biscuit is highly experimental. it is a percursor to  snappy-personal-desktop and yes .. they are taking a sort of nonchalant attitude towards it because all the resources are being spent on the IoT and server... so i sort of feel hoodwinked about all this snappy-personal stuff  that we could play with .. so I guess I'll just keep hacking it :)

> 

reply from canonical software engineer
On 09/11/2015 03:25 PM, Dale ventrical wrote:
>  Yes .. I am using (89) as of todays update of snappy core. I am
> ubuntu.development.version  U+1 team admin at [www.ubuntuforums.org](www.ubuntuforums.org) 
> where we test development cycles  of all the various flavours of ubuntu.
> There are a few of us who are early adopters of convergence and I have
> tested unity8+ mir during the raring/saucy cycles. During testing on
> ubuntu-next we were able to install some apps through the GUI like the
> file folder manager and a few others but now with snappy the app store
> will just appear as if it is loading and then just crash from there.
 
Right, that's the behavior I experienced as well. Click and Snap weren't
really made to play nicely with each other, so it's not surprising that
installing clicks from the app store fails (since all that app _can_
install is clicks).
 
> There are a few of us who are particularily interested in getting the
> 'terminal app' to work.
 
Ha, that's the first thing I tried to install as well! Unfortunately no
terminal is packaged as a .snap just yet. In fact, no desktop-type apps
are-- right now Snappy is pretty focused on the IoT and server
environment, both of which are headless. Don't worry though, we're
working on it :) .
 
> During the convergence talk that was going on
> prior to wily development I assumed (as did others) that we would have a
> snappy-personal desktop to replace unity8 or work with unity8. So is it
> safe to assume that a stable working instance of snappy-personal for x86
> based desktop with slighty older hardware is a long way off and/or an
> unrealistic expectation?
 
It's definitely a realistic expectation, but yeah it's a ways off yet.
Snappy just isn't quite there yet, so us on the Personal team are trying
to poke and prod where we can. We're making progress, it's just a bit
slow since their priorities aren't the same as ours. Hang in there!
 
> I had pondered the possibility that we may be able to load up  a desktop
> manager like xmonad, razorqt .etc.. something where we can get under the
> hood, see whats going on , conduct test cases and have the ability of
> have a stable rolling release into convergence.
 
Not sure about this one. Do these work with Mir?
 
> Thanks for advice about installing webdm. Will give that a try.
 
Sure thing. Note that WebDM will allow for installing packages via a web
browser, and installing that also lets the Snappy Scope work so you can
install packages locally.
 
Some more info here if you're interested:
[https://rainveiltech.com/posts/snappy-scope-progress-update](https://rainveiltech.com/posts/snappy-scope-progress-update)
 
--Canonical Engineer


I omitted name.

Regards.

---

### Post by ventrical on 2015-09-12
> **grahammechanical said:**
> 

So, you were able to image restore personal_x86 to a hard disk? Were you able to create partitions out of the unused space? Or did it turn a 150 GB hard disk (for example) into a 10 GB disk? 

Regards.

All the partitions are there .. system-a, system-b etc..sda4,sda4 and the new MATE partition/install. Disks and Grub recognize all the partitons but the snappy-personal will not boot so there are major hurdles to overcome.. but since it is at the stage that it is in  I can then hack freely and try different things to see if I can get something brute forced on it. I am going to try a few more things. As I mentioned before .. I can get it running just fine on hdd now (non-kvm) so I think there may be some sort of tweak needed with grub or gparted that I can do.  It's a lot more convenient hacking snappy on a hard drive using a stable working flavour of ubuntu alongside it.

Regards..

---

### Post by ventrical on 2015-09-12
(90) and I am able to have it boot from hdd, The current solution is to have 2 hdds. 1 with ubuntu desktop flavours and one with personal_x86.img and then toggle boot sequence in BIOS.  Much more convenient. I can now use my snappy USB for Lenevo laptop which runs personal-snappy very fast.Also .. for the sake of adventure and to be industrious I am going to try and do an 'sudo update-grub' in snappy cli. hehehe :)  and see what happens there.regards..   edit - Ok.. I tried the  <sudo update-grub> and all the files are read only so it does nothing. I nice little failsafe built in so as no to corrupt the install inadvertently

---

### Post by ventrical on 2015-09-12
Bwwahahahahahah ... now I got the dreaded

grub>

prompt...  serves me right !!

Don't do

```

sudo update-grub

```

in snappy cli. It may work on USB but not hdd.

back to drawing board, pick myself up , and start all over again.

Regards..

---

### Post by grahammechanical on 2015-09-12
There is something I can add to this particular aspect of the discussion. Running update-grub from another Ubuntu install will detect Linux on my USB stick but it will not put a boot option in the grub menu. I think the folder layout is so different from standard that grub cannot do its stuff.

So, I agree that changing the boot sequence in the BIOS would be the way to boot Personal on a hard disk at the moment. And I would not install another OS on the same hard disk. It will surely over-write the grub for Personal. And if Personal breaks then re-flashing (image restore) the hard disk will wipe out any data in any other partition. Mind you Personal is not meant to break. It would not be the first time that the devs have been surprised at what users try to do.

I can see notebooks and laptops with Ubuntu Personal pre-installed and people complaining that 1) they cannot install an alternative desktop (no snap for it); 2) they installed another OS and now they have lost Personal; 3) they re-installed Personal (image restore) and lost the other OS; 4) nobody on Ubuntu Forums and Ask Ubuntu knows how to fix things; 5) all the knowledge collected by all the "gurus" is obsolete.

Regards.

---

### Post by ventrical on 2015-09-12
@graham

Thanks for the input. I did notice as I was watching the scroll up of verbose boot script of snappy personal that it noticed that there was "free space not used on disk- use GPT to use space' or something to this effect so perhaps there is a way to shim in a partition. I am going to look into that also, perhaps with gparted. You have made a very good point about pre-installed snappy IoT laptops and people wanting to put in traditional desktops. One could almost say if this be the future state of snappy framework that it could be likened somewhat to MicroSoft's secure boot. I'm sure that there will be a work-a-round soon :)

regards..

---

### Post by ventrical on 2015-09-12
@sudodus

I was able to install personal_x86.img to hdd using mkusb. (10.0.6 unstable) Twice as fast as the 'disks' restore option.

regards..

---

### Post by QDR06VV9 on 2015-09-12
> **ventrical said:**
> @sudodus

I was able to install personal_x86.img to hdd using mkusb. (10.0.6 unstable) Twice as fast as the 'disks' restore option.

regards..
Good to know Thanks Vent.
Oh and also Thanks for this
> [COLOR=#000000]*It's definitely a realistic expectation, but yeah it's a ways off yet.*[/COLOR]
[COLOR=#000000]*Snappy just isn't quite there yet, so us on the Personal team are trying*[/COLOR]
[COLOR=#000000]*to poke and prod where we can. We're making progress, it's just a bit*[/COLOR]
[COLOR=#000000]*slow since their priorities aren't the same as ours. Hang in there!*[/COLOR]

Guess I should curb my enthusiasm.:o
Regards

---

### Post by ventrical on 2015-09-12
> **runrickus said:**
> Good to know Thanks Vent.
Oh and also Thanks for this

Guess I should curb my enthusiasm.:o
Regards

That was right from the horses mouth. I still think however that  there could be some surprises to be enthused about... err.. ummm like for instance.. we now have arrow buttons on the browser scroll slider.:) which is rather awesome :) regards..

---

### Post by ventrical on 2015-09-21
version (99) core snappy personal now gives  a solid a reliable option to shutdown from GUI.

Yea! :)

regards..


n btw.. the browser is working really good ya know..

---

### Post by grahammechanical on 2015-10-07
Two days ago I downloaded the latest personal_x86.img file and used restore image to put on a 16 GB USB memory stick. I was expecting the operation to use only 10 GB of the space. I just now thought that I would use Gparted to expand the writable partition to take all the unallocated space on the memory stick but I did not need to. The writable partition had already been sized to the largest size possible. So, that is an improvement.

Regards

---

### Post by pixelro on 2015-10-07
> **ventrical said:**
> version (99) core snappy personal now gives  a solid a reliable option to shutdown from GUI.

Yea! :)

regards..


n btw.. the browser is working really good ya know..

hehe, nice :D

---

### Post by ventrical on 2015-10-08
> **pixelro said:**
> hehe, nice :D

Actually the newer images  ( I think we are at 108) have been very polemic. There are some bugs with mouse cursor on nVidia hardware. Seems like a unity-system-compositor problem (mir) - but then they will work on higher end Intel HD graphics hardware. The web browser has certainly digressed as one cannot grab the side bar slider with mouse. (also mouse wheel is useless) and this is very frustrating. The imgur web pages used to work with excellent graphics and animations and now just freeze up. Youtube is a no show as are other news site embedded videos so there is a long way to go.

 It appears that  just because we get a new version core number does not mean that snappy_personal has been improved. I actually think they are taking some backsteps with the intent of rearranging the framework of the core and there will probably  be more of this to come with snappy_personal DE.

Regards..

edit:

We are now at (112) snappy-core.

---

### Post by cariboo on 2015-10-08
I've been trying to run snappy personal on and off for the last couple of months, and all I ever get is the login screen, and that's it. I can't login or do anything else. I transferred the latest image to an external USB hard drive, and now on my system I get a black screen on my left monitor, and the login screen  on my right monitor. I can press Ctrl-Alt-Del and see the logout screen, but it is greyed out, pressing Ctrl-Alt-F1 brings me to a console where I can login, and shut down the system. I have to admit, that I didn't try Ctrl-Alt-F7 to login back into the graphical interface, but so far I'm not having any luck. Basic system information:

```
 inxi -b
System:    Host: skynet Kernel: 4.2.0-14-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: M5A97 R2.0 v: Rev 1.xx
           Bios: American Megatrends v: 2201 date: 12/10/2013
CPU:       Octa core AMD FX-8350 Eight-Core (-MCP-) speed/max: 1400/4000 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.2 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1360x768@60.02hz, 1680x1050@59.95hz
           GLX Renderer: GeForce 210/PCIe/SSE2
           GLX Version: 3.3.0 NVIDIA 340.93
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 1240.3GB (35.2% used)
Info:      Processes: 246 Uptime: 9 min Memory: 1206.6/15943.4MB
           Client: Shell (bash) inxi: 2.2.16 
```

If my resolutions looks a little weird, it's because I run my 22" monitor in portrait mode, which is rotated 90°, which makes for strange mouse action in console mode. :)

---

### Post by grahammechanical on 2015-10-08
Is it running on Nvidia 340.93 driver? I have the Nvidia GT220 which is simliar to your GT218 and I can get to a desktop. But I think that is with Nouveau.

---

### Post by cariboo on 2015-10-09
> **grahammechanical said:**
> Is it running on Nvidia 340.93 driver? I have the Nvidia GT220 which is simliar to your GT218 and I can get to a desktop. But I think that is with Nouveau.

I was running nouveau up until last week, I meant to try the personal image, but forgot and installed the proprietary driver. I may remove the Nvidia driver and give it a try tomorrow.

**Addendum:** this time I tried it booting from an external usb hard drive, and it still locked up at the login screen, :(

---

### Post by ventrical on 2015-10-09
> **cariboo said:**
> I was running nouveau up until last week, I meant to try the personal image, but forgot and installed the proprietary driver. I may remove the Nvidia driver and give it a try tomorrow.

**Addendum:** this time I tried it booting from an external usb hard drive, and it still locked up at the login screen, :(

As I was saying in this thread and another thread; the login screen was totally unaccessable because of mouse arrow jumpity behaviour on my nVidia machine. (I have same graphics card as you).

 I am not using a qemu (kvm) I am running the hard image on an hdd.  If you are trying to run snappy_personal from a raw image , remember, you cannot install nVidia drivers in a conventional way because apt-get no longer works and no more .deb packages. Are you using a kvm? If not , how are you installing nVidia drivers? (nouveau is default for core). Obviously snappy personal  (amd64) is very touchy about certain hardware.

Regards..

---

### Post by ventrical on 2015-10-09
> **grahammechanical said:**
> Is it running on Nvidia 340.93 driver? I have the Nvidia GT220 which is simliar to your GT218 and I can get to a desktop. But I think that is with Nouveau.

The default driver is nouveau. As I recall you could not use kvm and had to use raw image from USB. Just a reminder .. remember .. with snappy we can no longer install and uninstall nVidia driver . deb packages or any packages using apt-get install , the conventional ubuntu method.

```

sudo snappy install

```

only.

 Running snappy on a kvm that has nVidia proprietary installed on host is very edge atm.

---

### Post by ventrical on 2015-10-09
(112) Browser scroll slider is now working but you have to go into another tabe and press a few keys on the key board. The scroll slider will not work with mouse only when you open a new tabe but it remembers when you close browser and re-open it.

---

### Post by grahammechanical on 2015-10-09
As a follow up. After making that post I ran personal on USB stick and tried to run inxi -b and I was informed it is not installed. And of course, it cannot be installed as snappy personal does not use apt-get.

---

### Post by ventrical on 2015-10-09
> **grahammechanical said:**
> As a follow up. After making that post I ran personal on USB stick and tried to run inxi -b and I was informed it is not installed. And of course, it cannot be installed as snappy personal does not use apt-get.

Exactly. I even tried to finester a method of installing more traditional program - but to no avail at the moment. btw .. LXD containers lightvisor is in Snappy Scopes now but it does nothing. If you go to terminal and run 'top'  you can see some stuff under the hood there. I also had to learn for a third time that one cannot swap drives to other machines with any level of success. It appears that when a fresh load of snappy on a given machine from USB or hdd tends to 'burn-in' to that machine and when you try to swap out the drive and test on another machine it starts to lock up, does not remember browser tabs/settings .. etc.... and I am still getting 'not enough space' errors when I try to update the core .. now at (112) .. but I don't mind doing fresh installs.  Anyways .. the hdd has to be formatted to GPT with gparted I think to get rid of that error.  I am hoping when LXC containers comes on line we can slipstream a live image/iso or at least a fuctional DE so we can  be able to look under the hood of snappy and tinker with the cogs and wheels therein :)Regards..

---

### Post by grahammechanical on 2015-10-09
Well, today I bit the bullet. I have 2 hard drives and I used gparted (live session) to give sda a GPT partition table and then used Disks>Restore image to put personal-x86.img (version 111) on to sda. That also uses GPT.

It is a much quicker operation than doing it to USB stick. The loading process at the first boot into sda pauses very briefly with a message that not all the available space on the disk is being used and did I want to keep the present settings or use all available space. It defaults to using all the available space. So, I have a writeable partition that is 237.9 GB in size.

System Settings>Phone>Updates detects and downloads version 112. But when I click the install button I am invited to connect the phone to power and Cancel is the only option. So, it is back to sudo snappy update.

I thought I had messed up but three restarts proves that with version 112 there is a redesign but I think there are some unintended consequences.

1) The login screen does not have a background. It is black. The password panel is barely visible. What would we do without a white pointer?
2) The desktop does not have a background. Black again. So, the theme is messed up.
3) The launcher is black and the usual icons are missing.
4) There is only one app indicator - time. Click on that and we get a drop down menu with a slide-along set app indicators each with their own menus. So, we can still shutdown and other stuff.

I will see what version 113 will bring tomorrow. I am giving some thought to how to reinstall personal without loosing everything in the writeable partition. Not that I expect to have much stuff in there. What with being unable to install even the music app.

Regards.

P.S. Some months ago I got involved in a thread in either the Linux/Ubuntu discussion section or the Cafe on using LXC. The issues I found were 1) the database that is used to get OS images does not include development versions. 2) switching to the container did not come up with a desktop unless I used something called lxc-desktop. Then I could switch to cntrl+Alt+F8 and get a desktop. 3) the desktop was the bare minimum and not representative of a default install.

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)

[http://ubuntuforums.org/showthread.php?t=2271655](http://ubuntuforums.org/showthread.php?t=2271655)

I would very much like to use lxd/lxc to run development versions. Linux containers run on my system. Whereas, a VM would be impractical.

---

### Post by QDR06VV9 on 2015-10-09
> **grahammechanical said:**
> 
I will see what version 113 will bring tomorrow.

Regards.
Thank You you saved me some time and Bandwidth.
Regards

---

### Post by ventrical on 2015-10-09
> **grahammechanical said:**
> 
P.S. Some months ago I got involved in a thread in either the Linux/Ubuntu discussion section or the Cafe on using LXC. The issues I found were 1) the database that is used to get OS images does not include development versions. 2) switching to the container did not come up with a desktop unless I used something called lxc-desktop. Then I could switch to cntrl+Alt+F8 and get a desktop. 3) the desktop was the bare minimum and not representative of a default install.

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)

[http://ubuntuforums.org/showthread.php?t=2271655](http://ubuntuforums.org/showthread.php?t=2271655)

I would very much like to use lxd/lxc to run development versions. Linux containers run on my system. Whereas, a VM would be impractical.


  I had just noticed that after installing 'lex-dee' from the snappy scope that, after reboot, it is there and running in terminal  and top. However I think with snappy the process is a different animal because we are running on top of mir now.

 Also what is happening is that the snappy apps are installing but the icons are not coming on line. Whether they actually work on the desktop or not is an altogether other matter . I am thinking now that I might be a little too enthusiastic on trying to install a desktop image on snappy but I do not think it is a waste of time trying. Like I always say ... there are things to be discovered still when we try different methods  and approaches at testing. I am also going to try the GPT method that you have tired on my hdds.

Yes .. note on LXD .. once you get a *conventional*  image loaded in a container then 'lex-dee' should fundamentally pass control to that image - even if it is not set up for mir compositor. The caveat is that there is a little bit of terminal work to get the container set up and the repos loaded. It works in 15.04 and trusty but I have not tired it on snappy yet. I have been watching  some of the Canonical videos/symposiums on LXD/LXC and they are talking so fast (must be the java) :) that it is hard to understand what they are trying to say. btw .. LXD is build on top of LXC which is supposed to  much more easier to use that bare LXC. If this works on snappy then this might be the ways and means that they are going to deploy a workable desktop??? or will a snappy_personal desktop be available from a standard .iso?  Looks like XX is going to be , at least .... fun ! :)

Regards..

---

### Post by ventrical on 2015-10-09
> **grahammechanical said:**
> 
I thought I had messed up but three restarts proves that with version 112 there is a redesign but I think there are some unintended consequences.

1) The login screen does not have a background. It is black. The password panel is barely visible. What would we do without a white pointer?
2) The desktop does not have a background. Black again. So, the theme is messed up.
3) The launcher is black and the usual icons are missing.
4) There is only one app indicator - time. Click on that and we get a drop down menu with a slide-along set app indicators each with their own menus. So, we can still shutdown and other stuff.

.

Exactly the same here.  I am going to take this newly formatted hdd (with gpt - thanks for pointers) and swap it to one of my Intel based systems because it is currrently running on nVida 210 .. same as your's I think.

*edit*..  yep .. on Intel based graphics hardware also. It actually looks more like a phone/tablet now but with no gizzmos showing.
Regards..

---

### Post by grahammechanical on 2015-10-09
> [COLOR=#000000]If this works on snappy then this might be the ways and means that they are going to deploy a workable desktop??? [/COLOR]

The word is that Xserver apps like Libreoffice will run on xmir in a containter. I can only guess it will be LinuX Containers. Make use of existing development work. As an aside, OTA 7 for Ubuntu Phone is said to have some more convergence stuff. Should also see that in Personal at some point.

---

### Post by ventrical on 2015-10-09
Thanks graham.

Here is a link on LXD [https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/)  however , it does not currently work with snappy_personal but it can be loaded in snappy_core so.. since snappy_personal is so tight atm I am going to work on a pure snappy-core install from bare metal and as you will notice in the link you can execute the lxc and lxd  commands from the terminal.

Mind you , I can install LXD from Snappy Scopes but it will do nothing at all in cli.

Regards..

---

### Post by ventrical on 2015-10-09
> **grahammechanical said:**
> 
P.S. Some months ago I got involved in a thread in either the Linux/Ubuntu discussion section or the Cafe on using LXC. The issues I found were 1) the database that is used to get OS images does not include development versions. 2) switching to the container did not come up with a desktop unless I used something called lxc-desktop. Then I could switch to cntrl+Alt+F8 and get a desktop. 3) the desktop was the bare minimum and not representative of a default install.

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)



I would very much like to use lxd/lxc to run development versions. Linux  containers run on my system. Whereas, a VM would be  impractical.[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=2271655&p=13256442#post13256442](http://ubuntuforums.org/showthread.php?t=2271655&p=13256442#post13256442)

---

### Post by grahammechanical on 2015-10-10
I have been experimenting. I have 2 hard drives. On sdb I have 2 installs of Wily desktop. On sda I have Ubuntu Personal version 112.

_Experiment #1_

Personal version 112 was not upgrading to version 113 because it included an upgrade from kernel 4.2.0-14 to kernel 4.2.0-15. The update process gives an out of space on disk error. So, I thought that I would resize either or both of the boot partitions - sda1 (bios boot) sda2 (efi boot). I have a BIOS boot system and I could not resize the BIOS boot partition (sda1) even with the bios_grub flag removed. And resizing sda2 (boot, esp) still did not get version 112 upgrading to version 113. = failure.

_Experiment #2_

Create another partition (sda6) and install Wily into it with Grub installing into sda6. This was sucessful. It does not over-write the personal grub and once update-grub has been run from desktop Ubuntu on sdb I can load into wily on sd6.

_Experiment #3_

Install personal_x86.img version 113 on sda. I already know the result of this experiment before I run it. It will wipe out the wily install in sda6. But it does show the possibilities of using some of the space on sda for temporary/disposible installs such as ISO testing without messing up the loading of personal.

Regards.

---

### Post by ventrical on 2015-10-10
Mind Boggling.

An install I did yesterday that installed (112) snappy_personal came up with no background theme, empty icons on the unty8 panel.. etc...(just like grahammechanicals). I shut that machine down last night. Now hard booted up and I have background theme etc. this has happened a few times before. It's like parts of the frame work sleep and then all of a sudden wake up during a hard reboot 12 or 24 hours later.

Regards..

---

### Post by ventrical on 2015-10-10
> **grahammechanical said:**
> I have been experimenting. I have 2 hard drives. On sdb I have 2 installs of Wily desktop. On sda I have Ubuntu Personal version 112.

_Experiment #1_

Personal version 112 was not upgrading to version 113 because it included an upgrade from kernel 4.2.0-14 to kernel 4.2.0-15. The update process gives an out of space on disk error. So, I thought that I would resize either or both of the boot partitions - sda1 (bios boot) sda2 (efi boot). I have a BIOS boot system and I could not resize the BIOS boot partition (sda1) even with the bios_grub flag removed. And resizing sda2 (boot, esp) still did not get version 112 upgrading to version 113. = failure.


Regards.


I have both BIOS and efi installs on different machines. Tried the gpt fix but I am getting the same as you.  The update process worked early on but now it is just not working.  So it is obvious that the devs are developing snappy_personal through high-grade kvms. I have the space , speed and  resources but I have no interest  in testing on VMs. Containers? .. using LXD? .. yes.. but not VMs. That method does not give accurate field test results IMO.

Regards..

---

### Post by grahammechanical on 2015-10-11
I have done another experiment. I am looking for a way to re-install personal without losing the data in the writeable partition. Version 114 has another kernel upgrade (4.2.0-16). So this is an opportunity. I have

personal version 113 on hard disk sda and personal version 114 on USB stick sdc. I use live session gparted to copy partitions sdc2; sdc3; sdc4 over partitions sda2; sda3; sda4. I could not copy sdc1 (bios_grub) as the copy/paste options were grayed out even though the partition was unmounted. Result = grub rescue.

Need to do some more thinking. Oh, by the way personal has an emergency mode. I hit it today after installing version 114 to USB stick and loading. It has these options.

Type
 journalctl -xb  to view system logs
systemctl reboot to reboot
systemctl default or ^D to try again to boot default mode.

The reboot fixed whatever was wrong. The system logs mystified me, as ever.

Regards.

---

### Post by ventrical on 2015-10-11
I noticed this while flashing (114). The large freespace area is no longer and the writeable space area has been honed down to 1.1GB. maybe a fix in the workings?

ps .. dont' mind bad sectors - just working with surplus stuff :)
Regards..

---

### Post by grahammechanical on 2015-10-11
Have you booted that new version yet? The first boot will pause very briefly to offer the option to keep the present partition sizes or use up all the available space. It is not easy to see this message among all the system messages and it quickly defaults to use all available space. This is version 114 installed earlier.

---

### Post by ventrical on 2015-10-12
> **grahammechanical said:**
> Have you booted that new version yet? The first boot will pause very briefly to offer the option to keep the present partition sizes or use up all the available space. It is not easy to see this message among all the system messages and it quickly defaults to use all available space. This is version 114 installed earlier.

Yes .. I got that message .. and it quickly rolls by . But I am not confident that it will let us upgrade to (115) without that error. Whether BIOS or efi boot, it has so far no been able to load the kernel into Grub after updating.

  The browser works pretty well. It is somewhat functional unity8 desktop. Lot's of improvements. I am assuming we will see rapid development come the next cycle  of XX for the amd64 desktop environment. It's good to be an early adopter .. even since back testing with unity8 and first  mentions of mir.

Regards..

---

### Post by ventrical on 2015-10-12
This is the main error context code that is received when trying to update snappy_personal:

```

Oct 10 21:20:34 localhost snappy[2627]: main.go:57: DEBUG: [snappy update] failed: Failed to run command '/bin/cp /writable/cache/assets/vmlinuz-4.2.0-15-generic.efi.signed /boot/grub/b': /bin/cp: error writing &#8216;/boot/grub/b/vmlinuz-4.2.0-15-generic.efi.signed&#8217;: No space left on device#012/bin/cp: failed to extend &#8216;/boot/grub/b/vmlinuz-4.2.0-15-generic.efi.signed&#8217;: No space left on device#012 (exit status 1)

```

Can be found in:

writable/system-data/var/log/syslog

edit:

 I have posted this problem on snappy-dev mailing list.

---

### Post by ventrical on 2015-10-19
I got a reply from a developer off the mailing list and he tells me that he is not sure that snappy_personal is really being looked at and that the snappy_personal core is a different core than snappy_core and that it needs lots of tweaking , hence, looks like a fix is not in the works for the <out of space> error when updating to a new version any time soon.

 It's frustrating because it was working earlier on in the cycle.

Regards..

---

### Post by grahammechanical on 2015-10-19
That statement is certainly confusing. Of course snappy_personal core is different from snappy_core. One has a DE and a UI the other does not. Also, I think that snappy_core is built on 15.04 code. Therefore, it will not have a problem with a kernel upgrade as personal does due to it being built on Wily code.

I was listening again to Mark's keynote speech from the last UOS. He definitely said that there will be this year a Ubuntu converged device on the market and it will be a phone and it will give a desktop experience, "Desktop in your pocket" it what he called it. And then there is this comment in a blog by Ollie Reis:

> Ubuntu Personal will provide all the benefits of snappy apps to users of  devices with built-in and attached displays. Considering that snappy  systems were born out of our experience with mobile devices, _Ubuntu  Personal is the next evolution of the phone code base on our path to  reach code convergence_.

And then there is this about Ubuntu Touch:

> Ubuntu Touch is a *code base* built on top of Ubuntu, that is used on our currently shipping devices, powered by Ubuntu. *&#8220;Touch&#8221; *is the project name but it has taken on a life of its own when the project became more successful. The official name is **Ubuntu phone**.

 
It has implemented required key features for mobile operating systems  such as system image updates, mobile & converged apps and an app  store. _The Ubuntu phone code base will converge with the Ubuntu Personal  code base_.



Personal has a snappy core with an X86 kernel, Mir, LightDM, Unity 8. What it does not have is a snap app store with converged apps and desktop apps. They way things look, Santa can forget about getting mince pies from me. No sherry for him either. :)

Regards.

---

### Post by ventrical on 2015-10-20
The person I got the reply from is not a snappy_personal dev. He just more or less chucked off an opinion on the matter.  I think it is all still experimental and the snappy sets are being honed more for Beagle Bone black and rasperryPi IoT devices so the resources are going there.  Gotta keep those drones a rolling :)

Yep .. and phones and devices .. but I still think that ubuntu personal can be hacked so that we can run unity8  as a desktop with the option of using debian package based desktop components in LXD containers.  I have had some success with LXD  on snappy_core but not on personal but I think we will in the furture - hence most likely we should be able to run pocket desktop in a container. High hopes and an impossible Christmas Wish list for Santa. The general message I am getting is " be patient .. it's being worked on" but I think the unity8 project is getting to be a thorn in the side of Canonical unless it is ultimately run in a VNC so then what's the sense in having a lightervisor?

Regards..

---

### Post by grahammechanical on 2015-10-21
It is my understanding that apps like Libreoffice will be run on XMir in LXC containers as a way of confining them and not break the security model that is present on Ubuntu Phone. There are videos of lots of experimental code which is yet to be merged into the core code. At least Personal is being built on Wily code and I assume it will continue to receive code updates when development moves on to XX code name. So, I still have hopes of seeing Personal morph into something usable.

Regards.

---

### Post by ventrical on 2015-10-21
> **grahammechanical said:**
>  So, I still have hopes of seeing Personal morph into something usable.

Regards.

 Yeah. I am optimistic about it all, refuse to curb my enthusiasm and will go as far as to say that the writing is on the wall in respect to some new tools 'n things and a usable snappy_amd64 DE and I think there may be a way to get around having to use LXD containers on a standard i368 based desktop.

Regards..

---

### Post by ventrical on 2015-10-21
@graham from snappy list

> 
hi,
Am Mittwoch, den 21.10.2015, 10:20 -0400 schrieb Darren Landoll:
> Is there currently a way to boot a Snappy image in some sort of
> "read-only" mode where it only runs from a ramdisk (or something
> similar to that)? I'm looking at a scenario where I boot an x86 based
> PC using a USB stick to run an installer that installs a Snappy image
> to the HDD.
> 
an installer (recovery mode) is currently being worked on, but still a
bit early to talk about in detail ... (it is on the delivery list for
16.04)
 
ciao
     oli
 
 
-- 
snappy-devel mailing list
snappy-devel@lists.ubuntu.com



---

### Post by grahammechanical on 2015-10-21
Its Ubuntu Jim, but not as we know it. 

The installer will need to create 4 partitions. We know that it is now easier for the user to increase the size of the writeable partition after install. Just create unallocated space after the writeable partition and restart and the writeable partition will be resized to take up the extra space.

That kernel upgrade issue will need to be solved. It is stopping kernel upgrades. I have yet to find where they put the kernel. It should be its own snap with the OS being another snap running on top. I am guessing that the kernel is in the boot partition. Which nautilus cannot access. I am wondering if increasing the size of the boot partition will solve the problem. 

It does not have a boot/grub/grub.cfg. Which is why running update-grub from another install is unable to put personal as a menu option in its grub menu. It cannot dual boot. Even if grub.cfg was modified an OS update would overwrite it.

The layout of folders and configuration files looks familiar but also different. Many of the usual folders are unused and new folders added. It is a hybrid layout at the moment which may be cleaned up once personal becomes road worthy.

Yes, this is Ubuntu from a parallel universe.

Regards.

---

### Post by ventrical on 2015-10-21
> **grahammechanical said:**
> Its Ubuntu Jim, but not as we know it. 

I guess you're right Bones.  It certainly doesn't seem to be the real McCoy.


> 
The installer will need to create 4 partitions. We know that it is now easier for the user to increase the size of the writeable partition after install. Just create unallocated space after the writeable partition and restart and the writeable partition will be resized to take up the extra space. 

That's an interesting declaration that I have seen work in action.

> 
That kernel upgrade issue will need to be solved. It is stopping kernel upgrades. I have yet to find where they put the kernel. It should be its own snap with the OS being another snap running on top. I am guessing that the kernel is in the boot partition. Which nautilus cannot access. I am wondering if increasing the size of the boot partition will solve the problem. 

I tried that here .. but with no success.

> 
It does not have a boot/grub/grub.cfg. Which is why running update-grub from another install is unable to put personal as a menu option in its grub menu. It cannot dual boot. Even if grub.cfg was modified an OS update would overwrite it.

The layout of folders and configuration files looks familiar but also different. Many of the usual folders are unused and new folders added. It is a hybrid layout at the moment which may be cleaned up once personal becomes road worthy.

Yes, this is Ubuntu from a parallel universe.

Regards.

It is a very cryptic layout. Almost as if it is bending the space/time continuum atm . I'll get Scotty  to build a matter- antimatter aperature hyferactor field  and try to stabilize it. I think it is cryptic also because , remember, the snappy repos are not using apt-get as we know it so, even though we are getting a FOSS OS it may be Canonical's right to guard the possible proprietary updating method.  I think this is actually the fly in the ointment. 

Regards..

---

### Post by ventrical on 2015-10-23
Well... I was just experimenting with one of my (what I thought was busted installs) of snappy_personal that had kept giving me grub errors when I tried to update the core on an hdd install: ```
sudo snappy update 
``` and it installed the 121 core from the 114 core (which was where I left off). It is now *very* snappy in the sense of speed on the browser. I look at this as progress. I am writing this message from the browser now. I can't say if it was a fix or etc.. but there might be a slim possibility that the grub error that was displaying warnings could have been an f/p and that perhaps a reboot or a retry of upgrading the snappy core may have been in order (perhaps being some breakage along the *stop* ..Ok .. what happened was as I was typing this message on one my nVidia graphics setups the screen froze up.. so I swapped out the hdd to a Intel Xeon based graphics tower and I was able to use the auto-saved tab to bring up that which I have already written.There are differences between nVida graphics and Intel graphics. Intell graphics will not allow for grab of scroll slider bar in browser where as nVidia will.. so there are certainly driver/mir (unity-system-compositor) issues.  I am going to publish this now and explore whats up with anything new. Certainly progress with updating core - but who knows how long that will last.

Regards..

---

### Post by mikodo on 2015-10-23
Hey folks.

From your experience in working and following Ubuntu-next over longer periods, do you expect there is the possibility that MIR, Unity8 and Snappy-core with snaps will be on the Ubuntu 16.04 .iso LTS? Parts?

Or, am I asking you to star-gaze, for an answer? ... ;-)

Regards, seems to be the valediction in this thread.

Addendum: I shouldn't have asked that here. I apologize.

---

### Post by ventrical on 2015-10-23
@mikodo

unity-system-compositor (mir) is par for the course with snappy_personal while running unity8. I believe there will be options to jockey out to xorg, xmir and etc  and snappy-core using LXD containers  will most likely use u-s-c or xmir if unity8 is running. But we were able to run unity-system-compositor  though and ran unity7 /unity-system-compositor on Vivid and Wily which is an option.

Regards..

---

### Post by mikodo on 2015-10-23
Thanks.

---

### Post by grahammechanical on 2015-10-23
What we know for certainty is that 16.04 will be a traditional Ubuntu distribution. The Ubuntu archives with debian packages will continue to exist and be renewed because all Ubuntu versions are built from those debian packages.

There is talk of a 16.04 login option for using Mir+Unity 8. I tried this during wily development and never got it to log in. So, I am not interested in that any more.

In my opinion, anything else is the vision of Canonical administrators and engineers. The vision is for Ubuntu Phone to be based upon Ubuntu snappy core as Ubuntu personal is. My prediction for the next year is that there will be ISO images of traditional Ubuntu; Pre-install images of Ubuntu Phone for OEM phones & tablets; Pre-install images of Ubuntu Personal for OEM laptop,notebooks & desktops.

A lot of this will be available for general download and use but I will be surprised if there is an ISO image of Ubuntu Personal. I will be even more surprised if there is not an outpouring of complaint by those who install it because Ubuntu Personal will prove to be more restrictive and limited in options than Ubuntu traditional is.

Now, I must reconnect to the Astral plane. Otherwise known as having a snooze. :)

Regards.

---

### Post by ventrical on 2015-10-23
> **grahammechanical said:**
> What we know for certainty is that 16.04 will be a traditional Ubuntu distribution. The Ubuntu archives with debian packages will continue to exist and be renewed because all Ubuntu versions are built from those debian packages.

There is talk of a 16.04 login option for using Mir+Unity 8. I tried this during wily development and never got it to log in. So, I am not interested in that any more.

It just quit on me half way through the cycle. Those DEs would just not load up from greeter. 

> 
In my opinion, anything else is the vision of Canonical administrators and engineers. The vision is for Ubuntu Phone to be based upon Ubuntu snappy core as Ubuntu personal is. My prediction for the next year is that there will be ISO images of traditional Ubuntu; Pre-install images of Ubuntu Phone for OEM phones & tablets; Pre-install images of Ubuntu Personal for OEM laptop,notebooks & desktops.

A lot of this will be available for general download and use but I will be surprised if there is an ISO image of Ubuntu Personal. I will be even more surprised if there is not an outpouring of complaint by those who install it because Ubuntu Personal will prove to be more restrictive and limited in options than Ubuntu traditional is.

Now, I must reconnect to the Astral plane. Otherwise known as having a snooze. :)

Regards.

It would be a real disappointment to not have a Snappy Personal .ISO but I am learning now to adapt to LXD containers with Snappy Core which , of course, I can run any linux system in the lightervisor.

Snooze well....

:)

Regards..

---

### Post by mikodo on 2015-10-23
Thank you!

I guess for we normal beings living in the third dimension, will have documentation available for use when, it is time for us.

I mean casual users whom, have to work hard to use the presently accepted norms. Not, the people in this thread except, for myself.

Regards.

---

### Post by grahammechanical on 2015-10-23
You do not have to be crazy to work here, but it helps.

---

### Post by ventrical on 2015-10-24
> **mikodo said:**
> Thank you!

I guess for we normal beings living in the third dimension, will have documentation available for use when, it is time for us.

I mean casual users whom, have to work hard to use the presently accepted norms. Not, the people in this thread except, for myself.

Regards.

We have the U+1 development tester's wiki [https://wiki.ubuntu.com/U+1](https://wiki.ubuntu.com/U+1) which several volunteers have partaken in to build a  library [https://wiki.ubuntu.com/U+1/library](https://wiki.ubuntu.com/U+1/library) and other sources of educational reference such as Instructional Development [https://wiki.ubuntu.com/U+1/InstructionalDevelopment](https://wiki.ubuntu.com/U+1/InstructionalDevelopment) and the Ubuntu Forums Portal [https://wiki.ubuntu.com/U+1/reports](https://wiki.ubuntu.com/U+1/reports) where certain aspects of development testing are a little more chronicled and of course the testers wiki itself [https://wiki.ubuntu.com/U+1/tester-wiki](https://wiki.ubuntu.com/U+1/tester-wiki) where a minimal of certain helps are offered.

  I am still hopeful that the Instructional Development section will grow and develop into somewhat of a tutorial centre sidekick where persons who are migrating to Ubuntu can have a snap understanding and smoother transition into the Ubuntu set, FOSS and linux overall. Canonical has hundreds of interactive areas that are dedicated  to instruction but it is somewhat scattered - and so here we try to collect that which is pertinent and hone it in.  The wiki is not an actual cloud in the cloud computing sense but more like a superstorm , a collection of clouds so to speak, something that I like to call 'storm computing' where information can come in buckets rather than in drops  for those so inclined and yet easy to understand :) Some of the most gifted and talented triagers, bug-fixers, hackers, beta-testers and coders reside here amongst the forums and we all contribute the best  of the sum of our parts no matter how small or how large. Believe it or not - proof reading - is probably one of the most underrated tasks as 90% of the time most serious bugs originate from a missed or overlooked typo. :)

You are welcome to join the team (if you have not already) as I could use some help in Instructional Development area. Even some ideas or suggestions.

-Well now .. I am entirely off topic once again :)

Regards..

---

### Post by ventrical on 2015-10-30
Checking daily mail:

Mark wrote:

                                                                              [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]                
                [h=2]rolling edge channel now re-based to xenial[/h]                      
                                                                                                                                                                                                                                                  [    Actions        [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]      ]("https://blu185.mail.live.com/ol/#")                                            
                                  
              
                                                                                                       Mark Shuttleworth                                                                       
                                                                  
                                                                  [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]                
                                                                                          28/10/2015                                                      
                                                                                                          [      [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]    ]("https://blu185.mail.live.com/ol/#")                     
                            
                                                                  [                    Groups                  ]("https://blu185.mail.live.com/ol/#")                                              
            
                                                                                                              To:  Oliver Grawert, [email]snappy-devel@lists.ubuntu[/email]









                                      The sprint to 16.04 LTS begins!
 
 On 29/10/15 04:21, Oliver Grawert wrote:
 
  hi,

with the opening of xenial I invested a bit of time today to move the
rolling edge builds over to it, all future rolling images will be xenial
based from now on ...

ciao
   oli

------------------------end quotes

However .. if you have had a current snappy_personal image  build you have been nursing you will notice that you will not be able to update snappy core?

Did I miss something here?

Regards..

---

### Post by ventrical on 2015-10-30
These apples :

```

ventrical@ventrical-luntiy-betatest:~$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
[sudo] password for ventrical: 
Determining oem configuration
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 192.45 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 230.13 KB/s 
Done
Fetching information from server...
Downloading and setting up...
86.60 MB / 86.60 MB [====================================] 100.00 % 177.09 KB/s 
90.89 MB / 464.91 MB [====>_________________________] 19.55 % 180.05 KB/s 35m26serror while executing external command kpartx -ds personal_x86.img: device-mapper: remove ioctl on loop0p5 failed: Device or resource busy
loop deleted : /dev/loop0


```


try again !

---

### Post by ventrical on 2015-10-30
Uh .. (121) still . Wonder what happened or if we need to enter new code.

```

ventrical@ventrical-luntiy-betatest:~$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
Giving up, the desired target output file "personal_x86.img" already exists
ventrical@ventrical-luntiy-betatest:~$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
Determining oem configuration
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 190.58 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 232.44 KB/s 
Done
Fetching information from server...
Downloading and setting up...
464.91 MB / 464.91 MB [==================================] 100.00 % 415.26 KB/s 
Installing generic-amd64
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 197.65 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 227.20 KB/s 
Done
New image complete
Summary:
 Output: personal_x86.img
 Architecture: amd64
 Channel: edge
 Version: 121
ventrical@ventrical-luntiy-betatest:~$ 

```

---

### Post by grahammechanical on 2015-10-30
According to system-image.ubuntu.com the last build was on 17-Oct-2015. So, no updates. But there is a session about Ubuntu Personal at the Ubuntu Online summit next week.

It is 15.00 UTC Wednesday 4th November. Supporting legacy applications on Ubuntu Personal. The session that starts at 14.00 UTC on the same day is also interesting. Developer Desktop Plane 16.04.

I am hoping that the delay in building new system images for Ubuntu Personal is because of plans being put in place for a Ubuntu ISO Image. An ISO image would require QA build tests and test cases and links to report bugs. I cannot see a place holder for it on iso.qa but there is a session on Tuesday at 1600 UTC LTS desktop QA plan ans it is in the Convergence category.

Regards.

---

### Post by kagashe on 2015-10-30
```
$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
[sudo] password for user: 
Determining oem configuration
Starting download of generic-amd64
41.70 KB / 41.70 KB [=====================================] 100.00 % 60.11 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [=====================================] 100.00 % 59.24 KB/s 
Done
Fetching information from server...
Downloading and setting up...
86.60 MB / 86.60 MB [=====================================] 100.00 % 29.51 KB/s 
464.91 MB / 464.91 MB [===================================] 100.00 % 48.49 KB/s 
Installing generic-amd64
Starting download of generic-amd64
41.70 KB / 41.70 KB [=====================================] 100.00 % 59.13 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [=====================================] 100.00 % 58.59 KB/s 
Done
New image complete
Summary:
 Output: personal_x86.img
 Architecture: amd64
 Channel: edge
 Version: 121
user@Lenovo-G50-45:~$ kvm -m 2048 -vga qxl personal_x86.img
WARNING: Image format was not specified for 'personal_x86.img' and probing guessed raw.
         Automatically detecting the format is dangerous for raw images, write operations on block 0 will be restricted.
         Specify the 'raw' format explicitly to remove the restrictions.
qemu-system-x86_64: cannot set up guest memory 'pc.ram': Cannot allocate memory
Aborted (core dumped)
user@Lenovo-G50-45:~$ 

```
My laptop has only 2 GB RAM changed 2048 to 1024 but I got only login screen
I copied the img file through dd command on 16 GB USB stick and could boot from it. Posting this from live session of Ubuntu Snappy Personal.
Kamalakar

---

### Post by ventrical on 2015-10-31
> **kagashe said:**
> ```
$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
[sudo] password for user: 
Determining oem configuration
Starting download of generic-amd64
41.70 KB / 41.70 KB [=====================================] 100.00 % 60.11 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [=====================================] 100.00 % 59.24 KB/s 
Done
Fetching information from server...
Downloading and setting up...
86.60 MB / 86.60 MB [=====================================] 100.00 % 29.51 KB/s 
464.91 MB / 464.91 MB [===================================] 100.00 % 48.49 KB/s 
Installing generic-amd64
Starting download of generic-amd64
41.70 KB / 41.70 KB [=====================================] 100.00 % 59.13 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [=====================================] 100.00 % 58.59 KB/s 
Done
New image complete
Summary:
 Output: personal_x86.img
 Architecture: amd64
 Channel: edge
 Version: 121
user@Lenovo-G50-45:~$ kvm -m 2048 -vga qxl personal_x86.img
WARNING: Image format was not specified for 'personal_x86.img' and probing guessed raw.
         Automatically detecting the format is dangerous for raw images, write operations on block 0 will be restricted.
         Specify the 'raw' format explicitly to remove the restrictions.
qemu-system-x86_64: cannot set up guest memory 'pc.ram': Cannot allocate memory
Aborted (core dumped)
user@Lenovo-G50-45:~$ 

```
My laptop has only 2 GB RAM changed 2048 to 1024 but I got only login screen
I copied the img file through dd command on 16 GB USB stick and could boot from it. Posting this from live session of Ubuntu Snappy Personal.
Kamalakar

Thanks Kam,

 I have had it running for some time now  but my most recent message was eluding to an e-mail from Mark to Oli about the  edge channel being changed from wily to xenial and that an existing install will not update the snappt_core .. but I think that grahammechanical has asnwered it.

Thanks and regards..

---

### Post by ventrical on 2015-10-31
> **grahammechanical said:**
> According to system-image.ubuntu.com the last build was on 17-Oct-2015. So, no updates. But there is a session about Ubuntu Personal at the Ubuntu Online summit next week.

It is 15.00 UTC Wednesday 4th November. Supporting legacy applications on Ubuntu Personal. The session that starts at 14.00 UTC on the same day is also interesting. Developer Desktop Plane 16.04.

I am hoping that the delay in building new system images for Ubuntu Personal is because of plans being put in place for a Ubuntu ISO Image. An ISO image would require QA build tests and test cases and links to report bugs. I cannot see a place holder for it on iso.qa but there is a session on Tuesday at 1600 UTC LTS desktop QA plan ans it is in the Convergence category.

Regards.

Nicely put. The most logical assumption.

Regards..

---

### Post by ventrical on 2015-11-26
Just as a bump! There is still no activity with this command:

```

ventrical@ventrical-luntiy-betatest:~$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
[sudo] password for ventrical: 
Determining oem configuration
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 169.18 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 210.54 KB/s 
Done
Fetching information from server...
Downloading and setting up...
Installing generic-amd64
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 169.29 KB/s 
Done
35.77 KB / 41.70 KB [==============================>______] 85.77 % 135.09 KB/s Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 214.74 KB/s 
Done
New image complete
Summary:
 Output: personal_x86.img
 Architecture: amd64
 Channel: edge
 Version: 121
ventrical@ventrical-luntiy-betatest:~$ 

```

It does not actually download the image but you will see it in /home.

Regards..

---

### Post by grahammechanical on 2015-11-26
I have Snappy personal installed on sda and the other week I put another install of Xenial in sdb but forgot to change the default location of Grub. So, the Grub in sda that loaded personal got over-written. So, early on in the week I installed personal image 121 on sda again and ran sudo snappy update, but there was nothing to update. So, I can confirm, still no movement of this front.

---

### Post by ventrical on 2015-11-26
> **grahammechanical said:**
> I have Snappy personal installed on sda and the other week I put another install of Xenial in sdb but forgot to change the default location of Grub. So, the Grub in sda that loaded personal got over-written. So, early on in the week I installed personal image 121 on sda again and ran sudo snappy update, but there was nothing to update. So, I can confirm, still no movement of this front.

Thanks for confirming this. I wrote to Oliver G. and asked him where we are going with this because I want to keep testing it. I want to be ready for any surprises.  I 'll keep all apprised if I hear anything from Ollie.

Regards..

> 
                                                                              [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]                
                **Snappy personal image**

                      
                                                                                                                                                                                                                                                  [    Actions        [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]      ]("https://blu185.mail.live.com/ol/#")                                            
                                  
              
                                                                                                         ventrical
                                                                  
                                                                                                          8:35 PM                                                      
                                                                                                          [      [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]    ]("https://blu185.mail.live.com/ol/#")                     
                            
                                                                  [                    Groups                  ]("https://blu185.mail.live.com/ol/#")                                              
            
                                                                                                              To:  [EMAIL="snappy-devel@lists.ubuntu.com"]snappy-devel@lists.ubuntu.com[/EMAIL]                                                    
                                              
I recently attempted to continue my testing of (snappy) personal_x86.img using the command in terminal:

sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode

and it emulates it is downloading :
Version: 121

but it actually only downloads  the icon package.

When will we be able to test (snappy) personal_x86.img again?


Regards..
ventrical - ubuntu development version testing


---

### Post by ventrical on 2015-12-18
@grahamechanical

I am not sure what to make of this from snappy-dev-mailing-list

> 
On Tue, Nov 24, 2015 at 02:30:04PM +0100, Michael Vogt wrote:
 > On Wed, Nov 11, 2015 at 04:26:13PM -0200, Gustavo Niemeyer wrote:
 > > This is (perhaps) the last major change which I'd like to raise attention
 > > to, and it's perhaps one of the most disruptive and exciting ones too.
 > >
 > > In the coming weeks we'll be landing relevant changes related to how the
 > > ubuntu core image itself is organized, and also to the packaged format of
 > > snaps. The new format is not backwards compatible, but there are relevant
 > > benefits that will become apparent as that work lands and unrolls. Michael
 > > Vogt is leading these changes for quite some time now, and we're expecting
 > > them to become visible in the following weeks.
 >
 > We made some good progress here in the last few weeks and there is an
 > experimental "all-snap" image available at:
 [..]
 
 The all-snap image [1] has reached a new milestone, I pushed a new amd64
 image to:
 
   [https://people.canonical.com/~mvo/all-snaps/]("https://people.canonical.com/%7Emvo/all-snaps/")
 
 that boot directly from the squashfs kernel-snap using the grub loop
 mount support (no need to extract the kernel anymore). It also uses a
 squashfs based gadget snap and follows the snap package names
 discussed during the most recent snappy sprint.
 
 Here is what it looks like on amd64:
 
 """
 ubuntu@localhost:~$ snappy list
 Name               Date       Version   Developer
 canonical-linux-pc 2015-12-14 4.3.0-2-1 canonical
 ubuntu-core        2015-12-17 16.04.0-2 canonical
 canonical-pc       2015-12-17 2.1       canonical
 """
 
 Note that when looking at /boot/grub there is no unpacked
 kernel/initramfs anymore:
 
 """
 ubuntu@localhost:~$ ls /boot/grub/
 fonts  grub.cfg  grubenv  i386-pc  install.yaml  locale  x86_64-efi
 """
 
 I also pushed a new rpi2 all-snap image which looks like this:
 """
 ubuntu@localhost:~$ snappy list
 Name                   Date       Version      Developer
 canonical-linux-raspi2 2015-12-17 4.2.0-1014-2 canonical
 ubuntu-core-armhf      2015-12-17 16.04.0-2    canonical
 canonical-pi2          2015-12-17 2.2          canonical
 """
 There we do have to unpack the kernel/initrd as uboot does not support
 squashfs4.
 
 Updates from the store should work on both images (as long as we keep
 the snap package names :) But be warned that this is all pretty new
 stuff.
 
 Enjoy the new images!


Certainly they are not talking about snappy personal are they?

Regards..

---

### Post by grahammechanical on 2015-12-18
I am not sure. I will attempt to try it out. I noticed something the other day. An update brought in something called ubuntu-snappy-cli. I am wondering if that package has something to do with the intention to have snap apps installed & working on Unity 7

[http://packages.ubuntu.com/search?keywords=ubuntu-snappy-cli](http://packages.ubuntu.com/search?keywords=ubuntu-snappy-cli)

Re-reading the mailing list post I think I see a reason why personal_x86.img was no longer developed. Changing how the Ubuntu core image is organised. So, a clean break between one experiment another.

And we already found this out from personal-x86.img

> Note that when looking at /boot/grub there is no unpacked kernel/initramfs anymore:

Regards.

---

### Post by ventrical on 2015-12-18
> **grahammechanical said:**
> 

Re-reading the mailing list post I think I see a reason why personal_x86.img was no longer developed.

Regards.

This is a real disappointment. I have been waiting for news on the mailing list and nothing. Your report is the first I heard of it.  Well .. maybe all our efforts on testing snappy personal are not wasted - as per the good news you have pointed out. I too have downloaded that image and will give it a spin.

Regards..

---

### Post by grahammechanical on 2015-12-18
I have just use Disks>Restore Image to put it on a USB stick. amd-all-snap.img.xz is a 222.3MB download of a raw image file. It becomes a 4 GB install on the USB stick with a GTP partition layout.

Free space = 4.2 MB
Partition 1 = 4.2 MB BIOS boot
Partition 2 = 537 MB FAT EFI system boot
Partition 3 = 3.4 GB Ext4 Writeable

In order to do transactional updates Snappy Personal had system-a & system-b partitions as well as Writeable & BIOS boot & EFI boot partitions. It seems that this image has not reached the stage of doing transactional updates with roll-back. Either that or the developers have found another way to do it.

Let us see how she runs

EDIT: It is snappy ubuntu core. It loads to a Linux login prompt. It does update. The system seems to be in the Writeable partition. Ah, well. We tried. I might experiment with snappy ubuntu core some more or install new versions of this image to see if it is morphing into something interesting to desktop users.

Regards.

---

### Post by ventrical on 2016-01-05
> **grahammechanical said:**
> I have just use Disks>Restore Image to put it on a USB stick. amd-all-snap.img.xz is a 222.3MB download of a raw image file. It becomes a 4 GB install on the USB stick with a GTP partition layout.

Free space = 4.2 MB
Partition 1 = 4.2 MB BIOS boot
Partition 2 = 537 MB FAT EFI system boot
Partition 3 = 3.4 GB Ext4 Writeable

In order to do transactional updates Snappy Personal had system-a & system-b partitions as well as Writeable & BIOS boot & EFI boot partitions. It seems that this image has not reached the stage of doing transactional updates with roll-back. Either that or the developers have found another way to do it.

Let us see how she runs

EDIT: It is snappy ubuntu core. It loads to a Linux login prompt. It does update. The system seems to be in the Writeable partition. Ah, well. We tried. I might experiment with snappy ubuntu core some more or install new versions of this image to see if it is morphing into something interesting to desktop users.

Regards.

yep... can install apps (not mir) but nothing works at all. None of the apps run like in earlier versions. Not even the 'hello-world' app.

Also it comes up with- visit  [https://ubuntu.com/snappy](https://ubuntu.com/snappy) and deprecates to [https://ubuntu.com/core/snappy](https://ubuntu.com/core/snappy) and then we have outdated info from the days back in 15.04 or 15.10 so there has been zero maintenance on the knowledge base. It is par for the course being  we are just coming out of holidays.

There is new:
```

canonical-linux-pc
canonical-pc

```

but nothing resembles any type of a coherent desktop. 'top' still works.

Regards..

---

### Post by ventrical on 2016-01-08
I realized that I had to use the old method of downloading (flashing) the new images.

```

ventrical@ventrical-luntiy-betatest:~$ sudo ubuntu-device-flash personal rolling --channel edge -o amd64-all-snap.img --developer-mode
[sudo] password for ventrical: 
Determining oem configuration
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 170.63 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 217.38 KB/s 
Done
Fetching information from server...
Downloading and setting up...
Installing generic-amd64
Starting download of generic-amd64
41.70 KB / 41.70 KB [====================================] 100.00 % 170.58 KB/s 
Done
Starting download of icon for package
38.97 KB / 38.97 KB [====================================] 100.00 % 217.29 KB/s 
Done
New image complete
Summary:
 Output: amd64-all-snap.img
 Architecture: amd64
 Channel: edge
 Version: 121
ventrical@ventrical-luntiy-betatest:~$ 

```

---

### Post by ventrical on 2016-01-09
After  restoring this image to hdd I booted it and it went right into a unity8 session ??!! My camera actually works and I can get youtube and browser is much more stable but I cannot get into the other part of all the partitons *writeable* where canonical-linux-pc is. Also this unity8 session is running on Wily Werewolf so the image  brought in unity8 Desktop Next with it and it has me totally baffled as to what is going on here.  Thing is .. somthing is going on with possible snappy personal desktop development.

Regards..

---

### Post by adasiko256 on 2016-01-09
> **ventrical said:**
> I realized that I had to use the old method of downloading (flashing) the new images.
New?
version-121: 17-Oct-2015

---

### Post by grahammechanical on 2016-01-09
I think that Ventrical is referring to the method of downloading the image and not the image itself. Which, as far as I can determine does  not have a build image later than image 121 and has therefore not been moved on to the Xenial code base.

Regards

---

### Post by ventrical on 2016-01-09
Using the old flash method it downloaded both images and appended them to each other and called it amd64-all-snap.img but it will only boot into the old personal_x86.img which is unity8 on wily werewolf. So actually it is a fail and it looks as if you can use the device-flash method and name the personal_x86.img anything you want ie; amd64-all-snap.img

Regards..

---

### Post by Zerrax on 2016-01-12
Hi all,
  	 	 	 	   I have a question: I have a Asus C201 (arm based) Chrome-book, I know that the development of "Ubuntu Personal" is still very ALPHA, but I would like to know
if it is possible to get "Ubuntu Personal" working on armhf? (Rockchip RK3288 ) or has first the OS being specially compiled for this type of SOC?
or is "Ubuntu Personal" development going towards Intel based CPU's?

---

### Post by grahammechanical on 2016-01-12
I would not describe Ubuntu Personal as Alpha code. I would not even call it pre-alpha code. The only image available that I know of with the label "personal" is for x86 CPUs and it is built on wily code and has not been rebuilt since 17th October. Now I call that a "dead end." The best I can say about it is that is it a mock-up for proof of concept purposes. And the concept does indeed work and work well.

Ubuntu Touch/Ubuntu phone images are built for the ARM architecture. They are phone OS type user interface and applications. Not desktop applications. The apps are click packages and I do not think that there are any traditional Ubuntu desktop applications packaged as click packages.

As I understand it Ubuntu Personal will be for the x86 architecture. It will be built on snappy Ubuntu core & as far as I can make out snappy Ubuntu core can be installed on the Cloud, Raspberry Pi, Beaglebone Black & x86 devices. I see no mention of ARM devices. I may have missed them.

[https://developer.ubuntu.com/en/snappy/start/](https://developer.ubuntu.com/en/snappy/start/)

[https://developer.ubuntu.com/en/snappy/start/gadget-snaps/](https://developer.ubuntu.com/en/snappy/start/gadget-snaps/)

Regards

---

### Post by Zerrax on 2016-01-12
Thank you for the answer, it's clear to me now, 

Of course I hope there will be also a ARM version of "Ubuntu Personal" when it will be released, because it would be nice to see "open source" software, working on "open hardware" like ARM platforms like: 
Beagleboard X15, OLinuXino,etc 
[h=1][/h]

---

### Post by mc4man on 2016-01-12
> **Zerrax said:**
> Thank you for the answer, it's clear to me now, 

Of course I hope there will be also a ARM version of "Ubuntu Personal" when it will be released, because it would be nice to see "open source" software, working on "open hardware" like ARM platforms like: 
Beagleboard X15, OLinuXino,etc 
[h=1][/h]
Almost every Ubuntu launchpad source build produces .deb's for armhf, has been for some time now, they must be for something...
one example - [https://launchpad.net/ubuntu/+source/nautilus/1:3.18.4-0ubuntu1/+build/8767415](https://launchpad.net/ubuntu/+source/nautilus/1:3.18.4-0ubuntu1/+build/8767415)

---

### Post by ventrical on 2016-01-15
> **grahammechanical said:**
> I think that Ventrical is referring to the method of downloading the image and not the image itself. Which, as far as I can determine does  not have a build image later than image 121 and has therefore not been moved on to the Xenial code base.

Regards

@grahammechanical. all..

 Just found out that we have to use the NEW ubuntu-device-flash to get the new image - found here- [https://people.canonical.com/~mvo/all-snaps/](https://people.canonical.com/~mvo/all-snaps/)

  That is why all my downloads were borked.

Regards..

---

### Post by grahammechanical on 2016-01-15
What command are you using? The command that you give in an earlier post is pointing to the personal rolling edge directory. But the all snap image is in a different place.

apt-get is telling me that I already have the newest version of ubuntu-device-flash installed.

Regards

---

### Post by ventrical on 2016-01-16
> **grahammechanical said:**
> What command are you using? The command that you give in an earlier post is pointing to the personal rolling edge directory. But the all snap image is in a different place.

apt-get is telling me that I already have the newest version of ubuntu-device-flash installed.

Regards

I had been just downloading the compressed image and installing it to surplus hdds using gnome 'disks'. But the other method is what we need. One sec....

Edit:

Ok.. here is where a few things have got lost in translation.

The old method was to use:

```

ventrical@ventrical-luntiy-betatest:~$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode


```

but now instead of 'personal_x86.img" we use: 'amd64-all-snap.img' which should look like this:

```

sudo ubuntu-device-flash personal rolling --channel edge -o amd64-all-snap.img --developer-mode 


```

and the latest ubuntu-device-flash is Jan 13th 2016 - here - [https://people.canonical.com/~mvo/all-snaps/](https://people.canonical.com/~mvo/all-snaps/)

... is that the same ubuntu-device-flash you are using ? I ask because they say it is important to use the new ubuntu-device-flash unit.

 I am set now to experiment with retrieving this image in the manner stated above.

Regards..

---

### Post by ventrical on 2016-01-16
Just found up that the :

```

ubuntu-device-flash

```

will not update manually with regular updates...

So I will install it from the link.

Regards..

---

### Post by ventrical on 2016-01-16
Big problems with ubuntu-device -flash. Last regular update for wiley was in Sept. I think there has been a new channel change and we have to use xenial xerus.

So will try this in xenial.

Otherwise I cannot get downloaded NEW ubuntu-device-flash to install.

Here goes..

#note#- ubuntu-device-flash version should be  0.33-ubuntu2, not 0.30-ubuntu1

@graham.. get back to me on your last current version number for ubuntu-device-flash please. 

Thanks..

---

### Post by ventrical on 2016-01-16
Some kind of fail:

```

ventrical@ventrical-System-Product-Name:~$ sudo ubuntu-device-flash personal rolling --channel edge -o amd64-all-snap.img --developer-mode
Determining oem configuration
generic-amd64 failed to install: snappy package not found
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by grahammechanical on 2016-01-16
I get the same fail. That is why I say it is pointing to the wrong repository. Is this not the archive? [https://people.canonical.com/~mvo/all-snaps/](https://people.canonical.com/~mvo/all-snaps/)

I have downloaded amd64-all-snap.img.xz and used disks>restore image to put it on a USB stick but it loads to initramfs prompt. I did this yesterday.

Synaptic says I have ubuntu-device-flash 0.33-0ubuntu2 - the latest version. The last personal_x86.img was built on wily code. I am wondering if the devs are holding back building images for personal on xenial until xenial code becomes less changeable. Or to put it another way, will Ubuntu Personal be built on 16.04 LTS code for release sometime after April 2016?

Build on development code and the system image has to be built & tested daily. Build on released code and the system image only needs to be built & tested when there are security and major bug fixes. Effort can then go into bring Unity 8 up to Unity 7 levels and getting the traditional type apps in the app store as snaps or loadable as debs through Libertine. Just some thoughts of mine.

Regards.

---

### Post by ventrical on 2016-02-02
> **grahammechanical said:**
> I get the same fail. That is why I say it is pointing to the wrong repository. Is this not the archive? [https://people.canonical.com/~mvo/all-snaps/](https://people.canonical.com/~mvo/all-snaps/)

I have downloaded amd64-all-snap.img.xz and used disks>restore image to put it on a USB stick but it loads to initramfs prompt. I did this yesterday.

Synaptic says I have ubuntu-device-flash 0.33-0ubuntu2 - the latest version. The last personal_x86.img was built on wily code. I am wondering if the devs are holding back building images for personal on xenial until xenial code becomes less changeable. Or to put it another way, will Ubuntu Personal be built on 16.04 LTS code for release sometime after April 2016?

Build on development code and the system image has to be built & tested daily. Build on released code and the system image only needs to be built & tested when there are security and major bug fixes. Effort can then go into bring Unity 8 up to Unity 7 levels and getting the traditional type apps in the app store as snaps or loadable as debs through Libertine. Just some thoughts of mine.

Regards.

The amd64-all-snap.img.xz is now dated Feb 2 so I think it is that one. I will download it and use disks or mkusb to put it on an hdd.

Regards..

---

### Post by ventrical on 2016-02-02
I downloaded Feb02 image and installed it using disks. It is using xenial code and you can use:

```

lsb_release -a

```
to comfirm it.

It is also using the 4.3-n-n kernel.

So I am going to install LXD and try to break it or import an image inot a container.

Since this is not snappy personal I will open a new thread.

Regards..

---

