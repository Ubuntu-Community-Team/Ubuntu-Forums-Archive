---
title: "Trouble running VirtualBox with &quot;real&quot; partition"
date: 2008-01-11
forum: Virtualisation
---

### Post by Mr. Picklesworth on 2008-01-11
My laptop is set up with Windows Vista on one smallish partition, and Ubuntu on the rest of the (single) hard drive. While I do use Windows mostly for just running Windows-based games easily, there are a few tools on it that I still like to use. I decided to look at virtualization again, since that allows me to use those tools without straying too far away from Linux's comforting presence.

First, the good news: I have it working!

I set up a virtual disk that points to the real hard drive as follows:

*VBoxManage internalcommands createrawvmdk -filename /home/dmccall/Documents/VirtualBox/WindowsVista_PhysicalPartition/sda.vdmk  -rawdisk /dev/sda -register*

The problem here is that this makes the entire hard drive be accessed by the virtual machine! Clearly, I now run the risk of the universe imploding and it being my fault.
Indeed, I have 3 critical seconds every time I boot that virtual machine in which to press Escape to open the GRUB menu, scroll down and choose Windows, or else Ubuntu will meet its duplicate self, creating a giant rift in time ultimately destroying us all!
Obviously, being a kind and forgiving person, I do not want this to happen, so I hope to repair this doomsday machine before it is too late.

That actual working solution was actually the last thing I tried, but I am sure many people here understand this stuff way better than I do. Initially, I had hoped to use the "-partition 1" argument to restrict access to just that one partition Windows lives on. This led to Error 17 in GRUB (and I do not want to kill GRUB). Changed the MBR using "dd" (note: I have no idea how this command works. Just copied "*dd if=/dev/sda1 of=windowsvista.mbr bs=512 count=1*" from a forum post and it seemed to do, err, something).
Changing the MBR got me to Windows, but it gave an error immediately that \Windows\System32\winload.exe was corrupted or missing, thus could not boot. This is not the case. I had unmounted /media/sda1, so it was not because the partition was already in use, unless Ubuntu mounts it elsewhere, too.

I get the following output from *VBoxManage internalcommands listpartitions -rawdisk /dev/sda*```
VirtualBox Command Line Management Interface Version 1.5.4
(C) 2005-2007 innotek GmbH
All rights reserved.

Number  Type   StartCHS       EndCHS      Size (MiB)  Start (Sect)
1       0x07  0   /32 /33  1023/254/63         76368         2048
2       0x83  1023/254/63  1023/254/63         14300    156408840
5       0x83  1023/254/63  1023/254/63         61318    185695398
6       0x82  1023/254/63  1023/254/63           635    311275503

```
As you can see, Windows resides on number 1, the others are all Linuxy partitions.

Any help in getting this working with virtualized Windows restricted to just its partition would be much appreciated. Remember: It is for the good of us all. Otherwise, *we're all doomed!*

---

### Post by crunchfighter on 2008-01-15
I don't know about limiting it to the partition added.  I changed the boot menu:

System->Administration->Start-Up Manager

Uncheck "use timeout in bootloader menu"

You can also make the default OS Windows if you are concerned that you'll have a moment of insanity even though you now have longer than three seconds to Armageddon.

FYI, I just deleted the VMWare and VirtualBox rawdisk experiments on my computer.  I use VirtualBox with a .vdi only now.  It's much faster.  The rawdisk versions took an eternity to load and brought the whole machine to screeching halt.

---

### Post by popch on 2008-01-15
> **Mr. Picklesworth said:**
> 
*VBoxManage internalcommands createrawvmdk -filename /home/dmccall/Documents/VirtualBox/WindowsVista_PhysicalPartition/sda.vdmk  -rawdisk **/dev/sda** -register*


Is there any particular reason why you can't use ***/dev/sda_1_*** in that statement?

---

### Post by Mr. Picklesworth on 2008-01-16
Yup; it scares Windows if it suddenly wakes up in what looks like a completely different hard drive. If I don't want to confuse it, I have to use /dev/sda and the -partitions 1 argument. The -partitions argument says "Permit access to the listed partitions", and provides a whole lot of 0s for the other partitions. Thus, Windows still sees them but does nothing to them.

