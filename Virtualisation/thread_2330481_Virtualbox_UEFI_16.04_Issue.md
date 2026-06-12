---
title: "Virtualbox UEFI 16.04 Issue"
date: 2016-07-11
forum: Virtualisation
---

### Post by fjgaude on 2016-07-11
After new install of 16.04 in UEFI mode, can't get Virtualbox to load. A conflict is stated in error msg. No issue in BIOS mode with 16.04.

Anyone have this issue, and if so, please help me out.

Thanks you!

---

### Post by howefield on 2016-07-12
Thread moved to the "*Virtualisation*" forum for a better fit.

---

### Post by MAFoElffen on 2016-07-13
From notes I took from the [VirtualBox Forum]("https://forums.virtualbox.org/viewtopic.php?f=1&t=45065#p322243"):
```

Settings:
* System -> Motherboard -> Extended Features: Enable EFI 
* Boot HDD must be attached to SATA controller! IDE, SCSI or SAS will not work (bug report: Ticket #14142)


EFI Boot Screen:
When the UEFI boot screen appears, it should show blkX: and fsX: devices. fsX: are file systems accessible by the boot loader. If the EFI boot partition does not appear as fsX:, the boot manager will not be able to boot. This will happen if the EFI partition is on a disk attached to an IDE, SCSI or SAS controller (see above).


Boot from the EFI boot shell (for Ubuntu system, others may be different):


efi\ubuntu\grubx64.efi

Once you know what to boot (in my case: efi\ubuntu\grubx64.efi), put this line into a new file startup.nsh in the root directory of the EFI file system. Then, the EFI boot loader will boot it automatically after 5s.

```

---

### Post by fjgaude on 2016-07-13
MAFoElffen, no issue with booting the UEFI install, either from an m.2 or SSD. The issue is installing VBox.

frank

---

### Post by MAFoElffen on 2016-07-13
Wait... just read your "otehr thread, where you said you thought your problem with VirtualBox was tied to UEFI booting... seems liek you are going in circles.

So ltes just try to solev your problem in one thread.

What is your chief complaint? Seesm liek you are not going to get the the step I thought you were on... until you get VirtualBox installed and working.

And you can't install from the repos -AND- from external. Even Oracle say to uninstall VitualBox before installing another version of it. Less problems that way... That is how it ends up with mix-matched pieces from different versions... and a vboxdrv kernel driver failure. So no --reinstall.

Do an uninstall. When finished, do an install.

---

### Post by fjgaude on 2016-07-13
Gosh, no circles here. I can't uninstall because I have not been able to install, but only if my 16.04 is installed as UEFI which I have stated a few times.

frank

---

### Post by MAFoElffen on 2016-07-14
meanwhile, back here ... please post the results of:
```

dpkg -l | grep -i virtualbox
ls /usr/lib/virtualbox/VBoxManage
apt-cache policy virtualbox-dkms
ls -l /var/lib/dkms/virtualbox/5.0.??/build/vboxdrv/vboxdrv.*
lsmod | grep vbox

```
Also, you say that your Host boots UEFI. Please explain how you think (in your own words) that affects how VirtualBox is installed any differently, compared to a Host that boots in BIOS mode. You say you've been doing this since 12.04, so you have some insight, on your own hardware, that may help with this. 

As far as I see it, efi files just point to where to boot from (simplistically). It is a boot manager loading method. As with BIOS, it looks at the boot order, then, the MBR, which points to a partition (branched from the boot manager). Once those pointers are wired, as far as I know, that wiring has nothing to do with how or what kernel modules are loading, that is managed by the installed OS itself, not the boot loader. But maybe you could educate me if that has changed in some way, right?

Basically, the module is not loading. That is usally a confilct, or not finding something, somewhere. If you are getting the "run this script in /sbin/..." error, like you said in that other script... That is an Oracle upstream error in the error message that tells users of another Linux Branch, to run a script... where as for us in the Debian Branch... yes that script is not at that location, as you are finding.

EDIT-- And my apologies for any confusion between the two threads. Too may ideas going on at the same between three users, with 3 different hardware & OS setups. Was getting hard to keep track of what was directed to whom. LOL.

---

### Post by fjgaude on 2016-07-14
Gosh, I've tried to move by turning this drive back into MSDOS format. Then tried to install VBOX. Conflict with mismatch:

The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

```
'/sbin/vboxconfig'

may correct this. Make sure that you do not mix the OSE version and the PUEL version of VirtualBox.

where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user.
``` 

Here's what I get running your suggested commands:

