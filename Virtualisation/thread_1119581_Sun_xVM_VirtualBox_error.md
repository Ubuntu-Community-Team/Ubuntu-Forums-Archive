---
title: "Sun xVM VirtualBox error"
date: 2009-04-08
forum: Virtualisation
---

### Post by drapsjap on 2009-04-08
I've recently switched from a WindowsXP-only system to an Ubuntu/Fedora dual-boot. Both, Ubuntu and Fedora, are installed on the primary hard drive and seem to run smoothly. Since I'd like to use some software which will only work in Windows, I'd like to install WindowsXP(sp3)in virtualbox. I've tried the open source version as well as the Sun xVM version, both gave the same error(after pressing 'start') :


[I]Virtual machine 'Windows XP' has terminated unexpectedly during startup.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}

[/I]The second problem is that VirtualBox doesn't seem to detect my second hard drive- I want to install XP on my second hard drive so the first one can be used entirely by linux. Is there any way to create a VirtualBox file in which Windows can be installed on my second hard drive? 

I've added the correct cd-drive, inserted the cd and made enough space available for XP to install. Searching google for solutions didn't give me any results. Some information on the Ubuntu distribution I'm using:

Release 8.10 (intrepid)
Kernel Linux 2.6.24-22-generic



*[SIZE=1]Feel free to move this post if it's placed in the wrong section, or to delete it if it's been posted before. [/SIZE]*;)

---

### Post by MaindotC on 2009-04-08
I'm not sure about that error code.  I always use the deb from VB's website and not what's in the repo.

As for the hard drive - is the 2nd hard drive mounted?  If so, then it should be listed in /media.  Once it is mounted, tell VB to host the virtual machine in /media/<drive_name>.

---

### Post by drapsjap on 2009-04-08
> **strAlan said:**
> 
As for the hard drive - is the 2nd hard drive mounted?  If so, then it should be listed in /media.  Once it is mounted, tell VB to host the virtual machine in /media/<drive_name>.

Thanks for the quick reply. I did indeed find the hard drive, but wasn't able to use it. After trying to create the virtualbox file on this drive it gave the following error:


