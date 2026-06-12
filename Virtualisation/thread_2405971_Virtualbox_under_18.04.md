---
title: "Virtualbox under 18.04"
date: 2018-11-13
forum: Virtualisation
---

### Post by jakisback on 2018-11-13
I have the same problem with VirtualBox, I used the comman dmesg and searched for[COLOR=#0000FF]  [/COLOR][COLOR=#0000FF]/sbin/vboxconfig but there is no such directory as sbin or vboxconfig. [/color]
Can someone please give me the command to install these directories, I'm new to linux.

I downloaded my virtualbox from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) version 5.2.22,
My OS is Ubuntu release 18.04.1 LTS (Bionic Beaver) 64 bit
Kernel Linux 4.15.0-38-generic x86_64
MATE 1.20.1

---

### Post by QIII on 2018-11-13
Moved to its own thread.

Please don't hijack the threads of other users -- particularly old ones.  Hijacking causes confusion for the original poster, for anyone who tries to help -- and for you.  Similar symptoms often arise from very different causes, so both you and the OP need individual help.

Thanks.

---

### Post by ajgreeny on 2018-11-14
As I have no idea what your basic problem is, can you please give more details.

I have VBox 5.2.22 direct from the repos available from the VBox site and that works very well for both Windows and Linux distro VMs.
What are you having problems with; what does not work as you want?

---

### Post by jakisback on 2018-11-14
When I try to start my **linuxmint-19-cinnamon-64bit-v2.iso** virtual machiene on VirtualBox I get this,


Failed to open a session for the virtual machine Linux Mint.

The virtual machine 'Linux Mint' has terminated unexpectedly during startup with exit code 1 (0x1).

```
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {85cd948e-a71f-4289-281e-0ca7ad48cd89}
```


And this,

```

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/sbin/vboxconfig'

as root.
```

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.

When I run the command I get 

```
:~$ sudo /sbin/vboxconfig
[sudo] password for jak: 
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.
```

And I cant find /sbin/vboxconfig in dmesg,
if that even what i'm supposed to be doing for this

---

### Post by SeijiSensei on 2018-11-15
OK.  I suggest you remove whatever version of VirtualBox you have now and follow this procedure to install the version in the Oracle repository:  [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

VB needs to install a kernel module which must be compiled from source each time the software is installed or updated.  You likely don't have the required infrastructure (the gcc compiler, the dkms module manager, etc.) on your machine.  The version at Oracle will automatically download all such "dependencies" it needs and will compile and install the module.  Future updates to VB will be managed just like all other updates to your machine's software as well.

---