```
frank@flash:~$ dpkg -l | grep -i virtualbox
ii  unity-scope-virtualbox                      0.1+13.10.20130723-0ubuntu1                                 all          VirtualBox scope for Unity
rc  virtualbox                                  5.0.18-dfsg-2ubuntu1                                        amd64        x86 virtualization solution - base binaries
ii  virtualbox-5.1                              5.1.0-108711~Ubuntu~xenial                                  amd64        Oracle VM VirtualBox
ii  virtualbox-dkms                             5.0.18-dfsg-2ubuntu1                                        all          x86 virtualization solution - kernel module sources for dkms
rc  virtualbox-qt                               5.0.18-dfsg-2ubuntu1                                        amd64        x86 virtualization solution - Qt based user interface
frank@flash:~$ ls /usr/lib/virtualbox/VBoxManage
/usr/lib/virtualbox/VBoxManage
frank@flash:~$ apt-cache policy virtualbox-dkms
virtualbox-dkms:
  Installed: 5.0.18-dfsg-2ubuntu1
  Candidate: 5.0.18-dfsg-2ubuntu1
  Version table:
 *** 5.0.18-dfsg-2ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages
        100 /var/lib/dpkg/status
     5.0.18-dfsg-2build1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages
frank@flash:~$ ls -l /var/lib/dkms/virtualbox/5.0.??/build/vboxdrv/vboxdrv.*
-rw-r--r-- 1 root root 591792 Jul 14 09:00 /var/lib/dkms/virtualbox/5.0.18/build/vboxdrv/vboxdrv.ko
-rw-r--r-- 1 root root   6469 Jul 14 09:00 /var/lib/dkms/virtualbox/5.0.18/build/vboxdrv/vboxdrv.mod.c
-rw-r--r-- 1 root root   9600 Jul 14 09:00 /var/lib/dkms/virtualbox/5.0.18/build/vboxdrv/vboxdrv.mod.o
-rw-r--r-- 1 root root 723200 Jul 14 09:00 /var/lib/dkms/virtualbox/5.0.18/build/vboxdrv/vboxdrv.o
frank@flash:~$ lsmod | grep vbox
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci

```

---

### Post by fjgaude on 2016-07-14
My system is Skylake, 64bit, 170 ASUS MB, and I would think 16.04 is still doing things to cover compatibility issues, if any. Using Unity.

The whole thing for me has been when I GPTed and UEFIed the m.2 drive, Samsung SM950, which boots nicely on Linux.

Likely will have to start completely over. <sigh>

Thanks for all your efforts to help.

frank

---

### Post by MAFoElffen on 2016-07-15
Like I said, or maybe that post maight have lost in yesterdays crash...

Your VirtualBox Install and your module not loading has nothing to do with how your host's disk is installed. Whether you are booting as BIOS or UEFI on your host <-- No affect on that.

You have ASUS Skyrock Z170 right? On that board, if you get into the BIOS setup: Advanced > CPU setup > Virtualization... make sure it says enabled.

Like I said before, you did a partial install several times, several different versions. You have different versions of the virtualbox kernel module installed. Now the newer module will not load, because it conflicts, version wise. That is why Oracle says to uninstall the old completely before installing a newer version.

I see that since you are a new, fresh install of Ubuntu, you have 2 options open to you:

(1) Reinstall a clean install of Ubuntu, fromatting the disk when you do it. Beig a fresh install, there would be nothing there to conflict with anything.

(2) Repair your present install.
To uninstall what I saw:
```

sudo apt-get update && sudo apt-get remove --purge virtualbox-5.0
sudo apt-get install virtualbox-5.0

```

---

### Post by fjgaude on 2016-07-16
You have been so right from the beginning. Thank you!

Now, do you know a way to clean a disk that has GPT, UEFI, and EFI partition?

---

### Post by MAFoElffen on 2016-07-16
If you have it booting, then I would leave it... but if you wanted to, you are still at the start of this, so less work and risk now, rather than later down the road.

You could always start over, fresh and clean. If it where me, I would leave the layout as EFI. That is what is current tech and is not really going away soon. It adds value to what you have and makes things easier.

On an EFI layout scheme on a GPT Disk... A GPT disk has two GPT partition tables (at beginning and end of the disk) ... then your partition layout should resemble:
```

1 sector unused space
Partion1: boot_grub
Partion2: EFI
... other partitions

```
Or you if you wanted to convert your GPT EFI disk from UEFI boot to an MBR Legacy BIOS boot disk, you can do that with that same partition layout... and I could tell you how to make it bootable with a Legacy BIOS Boot...

But what do you think you need to clean up in your present install, besides VirtualBox?

---

### Post by fjgaude on 2016-07-16
Okay, I'll take your advise and leave things the way they, since all is working.

Again, again thank you!

---

### Post by MAFoElffen on 2016-07-16
If you have any question feel free to ask. 

Do others a favor. When you get things working and sorted out, come back here and document what worked for you, and what the solution was for you (in your own words).

I can tell by your post count, that you have a lot to share in your experience with others. Documenting and sharing that with others will help others reading this later to solve their similar problems. Marking it solved when you are satisfied with your solution will help others to find that solution quickly.

---

### Post by vaseem007 on 2016-08-17
I have successfully fixed the issue in my Ubuntu 16.04.1 LTS
Check the package
dpkg -l | grep -i virtualbox

Uninstall from system
sudo apt-get remove unity-scope-virtualbox
sudo apt-get update && sudo apt-get remove --purge virtualbox-5.1

wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add -
wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -

Finally install it:

sudo apt-get update
sudo apt-get install virtualbox-5.1


This fixed the issue for me :)

---

### Post by MAFoElffen on 2016-08-17
Glad it all worked out. If you could please return ti this thread > Upper right of page link "Thread Tools" > Link "Mark Thread As Solved"... which will help others to find answers to their similar questions.

Edit-- Thanks. By the time I posted this, you were lready doing that. LOL

---

