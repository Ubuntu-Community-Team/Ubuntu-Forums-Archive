---
title: "Need Help with Error Message In Trying to Install a Virtual Machine"
date: 2017-01-23
forum: Virtualisation
---

### Post by jaydub868 on 2017-01-23
I'm a new user to Ubuntu.  I downloaded VirtualBox 5.1.14 to UbuntuMate 16.04 so that I can run a virtual install of Win10.  I also downloaded the related extension set.  When I start the virtual machine to install Win10, I get the following error message:

```
Failed to open a session for the virtual machine Win10.
The virtual machine 'Win10' has terminated unexpectedly during startup with exit code 1 (0x1).
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {b2547866-a0a1-4391-8b86-6952d82efaa0}
```

On a sub-screen, the error code continues:

```
Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing
'/sbin/vboxconfig' as root.
where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 
```


So, then I open up the terminal, change the directory to '/', type in '/sbin/vboxconfig', and I get the following response: 

```
jaydub@jaydub-System-Product-Name:~$ cd /
jaydub@jaydub-System-Product-Name:/$ /sbin/vboxconfig
rm: cannot remove '/sbin/rcvboxdrv': Permission denied
ln: failed to create symbolic link '/sbin/rcvboxdrv': File exists
/sbin/vboxconfig: 130: /sbin/vboxconfig: cannot create /lib/systemd/system/vboxdrv.service: Permission denied
```


In System, Administration, Users and Groups, Advanced Settings, User Privileges I see that "Use Virtual Box Virtualization Solution" is checked.

So, I'm really stumpted.  Any ideas for a solution?

---

### Post by wildmanne39 on 2017-01-23
*Thread moved to **Virtualisation**.*

---

### Post by ODTech on 2017-01-24
> **jaydub868 said:**
> I'm a new user to Ubuntu.  I downloaded VirtualBox 5.1.14 to UbuntuMate 16.04 so that I can run a virtual install of Win10.  I also downloaded the related extension set.  When I start the virtual machine to install Win10, I get the following error message:

[I]Failed to open a session for the virtual machine Win10.
The virtual machine 'Win10' has terminated unexpectedly during startup with exit code 1 (0x1).
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {b2547866-a0a1-4391-8b86-6952d82efaa0}[/I]

On a sub-screen, the error code continues:

[I]Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing
'/sbin/vboxconfig' as root.
where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 
[/I]

So, then I open up the terminal, change the directory to '/', type in '/sbin/vboxconfig', and I get the following response: 

[I]jaydub@jaydub-System-Product-Name:~$ cd /
jaydub@jaydub-System-Product-Name:/$ /sbin/vboxconfig
rm: cannot remove '/sbin/rcvboxdrv': Permission denied
ln: failed to create symbolic link '/sbin/rcvboxdrv': File exists
/sbin/vboxconfig: 130: /sbin/vboxconfig: cannot create /lib/systemd/system/vboxdrv.service: Permission denied
[/I]

In System, Administration, Users and Groups, Advanced Settings, User Privileges I see that "Use Virtual Box Virtualization Solution" is checked.

So, I'm really stumpted.  Any ideas for a solution?

Hi There.

In most cases executing any command outsides of your home folder requires root privileges so do.

 ```
sudo /sbin/vboxconfig
```
Then type your own user password.

It doesn't matter in what directory you are in as the path to the file to be executed is complete.

---

### Post by jaydub868 on 2017-01-24
Many thanks for that.  So, I did that and I get this:

```
jaydub@jaydub-System-Product-Name:~$ cd /
jaydub@jaydub-System-Product-Name:/$ sudo /sbin/vboxconfig
[sudo] password for jaydub: 
vboxdrv.sh: Building VirtualBox kernel modules.
This system is not currently set up to build kernel modules (system extensions).
Running the following commands should set the system up correctly:

  apt-get install gcc make
vboxdrv.sh: failed: Look at /var/log/vbox-install.log to find out what went wrong.
This system is not currently set up to build kernel modules (system extensions).
Running the following commands should set the system up correctly:

  apt-get install gcc make

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.
jaydub@jaydub-System-Product-Name:/$ 
```

Is it asking me to re-install.  If I do that, should I also be doing something in addition?

---

### Post by ian-weisser on 2017-01-24
> **jaydub868 said:**
> I downloaded VirtualBox 5.1.14 to UbuntuMate 16.04 so that I can run a virtual install of Win10.
Win10 runs just fine in the default version of VirtualBox already in the Ubuntu repositories...along with it's dependencies (like virtualbox-dkms). There is no need to download it from elsewhere.

Where exactly did you get 5.1.14 from?
Did you have any errors while installing it?
Do you have virtualbox-dkms 5.1.14 installed?

---

### Post by jaydub868 on 2017-01-24
My original install was downloaded by me directly from the Oracle website.  Didn't know you could retrieve from Ubuntu repositories.
Anyway, after googling around for instructions, I successfully uninstalled it from my system, including the virtual machines folder.
I found Vbox in Ubuntu Software Center (version 5.0.24, slightly older than the current version 5.1.14).  Should I just do a straight away install from there, or are there preparatory steps to take?  
I'm pretty sure that if virtualbox-dkms was installed, it's no longer there now.

EDIT:
I see that it is also in Synaptic Package Manager and that there are several affiliated files, including two with 'dkms' in the title.  

Any advice on that best way to proceed would be highly helpful.

---

### Post by ian-weisser on 2017-01-24
Simply install the Ubuntu 'virtualbox' package using any convenient package manager frontend.

If the install fails, then use apt in a terminal (sudo apt install virtualbox) and show us the complete output.

---

### Post by ODTech on 2017-01-24
> **jaydub868 said:**
> My original install was downloaded by me directly from the Oracle website.  Didn't know you could retrieve from Ubuntu repositories.
Anyway, after googling around for instructions, I successfully uninstalled it from my system, including the virtual machines folder.
I found Vbox in Ubuntu Software Center (version 5.0.24, slightly older than the current version 5.1.14).  Should I just do a straight away install from there, or are there preparatory steps to take?  
I'm pretty sure that if virtualbox-dkms was installed, it's no longer there now.

EDIT:
I see that it is also in Synaptic Package Manager and that there are several affiliated files, including two with 'dkms' in the title.  

Any advice on that best way to proceed would be highly helpful.

You can also do 
```
sudo apt-get update
```
then
```
sudo apt-get install virtualbox
```
If it fails with a dependency problem then do.
```
sudo apt-get install -f
```

---

### Post by jaydub868 on 2017-01-24
Thanks Ian Weisser.  I installed VirtualBox from Ubuntu Software Center, and then the extension pack and guest additions from Synaptic Package Manager.  All is working great!!!!  Thanks much.

---

### Post by jaydub868 on 2017-01-24
My specs are:
Host: UbuntuMate 16.04  64-bit
Virtualization:  VirtualBox 5.0.24_Ubuntu r108355 + Extension Pack + Guest Additions (all installed via Ubuntu Software Center and SPM).
Guest:  Windows 10 Anniversary Edition 1067   64-Bit

Everything is running great, except audio is terrible.  Lots of static, some breakup, and uneven sound speed (warbling).  I found a few other threads that complain about the same thing. 
I'm using INTEL HD Audio + Pulse, which are the Vbox defaults.  I tried the other options AC'97, Alsa, Null and OSS and they either don't work or have the same problem.
Are there any workarounds yet?

---

