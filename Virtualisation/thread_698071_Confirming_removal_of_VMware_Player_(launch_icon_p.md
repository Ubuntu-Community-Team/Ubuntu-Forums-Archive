---
title: "Confirming removal of VMware Player (launch icon persists)"
date: 2008-02-15
forum: Virtualisation
---

### Post by gregconquest on 2008-02-15
I have a launch icon in Applications -- System Tools for VMware Player. If I click it, I get an  application button in the bottom panel saying, "Starting VMware Player". It last ten seconds or so then goes away.

I've tried several approaches from different threads to removing failed VMware Player installs, but none of them find anything (synaptic did say it was removing one package when I asked to completely remove vmware-player-kernel-modules...). After following all the steps for removal, including the script at the bottom of this message, I did just find and manually remove the /etc/vmware folder as a last resort. There were lots of files in there, but still the icon and failed launch sequence persists.

**So, before I go on** to try and install VMware Server or try to use my WindowsXPPro.vmx / WindowsXPPro.vmdk with qemu (2.8GHz Pentium with no virtualization circuitry),** how can I confirm VMware Player has been removed?**

Thank you.
Greg Conquest
ubuntu 7.10 

note:
```
gc@DIYubuntu:~$ sudo killall vmnet-natd
vmnet-natd: no process killed
gc@DIYubuntu:~$ sudo apt-get remove --purge vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vmware-player is not installed, so not removed
```

also:
If I try to reinstall VMware Player from "Add/Remove", I get a message "VMware Player cannot be installed on your computer type (i386)"

---

### Post by gregconquest on 2008-02-18
2-day bump -- it's a basic question that hasn't been answered anywhere I can see.

---

### Post by fjgaude on 2008-02-18
You must completely remove all aspects of Player from your computer before you can re-install.

Go into Synaptic, click Status, then do a Search for vmware. Click on player and then do a Mark for Complete Removal. That should permit you to reinstall.

Let us know how you do.

---

### Post by tact on 2008-02-18
I had a problem removing vmware player completely from my system before installing vmware server.  Using the "mark for complete removal" option in synaptic seemed to do its job but in reality did not work, vmware server install still failed as there were still vestiges of vmware player littering my filesystem.

In the end I went CLI and did a hunt and destroy mission... using "locate" and "whereis" etc to find any reference at all to vmware and removing it manually.

Then only would vmware server install properly for me.

---

### Post by fjgaude on 2008-02-18
We have to do what works for us.

I didn't ever have to do what you suggest.

---

### Post by gregconquest on 2008-02-23
> **fjgaude said:**
> You must completely remove all aspects of Player from your computer before you can re-install.

Go into Synaptic, click Status, then do a Search for vmware. Click on player and then do a Makl for Complete Removal. That should permit you to reinstall.

Let us know how you do.

Thanks, but I get nothing here now. Using Synaptic was one of the steps I've already taken. Presently, I do still have
```
X.Org X server -- VMware display drive
```
listed in synaptic, but this appears to be unrelated to my VMware installation.

Greg

---

### Post by gregconquest on 2008-02-23
> **tact said:**
> I had a problem removing vmware player completely from my system before installing vmware server.  Using the "mark for complete removal" option in synaptic seemed to do its job but in reality did not work, vmware server install still failed as there were still vestiges of vmware player littering my filesystem.

In the end I went CLI and did a hunt and destroy mission... using "locate" and "whereis" etc to find any reference at all to vmware and removing it manually.

Then only would vmware server install properly for me.

I can hunt down all files, links, folders, and references to vmware, but it seems that many of them pre-date the VMware Player installation. Can I safely delete everything that has vmware in its name?

Here are the search results for "vmware":
```
/var/lib/dpkg/info/xserver-xorg-video-vmware.md5sums
/var/lib/dpkg/info/xserver-xorg-video-vmware.list
/etc/init.d/vmware
/etc/rc2.d/S90vmware
/etc/rc2.d/K08vmware
/etc/rc3.d/S90vmware
/etc/rc3.d/K08vmware
/etc/rc5.d/S90vmware
/etc/rc5.d/K08vmware
/etc/rc0.d/K08vmware
/etc/rc6.d/K08vmware
/etc/xdg/menus/applications-merged/vmware-ace-vms.menu
/usr/share/doc/xserver-xorg-video-vmware
/usr/share/doc/vmware
/usr/share/man/man4/vmware.4.gz
/usr/share/pixmaps/vmware-player.png

  /usr/share/icons/ removed from search results

/usr/share/mime/application/x-vmware-vmfoundry.xml
/usr/share/mime/application/x-vmware-vm.xml
/usr/share/mime/application/x-vmware-team.xml
/usr/share/mime/application/x-vmware-vmdisk.xml
/usr/share/mime/application/x-vmware-snapshot.xml
/usr/share/mime/packages/vmware.xml
/usr/share/app-install/desktop/vmware-player.desktop
/usr/share/app-install/icons/vmware-player.png
/usr/share/app-install/icons/_usr_share_pixmaps_vmware-player.png
/usr/share/desktop-directories/vmware-ace-vms.directory
/usr/share/restricted-manager/groups/vmware
/usr/bin/vmware-uninstall.pl
/usr/bin/vmware-ping
/usr/bin/vmware-acetool
/usr/bin/vmware-config.pl
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/lib/vmware
/usr/lib/vmware/messages/ja/vmware.vmsg
/usr/lib/vmware/lib/libvmwarebase.so.0
/usr/lib/vmware/lib/libvmwarebase.so.0/libvmwarebase.so.0
/usr/lib/vmware/lib/libvmwareui.so.0
/usr/lib/vmware/lib/libvmwareui.so.0/libvmwareui.so.0
/usr/lib/vmware/bin/vmware-vmx
/usr/lib/vmware/bin/vmware-tray
/usr/lib/vmware/bin/vmware-acetool
/usr/lib/vmware/bin-debug/vmware-vmx
/usr/lib/vmware/bin-stats/vmware-vmx

  /usr/lib/vmware/share/icons/ removed from search results

/usr/lib/vmware/share/pixmaps/vmware-player.png
/usr/lib/vmware/share/pixmaps/vmware-acevm.png
/usr/sbin/vmware-authd
  /mnt/ everything under /mnt also removed from search results
```

3 questions:
1) Should I delete these all (minus the images)?
2) Is it common for an application to not correctly uninstall like this? I really don't like having a system littered with partial installs.
3) Can I install VMware Server from source and have it working with or without resolving this VMware Player uninstall issue?

