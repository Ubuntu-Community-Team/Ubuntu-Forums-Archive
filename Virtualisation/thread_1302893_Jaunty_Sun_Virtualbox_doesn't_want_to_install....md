---
title: "Jaunty Sun Virtualbox doesn't want to install..."
date: 2009-10-27
forum: Virtualisation
---

### Post by guiliker on 2009-10-27
Recently upgraded to Jaunty, from the CD image.

I come to install Sun Virtual box (virtualbox-3.0_3.0.8-53138_Ubuntu_jaunty_i386.deb) because I need USB support, however it doesn't seem to exist, even when it says it has installed.

install log:```
** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.0.8/source ->
                 /usr/src/vboxdrv-3.0.8

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-16-generic -C /lib/modules/2.6.28-16-generic/build M=/var/lib/dkms/vboxdrv/3.0.8/build........

Running the post_build script:
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.28-16-generic/updates/dkms/

depmod....

DKMS: install Completed.
** Compiling vboxnetflt
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetflt/3.0.8/source ->
                 /usr/src/vboxnetflt-3.0.8

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-16-generic -C /lib/modules/2.6.28-16-generic/build M=/var/lib/dkms/vboxnetflt/3.0.8/build.......
cleaning build area....

DKMS: build Completed.

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/2.6.28-16-generic/kernel/misc/vboxnetflt.ko
   - Storing in /var/lib/dkms/vboxnetflt/original_module/2.6.28-16-generic/i686/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/2.6.28-16-generic/updates/dkms/

depmod....

DKMS: install Completed.
** Compiling vboxnetadp
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetadp/3.0.8/source ->
                 /usr/src/vboxnetadp-3.0.8

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-16-generic -C /lib/modules/2.6.28-16-generic/build M=/var/lib/dkms/vboxnetadp/3.0.8/build.......
cleaning build area....

DKMS: build Completed.

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/2.6.28-16-generic/kernel/misc/vboxnetadp.ko
   - Storing in /var/lib/dkms/vboxnetadp/original_module/2.6.28-16-generic/i686/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/2.6.28-16-generic/updates/dkms/

depmod....

DKMS: install Completed.
```

Also there is no click onto icon on the application menu nor does the command virtualbox-3.0 do anything.

help!

---

### Post by spongypants23 on 2009-10-27
I've found the the menu item for VirtualBox tends to be sneaky. It should show up under Applications > System Tools (or something like that, my system is in Swedish), but sometimes you have to put it there manually by editing the menus. (Not sure why this is the case.)

If you try to lauch it manually, what happens? Enter "VirtualBox" in a terminal window (CASE SENSITIVE!).

By the way, virtualbox-3.0 is just the name of the package, not the binary.

---

### Post by guiliker on 2009-10-27
I always feel like such a fool when it turns out to be so obvious!

I had tried entering 'virtualbox' into the terminal and had been greeted with an invitation to install virtualbox-ose, however now I have done it capitalised with a 'V' and a 'B' it works like a treat!

I still do not have a clicky icon though :-(

---

### Post by spongypants23 on 2009-10-27
[LIST]
[*]Right-click the GNOME menu.
[*]Edit menus
[*]Select "System Tools"
[*]There should be an entry for VirtualBox. If checked, Click on the check mark to unmark it, then click the box to mark it again. It should now show up. If it is unmarked, click the unchecked box to check it. It should now show up.
[*]If there is no entry for VirtualBox, click the "New Object" button and create one manually.
[/LIST]

---

### Post by guiliker on 2009-10-28
I've had to create a launcher manually, in the "other" menu, as it doesn't exist and to make matters more irritating the "System Tools" menu doesn't work (I have a separate post for that on the forums: [http://ubuntuforums.org/showthread.php?t=1302881](http://ubuntuforums.org/showthread.php?t=1302881)) even when I select it or de-select it. I have also tried deleting the menu config files but alas no difference.

Thanks for the advice by the way :)

---

### Post by joewski on 2009-10-29
You need to log out and log back in for the menu's to update. You will find Suns Virtualbox under applications->system tools

Also it Virtualbox will not appear in apps launcher either until you log out and back in again..

---

### Post by spongypants23 on 2009-10-29
> **joewski said:**
> You need to log out and log back in for the menu's to update. You will find Suns Virtualbox under applications->system tools

Also it Virtualbox will not appear in apps launcher either until you log out and back in again..

Something must be wrong with your system if this is the case. I've always had my menus update right after apt-get is finished.

---

### Post by guiliker on 2009-10-29
The menu updates every other section e.g. "Office", "Internet", "Accessories" with application launchers e.g. Wine, Scribus, Gramps, etc just not the "System Tools" menu. Nothing on the that specific menu such as Sun VirtualBox, Compiz-Fusion-Icon, Sysinfo appears no matter if they are there to be selected in Alarcarte, even though Sun VirtualBox is not.

I guess because of another bug with console-kit-daemon which has apparently been fixed in Karmic I will try upgrading to that and see if that solves it otherwise I'll downgrade back to Intrepid...

---

