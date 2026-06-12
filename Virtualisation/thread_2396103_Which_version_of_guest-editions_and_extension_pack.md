---
title: "Which version of guest-editions and extension packs shall I installs"
date: 2018-07-11
forum: Virtualisation
---

### Post by satimis on 2018-07-11
Hi all,

Host - Ubuntu 16.04 gnome desktop
VM - Ubuntu 18.04 gnome desktop
VirtualBox Graphical User Interface Version 5.1.34_Ubuntu r1 (VM manager)

Please advise which version of guest-editions on the repo shall I install ?
and
which version of extension packs on the repo shall I install ?

Thanks

Regards
satimis

---

### Post by Claus7 on 2018-07-12
Hello,

I'm using VB myself, yet the installation has taken place from the website of oracle:
[https://www.virtualbox.org/wiki/Download_Old_Builds_5_1](https://www.virtualbox.org/wiki/Download_Old_Builds_5_1)

Actually, the link I have provided is about older builds of VB, like the one you are using. From there you will be able to find the extension pack you are after. 
As far as the guest additions are concerned when your guest os is on and running, from Desktop there is:
VBox_GAs 

and from there, as root, we install the VBoxLinuxAdditions.run, which corresponds to the version of your VB.

I suppose that this helps, unless I have not understood correctly your issue.

Regards!

---

### Post by satimis on 2018-07-12
> **Claus7 said:**
> Hello,

I'm using VB myself, yet the installation has taken place from the website of oracle:
[https://www.virtualbox.org/wiki/Download_Old_Builds_5_1](https://www.virtualbox.org/wiki/Download_Old_Builds_5_1)

Actually, the link I have provided is about older builds of VB, like the one you are using. From there you will be able to find the extension pack you are after. 
As far as the guest additions are concerned when your guest os is on and running, from Desktop there is:
VBox_GAs 

and from there, as root, we install the VBoxLinuxAdditions.run, which corresponds to the version of your VB.

I suppose that this helps, unless I have not understood correctly your issue.

Regards!
Hi,

Thanks for your advice.

This is a spare PC only used occasionally.  I supposed VirtualBox manager was installed on Ubuntu repo. Please see attached screenshots;
1) screenshot_vm_manager.png
2) screenshot_vm_icon.png

Sorry I couldn't recall when it was installed.  IIRC I ran VirtualBox download on Oracle website first.  Then I changed to install it on Ubuntu repo.  Therefore some VMs were built on Oracle version and others on Ubuntu repo version

Just installed Ubuntu 18.04 VM and copy/paste between Host and VM doesn't work.  I suppose it needs to install the guest-addition.  But I have no idea which package on the repo is correct?

Also some VMs there can't be started.

Warning:```

Implementation of the USB 3.0 controller not found!
Because the USB 3.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 3.0 support in the VM settings (VERR_NOT_FOUND).

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
ConsoleWrap
Interface: 
IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

```

But others can be started.  It is very strange to me.

Regards
satimis

---

### Post by Claus7 on 2018-07-12
Hello,

your version is one of the latest ones of virtualbox. In order to verify that indeed is installed from repo, then you can open synaptic, search for virtualbox and check if there is an option to update it (which I doubt). If you can, then it seems that you installed it from a repository, which escapes me how you did it. If not, then you installed it manually.

Irrespective of how you installed it, as I mentioned before, in order to enable the copy-paste feature between host and guest among others, you should first have to install the Guest Additions in your guest os. This can take place inside the guest os. You should be able to see an optical drive icon in the Desktop of your guest os. Then, in order to enable that feature, you should:
click Devices | Shared Clipboard | Bidirectional

I do not understand the "can be started" quote of yours. Support of usb 3.0 is not enabled by default. You should enable it from Settings->usb->usb 3.0.

Regards!

---

### Post by satimis on 2018-07-12
> **Claus7 said:**
> 
your version is one of the latest ones of virtualbox. In order to verify that indeed is installed from repo, then you can open synaptic, search for virtualbox and check if there is an option to update it (which I doubt). If you can, then it seems that you installed it from a repository, which escapes me how you did it. If not, then you installed it manually.
Hi,

I trust that this VirtualBox Manager was installed on repo.  On my daily working PC the VirtualBox Manager was installed on the ISO download on Oracle website.  The icon looks completely different.

> 
Irrespective of how you installed it, as I mentioned before, in order to enable the copy-paste feature between host and guest among others, you should first have to install the Guest Additions in your guest os. This can take place inside the guest os. 

In the past I have done many times installing Guest Addtions.  But if installing a wrong version the VM can't be started.  The only solution is to delete the VM.

> 
You should be able to see an optical drive icon in the Desktop of your guest os. Then, in order to enable that feature, you should:
click Devices | Shared Clipboard | Bidirectional
Already checked

> 
I do not understand the "can be started" quote of yours. Support of usb 3.0 is not enabled by default. You should enable it from Settings->usb->usb 3.0.

I must check USB 1.1 otherwise the VM can't be started.  Also I can resolve WHY?

Regards
satimis

---

### Post by Claus7 on 2018-07-14
Hello,

I would like to inform you that even if VB is deleted, this won't delete the Machines (operating systems) you have installed. I had upgraded the other time my ubu box and the VB was not capable of starting. When the new version of VB was released, supporting ubuntu 18.04, all my machines were there (of course I had not deleted them from my ubu box, apart from VB itself).

As a result: since there is an issue about the version of VB you have installed and how it is installed: Why don't you get rid of what you have and install a fresh new version? That way, when you install VB, you will be verify that Guest Additions will be the right ones. My impression is that you have messed the installations, that's why you get the problems you are facing.

Some more info:

1) Verify version of VB
(you have already showed a screenshot - mine is:)
VirtualBox Graphical User Interface
Version 5.2.8 r121009 (Qt5.9.5)
Copyright © 2018 Oracle Corporation and/or its affiliates. All rights r

2) Verify version of Guest Additions
i) start desired OS from VB
ii) on top go to: Devices->Insert Guest Additions CD image...
iii) the icon that will appear on Desktop will show the version of Guest Additions
mine is: VBox_GAs_5.2.8

3) check version from synaptic
open synaptic package manager and type: virtualbox
in the search tab, in order to check what is going on there

Now, using ubuntu 18.04, I have installed VB from oracle's website. In synaptic I can see 2 packages installed:
unity-scope-virtualbox
virtualbox-5.2 (in the description I can see: Oracle VM VirtualBox)