[I]Could not create the hard disk storage unit '/media/sdb1/WindowsXP.vdi'.
VDI: cannot create image '/media/sdb1/WindowsXP.vdi' (VERR_ACCESS_DENIED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
HardDisk2
Interface: 
IHardDisk2 {ed6e2525-c2fd-42a4-917a-7a9045ac9e15}

[/I]If these error messages(especially the first one) are unfamiliar to more people, I'll write a short guide about how to fix it after someone came with a solution. Thanks in advance! ;)

---

### Post by MaindotC on 2009-04-08
The hard drive is typically mounted with root permissions.  Post the output of:
```

ls -l /media

```
I suggest creating a folder on sdb1 named "VDI" and giving it your owner and group permissions and just using that folder instead of changing the entire disk permissions to your own.

---

### Post by drapsjap on 2009-04-08
The code you suggested resulted in multiple entries, one of which included my second drive (/sdb1):


```
drwxr-xr-x 2 root root  4096 2009-04-07 11:37 sdb1
```

Creating a folder shouldn't be an issue, and sounds like a good suggestion. However, it wont be of any use without my primary problem being fixed. Instead of just waiting for replies, I'll try some different versions of VirtualBox. If it gets me any results, I'll post them here asap. Thanks.

---

### Post by MaindotC on 2009-04-08
You can't create a vdi in sdb1 because it is mounted with root permissions.  Vbox runs as the user which is logged into tty7.  You need to create a folder with permissions of the owner and group associated with whoever is running virtualbox.  As you may notice, you can create a vm in your ~ directory because that is your directory.  You can't create it on /media/sdb1 because it is owned by root.  Make a folder that has the same owner and group permissions as your ~ directory.

Now, regarding your first problem, can you run VBox from the command line and post the debugging output when your XP machine terminates?

---

### Post by MaindotC on 2009-04-08
From a terminal, type:
```

VirtualBox

```
Start your XP vm and when the machine closes there should be some errors that are printed in the terminal.  Copy them from the terminal so I can see them.

---

### Post by drapsjap on 2009-04-08
Before even starting the VM, the terminal gives the following error: 

```
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.24-22-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
WARNING: The compilation of the vboxdrv.ko kernel module failed during the
         installation for some reason. Starting a VM will not be possible.
         Please consult the User Manual for build instructions.
```

I've tried reinstalling VirtualBox, no results yet. Might this problem be the cause for the error I've posted before?

---

### Post by drapsjap on 2009-04-08
I've tried recompiling the module using the command given by the previous error message. After a few seconds I got the following response:

```
 * Look at /var/log/vbox-install.log to find out what went wrong
```

Here's the content of the vbox-install.log file:
```

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  2.1.4

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 2.1.4
Kernel:  2.6.27-11-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.27-11-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod......

DKMS: uninstall Completed.

------------------------------
Deleting module version: 2.1.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.1.4/source ->
                 /usr/src/vboxdrv-2.1.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-22-generic cannot be found at
/lib/modules/2.6.24-22-generic/build or /lib/modules/2.6.24-22-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop. 
```

---

### Post by MaindotC on 2009-04-08
I'm not familiar with this error message but judging by the message it's looking for the source code of the kernel.  Just search for the 2.6.24-22 source in one of the package managers and install it.  Do you not have any folders in /lib/modules?  Mine looks like this:
```

name@name:~$ ls /lib/modules/
2.6.24-16-generic  2.6.24-21-generic  2.6.24-23-386      2.6.24-23-rt
2.6.24-19-generic  2.6.24-22-generic  2.6.24-23-generic  2.6.24-23-server
name@name:~$

```

---

### Post by Perryg on 2009-04-09
I had this happen once.  Here is what I did to fix it:
uninstall VBox.
uninstall dkms
uninstall kernel-headers
reinstall dkms
reinstall kernel-headers

installed the latest vbox direct from vbox by adding its repository to Ubuntu.(shows how on the virtualbox.org site) While I was at it I got the PUEL version because it has all of the features.

The reason for all of the above is I had corrupt entries in dkms that vbox sometimes causes when you uninstall.  It was quicker to uninstall and reinstall then to figure out how to clean up the mess.  The reason for the kernel-headers is so they would stay in sync with the kernel and vbox would not complain.

---

### Post by dseybert on 2009-05-12
I'm having the same problem. I've tried the above... re-installing, re-compiling, etc... Here's my folders in /lib/modules:

```
ls /lib/modules/
2.6.20-16-generic  2.6.24-19-generic  2.6.28-11-generic  2.6.28-3-rt
2.6.22-14-generic  2.6.27-11-generic  2.6.28-11-server   2.6.28-6-386

```

And here's my log file:

```
Deleting module version: 2.2.2
completely from the DKMS tree.
------------------------------
Done.
  removing old DKMS module vboxdrv version  2.2.2

Error! There are no instances of module: vboxdrv
2.2.2 located in the DKMS tree.
  removing old DKMS module vboxdrv version  2.2.2

Error! There are no instances of module: vboxdrv
2.2.2 located in the DKMS tree.

Creating symlink /var/lib/dkms/vboxdrv/2.2.2/source ->
                 /usr/src/vboxdrv-2.2.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.27-11-generic cannot be found at
/lib/modules/2.6.27-11-generic/build or /lib/modules/2.6.27-11-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:140: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```


Please help!!!

---

### Post by MaindotC on 2009-05-12
Is this from the repos?  You can download a .deb for Jaunty [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)  Also, I see those directories you listed but could you verify that you installed the kernel source (i believe that is referred to as kernel headers)?

---

### Post by dseybert on 2009-05-12
I added that loaction to my repos and installed it from there, so I have the latest 2.2. I also have un-installed and re-installed kernel-headers. There are quite a few different packages associated with kernel-headers. I wasn't sure which one I needed, so I just installed them all.

---

### Post by dseybert on 2009-05-13
Anybody?

---

### Post by Perryg on 2009-05-13
What does this give you?
sudo apt-get install linux-headers-$(uname -r)

---

### Post by dseybert on 2009-05-13
This is what I get:

> root@xxx-:/home/xxxx# sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.27-11-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.27-11-generic has no installation candidate


---

### Post by Perryg on 2009-05-13
Well that pretty much says it all.  From what I see they are not supporting the kernel-headers any more on your kernel version and OS version (at least in the Repo's).  I have seen this a few times now.  You only have a few options here.  Contact Ubuntu about the headers or upgrade.

---

### Post by dseybert on 2009-05-14
I just looked around a bit (and I'm still looking) but could you please point me in the direction of some instructions on updating my kernel?

Thanks!

---

### Post by MaindotC on 2009-05-14
Use Synaptic instead of apt. It should fix that stuff for you.

---

### Post by dseybert on 2009-05-14
> **strAlan said:**
> Use Synaptic instead of apt. It should fix that stuff for you.

I've tried using synaptic to un-install and re-install Vbox, DKMS, and kernel-headers. Synaptic shows that I have the files installed for kernel-headers-2.6.28, but when I look under system info it shows that I'm running 2.6.27.

---

### Post by Perryg on 2009-05-14
When you boot the machine are you presented with a choice of which kernel you want to load?

---

### Post by dseybert on 2009-05-14
I am. My choices are 2.6.27-11, 2.6.24-19, 2.6.22-14, 2.6.20-16. I don't have 2.6.28 as an option. :(

---

### Post by dseybert on 2009-05-15
bump

---

### Post by miwaypet on 2009-05-15
Time to start over. I know, but is best.

```
sudo apt-get remove --purge virtualbox*
```

Now go [here]("http://writingoutloudblog.blogspot.com/2009/05/virtualbox-in-ubuntu-904.html"). Follow the instructions for installing VB. There should be no problems with making a machine after that. 

Let me emphasize this: some linux distros that you may want to virtualize will not have GNU compilers, make, or kernel source. Just a heads up.

I have not had many issues with vitualizing windows. Let me know how you get on.

---

### Post by MaindotC on 2009-05-15
miwaypet, forgive me for going back a little further but he should also address the issue of menu choices.

dseybert post the output of (two commands):
```

ls /boot
cat /boot/grub/menu.lst

```
Your menu.lst may be messed up.

---

### Post by dseybert on 2009-05-15
> doug@dougs-laptop:~$ ls /boot
abi-2.6.20-16-generic             initrd.img-2.6.24-19-generic.bak
abi-2.6.22-14-generic             initrd.img-2.6.27-11-generic
abi-2.6.24-19-generic             initrd.img-2.6.28-11-generic
abi-2.6.27-11-generic             memtest86+.bin
abi-2.6.28-11-generic             System.map-2.6.20-16-generic
config-2.6.20-16-generic          System.map-2.6.22-14-generic
config-2.6.22-14-generic          System.map-2.6.24-19-generic
config-2.6.24-19-generic          System.map-2.6.27-11-generic
config-2.6.27-11-generic          System.map-2.6.28-11-generic
config-2.6.28-11-generic          vmcoreinfo-2.6.27-11-generic
grub                              vmcoreinfo-2.6.28-11-generic
initrd.img-2.6.20-16-generic      vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak  vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic      vmlinuz-2.6.24-19-generic
initrd.img-2.6.22-14-generic.bak  vmlinuz-2.6.27-11-generic
initrd.img-2.6.24-19-generic      vmlinuz-2.6.28-11-generic


> title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ce9b55d7-894d-420d-86c5-1956adacf5ca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ce9b55d7-894d-420d-86c5-1956adacf5ca ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce9b55d7-894d-420d-86c5-1956adacf5ca ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce9b55d7-894d-420d-86c5-1956adacf5ca ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ce9b55d7-894d-420d-86c5-1956adacf5ca ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ce9b55d7-894d-420d-86c5-1956adacf5ca ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ce9b55d7-894d-420d-86c5-1956adacf5ca ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ce9b55d7-894d-420d-86c5-1956adacf5ca ro  single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

From the looks of it it's in there waiting to come out. 

> config-2.6.28-11-generic          vmcoreinfo-2.6.27-11-generic

How do I get it as an option on the boot list?

Thanks for the help!

---

### Post by Perryg on 2009-05-16
That's what I thought.  Failed install somehow.
You need to edit the menu.lst to add the missing information.

First be very careful when editing this file!
Open the menu.lst in vi or gedit and copy the top line in the file with the newest kernel version that is available in the menu list that DOES NOT have recovery in the line.  Paste it just above the one you copied and edit the version information to match the 2.6.28-11-generic.  Remember that you will just be changing the numbers.  Save and then boot to that version.  You may need to press esc at boot to select but if it is at the top it should be the default.  This way you can see that it will actually boot to that kernel.  If this works then there are a few things that you can do.  After you are sure that everything is working I would run an autoclean to cleanup the grub and also get rid of unneeded files. Read up on the apt-get autoclean and autoremove functions to see if this is something that you want to do.

---

