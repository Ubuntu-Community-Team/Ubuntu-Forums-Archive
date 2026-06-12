---
title: "The guest's resolution can't adjust to VMPlayer's window in the host"
date: 2019-03-31
forum: Virtualisation
---

### Post by yys2 on 2019-03-31
Hi all,
I use Ubuntu18.04.2, and I can't change the guest's resolution by adjusting VMPlayer's window size in host. The screenshot is attached, you can see the black margin which is  caused by the problem that the guest resolution does not adjust to the  VMPlayer window.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=282899&d=1554035448&thumb=1&stc=1[/IMG]

Here are my steps:
- On host Ubuntu18.04.2, I installed a guest Ubuntu 18.04.2 in VMware Player15. "Virtual Machine Settings > Hardware > Display >Monitors > Use host settings for monitors" is selected, which is the default value. 
I remember that, at this stage, the guest's resolution can adjust to VMPlayer's window size in host.
- Then, I thought it would be better to install vmware tools. And I followed this guide([https://linuxconfig.org/install-vmware-tools-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/install-vmware-tools-on-ubuntu-18-04-bionic-beaver-linux)) to install vmware tools. Here are the steps:
- sudo apt install open-vm-tools-desktop
- Download VMwareTools-10.3.2-9925305.tar.gz from VMware official website, and  unzip it.
- $sudo ./VMwareTools-10.3.2-9925305/vmware-tools-distrib/vmware-install.pl. And use all the default settings, here is the log:
```

========================Log begin===================================
user0@mypc:~/Documents/VMwareTools-10.3.2-9925305/vmware-tools-distrib$ ls
bin  doc  FILES    installer  vgauth
caf  etc  INSTALL  lib        vmware-install.pl
user0@mypc:~/Documents/VMwareTools-10.3.2-9925305/vmware-tools-distrib$ sudo ./vmware-install.pl 
[sudo] password for lsolory: 
The installer has detected an existing installation of open-vm-tools packages 
on this system and will not attempt to remove and replace these user-space 
applications. It is recommended to use the open-vm-tools packages provided by 
the operating system. If you do not want to use the existing installation of 
open-vm-tools packages and use VMware Tools, you must uninstall the 
open-vm-tools packages and re-run this installer.
The packages that need to be removed are:
open-vm-tools
Packages must be removed with the --purge option.
The installer will next check if there are any missing kernel drivers. Type yes
if you want to do this, otherwise type no [yes] 

INPUT: [yes]  default

Creating a new VMware Tools installer database using the tar4 format.

Installing VMware Tools.

In which directory do you want to install the binary files? 
[/usr/bin] 

INPUT: [/usr/bin]  default

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

INPUT: [/etc]  default

What is the directory that contains the init scripts? 
[/etc/init.d] 

INPUT: [/etc/init.d]  default

In which directory do you want to install the daemon files? 
[/usr/sbin] 

INPUT: [/usr/sbin]  default

In which directory do you want to install the library files? 
[/usr/lib/vmware-tools] 

INPUT: [/usr/lib/vmware-tools]  default

The path "/usr/lib/vmware-tools" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

INPUT: [yes]  default

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware-tools] 

INPUT: [/usr/share/doc/vmware-tools]  default

The path "/usr/share/doc/vmware-tools" does not exist currently. This program 
is going to create it, including needed parent directories. Is this what you 
want? [yes] 

INPUT: [yes]  default

The installation of VMware Tools 10.3.2 build-9925305 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 

INPUT: [yes]  default


You have chosen to install VMware Tools on top of an open-vm-tools package.  
You will now be given the option to replace some commands provided by 
open-vm-tools.  Please note that if you replace any commands at this time and 
later remove VMware Tools, it may be necessary to re-install the open-vm-tools.

The file /usr/bin/vmware-hgfsclient that this program was about to install 
already exists.  Overwrite? [no] 

INPUT: [no]  default

The file /sbin/mount.vmhgfs that this program was about to install already 
exists.  Overwrite? [no] 

INPUT: [no]  default

The file /usr/bin/vmhgfs-fuse that this program was about to install already 
exists.  Overwrite? [no] 

INPUT: [no]  default

Initializing...


Making sure services for VMware Tools are stopped.

Stopping VMware Tools services in the virtual machine:
   VMware User Agent (vmware-user):                                    done
   Unmounting HGFS shares:                                             done
   Guest filesystem driver:                                            done


The module vmci has already been installed on this system by another installer 
or package and will not be modified by this installer.

The module vsock has already been installed on this system by another installer
or package and will not be modified by this installer.

The module vmxnet3 has already been installed on this system by another 
installer or package and will not be modified by this installer.

The module pvscsi has already been installed on this system by another 
installer or package and will not be modified by this installer.

The module vmmemctl has already been installed on this system by another 
installer or package and will not be modified by this installer.

The VMware Host-Guest Filesystem allows for shared folders between the host OS 
and the guest OS in a Fusion or Workstation virtual environment.  Do you wish 
to enable this feature? [yes] 

INPUT: [yes]  default

The vmxnet driver is no longer supported on kernels 3.3 and greater. Please 
upgrade to a newer virtual NIC. (e.g., vmxnet3 or e1000e)

VMware automatic kernel modules enables automatic building and installation of
VMware kernel modules at boot that are not already present. This feature can
be enabled/disabled by re-running vmware-config-tools.pl.

Would you like to enable VMware automatic kernel modules?
[yes] 

INPUT: [yes]  default

Creating a new initrd boot image for the kernel.
update-initramfs: Generating /boot/initrd.img-4.18.0-16-generic
The configuration of VMware Tools 10.3.2 build-9925305 for Linux for this 
running kernel completed successfully.

Enjoy,

--the VMware team

========================Log End============================

```

- Then I rebooted the guest OS. The problem still exists.



- Then I reinstalled vmware tools:
$sudo ./VMwareTools-10.3.2-9925305/vmware-tools-distrib/vmware-install.pl.
And let the following file be overwritten:
/usr/bin/vmware-hgfsclient
/sbin/mount.vmhgfs
/usr/bin/vmhgfs-fuse
Here is the log:
```

========================Log Begin==========================
user0@mypc:~/Documents/VMwareTools-10.3.2-9925305/vmware-tools-distrib$ ls
bin  caf  doc  etc  FILES  INSTALL  installer  lib  vgauth  vmware-install.pl
user0@mypc:~/Documents/VMwareTools-10.3.2-9925305/vmware-tools-distrib$ sudo ./vmware-install.pl 
[sudo] password for lsolory: 
The installer has detected an existing installation of open-vm-tools packages 
on this system and will not attempt to remove and replace these user-space 
applications. It is recommended to use the open-vm-tools packages provided by 
the operating system. If you do not want to use the existing installation of 
open-vm-tools packages and use VMware Tools, you must uninstall the 
open-vm-tools packages and re-run this installer.
The packages that need to be removed are:
open-vm-tools
Packages must be removed with the --purge option.
The installer will next check if there are any missing kernel drivers. Type yes
if you want to do this, otherwise type no [yes] 

INPUT: [yes]  default

A previous installation of VMware Tools has been detected.

The previous installation was made by the tar installer (version 4).

Keeping the tar4 installer database format.

You have a version of VMware Tools installed.  Continuing this install will 
first uninstall the currently installed version.  Do you wish to continue? 
(yes/no) [yes] 

INPUT: [yes]  default

Uninstalling the tar installation of VMware Tools.

Stopping services for VMware Tools

Stopping VMware Tools services in the virtual machine:
   VMware User Agent (vmware-user):                                    done
   Unmounting HGFS shares:                                             done
   Guest filesystem driver:                                            done

The removal of VMware Tools 10.3.2 build-9925305 for Linux completed 
successfully.

Installing VMware Tools.

In which directory do you want to install the binary files? 
[/usr/bin] 

INPUT: [/usr/bin]  default

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

INPUT: [/etc]  default

What is the directory that contains the init scripts? 
[/etc/init.d] 

INPUT: [/etc/init.d]  default

In which directory do you want to install the daemon files? 
[/usr/sbin] 

INPUT: [/usr/sbin]  default

In which directory do you want to install the library files? 
[/usr/lib/vmware-tools] 

INPUT: [/usr/lib/vmware-tools]  default

The path "/usr/lib/vmware-tools" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

INPUT: [yes]  default

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware-tools] 

INPUT: [/usr/share/doc/vmware-tools]  default

The path "/usr/share/doc/vmware-tools" does not exist currently. This program 
is going to create it, including needed parent directories. Is this what you 
want? [yes] 

INPUT: [yes]  default

The installation of VMware Tools 10.3.2 build-9925305 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 

INPUT: [yes]  default


You have chosen to install VMware Tools on top of an open-vm-tools package.  
You will now be given the option to replace some commands provided by 
open-vm-tools.  Please note that if you replace any commands at this time and 
later remove VMware Tools, it may be necessary to re-install the open-vm-tools.

The file /usr/bin/vmware-hgfsclient that this program was about to install 
already exists.  Overwrite? [no] yes

INPUT: [yes]

The file /sbin/mount.vmhgfs that this program was about to install already 
exists.  Overwrite? [no] yes

INPUT: [yes]

The file /usr/bin/vmhgfs-fuse that this program was about to install already 
exists.  Overwrite? [no] yes

INPUT: [yes]

Initializing...


Making sure services for VMware Tools are stopped.

Stopping VMware Tools services in the virtual machine:
   VMware User Agent (vmware-user):                                    done
   Unmounting HGFS shares:                                             done
   Guest filesystem driver:                                            done


The module vmci has already been installed on this system by another installer 
or package and will not be modified by this installer.

The module vsock has already been installed on this system by another installer
or package and will not be modified by this installer.

The module vmxnet3 has already been installed on this system by another 
installer or package and will not be modified by this installer.

The module pvscsi has already been installed on this system by another 
installer or package and will not be modified by this installer.

The module vmmemctl has already been installed on this system by another 
installer or package and will not be modified by this installer.

The VMware Host-Guest Filesystem allows for shared folders between the host OS 
and the guest OS in a Fusion or Workstation virtual environment.  Do you wish 
to enable this feature? [yes] 

INPUT: [yes]  default

The vmxnet driver is no longer supported on kernels 3.3 and greater. Please 
upgrade to a newer virtual NIC. (e.g., vmxnet3 or e1000e)

VMware automatic kernel modules enables automatic building and installation of
VMware kernel modules at boot that are not already present. This feature can
be enabled/disabled by re-running vmware-config-tools.pl.

Would you like to enable VMware automatic kernel modules?
[yes] 

INPUT: [yes]  default

Creating a new initrd boot image for the kernel.
update-initramfs: Generating /boot/initrd.img-4.18.0-16-generic
The configuration of VMware Tools 10.3.2 build-9925305 for Linux for this 
running kernel completed successfully.

Enjoy,

--the VMware team
========================Log End============================

```


- Then rebooted the guest OS. But it doesn't help.

Could anyone tell me how to solve this problem?

---

### Post by deadflowr on 2019-03-31
*Thread moved to **Virtualization***

---