I have other packages listed (17 in total) that comprise the name virtualbox, including one that is virtualbox-guest-additions-iso, yet they are not installed. Check from there if you have installed anything more. If you have more packages and versions installed, it would be advisable to remove them and then add only the latest one.

Under my home directory I can see the folder:
VirtualBox VMs

this is the folder where all your machines are found. You can backup this folder, in case accidentally removed, so as not to mess with your virtual machines.

4) How to enable copy/paste between Host and VM:
i) start desired OS from VB
ii) on top go to: Devices->Insert Guest Additions CD image...
iii) click on the icon that will appear on Desktop
iv) install as root the VBoxLinuxAdditions.run file:
sudo ./VBoxLinuxAdditions.run
(having the Bidirectional option checked without following these steps, copy/paste won't work) 
v) restart OS
vi) go to Deviced->Shared Clipboard->Bidirectional
vii) copy/paste from guest to host and vice versa for testing: it should work!

Regards!

---

### Post by satimis on 2018-07-14
Hi Claus7,

Thanks for your detail advice.

In the past I have installed Guest Additions for many times.  Also I learned bitter lessons if installing the wrong version unable to boot the VM would be the result.

For safety I cloned a new VM on Ubuntu18.04 VM.  If failure unable to reboot the cloned VM after installing the Guest Additions I just delete it.

Steps performed as follows;
1. Clone a new VM and start it
2. On terminal run;```

sudo apt install linux-headers-$(uname -r) build-essential dkms

```
3. Reboot the cloned VM
4. Devices -> Insert Guest Additions CD image
Guest Additions was automatically installed straightforwards after entering the root password and without problem.
5. Reboot the cloned VM

Failed to boot;
warning: failed to connect to lvmetad. Falling back to device scanning.

Regards
satimis

---

### Post by Claus7 on 2018-07-16
Hello,

from some search I came across these two links:
[https://askubuntu.com/questions/745218/ubuntu-wont-boot-because-of-lvmetad](https://askubuntu.com/questions/745218/ubuntu-wont-boot-because-of-lvmetad)
and
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230)

From the first one you could try the following:
start virtual machine and drop to command line (press Ctrl+Alt+F2). Then try to change the file lvm.conf as mentioned in the first link.

From the second one you have a lot of things to read, since it is mentioned that what affects you is a bug. If you cannot solve your issue, I would suggest you the oracle's vb, since the version I'm using is pretty descent.

Regards!

---

### Post by satimis on 2018-07-16
> **Claus7 said:**
> Hello,

from some search I came across these two links:
[https://askubuntu.com/questions/745218/ubuntu-wont-boot-because-of-lvmetad](https://askubuntu.com/questions/745218/ubuntu-wont-boot-because-of-lvmetad)
and
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230)

From the first one you could try the following:
start virtual machine and drop to command line (press Ctrl+Alt+F2). Then try to change the file lvm.conf as mentioned in the first link.

From the second one you have a lot of things to read, since it is mentioned that what affects you is a bug. If you cannot solve your issue, I would suggest you the oracle's vb, since the version I'm using is pretty descent.

Regards!
Hi,

Thanks for your advice and links.

I have made another test as follow;
1. Clone another new VM and start it
2. On terminal run;
```

sudo apt install linux-headers-$(uname -r) build-essential dkms

```
3. Reboot the cloned VM
4. Devices -> Optical Drives -> Choose Disk Images
-> VBoxGuestAddition_5.0.4.iso
(It was previously download on Oracle website)

Install VBoxGuestAddition_5.0.4.iso
Reboot VM

Now this VM can be started without problem but copy/paste between Host and VM still not working.

Settings -> General -> Advanced
Shared Clipboard: [Bidriectional]
Drag'n'Drop:  [Bidriectional]

I suppose it is because the correct version of Oracle VM virtualBox Extension Pack has not been installed.

This is a spare PC running VirtualBox and having been working for more than years.
Host - Ubuntu16.04

At the beginning the VirtualBox was download on Oracle website, later changing installing it on Ubuntu repo.  Some VMs were created at the early stage and others were created on the repo version making the system too complicate.  Now some VMs can be started and others unable to start.  The working VMs retain full features, copy/paste between Host and VM working without problem.

I'm prepare to rebuild this spare PC.  

I have a daily working PC with 1TB SSD as HD, also running VirtualBox.  The 1TB SSD is nearly full and I just ordered a new 2TB SSD;```

Samsung SSD 860 EVO SATA III 2.5 " 2TB (MZ-76E2T0BW) 

```

I'll install the old 1TB SSD on this spare PC and will come back later.

Thanks

Regards
satimis

---

### Post by SeijiSensei on 2018-07-16
There are no "guest editions" for VirtualBox 5.1 or 5.2 as far as I know.  There's just the Extension Pack.

The simplest and best method to install VB and keep it up to date is to follow the instructions at [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).  First, purge any existing versions of VB you may have, then add the Oracle repo to your system as described in that link, update apt, then install the "virtualbox-5.2" package as you would anything else.  You'll get prompted to install the matching Extension Pack when you open the VB manager, or maybe not until you start an existing VM.  The manager will handle all the steps required.  

When your system next upgrades VirtualBox, you'll be prompted to install the matching Extension Pack the next time you open the VB manager.

---

### Post by satimis on 2018-07-16
> **SeijiSensei said:**
> There are no "guest editions" for VirtualBox 5.1 or 5.2 as far as I know.  There's just the Extension Pack.

The simplest and best method to install VB and keep it up to date is to follow the instructions at [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).  First, purge any existing versions of VB you may have, then add the Oracle repo to your system as described in that link, update apt, then install the "virtualbox-5.2" package as you would anything else.  You'll get prompted to install the matching Extension Pack when you open the VB manager, or maybe not until you start an existing VM.  The manager will handle all the steps required.  

When your system next upgrades VirtualBox, you'll be prompted to install the matching Extension Pack the next time you open the VB manager.
Hi,

Thanks for your advice and links.

I'll reinstall VirtualBox on both my PC for daily working as well as the spare PC after the arrival of the new 2TB SSD.  I shall install Ubuntu 18.04 gnome desktop as Host.

I suppose the line to be added to /etc/apt/source.list will be```

deb https://download.virtualbox.org/virtualbox/debian bionic beaver contrib

```

Do I need hyphenating
```

bionic beaver

```

as;
```

bionic-beaver

```
?

Thanks

Regards
satimis

---

### Post by Claus7 on 2018-07-17
Hello,

you need to type:
deb [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) bionic contrib

Regards!

---

### Post by satimis on 2018-07-17
> **Claus7 said:**
> Hello,

you need to type:
deb [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) bionic contrib

