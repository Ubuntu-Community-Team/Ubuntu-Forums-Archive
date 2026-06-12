---
title: "How to automate grub or send commands to grub via ssh"
date: 2010-09-09
forum: Server Platforms
---

### Post by joeaura7 on 2010-09-09
I have a server that is triple boot and the server is headless and accessed using ssh. So is there a way to tell grub before hand what os to choose or send commands to grub (of course I get rid of the timeout) to pick a different os other than the default one. Any ideas? I already know this is bad practice to have multiple os's on the same machine to be used as a server, but what about selecting a different kernel at start up. Please help](*,)

---

### Post by gobbledigook on 2010-09-09
grub loads before the network service (which will load after you select an os) so you will not be able to choose which os remotely.

have you considered running the other os as [virtual machines]("https://help.ubuntu.com/community/VirtualMachines")? you could have them all start on boot or start individually from ssh

---

### Post by joeaura7 on 2010-09-09
yes, i have considered virtual machines. Regular virtual machines would overload the computer. I can barely run the other os's by themselves let alone running on top of Linux. I am looking at chroot envirnments, however I think it is only deigned for Linux. So apparently it will not work in real time. What about telling grub beforehand like changing the default os temporarily, restart into another os and change back when I restart again?

---

### Post by oldfred on 2010-09-09
Back in os/2 days we had something like that. What I think it must have been was like two copies of the MBR and a dd like command to copy the windows boot loader into the MBR if you wanted to boot it and then in windows copy the OS/2 boot loader. It may have just been what we now know is the boot flag being set and the boot loader in the partition boot sector, but I was not that involved with the details back then.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1
Zero out MBR and partition table
dd if=/dev/zero of=/dev/sda bs=512 count=1

If you have old grub for each system installed to the PBR, then you could install lilo to the MBR, it is like windows and just looks for the boot flag and jumps to the PBR to continue booting.

You can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
OR:
    #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-

---

### Post by gobbledigook on 2010-09-09
> **joeaura7 said:**
> What about telling grub beforehand like changing the default os temporarily, restart into another os and change back when I restart again?

this depends on what os you want to load? in theory you could have a script to run on shutdown that alters the menu.lst automatically to alternate the boot list or if you ran it manually... the obvious issue here is with a windows os where you would need to install a ext3 driver AND write the damned script in windows speak ;) other issues are "which" menu.lst it alters.. i'm really not sure here, but if you had more than one linux install... which menu.lst does it load? 

i'll be honest here... what oldfred suggests is above me :)

sorry if i have brought more questions than answers ;)

---

### Post by joeaura7 on 2010-09-09
I wish grub would default to whatever partition the boot flag is on. Could what you are describing can be done in grub instead of lilo? If not, I am looking for a script that would change grub. As gobbledigook, pointed out the obvious problem by doing that unless there is a trick to it so that I do not have to change it back when I am on the Windows side.  I only have one Linux install on the server which uses grub2.

---

### Post by oldfred on 2010-09-09
If you have windows you will not be able to edit a grub menu in a linux partition. One alternative is to install a grub partition as fat32 or NTFS as grub will install to just about anything, but editing grub menu with a script is probably more difficult than just changing MBR or boot flag. The only thing I do not know is how to easily change the boot flag from windows. It normally just does it behind the scenes as part of an install. You can install grub2 to a partition boot sector PBR but it uses blocklists. They say that is less relaiable as then if any of the grub files get moved on the hard drive it will not boot without a grub reinstall to the PBR.

Found a link to changing active (boot flag) partition in windows.
[http://www.online-tech-tips.com/computer-tips/set-active-partition-vista-xp/](http://www.online-tech-tips.com/computer-tips/set-active-partition-vista-xp/)

---

### Post by joeaura7 on 2010-09-09
I will see if changing the boot flag will do the trick. It looks really easy, if not I will try the change the MBR. Thanks :cool:

---