By the way, thanks for moving this thread!

---

### Post by Tichondrius on 2008-01-25
> **Mr. Picklesworth said:**
> Yup; it scares Windows if it suddenly wakes up in what looks like a completely different hard drive. If I don't want to confuse it, I have to use /dev/sda and the -partitions 1 argument. The -partitions argument says "Permit access to the listed partitions", and provides a whole lot of 0s for the other partitions. Thus, Windows still sees them but does nothing to them.

By the way, thanks for moving this thread!

right, this will never work smoothly with windows. That is, being able to boot the same windows partition inside a VM, and directly from the real boot. Windows is just too sensitive to any changes between the real environment with its real devices, and the virtual machine with its virtual devices.

For a Linux VM, it IS possible to achieve that (I have that working) but even then it's not totally smooth. I created a raw-disk drive in Virtual box, and installed linux there (running in a VM under a Windows host). since linux is installed in its own (raw) disk, I can boot it directly from the BIOS, but there is still a problem with the X-windows video driver. When running as a VM under virtualbox, the graphics card is a virtual device created by the VM, which uses a special driver (installed as part of the guest tools). But when booting the Linux partition directly, it needs a regular driver for the real video card (either generic VESA driver, or NVIDIA driver in my case). So I either have to change the video driver by modifying xorg.conf, or run without X-windows. 


In any case, I don't see much reason to boot Linux directly, since it works almost as fast running as a guest under the VMM. And I have the convenience of having both windows and linux running simultaneously.  In fact, my linux VM is running apache web server, python application server (running gallery, trac, phpmyadmin as well as various custom web apps) , mySQL server, SSH server, IMAP server, postfix SMTP server, Samba server, and subversion server. And it's running incredibly stable and fast 24x7. 

And when I need to relax, I can still fire up my favourite windows games like UT3, Bioshock, Crysis, etc.... I also prefer doing web browsing and document edition in windows, And since I'm running X-ming X-server in windows, I can run Linux apps directly on the windows desktop (outside the VM window) using X remote display. Life is good !

---

### Post by Mr. Picklesworth on 2008-01-25
I see what you mean about running Linux in a VM. Haven't done it in a while. I just had the pleasure of running the Mandriva Live CD in VirtualBox, and was very impressed by the changes! Mouse pointer integration is fantastic :)

However, I am turning into an open source zealot, so running Ubuntu in a virtual machine aboard *Windows* would simply not do. Thanks for the suggestion, though!

---

### Post by notepad on 2008-01-29
how did you use this "dd if=/dev/sda1 of=windowsvista.mbr bs=512 count=1" command?
you got around your grub error 17 problem? im stuck on it about now =o\

---

### Post by alexsb on 2008-02-01
Exactly the same problem here! winloader.exe is not found. Would appreciate any help :)

---

### Post by abalter on 2008-02-27
I have been wondering for a long time how to use vbox to run a physical (raw) partition!  Can you please tell me how to do it?  Suppose I have a partition with linux installedl.  How do I use vbox in windows host to boot into it?  Thanks in advance,
Ariel

---

### Post by pete on 2008-03-27
Mr. Picklesworth--