Regards!
Thanks

Regards
satimis

---

### Post by satimis on 2018-07-19
Hi all,

Now I have received the new Samsung 860 EVO 2TB SSD ordered previously.
(Samsung SSD 860 EVO SATA III 2.5 " 2TB (MZ-76E2T0BW))

I'll use it to replace the old 1TB SSD which has been running for about 10 years, almost fully occupied and leaving about 90GB free space.

Host - Ubuntu 18.04 gnome desktop (OS)
VirtualBox

1)
Installation of OS and Virtualbox

1a)
The installer will be on an USB drive.  I suppose it doesn't need to format the new 2TB SSD manually.  The installer will format it before installing the OS?  If I'm wrong please correct me.  Thanks 

(Remark:
Sorry, I haven't built new PC for at lease 10 years)

1b)
I shall not manually create partitions on the 2TB SSD, except LVM created by the installer.  The entire new SSD will be used for running OS, VirturalBox, VMs as well as for storage of daily working files.  The old files will be stored on a 2TB WD Black Label HD on the same PC.

1c)
I shall follow the steps listed on;
Debian-based Linux distributions
[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

to install VirtualBox, download on Oracle website

I'll download and install "Oracle_VM_VirtualBox_Extension_Pack-5.2.16.vbox-extension pack" on;
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

If I'm wrong please advise me.  Thanks in advance

2)
For safety reason, before installation, I shall only connect the new 2TB SSD on the PC and all other drives will be disconnected.

Although following commands will list all HDs on the PC
```

&#10219; hwinfo --disk

```

and

```

&#10219; sudo fdisk -l

```
But to avoid making mistake, in acident, I prefer disconnecting all HDs leaving only the new 2TB SSD connected.

However I learned a bitter lessen before with this arrangement.  All other drives after connected will not be mounted automatically at booting the PC.  After booting up the PC, I have to mount them manually with following step;

On the (left vertical) menu
right-click (each drive) -> Open

Is there any solution?

3)
Migration of all VMs from the old 1TB SSD to the new 2TB SSD

Either
3a)
Export all VMs and import them to the VirtualBox Manager on the new 2TB SSD

OR
3b)
Copy/Paste or rsync all VMs including the folder "VirtualBox VMs" from the old 1TB SSD to the new 2TB SSD.  Afterwards add the VMs to VirtualBox Manager manually, one by one?

On VirtualBox Manager
Machine -> Add

Which steps, 3a) or 3b) will be more reliable?  Thanks

3c)
If selecting 3b) above, do I need to make any change on;
VM.vbox-prev
?

Please advise.  Thanks

Any other advices would be appreciated.

Regards
satimis

---

### Post by Claus7 on 2018-07-20
Hello,

some effort from my perspective to answer your questions:

> **satimis said:**
> Hi all,

Now I have received the new Samsung 860 EVO 2TB SSD ordered previously.
(Samsung SSD 860 EVO SATA III 2.5 " 2TB (MZ-76E2T0BW))

enjoy your brand new drive!

> **satimis said:**
> 
I'll use it to replace the old 1TB SSD which has been running for about 10 years, almost fully occupied and leaving about 90GB free space.

Host - Ubuntu 18.04 gnome desktop (OS)
VirtualBox

1)
Installation of OS and Virtualbox

1a)
The installer will be on an USB drive.  I suppose it doesn't need to format the new 2TB SSD manually.  The installer will format it before installing the OS?  If I'm wrong please correct me.  Thanks 

(Remark:
Sorry, I haven't built new PC for at lease 10 years)


yes! By installing ubuntu, the hdd will be prepared by default.

> **satimis said:**
> 
1b)
I shall not manually create partitions on the 2TB SSD, except LVM created by the installer.  The entire new SSD will be used for running OS, VirturalBox, VMs as well as for storage of daily working files.  The old files will be stored on a 2TB WD Black Label HD on the same PC.


Since from question (2) you want to add a 2nd drive from storage, it would be advised to follow this link:
[https://askubuntu.com/questions/125257/how-do-i-add-an-additional-hard-drive](https://askubuntu.com/questions/125257/how-do-i-add-an-additional-hard-drive)

That way, first you install your os to your ssd, and then you add the hdd storage drive.

> **satimis said:**
> 
1c)
I shall follow the steps listed on;
Debian-based Linux distributions
[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

to install VirtualBox, download on Oracle website

I'll download and install "Oracle_VM_VirtualBox_Extension_Pack-5.2.16.vbox-extension pack" on;
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

If I'm wrong please advise me.  Thanks in advance


You could. If it does not work, you can remove any time the repository from synaptic package manager (settings->repositories->other software) and download VB from oracle's website.

> **satimis said:**
> 
2)
For safety reason, before installation, I shall only connect the new 2TB SSD on the PC and all other drives will be disconnected.

Although following commands will list all HDs on the PC
```

&#10219; hwinfo --disk

```

and

```

&#10219; sudo fdisk -l

```
But to avoid making mistake, in acident, I prefer disconnecting all HDs leaving only the new 2TB SSD connected.

However I learned a bitter lessen before with this arrangement.  All other drives after connected will not be mounted automatically at booting the PC.  After booting up the PC, I have to mount them manually with following step;

On the (left vertical) menu
right-click (each drive) -> Open

Is there any solution?

See above...

> **satimis said:**
> 
3)
Migration of all VMs from the old 1TB SSD to the new 2TB SSD

Either
3a)
Export all VMs and import them to the VirtualBox Manager on the new 2TB SSD

OR
3b)
Copy/Paste or rsync all VMs including the folder "VirtualBox VMs" from the old 1TB SSD to the new 2TB SSD.  Afterwards add the VMs to VirtualBox Manager manually, one by one?

On VirtualBox Manager
Machine -> Add

Which steps, 3a) or 3b) will be more reliable?  Thanks

3c)
If selecting 3b) above, do I need to make any change on;
VM.vbox-prev
?

Please advise.  Thanks

Any other advices would be appreciated.

Regards
satimis

I did 3b without any problem, yet i)at the same computer though and ii)by leaving the folder "VirtualBox VMs" intact. By transferring (copy/paste) the folder "VirtualBox VMs" to the other computer it should work. You could test it easily, since you will have already a backup to your old disk.

Regards!

---

### Post by satimis on 2018-07-21
> **Claus7 said:**
> Hello,

some effort from my perspective to answer your questions:

..... 

Hi,

Thanks for your help.

Performed following steps:
=====================

1)
Disconnected all drives on the PC, leaving only the new 2TB SSD connected.

