---
title: "Suggest some Light-weight OS to run in virtualbox on Ubuntu 20.04.2"
date: 2021-06-22
forum: Virtualisation
---

### Post by EngineerStrange on 2021-06-22
I am using Ubuntu 20.04. I need a OS to run in virtualbox and use google meet there occasionally (with less than 2 incoming videos). What OS should I use so to use least RAM and storage (performance of guest doesn't matter that much)?
If you know please include (apart from your suggestions) how is (size, ram mainly) the minimal installation of Ubuntu, debian etc? And how are Alpine Linux, Damn Small Linux, NanoLinux ( is it possible to use a browser in these OS)?

---

### Post by sudodus on 2021-06-22
You should use a Linux distro that is still maintained, and if I remember correctly, that excludes Damn Small Linux.

Have a look at Lubuntu and Xubuntu, Tiny Core and Puppy Linux.

I think Tiny Core has the smallest footprint among these [Ubuntu flavours and other] Linux distros. But I don't know how Google Meet will work in the lightest distros. You have to try it out ...

-o-

I think you get away with less 'overhead' if you use KVM+VirtManager instead of VirtualBox.

---

### Post by EngineerStrange on 2021-06-22
> **sudodus said:**
> You should use a Linux distro that is still maintained, and if I remember correctly, that excludes Damn Small Linux.

Have a look at Lubuntu and Xubuntu, Tiny Core and Puppy Linux.

I think Tiny Core has the smallest footprint among these [Ubuntu flavours and other] Linux distros. But I don't know how Google Meet will work in the lightest distros. You have to try it out ...

-o-

I think you get away with less 'overhead' if you use KVM+VirtManager instead of VirtualBox.

But I don't know how to use KVM+VirtManager from my side. I use this for running android virtual device.

---

### Post by EngineerStrange on 2021-06-22
But I don't know how to use KVM+ VirtManager manually. Sorry for replying at wrong place first time.

---

### Post by sudodus on 2021-06-22
> **EngineerStrange said:**
> But I don't know how to use KVM+VirtManager from my side. I use this for running android virtual device.

[KVM+VirtManager](https://help.ubuntu.com/community/KVM/VirtManager) works in Ubuntu (and other Linux distros). But you can certainly use VirtualBox too (which is available for most operating systems).

---

### Post by tea for one on 2021-06-22
gnome-boxes is pretty friendly for new users to virtual machines.

[https://wiki.gnome.org/Apps/Boxes](https://wiki.gnome.org/Apps/Boxes)

```
sudo apt install gnome-boxes
```

---

### Post by EngineerStrange on 2021-06-23
I don't know why but now I can't even remove virtualbox. The problem maybe because i haven't signed kernel modules.

---

### Post by sudodus on 2021-06-23
How did you install VirtualBox?

---

### Post by EngineerStrange on 2021-06-23
I downloaded the .deb package from virtualbox website and installed using ubuntu software

---

### Post by sudodus on 2021-06-23
Use 'the same' method [as you used to install] to remove the package. Your tool should have an option to remove a package, that it installed. (But it will probably not work to use some other tool. Or it can be very difficult)

---

### Post by EngineerStrange on 2021-06-23
No it shows some error like pre-removal script subprocess returned error exit status 1.

---

### Post by sudodus on 2021-06-23
A problem for us is that we  [might] have installed VirtualBox some other way, and therefore cannot reproduce exactly the errors that you get. For that reason it is important that you show **exactly** what you do and how the system responds (copy&paste the commands and the output to a new post in this thread).

Let us hope that someone will recognize your problem and help you solve it.

---

### Post by EngineerStrange on 2021-06-23
This is what happens on trying to remove it:

```
sudo apt remove virtualbox-6.1 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmessaging-menu0 linux-headers-5.8.0-53-generic
  linux-hwe-5.8-headers-5.8.0-53 linux-image-5.8.0-53-generic
  linux-modules-5.8.0-53-generic linux-modules-extra-5.8.0-53-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-6.1
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 216 MB disk space will be freed.
Do you want to continue? [Y/n] Y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 245854 files and directories currently installed.)
Removing virtualbox-6.1 (6.1.22-144080~Ubuntu~eoan) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package virtualbox-6.1 (--remove):
 installed virtualbox-6.1 package pre-removal script subprocess returned error e
xit status 1
dpkg: too many errors, stopping
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess: Resource temporarily unavailable
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.
Errors were encountered while processing:
 virtualbox-6.1
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by EngineerStrange on 2021-06-23
And this is what I get to see when I try to start a created Virtual machine on virtualbox:

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please try setting it up again by executing

[COLOR=#0000ff]'/sbin/vboxconfig'[/COLOR]

as root.

If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.

---

### Post by sudodus on 2021-06-23
Are you booting in UEFI mode and are you using 'secure boot'? Please check in the UEFI/BIOS system of the computer. 

If secure boot is on, it should be possible to turn it off, reboot, and then try again with VirtualBox.

---

### Post by EngineerStrange on 2021-06-23
Yeah I have UEFI and sercure boot both since I purchased the computer. I can run the virtual machine after signing kernels, however I haven't tried to uninstall.

---

### Post by sudodus on 2021-06-23
I think your computer is safe, when you turn off secure boot, and then we can expect that VirtualBox will work. I think it is very complicated to sign the VirtualBox modules, and not at all worth the effort.

---

### Post by monkeybrain20122 on 2021-06-23
BTW, VB messes up your python in Ubuntu-20.04. After you remove it, make sure you install the package 

python-is-python3

VB installs python-is-python2 as a dependency and sets your default python to python2, which is unmaintained and kind of broken (since there are only some core packages in Ubuntu-20.04 for legacy software), this may mess up other applications that depend on python. so until VB retires python2 or makes it a recommended only package I don't recommend it for Ubuntu 20.04 or newer (it doesn't really need python except for scripting) At least this should come with a warning.

---

### Post by MAFoElffen on 2021-06-24
I'm sold on KVM and Virtual Manager also, as some other's mentioned, over using VirtualBox... but that is a personal preference.

Getting back to "light versions"... Which also is personal preferences...

Have you thought about installing a VM of Ubuntu Core? Then minimal XServer, and what flavor of a grahical logon manager, with flavor(s) of Desktop Environments. Then you could install light-weight applications as needed. The thing with Linux is that you can interchange things as you please.

For instance, with LightDM as a DM, you can easily change which DE you want to use. OpenBox is a very lightweight DE, but then you have to edit the OpenBox aplications menu manually with the OpenBox Menu editor. 

If you want something really light, don't install a login manager, and install just OpenBox. It will boot to the virtual TTY's. On starting X, use startX, which will boot X and OpenBox (or whatever is in the rcinit scripts). On exiting OpenBox, it then unloads the DE and X back down to the TTY's.

That option is limitless to what you want to do, and end up with... Based on your preferences and choices.

In that manner, you can create something that will run in a 256MB to 1GB RAM container, depending on the combination you create.

And on a VM, you can play with the assigned RAM, to see how it runs and works in the recources you give it.

---

### Post by MAFoElffen on 2021-06-24
> **EngineerStrange said:**
> This is what happens on trying to remove it:

```
sudo apt remove virtualbox-6.1 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmessaging-menu0 linux-headers-5.8.0-53-generic
  linux-hwe-5.8-headers-5.8.0-53 linux-image-5.8.0-53-generic
  linux-modules-5.8.0-53-generic linux-modules-extra-5.8.0-53-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-6.1
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 216 MB disk space will be freed.
Do you want to continue? [Y/n] Y
[COLOR=#ff0000]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable[/COLOR]
(Reading database ... 245854 files and directories currently installed.)
Removing virtualbox-6.1 (6.1.22-144080~Ubuntu~eoan) ...
[COLOR=#ff0000]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package virtualbox-6.1 (--remove):
 installed virtualbox-6.1 package pre-removal script subprocess returned error e
xit status 1
dpkg: too many errors, stopping[/COLOR]
[COLOR=#daa520]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess: Resource temporarily unavailable
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.
[/COLOR]
[COLOR=#800080]There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.
Errors were encountered while processing:
 virtualbox-6.1[/COLOR]
[COLOR=#ff0000]Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```
Going back to what you tried... It broke leaving a broken VBox system while trying to remove it, but then, could not roll back to a working VBox system. It's in currenlty in "Limbo."

In dmesg check to see if there is any addition hints on why the vbox kernel drivers are loading or not:
```

dmesg --facility kern | grep -A6 -i "vbox"

```
And/or checking if the vbox* are loaded as a modules
```
lsmod | grep -i "vbox"

```
You should get output simular to this:
```
vboxpci                24576  0vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci

```
Your output gave you this hint to correct it:
```
To re-start the set-up process, run  /sbin/vboxconfig
# As root or
sudo /sbin/vboxconfig

```
If that fails, then I suspect it's because it's still in limbo somehow... It said it couldn't roll back. Relinstalling VirtualBox would then fix that with less effort.. 

To get back to where you were, since it said it had lock problems... unlock any file locks that will affect apt:
```

sudo rm /var/lib/apt/lists/lock
sudo rm /var/lib/dpkg/lock
sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/cache/apt/archives/lock
sudo apt-get install -f
sudo apt-get clean
sudo apt-get update --fix-missing
apt-get --reinstall install virtualbox-6.1

```

But if your goal is to continue to remove VirtualBox, unload the 4 VBox kernel modules on-demand, in realtime, then remove the Vbox package (that way, nothing of vbox is being used and causing any conflict):
```
sudo modprobe -r vbox*
sudo apt-get remove --purge virtualbox-6.1

```

---

### Post by MAFoElffen on 2021-06-24
The peculliarity of VitualBox on Linux, is how it is implemented, and the dependecies. It compiles is own drivers as kernel modules and adds them to a new kernal version as the kernel version is updated. So it has deep hooks into the kernel for it's software virtualization to work. 

That is why the depends on it's package are things like build-essentials and the kernel headers. That is also why VirtualBox sometimes breaks on a Linux Kernel update...

---

### Post by EngineerStrange on 2021-06-29
No it's done succesfully. Anyway for all of your help.

---

### Post by EngineerStrange on 2021-06-29
Yeah I can see pythin-is-python2 installed at this moment not python-is-python3. Is this because of virtual-box?
Please note that earlier when i wrote python to run a python code it used to say something like python2 not installed. When i want to run python3 i had to use command python3. I also found python2 to be installed in my computer now, which I never did myself.

---

### Post by EngineerStrange on 2021-06-29
I too have qemu-kvm and libvirt0 installed for running AVD but I dont know how to use those for operating system. Can you share any link etc? 
And also how's it as compared to xen?

---

### Post by bernard010 on 2021-07-01
Try Linux Lite for your VM guest OS. [https://www.linuxliteos.com/download.php](https://www.linuxliteos.com/download.php)

---