Check this thread on the VirtualBox forums...[http://forums.virtualbox.org/viewtopic.php?t=2019]("http://forums.virtualbox.org/viewtopic.php?t=2019"):

> install "mbr" package in your Linux host and run "install-mbr --force opensource.mbr". This will create a file called opensource.mbr in your home directory

then,
```
VBoxManage internalcommands createrawvmdk -filename [PATH_TO_XP_VMDK FILE] -rawdisk /dev/sda -partitions [XP_PARTITION] -mbr [PATH_TO_FAKE_MBR_FILE] -relative
```

That will bypass your actual MBR and go straight to Windows, bypassing the grub menu and thereby avoiding the risk of virtualizing your running host partition, cats and dogs sleeping together, mass hysteria, etc.

---

### Post by djbon2112 on 2008-03-31
^^ I do that, but I get this:

```
joshua@joshua-laptop:/home$ VBoxManage internalcommands createrawvmdk -filename /mnt/external/vmware/xp_real/xp.vdmk -rawdisk /dev/sda -partitions 4 -mbr /home/joshua/opensource.mbr -relative
VirtualBox Command Line Management Interface Version 1.5.6
(C) 2005-2008 innotek GmbH
All rights reserved.

Error opening the raw disk: VERR_ACCESS_DENIED
```

If I run it as sudo, I get this:

```
joshua@joshua-laptop:/home$ sudo VBoxManage internalcommands createrawvmdk -filename /mnt/external/vmware/xp_real/xp.vdmk -rawdisk /dev/sda -partitions 4 -mbr /home/joshua/opensource.mbr -relative
VirtualBox Command Line Management Interface Version 1.5.6
(C) 2005-2008 innotek GmbH
All rights reserved.

ERROR: VMDK: could not create new file '/mnt/external/vmware/xp_real/xp.vdmk'
Error code VERR_FILE_NOT_FOUND at /home/vbox/vbox-1.5.6/src/VBox/Devices/Storage/VmdkHDDCore.cpp(2146) in function int vmdkCreateImage(VMDKIMAGE*, const char*, VDIMAGETYPE, uint64_t, unsigned int, const char*, uint32_t, uint32_t, uint32_t)
Error while creating the raw disk VMDK: VERR_FILE_NOT_FOUND
```

Any suggestions?

---

### Post by karyonix on 2008-04-02
how about
```
sudo chown joshua:disk /dev/sda*
VBoxManage internalcommands createrawvmdk -filename /mnt/external/vmware/xp_real/xp.vdmk -rawdisk /dev/sda -partitions 4 -relative
install-mbr -f -p 4 /mnt/external/vmware/xp_real/xp-pt.vdmk
```

---

### Post by djbon2112 on 2008-04-02
> **karyonix said:**
> how about
```
sudo chown joshua:disk /dev/sda*
VBoxManage internalcommands createrawvmdk -filename /mnt/external/vmware/xp_real/xp.vdmk -rawdisk /dev/sda -partitions 4 -relative
install-mbr -f -p 4 /mnt/external/vmware/xp_real/xp-pt.vdmk
```


Tried it, but I still get the same error I got when I did sudo earlier ( VERR_FILE_NOT_FOUND at /home/vbox/vbox-1.5.6/src/VBox/Devices/Storage/VmdkHDDCore.cpp ).

---

### Post by analyzer123 on 2008-04-03
Hey  Tichondrius ,
    I am interested to know how you get the linux apps to run directly onto windows desktop. I use x-win32 server but how do i configure linux to export its display to windows?

---

### Post by karyonix on 2008-04-04
djbon2112,
1. Are you sure the disk you want to do raw access is /dev/**sda** partition **4**  ?  If the partition does not exist, create it first. 
2. After chmod, verify that you can read from /dev/sda and /dev/sda4. try "fdisk -l /dev/sda",  "hd -n 512 /dev/sda4". 
3. Make sure that the directory /mnt/external/vmware/xp_real/ exists. and you can write to that directory. 
4. If the files /mnt/external/vmware/xp_real/**xp.vmdk**, and /mnt/external/vmware/xp_real/**xp-pt.vmdk** already exist, delete them before running VBoxManage . 
5. Have you tried create raw vmdk for whole disk (without "-partitions 4 -relative") ?   successful or not ?

---

### Post by djbon2112 on 2008-04-04
It worked, all I had to do was mkdir the new directory.

---

### Post by vexorian on 2008-04-04
Do yourself a favor, and avoid running a virtual machine on physical hard drives, It looks like it works, until BAM! Windows becomes unable to boot...

---

### Post by DarkW0lf on 2008-04-19
I used :
```

VBoxManage internalcommands createrawvmdk -filename /media/data/vbox/guests/WinVista/WinVista.vmdk -rawdisk /dev/sda -partitions 1 -mbr /media/data/vbox/guests/WinVista/WinVista.mbr -relative -register

```

(that should be all one line).
And I get that winload.exe error on VM start.
The mbr was created using install-mbr.

Should I try dd instead ?

---

### Post by DarkW0lf on 2008-04-19
Just tried it with mbr from using dd (like first post) and I still get the winload.exe error (that my hardware or software changed).

So what do I about this ?

---

### Post by DarkW0lf on 2008-05-17
To get past the error for hardware changes on boot I found this recovery disc online:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Checksum:
aff5ceef6dbf202cc1beb9fc81e8d02b

I didn't have my system restore partition and Compaq didn't send cd's with the laptop. So that disc helped with the winload.exe error. I booted the Vista VM with that cd iso mounted to the drive. Ran through the repair steps and rebooted to Vista.

But now I got to reinstall device drivers for VBox hardware but it is working now.
(Have to find drivers for Ethernet and Base System Device[??])

---

### Post by dj_unforgetable on 2008-05-29
wait wait. darkwolf ... what did you do to get past the winload error ?

---

### Post by DarkW0lf on 2008-06-03
load the iso I posted a link to in VBox and boot from that.

Then follow the prompts and it will repair the bootloader so you can use the mbr made in the other posts in this thread.

---

### Post by Sand Lee on 2008-06-03
From the sticky:
[Boot an existing XP (Physical HD) install with VirtualBox]("http://ubuntuforums.org/showthread.php?t=769883")
Maybe that'll help...

---

### Post by DarkW0lf on 2008-06-08
Sand Lee: just a warning your instructions will not work with Vista. Upto the point where you need to make a hardware profile you are good but there are no Hardware profiles anymore with Vista.

I dont know about the wpa files, never saw Vista related information about that. For Vista, your guide could work. Just skip 4, 5 & 7; after you boot the vmdk, make sure to run the disc I linked to above (it will fix the ms bootloader). The MergeIDE utility at virtualbox doesn't seem to work for me. And don't switch back and forth, there are too many hardware changes.

I need to set linux not to mount the Vista partition, and keep it rw.

---

### Post by tors on 2008-09-05
I downloaded the version 2.0 binaries Hardy packages from virtualbox.org and when I try to create a "physical" vmdk-file, VBoxManage segfaults on my ThinkPad T60.

# sudo VBoxManage internalcommands createrawvmdk -filename /home/henrik/system/local.vmdk -rawdisk /dev/sda -partitions 3 -relative

VirtualBox Command Line Management Interface Version 2.0.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Segmentation fault


Has anyone found a solution to this?


PS. listing partitions works:

# VBoxManage internalcommands listpartitions -rawdisk /dev/sda

VirtualBox Command Line Management Interface Version 2.0.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Number  Type   StartCHS       EndCHS      Size (MiB)  Start (Sect)
1       0x83  0   /1  /1   1023/224/63         52454           63
5       0x82  1023/226/1   1023/14 /63          3906    107426718
3       0x07  1023/0  /1   1023/239/63         15326    115441200
4       0x1c  1023/0  /1   1023/239/63          4621    146830320

---

### Post by tors on 2008-09-05
It seems to be possible to create the file using VBoxManage from version 1.6.6.

---

### Post by TroyDowling on 2009-03-19
> **pete said:**
> Mr. Picklesworth--

Check this thread on the VirtualBox forums...[http://forums.virtualbox.org/viewtopic.php?t=2019]("http://forums.virtualbox.org/viewtopic.php?t=2019"):



then,
```
VBoxManage internalcommands createrawvmdk -filename [PATH_TO_XP_VMDK FILE] -rawdisk /dev/sda -partitions [XP_PARTITION] -mbr [PATH_TO_FAKE_MBR_FILE] -relative
```

That will bypass your actual MBR and go straight to Windows, bypassing the grub menu and thereby avoiding the risk of virtualizing your running host partition, cats and dogs sleeping together, mass hysteria, etc.

Hey, thanks! The above instructions got me past the fear of virtualizing my host machine. The only weird quirk is that when I boot it prints "MBR 12FA: " to the screen and waits for me to hit 1, 2, F, or A... No idea what it means, but hitting 2 gets me where I want to go. =)

Thanks again,
Troy.

---

### Post by howefield on 2012-12-28
Old thread closed.

Feel free to start a fresh one.

---