Booted PC with Ubuntu18.04 USB installer and installed Ubuntu 18.04 gnome desktop.  Installation went through without problem.

Reboot PC

Host - Ubuntu 18.04 Gnome desktop

$ sudo fdisk -l > fdisk_output_01.txt
(See file attached - fdisk_output_01.txt)```

Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors

```

$ free -m```

              total        used        free      shared  buff/cache   available
Mem:          32069        1777       28518         117        1774       30014
Swap:           975           0         975

```

Install bridge-utils
$ sudo apt install bridge-utils

$ ifconfig```

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.8.2  netmask 255.255.255.0  broadcast 192.168.8.255
        inet6 fe80::441d:62c7:b0bf:2dbb  prefixlen 64  scopeid 0x20<link>
        ether f0:79:59:65:2f:bb  txqueuelen 1000  (Ethernet)
        RX packets 19694  bytes 23264203 (23.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7432  bytes 1147548 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 754  bytes 72755 (72.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 754  bytes 72755 (72.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Add following line at the bottom of /etc/apt/sources.list```

deb https://download.virtualbox.org/virtualbox/debian bionic contrib

```

$ wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add - ```

OK

```

$ wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -```

OK

```

$ sudo apt-get update```

Hit:1 http://hk.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu bionic-updates InRelease                           
Hit:3 http://hk.archive.ubuntu.com/ubuntu bionic-backports InRelease                         
Get:4 https://download.virtualbox.org/virtualbox/debian bionic InRelease [4,429 B]                                 
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]                           
Get:6 https://download.virtualbox.org/virtualbox/debian bionic/contrib amd64 Packages [1,440 B]
Fetched 89.1 kB in 1s (71.6 kB/s)                                     
Reading package lists... Done
N: Skipping acquire of configured file 'contrib/binary-i386/Packages' as repository 'https://download.virtualbox.org/virtualbox/debian bionic InRelease' doesn't support architecture 'i386'

```

$ sudo apt-get install virtualbox-5.2```

Reading package lists... Done
Building dependency tree       
.....
Setting up gcc-7 (7.3.0-16ubuntu3) ...
Setting up gcc (4:7.3.0-3ubuntu2) ...
Setting up libqt5printsupport5:amd64 (5.9.5+dfsg-0ubuntu1) ...
Setting up libqt5opengl5:amd64 (5.9.5+dfsg-0ubuntu1) ...
Setting up libqt5svg5:amd64 (5.9.5-0ubuntu1) ...
Setting up virtualbox-5.2 (5.2.16-123759~Ubuntu~bionic) ...
Adding group `vboxusers' (GID 127) ...
Done.
Processing triggers for libc-bin (2.27-3ubuntu1) ...

```

VirtualBox Manager installed```

VirtualBox Graphical User Intertace
Version 5.2.16 r123759(Qt5.9.5)

```

Please refer to following photos attached```

screenshot01_vbox_manager.png
screenshot02_vbox_manager.png

```

Download and install extension pack;
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
Download it on```

VirtualBox 5.2.16 Oracle VM VirtualBox Extension Pack
     All supported platforms 

```

Please see;
screenshot_install_extension_pack.png

-> Install
Installation went through successfully

Rebooted PC

Host Unable to set static IP address.  After setting static IP address, Host can't connect Internet (ping yahoo.com fails)

I have encountered similar problem on installing all Ubuntu18.04 VMs in the past.  Following document helped me out.

How to Enable /etc/rc.local with Systemd
[https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd)

Shall I do the same on the Host?  Thanks


2)
Shut down PC and reconnected the old 1TB SSD.

Started PC and booted Ubuntu 18.04 on the new 2TB SSD.  Copy "Virtualbox VMs" folder including all VMs (about 70 VMs) from the old SSD to new SSD.  It took about 1hr and 15min to finish.

Started VirtualBox Manager

-> Open
/home/satimis/VirtualBox VMs/VM1/VM1.vbox

-> Open

Settings
Network -> Adapter 1
Attached to" [Bridged Adapter]
Name: [enp2s0] 

Please see;
screenshot_change_network_settings.png

VM1
$ ifconfig```

br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.8.79  netmask 255.255.255.0  broadcast 192.168.8.255
        inet6 fe80::a00:27ff:fed9:8f44  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:d9:8f:44  txqueuelen 1000  (Ethernet)
        RX packets 188  bytes 495628 (495.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 243  bytes 29079 (29.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.8.3  netmask 255.255.255.0  broadcast 192.168.8.255
        ether 08:00:27:d9:8f:44  txqueuelen 1000  (Ethernet)
        RX packets 478  bytes 517370 (517.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 272  bytes 39457 (39.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 85  bytes 6670 (6.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 85  bytes 6670 (6.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


$ cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.8.79
        dns-nameservers 218.xxx.xx.xxx 219.xx.xxx.xx
        network         192.168.8.0
        netmask         255.255.255.0
        broadcast       192.168.8.255
        gateway         192.168.8.1
        bridge_ports    enp0s3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

Tried adding another VM (VM2), also successful.  It may take me another day or 2 to finish adding all VMs to this new SSD.

To purchase a new SSD is simple and straightforwards. just paying its price.  But to replace the old SSD with it takes lengthy time and effort, even without problem encountered.

Regards
satimis

---

### Post by Claus7 on 2018-07-23
Hello,

> **satimis said:**
> Hi,

Thanks for your help.

you are welcome. I just provide some info.

> **satimis said:**
> 
Install bridge-utils
$ sudo apt install bridge-utils


I did not have to install such a package for my systems (host and guest network) to work. 

> **satimis said:**
> 
Host Unable to set static IP address.  After setting static IP address, Host can't connect Internet (ping yahoo.com fails)

I have encountered similar problem on installing all Ubuntu18.04 VMs in the past.  Following document helped me out.

How to Enable /etc/rc.local with Systemd
[https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd)

Shall I do the same on the Host?  Thanks


I do not know. Have you checked the connection of host, before trying to install vb and machines? If it is working, I think that you can avoid this step altogether and just install host, then install vb and then add the machines. 

> **satimis said:**
> 
2)
Tried adding another VM (VM2), also successful.  It may take me another day or 2 to finish adding all VMs to this new SSD.

To purchase a new SSD is simple and straightforwards. just paying its price.  But to replace the old SSD with it takes lengthy time and effort, even without problem encountered.

Regards
satimis

Nice that things are working! So, even transferring machines from one drive to the other it is working. It might take some time, yet this is not a process done every day.

Regards!

---

### Post by satimis on 2018-07-23
> **Claus7 said:**
> 
I did not have to install such a package for my systems (host and guest network) to work. 

Hi,

I'll try to remove it later to check what will happen.

> 
I do not know. Have you checked the connection of host, before trying to install vb and machines? If it is working, I think that you can avoid this step altogether and just install host, then install vb and then add the machines. 

Yes, Host can connect Internet with IP address assigned by router.  Also VMs can connect to Internet.  Yes, I'll leave it 

Continue:-
Reconnected all other drives;
Say;
Drive1 - 250G SSD running Ubuntu 16.04 and KVM
Drive2 - for data storage as well as KVM guest images
Drive3 - for data storage only
Drive4 - old 1TB SSD
Drive5 - new 2TB SSD

But KVM guests on Drive1 can't be started.

Warning```