Thank you.
Greg Conquest

---

### Post by fjgaude on 2008-02-23
> **gregconquest said:**
> 
3 questions:
1) Should I delete these all (minus the images)?
2) Is it common for an application to not correctly uninstall like this? I really don't like having a system littered with partial installs.
3) Can I install VMware Server from source and have it working with or without resolving this VMware Player uninstall issue?

Thank you.
Greg Conquest

We simply don't know what you have done to get all these items left over from an uninstall, partial install.
1) I would delete them all, including the images.
2) No, it is not common, but I guess it happens depending on how things are installed, uninstalled, partially installed.
3) There no reason to install from source. Install from binary from the vmware.com site. The server version is in the upper right-hand corner of their home page.

Good luck. But do let us know how you are doing.

---

### Post by gregconquest on 2008-02-25
I deleted all vestiges of the prior install, and then I tried an install of Server. Things went fine till I got here:
```
...
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

Execution aborted.

```

The instructions I had used up to this point were:
[http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/]("http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/")
```
   1. Download VMware Server from the VMware website.
   2. Unpack the contents of the archive to your system (perhaps /tmp)
   3. sudo aptitude install build-essential xinetd linux-headers-$(uname -r)
   4. Open a terminal (Applications > Accessories > Terminal), cd /tmp/vmware-server (or wherever you unpacked the archive)
   5. sudo ./vmware-install.pl

```

What can I do now?

Thanks,
Greg

UPDATE: I'm trying it again, and I'm getting the same pop-up error as before* during the install* :
```
The NetworkManager applet could not find some required resources.  It cannot continue.
```

---

### Post by gregconquest on 2008-02-25
I refreshed an image of my ubuntu partition and tried VMware Player again using the binary from the vmware website. The install balked as it found a few remnants of the prior install . . . after a couple of tries, I got them all cleared, and then the install went flawlessly. The making of the modules that threw Server went fine with Player.

So, thanks for the help, but Server is just waaayyyy too much trouble. With a working Player, I am finally able to access my virtual Windows XP again from ubuntu.

Greg

---

### Post by fjgaude on 2008-02-25
I really don't know what is the issues with your Server install tries... I've not had any troubles with Server over the last year on four different computers.

Glad Player works for you.

---

