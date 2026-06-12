---
title: "shortage of memory to complete a VMware Player installation."
date: 2013-11-05
forum: Virtualisation
---

### Post by psyclone on 2013-11-05
[COLOR=#000000]hi all,[/COLOR]

[COLOR=#000000]This is regarding a shortage of memory to complete a VMware Player installation.
[/COLOR][COLOR=#000000]
Just before i complete the installation process(to install win7), and error crops up saying the following:[/COLOR]

[COLOR=#000000]"The current amount of free space on the hard disk (1.1 GB) is not enough to create the specified disk file. Please choose a different location or specify a smaller disk size." (in a pop-up window)[/COLOR]

[COLOR=#000000]because according to the "Details in Settings": I have the following capacity.[/COLOR]

[COLOR=#000000]Memory 3.8 GiB[/COLOR]
[COLOR=#000000]Disk: 18.3 GB[/COLOR]

[COLOR=#000000]I have a hard-drive partition of 250GB for Ubuntu (ie. dual boot: 250GB for win7 & 250GB for Ubuntu; 500GB H/Drive total). And win7 requires 60GB to function. [/COLOR]
[COLOR=#000000]How do i adjust the memory to allow for the 60GB, or how to complete the installation?[/COLOR]

---

### Post by psyclone on 2013-11-05
I had another look. 

The restriction appears to be a free space allocation of 1.1GB per folder. Meaning the VMware folder where win7 would (or will be when installtion is complete, which it isn't at this stage) be stored in seems to have a limit of 1.1GB free space. Although if I look at the "home" drive/folder it has 5.4GB stored with 1.1GB free space in the folder properties?? 

Does anyone have any ideas ?

---

### Post by psyclone on 2013-11-09
I've been trying to work through the following post, i.e. to adjust the directory size to run VMware to install Windows, there's a restriction on the folder size.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html) {taken from the following ubuntu-fourm post }
[http://ubuntuforums.org/showthread.php?t=1698297](http://ubuntuforums.org/showthread.php?t=1698297)

I've edited the /etc/fstab file by adding:


/dev/hda2 /home ext3 defaults,usrgroup,grpquota 1 1 
chmod 600 /home/aquota.user


But my I can't mount/remount the /home partition to go onto the next stage. 

sudo mount -o remount /home 

I get the following response:
mount: /home not mounted or bad option

Also, rebooting doesn't fix this problem either.

Please help.

---