Error starting domain: Cannot access storage file '/media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/ubuntu1804pc1a02.qcow2' (as uid:64055, gid:129): No such file or directory

```

because Drive2 couldn't be mounted automatically.  I have to start 'File' -> right-click to mount and open it then KVM guests can be started.

But the most strange thing which I have to sort out FIRST is;
After connecting Drive1, Ubuntu 18.04 only boots to a dark screen.  I have tried ample times with the same result.

Ubuntu 16.04 on Drive4 can be booted and works without problem.

Any suggestion to sort out this strange thing?


Edit-1
====
Re: because Drive2 couldn't be mounted automatically.  I have to start 'File' -> right-click to mount and open it then KVM guests can be started.

Following the steps on your suggested link on Post #15

How do I add an additional hard drive?
[https://askubuntu.com/questions/125257/how-do-i-add-an-additional-hard-drive](https://askubuntu.com/questions/125257/how-do-i-add-an-additional-hard-drive)

I solved the problem.

Thanks


Edit-2
=====
bridge-utils is for setting static IP address.  All VMs of VirtualBox and guests of KVM here are running at static IP address, NOT NAT, so that other users on the internal network can use/share their applications/resource.


Regards
satimis

---

### Post by ajgreeny on 2018-07-23
The problem shown in your final attached image of post 16 suggests your guest VM is using a bridged network; try changing that to the default NAT network in the VM's settings and it may work fine.

---

### Post by satimis on 2018-07-23
> **ajgreeny said:**
> The problem shown in your final attached image of post 16 suggests your guest VM is using a bridged network; try changing that to the default NAT network in the VM's settings and it may work fine.
Hi,

Thanks.  Please explain in more detail.

"final attached image of post 16" refers to a VM of VirtualBox which was running on Drive4 (the old 1TB SSD) previously but now it is NOT running.  Would it cause a dark screen on booting Ubuntu 18.04 running on Drive5-new 2TB SSD?

Regards
satimis

---

### Post by ajgreeny on 2018-07-23
I can not help specifically with the change of disk problem but the error states that the machine musicub1404 could not be started because the physical network interface **Bro (adapter 1)** could not be found.

Such an error would not be seen if you were using the NAT network connection as it would then be using the host as the network connection, not bridged to use whatever network hardware you have in the host.

In the vbox window go to the VM settings ->Network and change from **Bridged adapter** to **NAT** and see if that allows you to start that problem VM.

---

### Post by satimis on 2018-07-23
> **ajgreeny said:**
> I can not help specifically with the change of disk problem but the error states that the machine musicub1404 could not be started because the physical network interface **Bro (adapter 1)** could not be found.

Such an error would not be seen if you were using the NAT network connection as it would then be using the host as the network connection, not bridged to use whatever network hardware you have in the host.

In the vbox window go to the VM settings ->Network and change from **Bridged adapter** to **NAT** and see if that allows you to start that problem VM.
Hi,

Your further advice noted.  Thanks

Regards
satimis

---

### Post by Claus7 on 2018-07-24
Hello,

> **satimis said:**
> Hi,

I'll try to remove it later to check what will happen.


Yes, Host can connect Internet with IP address assigned by router.  Also VMs can connect to Internet.  Yes, I'll leave it 


So, it seems that internet problem is solved.

> **satimis said:**
> 
Continue:-
Reconnected all other drives;
Say;
Drive1 - 250G SSD running Ubuntu 16.04 and KVM
Drive2 - for data storage as well as KVM guest images


Have you switched from virtualbox to kvm?

> **satimis said:**
> 
But KVM guests on Drive1 can't be started.

Warning```

Error starting domain: Cannot access storage file '/media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/ubuntu1804pc1a02.qcow2' (as uid:64055, gid:129): No such file or directory

```

because Drive2 couldn't be mounted automatically.  I have to start 'File' -> right-click to mount and open it then KVM guests can be started.


So, guests can be started as well.

> **satimis said:**
> 

But the most strange thing which I have to sort out FIRST is;
After connecting Drive1, Ubuntu 18.04 only boots to a dark screen.  I have tried ample times with the same result.

Ubuntu 16.04 on Drive4 can be booted and works without problem.

Any suggestion to sort out this strange thing?


Edit-1
====
Re: because Drive2 couldn't be mounted automatically.  I have to start 'File' -> right-click to mount and open it then KVM guests can be started.

Following the steps on your suggested link on Post #15

How do I add an additional hard drive?
[https://askubuntu.com/questions/125257/how-do-i-add-an-additional-hard-drive](https://askubuntu.com/questions/125257/how-do-i-add-an-additional-hard-drive)

I solved the problem.

Thanks


So, also ubuntu 18.04 boots normally.

Nice that things are working!

Regards!

---

### Post by satimis on 2018-07-24
> **Claus7 said:**
> Hello,
So, it seems that internet problem is solved.

Yes, if the Host is running on dynamic IP allocated by the router on each boot.  I trust I can solve the the static IP problem on the Host.  I have done many times on Ubuntu 18.04 VMs because of rc.local not coming with the OS.  All VirtualBox VMs here are running static IP.  Their applications can be run remotely and their data can be shared amongst PCs on internal network.

I set up this system several years ago for hosting my websites both on local server as well as on Godaddy server.  When the local server was up visitors browsed the local server version.  When the local server was done visitors browsed the websites on Godaddy server. The switching was fully automatic and visitors can't recognize the switching on servers.  It was a very interesting setup.  Of course I have to subscribe Static IP.  It can work on Dynamic IP as well but also I have to subscribe.  I have already ceased operating this system.  It was only done for testing.

> 
Have you switched from virtualbox to kvm?

No.  This PC is a dual boot system operated on BIOS.

Previous setup
1TB SSD (old SSD) running VirtualBox on Ubuntu 16.04 desktop
250G SSD running KVM also on Ubuntu 16.04 desktop, with all guest images stored on a 2TB WD Black Label HD.
They can co-exist without problem.

Both VirtualBox and KVM have Pros and Cons.  


> 
So, guests can be started as well.
So, also ubuntu 18.04 boots normally.

Yes, but the new 2TB SSD(VirtualBox on Ubuntu 18.04 desktop) and the 250G SSD(KVM on Ubuntu 16.04) can't co-exist.  If connecting both of them to the PC Ubuntu 18.04 is unable to boot, with only a black screen displayed finally.  GRUB menu popup.  But Ubuntu 16.04 on the 250G SSD can be booted without problem.  Both OS and KVM including guests work without problem.

Up to now I couldn't discover a solution.  

However both the old 1TB SSD and the new 2TB SSD can co-exist.  Both of them can be booted without problem.  Also both Ubuntu 18.04 and Ubuntu 16.04 work without problem including their VMs

It looks very strange to me.  I'll play around on BIOS later to see if I can sort out the problem.

Regards
satimis

---

### Post by satimis on 2018-07-24
Hi Claus7,

Performed following test:-

Document referred to:
UEFI
[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode)

Identifying if the computer boots the HDD in UEFI mode
On terminal: run
$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"```

EFI boot on HDD

```

The system and/or BIOS supports booting UEFI mode


Disconnect 250G SSD (Ubuntu 16.04 and KVM)

Playing around on BIOS:

Advanced Mode -> Boot -> 
CSM (Compatibity Support Module) ->
Launch CSM	Enabled		#default

Boot Device Control:
UEFI and Legacy OpROM	#default
Legacy OpROM only
UEFI only

Boot Network Devices:
Legacy OpROM first	#default
UEFI driver first	    #select this option
Ignore

Boot from Storage Device:
Both Legacy OpROM first		#default
Both, UEFI first		#select this option
Ignore

Boot from PCIe/PCI Expansion Devices:
Legacy OpROM first	#default
UEFI driver first	 #select this option

Advanced Mode -> Boot -> Secure Boot ->
OS Type:
Windows UEFI mode
Other OS		#select this option

Boot Ubuntu 18.04 Gnome desktop to make sure it works without problem including VM

Reconnect 250G SSD (Ubuntu 16.04 and KVM) and boot Ubuntu 18.04.  
Problem is still existing, booting to a dark screen finally, GRUB menu popup during booting

Pressing Ctrl+Alt+Del keys can restart the PC

Booting 250G SSD (Ubuntu 16.04 and KVM) is without problem.  Ubuntu 16.04 works without problem including KVM guests

Booting the old 1TB SSD (Ubuntu 16.04 and VirtualBox) is also without problem.  Ubuntu 16.04 works without problem including VMs

It looks very funny to me.  I'm stuck here!  What will be the solution?  
Go back to Ubuntu 16.04 desktop?
Re-install Ubuntu 18.04 without UEFI mode?

Regards
satimis

---

### Post by Claus7 on 2018-07-25
Hello,

I will provide some ideas. Maybe someone else might be more ideal for this issue. So, you have actually 2 different active ssds:
1) the new one that has 18.04 with vb 
2) another one which has 16.04 with kvm and
3) the old one that was replaced from (1) running 16.04 instead

could you check for each one of them:
i) [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"

so as to verify that all are using the same mode and

ii) could you run fdisk -l to disks (1) and (3) just to check if they are similar?

I suppose that if (i) is not the case then most probably you have to fix the grub configuration of the new ssd.

Regards!

---

### Post by satimis on 2018-07-25
> **Claus7 said:**
> Hello,

I will provide some ideas. Maybe someone else might be more ideal for this issue. So, you have actually 2 different active ssds:
1) the new one that has 18.04 with vb 
2) another one which has 16.04 with kvm and
3) the old one that was replaced from (1) running 16.04 instead

could you check for each one of them:
i) [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"

so as to verify that all are using the same mode and]
Hi,

1) the new one that has 18.04 with vb 
$ [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"```

Installed in UEFI mode

```

2) another one which has 16.04 with kvm
&#10219; [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"```

Installed in Legacy mode

```

3) the old one that was replaced from (1) running 16.04
&#10219; [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"```

Installed in Legacy mode

```


> 
ii) could you run fdisk -l to disks (1) and (3) just to check if they are similar?

I suppose that if (i) is not the case then most probably you have to fix the grub configuration of the new ssd.


They are NOT similar because (1) in UEFI mode and (3) in Legacy mode.  Please see attached files

(1) fdisk-1.txt  #(2) is NOT connected otherwise (1) can't boot up
(3) fdisk-3.txt  #with all disks connected to the PC

Regards
satimis

---

### Post by Claus7 on 2018-07-25
Hello,

then, I guess, from the results posted, that 18.04 (disk 1) should be installed as legacy mode as well, so as to match that of 16.04 (disk 2).

Don't you think?

Regards!

---

### Post by satimis on 2018-07-25
> **Claus7 said:**
> Hello,

then, I guess, from the results posted, that 18.04 (disk 1) should be installed as legacy mode as well, so as to match that of 16.04 (disk 2).

Don't you think?

Hi,

I agree with your suggestion.  To end the endless struggling I prefer to re-install Ubuntu 18.04 as Legacy mode.  There is not much effort having been put on it.

But I can't resolve why;
(1) and (3), one on UEFI mode and another on Legacy mode, can co-exist?
(1) and (2), one on UEFI mode and another on Legacy mode, can't co-exist?

A further thought, maybe find an old WD Black label HD installing Ubuntu 18.04 as legacy mode to see what will happen?

What will be your opinion?

Regards
satimis

---

### Post by Claus7 on 2018-07-25
Hello,

unless I'm wrong, I understood that (2) and (3) co-existed, which both were the drives that you possessed prior buying the new one. And both of them were on legacy mode. From a post above of yours, the 18.04 was the one that had a black screen when was connected with your other ssds.

Am I wrong?

Since you have an old spare drive it would be nice to test it before re-installing the new one on legacy mode.

Regards!

---

### Post by satimis on 2018-07-25
> **Claus7 said:**
> Hello,

unless I'm wrong, I understood that (2) and (3) co-existed, which both were the drives that you possessed prior buying the new one. And both of them were on legacy mode. From a post above of yours, the 18.04 was the one that had a black screen when was connected with your other ssds.

Am I wrong?

Yes (2) and (3) co-existed

(1) and (3) also co-existed
But
(1) and (2) can't be co-existed.  It surprises me???

> 
Since you have an old spare drive it would be nice to test it before re-installing the new one on legacy mode.

Yes, I'll search the shelves finding an old WD Black Label HD.  I'll come back after the test.

Regards
satimis

---

### Post by Claus7 on 2018-07-26
Hello,

> **satimis said:**
> 

1)
Disconnected all drives on the PC, leaving only the new 2TB SSD connected.

Booted PC with Ubuntu18.04 USB installer and installed Ubuntu 18.04 gnome desktop.  Installation went through without problem.

Reboot PC

Host - Ubuntu 18.04 Gnome desktop

...

2)
Shut down PC and reconnected the old 1TB SSD.

Started PC and booted Ubuntu 18.04 on the new 2TB SSD.  Copy "Virtualbox VMs" folder including all VMs (about 70 VMs) from the old SSD to new SSD.  It took about 1hr and 15min to finish.



> **satimis said:**
> Hi all,

Now I have received the new Samsung 860 EVO 2TB SSD ordered previously.
(Samsung SSD 860 EVO SATA III 2.5 " 2TB (MZ-76E2T0BW))

I'll use it to replace the old 1TB SSD which has been running for about 10 years, almost fully occupied and leaving about 90GB free space.

Host - Ubuntu 18.04 gnome desktop (OS)
VirtualBox

3)
Migration of all VMs from the old 1TB SSD to the new 2TB SSD

Either
3a)
Export all VMs and import them to the VirtualBox Manager on the new 2TB SSD

OR
3b)
Copy/Paste or rsync all VMs including the folder "VirtualBox VMs" from the old 1TB SSD to the new 2TB SSD.  Afterwards add the VMs to VirtualBox Manager manually, one by one?



> **satimis said:**
> Yes (2) and (3) co-existed

**(1) and (3) also co-existed**
But
(1) and (2) can't be co-existed.  It surprises me???


Yes, I'll search the shelves finding an old WD Black Label HD.  I'll come back after the test.

Regards
satimis

First good luck with the attempt of the old WD HD.

Now, checking what has taken place so far: when you transferred your VMs from the old drive (3) to the new one (1), did you have both of them connected and running simultaneously? I supposed that the copy/paste process took place via external usb drive, since, when both connected, you mentioned that you booted your new one...

Regards!

---

### Post by satimis on 2018-07-26
> **Claus7 said:**
> Hello,
Now, checking what has taken place so far: when you transferred your VMs from the old drive (3) to the new one (1), did you have both of them connected and running simultaneously? I supposed that the copy/paste process took place via external usb drive, since, when both connected, you mentioned that you booted your new one...

No, not via an external USB.  By Copy/Paste command, copied all VMs including the folder direct from the old SSD to the new SSD, without any problem encountered but only taking one hour and 15 minutes to complete.  I booted the new SSD OS, i.e. Ubuntu 18.04, to do the job.

I suspect the late problem, both (1) and (3) SSDs (Ubuntu 18.04 VB and Ubuntu 16.04 KVM) unable to co-exist, comes from Ubuntu 18.04.  I have encountered several problems running it as VMs.  Besides Ubuntu 18.04 takes longer time booting up to 'login page'. compared to Ubuntu 16.04, taking more than 1 min to complete.

This is a quite strong PC, running AMD 8-cores and 32G RAM onboard.  Ubuntu 18.04 is running on a latest SSD, not a mechanical HD.

I'm still searching a HD to make the test.

Regards
satimis

---

### Post by satimis on 2018-07-27
Hi Claus7 and all,

Performed following tests and found a strange thing.

Method I)
1) Disconnect all SSDs and HDs
2) Insert USB installer
3) Turned on the PC and boot

On BIOS, 2 boot options displayed
a) KingstonDataTrveler G2
b) UEFI: KingstonDataTraveller G2

Booting a) starting the page for selecting;
-Try Ubunutu - clicking it starts Ubuntu 18.04
-Install Ubuntu

Booting b) - start Ubuntu 18.04 staightforwards.  There is an icon for "install Ubuntu"

IIRC before I booted a) to install Ubuntu 18.04 on the new 2TB SSD

Method II)
1) Only connect the 250G SSD (Ubuntu16.04 KVM) to the PC
2) Insert USB installer
3) Turned on the PC and boot

On BIOS displaying
a) KingstonDataTrveler G2
b) P1 SanDisk SDSSDH3250G (Ubuntu16.04 KVM)

Clicking a) won't boot Ubuntu 18.04, instead it boots SanDisk (Ubuntu16.04 KVM) starting Ubuntu 16.04

I tried twice with the same result.

Any suggestion?  I find a spare WD Black Label 1TB HD

Regards
satimis

---

### Post by Claus7 on 2018-07-27
Hello,

> **satimis said:**
> No, not via an external USB.  By Copy/Paste command, copied all VMs including the folder direct from the old SSD to the new SSD, without any problem encountered but only taking one hour and 15 minutes to complete.  I booted the new SSD OS, i.e. Ubuntu 18.04, to do the job.

Forgive my ignorance, but something I'm missing. You have 2 different ssds.
Both of them have ubuntu installed.
The one has 16.04, the other 18.04.
You connect both of them to your computer.
You should be able, via grub, to choose one of the 2 while booting.
You choose 18.04. 
Then, via copy/paste, you transferred your files from the 16.04 to 18.04? 

> **satimis said:**
> 
I suspect the late problem, both (1) and (3) SSDs (Ubuntu 18.04 VB and Ubuntu 16.04 KVM) unable to co-exist, comes from Ubuntu 18.04.  I have encountered several problems running it as VMs.  Besides Ubuntu 18.04 takes longer time booting up to 'login page'. compared to Ubuntu 16.04, taking more than 1 min to complete.

This is a quite strong PC, running AMD 8-cores and 32G RAM onboard.  Ubuntu 18.04 is running on a latest SSD, not a mechanical HD.

I'm still searching a HD to make the test.

Regards
satimis

You should check your boot times for 18.04 drive.
Try:
systemd-analyze time
systemd-analyze blame

I do not know if the number of VMs affect so much your boot time, yet I suppose that it should be shorter, yet you can check.

> **satimis said:**
> Hi Claus7 and all,

Performed following tests and found a strange thing.

Method I)
1) Disconnect all SSDs and HDs
2) Insert USB installer
3) Turned on the PC and boot

On BIOS, 2 boot options displayed
a) KingstonDataTrveler G2
b) UEFI: KingstonDataTraveller G2

Booting a) starting the page for selecting;
-Try Ubunutu - clicking it starts Ubuntu 18.04
-Install Ubuntu

Booting b) - start Ubuntu 18.04 staightforwards.  There is an icon for "install Ubuntu"

IIRC before I booted a) to install Ubuntu 18.04 on the new 2TB SSD

Method II)
1) Only connect the 250G SSD (Ubuntu16.04 KVM) to the PC
2) Insert USB installer
3) Turned on the PC and boot

On BIOS displaying
a) KingstonDataTrveler G2
b) P1 SanDisk SDSSDH3250G (Ubuntu16.04 KVM)

Clicking a) won't boot Ubuntu 18.04, instead it boots SanDisk (Ubuntu16.04 KVM) starting Ubuntu 16.04

I tried twice with the same result.

Any suggestion?  I find a spare WD Black Label 1TB HD

Regards
satimis

So the problem now, lies to the fact that, you have a usb installer that it is not the first one that boots. Is it possible to change their boot priority on bios? 

Regards!

---

### Post by satimis on 2018-07-27
> **Claus7 said:**
> 
....... You have 2 different ssds.
Both of them have ubuntu installed.
The one has 16.04, the other 18.04.
You connect both of them to your computer.
You should be able, via grub, to choose one of the 2 while booting.
You choose 18.04. 
Then, via copy/paste, you transferred your files from the 16.04 to 18.04? 
I have 3 SSDs
(1) 1TB SSD (old) - running Ubuntu 16.04 and VirtualBox
(2) 2TB SSD (new) - running Ubuntu 18.04 and VirtualBox
(3) 250G SSD - running Ubuntu 16.04 and KVM

(1) and (3) have been running together in the PC at least 2 years and without problem.  Their booting is controlled via BIOS selected by me manually.

(2) is running Ubuntu 18.04 and Virtualbox.  I transferred all VMs from (1) to (2) with Copy/Paste command.  They can co-exist without problem.

My problem is (2) and (3) unable to co-exist.  If connecting (3) to the PC (2) is unable to boot.  The case is similar to my test on previous posting,

All bootings are via BIOS selected by me manually.  I haven't set boot priority yet.

> 
You should check your boot times for 18.04 drive.
Try:
systemd-analyze time
systemd-analyze blame

OK I'll check it later.  Now only (1) and (3) are connected in PC

> 
I do not know if the number of VMs affect so much your boot time, yet I suppose that it should be shorter, yet you can check.

No, only 6 VMs have been added.  Others are in the folder untouched.  Slow booting of Ubuntu 18.04 has been found on all Ubuntu 18.04 VMs

> 
So the problem now, lies to the fact that, you have a usb installer that it is not the first one that boots. Is it possible to change their boot priority on bios? 

First, I performed the test reported on my previous posting with all SSDs disconnected.  After connecting (3) back to the PC.  I encountered the problem as reported.  But why?


Edit-1
===
$ systemd-analyze time```

Startup finished in 152us (firmware) + 124us (loader) + 34.938s (kernel) + 4.780s (userspace) = 39.719s
graphical.target reached after 4.070s in userspace

```

$ systemd-analyze blame > blame.txt
Please see blame.txt attached


Edit-2
====
Instead of endless struggling without a trace of light to sort out the problem, I'm considering going back to Ubuntu 16.04 desktop.  The OS is solely for running VirtualBox with only the default application installed such as LibreOffice, Firefox etc.  All my work and testing are done on VMs.  

What do you think?

Regards
satimis

---

### Post by Claus7 on 2018-07-28
Hello,

> **satimis said:**
> 

(1) and (3) have been running together in the PC at least 2 years and without problem.  Their booting is controlled via BIOS selected by me manually.

Ok, so you open your pc and you choose which one to boot from BIOS. 

> **satimis said:**
> 
(2) is running Ubuntu 18.04 and Virtualbox.  I transferred all VMs from (1) to (2) with Copy/Paste command.  They can co-exist without problem.

The command you use is it like:
cp /media/sdb1/test_file /media/sdc1/ ?

> **satimis said:**
> 

Edit-1
===
$ systemd-analyze time```

Startup finished in 152us (firmware) + 124us (loader) + 34.938s (kernel) + 4.780s (userspace) = 39.719s
graphical.target reached after 4.070s in userspace

```


your kernel boot time is too high for the system you have. See also below.

> **satimis said:**
> 
$ systemd-analyze blame > blame.txt
Please see blame.txt attached

If everything is copied ok, I cannot see any problem here.

> **satimis said:**
> 
Edit-2
====
Instead of endless struggling without a trace of light to sort out the problem, I'm considering going back to Ubuntu 16.04 desktop.  The OS is solely for running VirtualBox with only the default application installed such as LibreOffice, Firefox etc.  All my work and testing are done on VMs.  

What do you think?

Regards
satimis

I think that you should stick to 16.04, unless you want to wait for an update for problem to get fixed. Just to inform you that now already 18.04.1 is out, so you could check if this version fixes the problems you are mentioning. Officially the release of that version was 2 days ago, so this might affect.

I wanted also to inform you about this:
[https://ubuntuforums.org/showthread.php?t=2393756](https://ubuntuforums.org/showthread.php?t=2393756)

which is about server edition, yet the problem about boot times is similar to your case, without having reached a definite solution yet.

Regards!

---

### Post by satimis on 2018-07-31
> **Claus7 said:**
> Hello,
Ok, so you open your pc and you choose which one to boot from BIOS.
On starting PC I hit 'Del' and choose the device to boot

> 
The command you use is it like:
cp /media/sdb1/test_file /media/sdc1/ ?
I used 'drag/drop' and selected 'copy' option to copy the directory 'Virtual VMs" including all VMs from the old 1TB SSD to new 2TB SSD.  It went through without complaint.

> 
your kernel boot time is too high for the system you have. See also below.

Noted.  Thanks

> 
If everything is copied ok, I cannot see any problem here.

Noted

> 
I think that you should stick to 16.04, unless you want to wait for an update for problem to get fixed. Just to inform you that now already 18.04.1 is out, so you could check if this version fixes the problems you are mentioning. Officially the release of that version was 2 days ago, so this might affect.

Yes, I'll install Ubuntu 16.04.4 first, already having its desktop ISO download. I have VMs running it as OS and so far without problem discovered.  If still encountering trouble I'll go back to Ubuntu 16.04

Also I am running Ubuntu 18.04 as VMs, having discovered some problems.

> 
I wanted also to inform you about this:
[https://ubuntuforums.org/showthread.php?t=2393756](https://ubuntuforums.org/showthread.php?t=2393756)

which is about server edition, yet the problem about boot times is similar to your case, without having reached a definite solution yet.

Noted

Regards
satimis

---

