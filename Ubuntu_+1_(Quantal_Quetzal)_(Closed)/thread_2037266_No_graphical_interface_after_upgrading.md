---
title: "No graphical interface after upgrading"
date: 2012-08-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by marc raes on 2012-08-04
I realize it is not very clever, but I took the risk to upgrade to 12.10 by setting de sources list in my 12.04 to quantal using de sed command. On restarting it automatically switches on tty1. No way to get to the GUI.
I acted very impulsively out of anger because there was something wrong with the extra-driver for ati that no longer did the job. I thought upgrading would fix it. (I suppose I had too many beer!)
Stupid fool that I am, I even forgot to save my stuff first.
What can I do to recover my valuable stuff? Or is there a way to get the GUI back?

---

### Post by jfernyhough on 2012-08-04
I'm going to assume you installed the AMD proprietary graphics driver (fglrx) before upgrading; this doesn't work correctly with the current versions of the X server in Quantal.

To get back to a GUI you can 1) move your xorg.conf or 2) remove fglrx (and reboot). Either will put into use the open-source driver which should be working fine.
1) $ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
2) $ sudo purge fglrx

If you need fglrx (e.g. for the better power management) you'll need to either downgrade X to 1.12* and install a manually patched version, then patch another library.

For Radeons series 5000 up, instructions are here: [http://ubuntuforums.org/showpost.php?p=12090910&postcount=26](http://ubuntuforums.org/showpost.php?p=12090910&postcount=26) . If you have a 2000-4000 series you'll need the "legacy" driver ([http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx](http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx)).

For the libpciaccess patch instructions, look here: [http://ubuntuforums.org/showthread.php?t=2031533](http://ubuntuforums.org/showthread.php?t=2031533)

* I haven't tried upgrading to xserver 1.13 yet but I'm guessing fglrx 8.98 won't be compatible yet due to the ABI bump

---

### Post by marc raes on 2012-08-04
Thanks... but this doesn't work.
First of all: what is the point of making a backup of the '/etc/X11/xorg.conf' file? That on itself does nothing.
Then the command 'sudo purge' doesn't seem to exist.
I tried : 'rm fglrx' but got the answer: 'no such file'
So I tried 'sudo apt-get install fglrx' and got the answer: "fglrx is already the latest version.'
Strange... its there but I cant remove it.
Then I tried to locate it using the 'locate' command (sic). But this damned TTY1 screen has no scrollbar. Is there a way to get a scrollbar?

---

### Post by cariboo on 2012-08-05
> **marc raes said:**
> Thanks... but this doesn't work.
First of all: what is the point of making a backup of the '/etc/X11/xorg.conf' file? That on itself does nothing.
Then the command 'sudo purge' doesn't seem to exist.
I tried : 'rm fglrx' but got the answer: 'no such file'
So I tried 'sudo apt-get install fglrx' and got the answer: "fglrx is already the latest version.'
Strange... its there but I cant remove it.
Then I tried to locate it using the 'locate' command (sic). But this damned TTY1 screen has no scrollbar. Is there a way to get a scrollbar?

Backing up configuration files is always a good idea, before changing or removing them. It has saved me several times from a non-working system. In your case it won't so anything, but it's a good habit to get into.

We all make mistakes,

```
sudo purge
```

is incorrect, the command should have been:

```
sudo apt -get --purge fglrx
```

To page up and down in a terminal/console use shift-PageUp or shift-PageDwn, what I prefer, is the less command:

```
cat /var/log/some.log | less
```

the log file can the be read a page at a time by pressing the space bar.

---

### Post by QIII on 2012-08-05
> ```
sudo apt -get --purge fglrx
```And sometimes we make typos. ;)

Do it this way:
```
sudo apt-get purge fglrx
```"purge" does the same thing as "remove" with the addition of getting rid of configuration files (but not those in your home directory, which may have to be removed manually.)

You will often see

```
sudo apt-get remove --purge fglrx
```which is redundant over-kill, but I do it that way often.

For more information, 

```
man apt-get
```

---

### Post by effenberg0x0 on 2012-08-05
Just a note: to go up/down in the terminal (there's no scrollbar in the console, as you mention) you hold Shift and press PgUp or PgDn. This is sort of universal for Linux/Unix and will generally work in console or GUI mode.

Regards,
Effenberg

---

### Post by marc raes on 2012-08-05
It seems 'remove' as a command doesn't exist. It should be rm. Neither does --purge exist any more. And I always get the message that 'fglrx' is not an known file, although, when I check it, it is noted as 'already installed'. I installed it in 12.04 using the 'jockey'. If it causing the trouble, as was suggested, how the hell do I get rid of it? Don't forget I have only a terminal screen at my disposal.

---

### Post by effenberg0x0 on 2012-08-05
> **marc raes said:**
> It seems 'remove' as a command doesn't exist. It should be rm. Neither does --purge exist any more. And I always get the message that 'fglrx' is not an known file, although, when I check it, it is noted as 'already installed'. I installed it in 12.04 using the 'jockey'. If it causing the trouble, as was suggested, how the hell do I get rid of it? Don't forget I have only a terminal screen at my disposal.

Hi, each of the lines below is a working command, but neither will fix things for you now. 
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get remove --purge fglrx

```
I believe you won't be able to achieve what you need (i.e. run one or two simple commands and get back a working GUI-capable setup). 

The only way for you to fix things now would be to run these commands, but also (and most importantly) download and install adequate drivers for your VGA model. You would have to Google for instruction on how to do it, read one of the countless pages about it, or read one of the articles about it in Ubuntu Help Wiki, following the exact procedures these tutorials suggest and learning with it. This means reading a lot, investing a lot of time. In my opinion, it will take too long and be risky (because you mentioned you have important stuff in this machine). 

People can try a wild guess and come up with a couple lines for you to copy and paste there. If you search for my name plus fglrx on the General Help section you'll see I did it quite a lot in the past. The problem is: It is always a guess. We know nothing about your setup. We don't know the model of your VGA. We don't know which modules you're loading, which are blacklisted, we don't know if you have broken packages and unresolvable deps, we don't know how your PPAs look like, we know nothing - we can make things worse by trying to help at this point.  

If I were you, I would first focus on getting your data to a safe place. You seem to have a working console. Good, don't take it for granted - Murphy's laws sometimes take even the terminal from us. 

You can use this terminal to copy your data to another partition, to a mounted USB unit, to another internal/external HDD, to a NAS, to another machine in the same LAN, FTP it to a server, you can even connect two NICs via crossover cables, etc. You're still in control, with a lot of options and with no real losses.

Then once your data is safe elsewhere, if you feel like learning, you'll do it more freely and relaxed. You can break the machine just for fun. And if you just want the damned thing to work, you can insert Ubuntu CD-ROM, boot, and have a working OS back in minutes.

Good luck,
Effenberg

---

### Post by marc raes on 2012-08-05
> 
You can use this terminal to copy your data to another partition, to a mounted USB unit
I have indeed a working console, and I inserted a usb-stick but I coulden't get to it. What are the necessary commands? So that I get at least my files back. (I consider joining AA).

---

### Post by marc raes on 2012-08-05
Mister Effenberg, instead of offering me a very entertaining preach on how to learn from the faults of an 58 years old Flemish drunkard, could you give me some commands to get my GUI back?

---

### Post by QIII on 2012-08-05
Actually marc raes, I believe the two commands effenberg0x0 suggested will work.

Upgrading to a new version, as opposed to doing a fresh install, fails more often than not when proprietary drivers are left installed.  This is complicated in your current case by the fact that Quantal, the development release, is not ready for the fglrx driver.  That will happen shortly before release.

Last night I deliberately installed the fglrx driver on a Quantal machine, which broke it as I expected.

I recovered by entering recovery mode from the GRUB menu (if you don't normally see it, hold the Shift key down during boot up until the GRUB menu appears).

From GRUB, select Recovery.  On the menu, select the fsck option.  This will mount your system in read write mode.

When you get back to the command prompt, type "exit" to get back to the recovery menu.

Select the option to drop to root.

From there, run these two commands in order

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bak
```

```
sudo apt-get remove --purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

You may get a couple of messages that some packages did not exist and so were not removed.  Don't worry about it.

Finally, ```
sudo reboot
```

This should leave you with a working Quantal running the default open source Radeon driver.  You can then recover you data and go back to Precise.

---

### Post by effenberg0x0 on 2012-08-05
> **marc raes said:**
> Mister Effenberg, instead of offering me a very entertaining preach on how to learn from the faults of an 58 years old Flemish drunkard, could you give me some commands to get my GUI back?


Hi Marc, in my part of the world it was time to sleep.

**[SIZE="4"]1. Saving your stuff[/SIZE]**
[https://help.ubuntu.com/community/Mount/USB/](https://help.ubuntu.com/community/Mount/USB/)

Basically:
**1.** Get the device for your attached USB media. Will be something like /dev/sdb1
```
sudo fdisk -l
```
**2.** Check that the attached USB device isn't already mount to some directory. 
```
mount
```
Example of a mounted Corsair USB media, formatted to FAT (Windows format) and with Read and Write permissions:
> /dev/sdd1 on /run/media/ahsl/B13D-132F type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks2)
If it's already mounted, take note of the directory it is mounted to. (Ex. /media/something, /mnt/something, /run/media/you/something, etc). Jump to step **3**.

If it's not mounted, you need to mount it.
**2.1** Create a directory for it. I'll name it mydevice as an example:
```
sudo mkdir -p /media/mydevice
```
**2.2** Mount the unit. You can use any filesystem. 
Example: This would be mounting it with FAT filesystem assuming the device you found previously with the fidsk command is at /dev/sdb1:
```
sudo mount -t vfat /dev/sdb1 /media/mydevice -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```
**3.** Change directory to your home:
```
cd
```
**4.** Change directory to the subdirectory where your content is. Example using the Documents directory:
```
cd Documents
```
**5.** List the contents of the Documents directory, so you can see your content and decide what to save:
```
ls -lah
```
**6.** Copy the relevant files and subdirectories of your content to your USB device. This example assumes you have the following content inside $HOME/Documents: a file named important.txt and two subdirectories named MyStuff and OtherPeopleStuff:
```
sudo cp important.txt /media/mydevice/
sudo cp MyStuff /media/mydevice/
sudo cp OtherPeopleStuff /media/mydevice/
```
**7.** Verify that the files/directories were indeed copied to the usb unit by listing the files there.
```
ls -lah /media/mydevice
```
**8.** Once you're finished, umount the device so it can be removed safely:
```
sudo umount /media/mydevice
```
**9.** It would be best to remove the device and test reading the files in other PC before moving on, but that's up to you.

[SIZE="4"][B]2. Making your VGA work:
[/B][/SIZE]https://help.ubuntu.com/community/BinaryDriverHowto/ATI

That's it. 

Regards,
Effenberg

**EDIT:** Just saw QIII's reply, it's absolutely correct, stick to it.

---

### Post by ronacc on 2012-08-05
I just tried that on my quantal install and the usb device ( usb stick ) in this case did not automount unless you were already logged into the terminal . I tried it from a normal boot , did not log in but ctrl>alt>F1 at the login screen not recovery mode .

---

### Post by marc raes on 2012-08-05
I don't want to be rude, but if one gets a root prompt one does not need to use 'sudo'. Further more, the commands 'remove' and 'purge' don't exist, so it didn't work at all.

---

### Post by ronacc on 2012-08-05
see " man apt-get "     purge and remove DO exist in the context of apt-get

---

### Post by jfernyhough on 2012-08-05
> **marc raes said:**
> I don't want to be rude, but if one gets a root prompt one does not need to use 'sudo'. Further more, the commands 'remove' and 'purge' don't exist, so it didn't work at all.I don't want to be rude, but you've had answers from three experienced forum members. The sentence "so it didn't work at all" means nothing, especially as you **still** haven't given anyone any information about your system. For example, what graphics card do you have? Which driver did you install? Have you added any PPAs e.g. xorg-edgers?

The AMD proprietary driver does not work with the current packages  supplied by the quantal repositories. You have to keep specific packages  installed, patch a library, and patch the driver itself.

You need to remove the xorg.conf that Jockey created when it installed the AMD graphics driver. If you delete it then you can't get it back. If you move it (or "make a backup") then you have a copy "just in case". This is because the xorg.conf tells X which driver to use; if it is not present it will revert back to the open source drivers which should always work. If when you boot you have a "terminal screen" this means you can remove the xorg.conf file and reboot. X will load with the open source driver. 

You can do this by running the following command in a terminal:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.acopyjustincase

Notice that **mv** means "move" or "rename". **cp** means "copy".

Just to make sure X will use the open source driver it is a good idea to remove (or fully purge, take your pick) the proprietary AMD driver (otherwise known as fglrx).

You do this, quite simply, in a terminal, however you get to a terminal with the command:

sudo apt-get purge fglrx

If you have a root terminal, then you don't need sudo. Correct.

If you now start Ubuntu normally and X still does not load then it's possibly not a fault of the graphics driver. We won't know that unless you try the process and report back with a little more information than "it doesn't work."

You might like to have a look at the Xorg.log files:

cd /var/log
ls
[Look for the first Xorg log file]
nano /var/log/Xorg.0.log

Scroll to the bottom (down arrow or Page Down). This will tell you (or us) why X refuses to load.

---

### Post by effenberg0x0 on 2012-08-05
> **marc raes said:**
> I don't want to be rude, but if one gets a root prompt one does not need to use 'sudo'.
Good, then don't.
> **marc raes said:**
> 
Further more, the commands 'remove' and 'purge' don't exist, so it didn't work at all.

[ATTACH]222307[/ATTACH]

Regards,
Effenberg

---

### Post by marc raes on 2012-08-05
I do apologize very much.
I don't understand what went wrong the first time. Being very inexperienced at using the terminal I must have made a mistake typing the commands.
Regaining my calm I did it over and 'apt-get remove fglrx' did the job. I have my GUI back and I thank you all very very much for taking the trouble to inform me. Again: Thanks a lot!:P

---

### Post by ronacc on 2012-08-05
please mark your thread "solved"

---

### Post by marc raes on 2012-08-07
Although I marked the topic 'solved' I checked the /var/Xorg.0.log as jfernyhough suggested and got the following, which is Chinese to me.
Perhaps there is something in it I should change?
```
[    19.462] 
X.Org X Server 1.12.1.902 (1.12.2 RC 2)
Release Date: 2012-05-19
[    19.462] X Protocol Version 11, Revision 0
[    19.462] Build Operating System: Linux 3.2.0-23-generic x86_64 Ubuntu
[    19.462] Current Operating System: Linux marc-V-M4A3000E 3.5.0-8-generic #8-Ubuntu SMP Sat Aug 4 04:42:28 UTC 2012 x86_64
[    19.462] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-8-generic root=UUID=c9345855-c51d-4aaa-bec1-c079beafe619 ro quiet splash vt.handoff=7
[    19.462] Build Date: 22 June 2012  03:24:25AM
[    19.462] xorg-server 2:1.12.1.902-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    19.462] Current version of pixman: 0.26.0
[    19.462] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.462] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.462] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug  7 14:55:57 2012
[    19.803] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.965] (==) No Layout section.  Using the first Screen section.
[    19.965] (==) No screen section available. Using defaults.
[    19.965] (**) |-->Screen "Default Screen Section" (0)
[    19.965] (**) |   |-->Monitor "<default monitor>"
[    19.965] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    19.965] (==) Automatically adding devices
[    19.965] (==) Automatically enabling devices
[    20.008] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.008] 	Entry deleted from font path.
[    20.008] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.008] 	Entry deleted from font path.
[    20.008] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.008] 	Entry deleted from font path.
[    20.009] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.009] 	Entry deleted from font path.
[    20.009] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.009] 	Entry deleted from font path.
[    20.009] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    20.009] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.009] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.009] (II) Loader magic: 0x7fa4cfcb2b00
[    20.009] (II) Module ABI versions:
[    20.009] 	X.Org ANSI C Emulation: 0.4
[    20.009] 	X.Org Video Driver: 12.0
[    20.009] 	X.Org XInput driver : 16.0
[    20.009] 	X.Org Server Extension : 6.0
[    20.010] (--) PCI:*(0:1:5:0) 1002:9616:1043:8388 rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, 0xfe900000/1048576, I/O @ 0x0000d000/256
[    20.010] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.010] (II) LoadModule: "extmod"
[    20.148] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.234] (II) Module extmod: vendor="X.Org Foundation"
[    20.234] 	compiled for 1.12.1.902, module version = 1.0.0
[    20.234] 	Module class: X.Org Server Extension
[    20.234] 	ABI class: X.Org Server Extension, version 6.0
[    20.234] (II) Loading extension MIT-SCREEN-SAVER
[    20.234] (II) Loading extension XFree86-VidModeExtension
[    20.234] (II) Loading extension XFree86-DGA
[    20.234] (II) Loading extension DPMS
[    20.234] (II) Loading extension XVideo
[    20.234] (II) Loading extension XVideo-MotionCompensation
[    20.234] (II) Loading extension X-Resource
[    20.234] (II) LoadModule: "dbe"
[    20.234] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.281] (II) Module dbe: vendor="X.Org Foundation"
[    20.281] 	compiled for 1.12.1.902, module version = 1.0.0
[    20.281] 	Module class: X.Org Server Extension
[    20.281] 	ABI class: X.Org Server Extension, version 6.0
[    20.281] (II) Loading extension DOUBLE-BUFFER
[    20.281] (II) LoadModule: "glx"
[    20.281] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/libglx.so
[    20.839] (II) Module glx: vendor="NVIDIA Corporation"
[    20.839] 	compiled for 4.0.2, module version = 1.0.0
[    20.839] 	Module class: X.Org Server Extension
[    20.839] (II) NVIDIA GLX Module  304.32  Thu Aug  2 19:03:23 PDT 2012
[    20.839] (II) Loading extension GLX
[    20.839] (II) LoadModule: "record"
[    20.839] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.857] (II) Module record: vendor="X.Org Foundation"
[    20.857] 	compiled for 1.12.1.902, module version = 1.13.0
[    20.857] 	Module class: X.Org Server Extension
[    20.857] 	ABI class: X.Org Server Extension, version 6.0
[    20.857] (II) Loading extension RECORD
[    20.857] (II) LoadModule: "dri"
[    20.857] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.897] (II) Module dri: vendor="X.Org Foundation"
[    20.897] 	compiled for 1.12.1.902, module version = 1.0.0
[    20.897] 	ABI class: X.Org Server Extension, version 6.0
[    20.897] (II) Loading extension XFree86-DRI
[    20.897] (II) LoadModule: "dri2"
[    20.897] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.898] (II) Module dri2: vendor="X.Org Foundation"
[    20.898] 	compiled for 1.12.1.902, module version = 1.2.0
[    20.898] 	ABI class: X.Org Server Extension, version 6.0
[    20.898] (II) Loading extension DRI2
[    20.898] (==) Matched fglrx as autoconfigured driver 0
[    20.898] (==) Matched ati as autoconfigured driver 1
[    20.898] (==) Matched vesa as autoconfigured driver 2
[    20.898] (==) Matched fbdev as autoconfigured driver 3
[    20.898] (==) Assigned the driver to the xf86ConfigLayout
[    20.898] (II) LoadModule: "fglrx"
[    21.007] (WW) Warning, couldn't open module fglrx
[    21.007] (II) UnloadModule: "fglrx"
[    21.007] (II) Unloading fglrx
[    21.007] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    21.007] (II) LoadModule: "ati"
[    21.007] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.007] (II) Module ati: vendor="X.Org Foundation"
[    21.007] 	compiled for 1.12.1.902, module version = 6.14.4
[    21.007] 	Module class: X.Org Video Driver
[    21.007] 	ABI class: X.Org Video Driver, version 12.0
[    21.007] (II) LoadModule: "radeon"
[    21.007] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    21.069] (II) Module radeon: vendor="X.Org Foundation"
[    21.069] 	compiled for 1.12.1.902, module version = 6.14.4
[    21.069] 	Module class: X.Org Video Driver
[    21.069] 	ABI class: X.Org Video Driver, version 12.0
[    21.070] (II) LoadModule: "vesa"
[    21.070] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.135] (II) Module vesa: vendor="X.Org Foundation"
[    21.135] 	compiled for 1.12.1.902, module version = 2.3.1
[    21.135] 	Module class: X.Org Video Driver
[    21.135] 	ABI class: X.Org Video Driver, version 12.0
[    21.135] (II) LoadModule: "fbdev"
[    21.135] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.166] (II) Module fbdev: vendor="X.Org Foundation"
[    21.166] 	compiled for 1.12.1.902, module version = 0.4.2
[    21.166] 	ABI class: X.Org Video Driver, version 12.0
[    21.166] (==) Matched fglrx as autoconfigured driver 0
[    21.166] (==) Matched ati as autoconfigured driver 1
[    21.166] (==) Matched vesa as autoconfigured driver 2
[    21.166] (==) Matched fbdev as autoconfigured driver 3
[    21.166] (==) Assigned the driver to the xf86ConfigLayout
[    21.166] (II) LoadModule: "fglrx"
[    21.167] (WW) Warning, couldn't open module fglrx
[    21.167] (II) UnloadModule: "fglrx"
[    21.167] (II) Unloading fglrx
[    21.167] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    21.167] (II) LoadModule: "ati"
[    21.167] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.167] (II) Module ati: vendor="X.Org Foundation"
[    21.167] 	compiled for 1.12.1.902, module version = 6.14.4
[    21.167] 	Module class: X.Org Video Driver
[    21.167] 	ABI class: X.Org Video Driver, version 12.0
[    21.167] (II) LoadModule: "vesa"
[    21.167] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.167] (II) Module vesa: vendor="X.Org Foundation"
[    21.167] 	compiled for 1.12.1.902, module version = 2.3.1
[    21.167] 	Module class: X.Org Video Driver
[    21.167] 	ABI class: X.Org Video Driver, version 12.0
[    21.167] (II) UnloadModule: "vesa"
[    21.167] (II) Unloading vesa
[    21.167] (II) Failed to load module "vesa" (already loaded, 0)
[    21.167] (II) LoadModule: "fbdev"
[    21.167] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.167] (II) Module fbdev: vendor="X.Org Foundation"
[    21.167] 	compiled for 1.12.1.902, module version = 0.4.2
[    21.167] 	ABI class: X.Org Video Driver, version 12.0
[    21.167] (II) UnloadModule: "fbdev"
[    21.167] (II) Unloading fbdev
[    21.167] (II) Failed to load module "fbdev" (already loaded, 0)
[    21.167] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA
[    21.169] (II) VESA: driver for VESA chipsets: vesa
[    21.169] (II) FBDEV: driver for framebuffer: fbdev
[    21.169] (++) using VT number 7

[    21.169] (II) [KMS] Kernel modesetting enabled.
[    21.169] (WW) Falling back to old probe method for vesa
[    21.169] (WW) Falling back to old probe method for fbdev
[    21.169] (II) Loading sub module "fbdevhw"
[    21.169] (II) LoadModule: "fbdevhw"
[    21.169] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.320] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.320] 	compiled for 1.12.1.902, module version = 0.0.2
[    21.320] 	ABI class: X.Org Video Driver, version 12.0
[    21.320] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.320] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    21.320] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.320] (==) RADEON(0): Default visual is TrueColor
[    21.320] (==) RADEON(0): RGB weight 888
[    21.320] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    21.320] (--) RADEON(0): Chipset: "ATI Radeon 3000 Graphics" (ChipID = 0x9616)
[    21.320] (II) RADEON(0): PCI card detected
[    21.320] drmOpenDevice: node name is /dev/dri/card0
[    21.320] drmOpenDevice: open result is 9, (OK)
[    21.320] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    21.320] drmOpenDevice: node name is /dev/dri/card0
[    21.320] drmOpenDevice: open result is 9, (OK)
[    21.320] drmOpenByBusid: drmOpenMinor returns 9
[    21.320] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    21.320] (II) Loading sub module "exa"
[    21.320] (II) LoadModule: "exa"
[    21.320] (II) Loading /usr/lib/xorg/modules/libexa.so
[    21.385] (II) Module exa: vendor="X.Org Foundation"
[    21.385] 	compiled for 1.12.1.902, module version = 2.5.0
[    21.385] 	ABI class: X.Org Video Driver, version 12.0
[    21.385] (II) RADEON(0): KMS Color Tiling: enabled
[    21.385] (II) RADEON(0): KMS Pageflipping: enabled
[    21.385] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    21.414] (II) RADEON(0): Output VGA-0 has no monitor section
[    21.417] (II) RADEON(0): Output DVI-0 has no monitor section
[    21.446] (II) RADEON(0): EDID for output VGA-0
[    21.446] (II) RADEON(0): Manufacturer: AOC  Model: 1943  Serial#: 10916
[    21.446] (II) RADEON(0): Year: 2010  Week: 43
[    21.446] (II) RADEON(0): EDID Version: 1.3
[    21.446] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    21.446] (II) RADEON(0): Sync:  Separate
[    21.446] (II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 23
[    21.446] (II) RADEON(0): Gamma: 2.20
[    21.446] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    21.446] (II) RADEON(0): First detailed timing is preferred mode
[    21.446] (II) RADEON(0): redX: 0.633 redY: 0.346   greenX: 0.323 greenY: 0.612
[    21.446] (II) RADEON(0): blueX: 0.148 blueY: 0.066   whiteX: 0.313 whiteY: 0.329
[    21.446] (II) RADEON(0): Supported established timings:
[    21.446] (II) RADEON(0): 720x400@70Hz
[    21.446] (II) RADEON(0): 640x480@60Hz
[    21.446] (II) RADEON(0): 640x480@67Hz
[    21.446] (II) RADEON(0): 640x480@72Hz
[    21.446] (II) RADEON(0): 640x480@75Hz
[    21.446] (II) RADEON(0): 800x600@56Hz
[    21.446] (II) RADEON(0): 800x600@60Hz
[    21.446] (II) RADEON(0): 800x600@72Hz
[    21.446] (II) RADEON(0): 800x600@75Hz
[    21.446] (II) RADEON(0): 832x624@75Hz
[    21.446] (II) RADEON(0): 1024x768@60Hz
[    21.446] (II) RADEON(0): 1024x768@70Hz
[    21.446] (II) RADEON(0): 1024x768@75Hz
[    21.446] (II) RADEON(0): Manufacturer's mask: 0
[    21.446] (II) RADEON(0): Supported standard timings:
[    21.446] (II) RADEON(0): #0: hsize: 640  vsize 400  refresh: 70  vid: 2609
[    21.446] (II) RADEON(0): Supported detailed timing:
[    21.446] (II) RADEON(0): clock: 85.5 MHz   Image Size:  410 x 230 mm
[    21.446] (II) RADEON(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
[    21.446] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
[    21.446] (II) RADEON(0): Supported detailed timing:
[    21.446] (II) RADEON(0): clock: 85.5 MHz   Image Size:  410 x 230 mm
[    21.446] (II) RADEON(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[    21.446] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[    21.446] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 95 MHz
[    21.446] (II) RADEON(0): Monitor name: 1943W
[    21.446] (II) RADEON(0): EDID (in hex):
[    21.446] (II) RADEON(0): 	00ffffffffffff0005e34319a42a0000
[    21.446] (II) RADEON(0): 	2b140103682917782a2f05a258529c26
[    21.446] (II) RADEON(0): 	115054bfee00310a0101010101010101
[    21.446] (II) RADEON(0): 	010101010101662156aa51001e30468f
[    21.446] (II) RADEON(0): 	33009ae61000001e662150b051001b30
[    21.446] (II) RADEON(0): 	407036009ae61000001e000000fd0032
[    21.446] (II) RADEON(0): 	4b1e5309000a202020202020000000fc
[    21.446] (II) RADEON(0): 	0031393433570a20202020202020001b
[    21.446] (II) RADEON(0): EDID vendor "AOC", prod id 6467
[    21.481] (II) RADEON(0): Using EDID range info for horizontal sync
[    21.481] (II) RADEON(0): Using EDID range info for vertical refresh
[    21.481] (II) RADEON(0): Printing DDC gathered Modelines:
[    21.481] (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    21.481] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    21.481] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    21.481] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    21.481] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    21.481] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    21.481] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    21.481] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.481] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    21.481] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    21.481] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    21.481] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    21.481] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    21.481] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    21.481] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    21.481] (II) RADEON(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz e)
[    21.481] (II) RADEON(0): Printing probed modes for output VGA-0
[    21.482] (II) RADEON(0): Modeline "1366x768"x59.8   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    21.482] (II) RADEON(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    21.482] (II) RADEON(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz e)
[    21.482] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    21.482] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    21.482] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    21.482] (II) RADEON(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[    21.482] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    21.482] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    21.482] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    21.482] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    21.482] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    21.482] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    21.482] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    21.482] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    21.482] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    21.482] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.482] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    21.482] (II) RADEON(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz)
[    21.484] (II) RADEON(0): EDID for output DVI-0
[    21.484] (II) RADEON(0): Output VGA-0 connected
[    21.484] (II) RADEON(0): Output DVI-0 disconnected
[    21.484] (II) RADEON(0): Using exact sizes for initial modes
[    21.484] (II) RADEON(0): Output VGA-0 using initial mode 1366x768
[    21.484] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.484] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fba0000
[    21.484] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    21.484] (**) RADEON(0): Display dimensions: (410, 230) mm
[    21.484] (**) RADEON(0): DPI set to (84, 84)
[    21.484] (II) Loading sub module "fb"
[    21.484] (II) LoadModule: "fb"
[    21.484] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.497] (II) Module fb: vendor="X.Org Foundation"
[    21.497] 	compiled for 1.12.1.902, module version = 1.0.0
[    21.497] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.497] (II) Loading sub module "ramdac"
[    21.497] (II) LoadModule: "ramdac"
[    21.497] (II) Module "ramdac" already built-in
[    21.497] (II) UnloadModule: "vesa"
[    21.497] (II) Unloading vesa
[    21.497] (II) UnloadModule: "fbdev"
[    21.497] (II) Unloading fbdev
[    21.497] (II) UnloadSubModule: "fbdevhw"
[    21.497] (II) Unloading fbdevhw
[    21.497] (--) Depth 24 pixmap format is 32 bpp
[    21.507] (II) RADEON(0): [DRI2] Setup complete
[    21.507] (II) RADEON(0): [DRI2]   DRI driver: r600
[    21.507] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    21.507] (II) RADEON(0): Front buffer size: 4224K
[    21.507] (II) RADEON(0): VRAM usage limit set to 228096K
[    21.508] (==) RADEON(0): Backing store disabled
[    21.508] (II) RADEON(0): Direct rendering enabled
[    21.516] (II) RADEON(0): Setting EXA maxPitchBytes
[    21.516] (II) EXA(0): Driver allocated offscreen pixmaps
[    21.516] (II) EXA(0): Driver registered support for the following operations:
[    21.516] (II)         Solid
[    21.516] (II)         Copy
[    21.516] (II)         Composite (RENDER acceleration)
[    21.516] (II)         UploadToScreen
[    21.516] (II)         DownloadFromScreen
[    21.517] (II) RADEON(0): Acceleration enabled
[    21.517] (==) RADEON(0): DPMS enabled
[    21.517] (==) RADEON(0): Silken mouse enabled
[    21.546] (II) RADEON(0): Set up textured video
[    21.546] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    21.546] (II) RADEON(0): [XvMC] Extension initialized.
[    21.546] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.546] (--) RandR disabled
[    21.546] (II) Initializing built-in extension Generic Event Extension
[    21.546] (II) Initializing built-in extension SHAPE
[    21.546] (II) Initializing built-in extension MIT-SHM
[    21.546] (II) Initializing built-in extension XInputExtension
[    21.546] (II) Initializing built-in extension XTEST
[    21.546] (II) Initializing built-in extension BIG-REQUESTS
[    21.546] (II) Initializing built-in extension SYNC
[    21.546] (II) Initializing built-in extension XKEYBOARD
[    21.546] (II) Initializing built-in extension XC-MISC
[    21.546] (II) Initializing built-in extension SECURITY
[    21.546] (II) Initializing built-in extension XINERAMA
[    21.546] (II) Initializing built-in extension XFIXES
[    21.546] (II) Initializing built-in extension RENDER
[    21.546] (II) Initializing built-in extension RANDR
[    21.546] (II) Initializing built-in extension COMPOSITE
[    21.546] (II) Initializing built-in extension DAMAGE
[    21.597] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    21.736] (II) RADEON(0): Setting screen physical size to 361 x 203
[    21.990] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.065] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.065] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.065] (II) LoadModule: "evdev"
[    22.065] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.094] (II) Module evdev: vendor="X.Org Foundation"
[    22.094] 	compiled for 1.11.3, module version = 2.7.0
[    22.094] 	Module class: X.Org XInput Driver
[    22.094] 	ABI class: X.Org XInput driver, version 16.0
[    22.094] (II) Using input driver 'evdev' for 'Power Button'
[    22.094] (**) Power Button: always reports core events
[    22.094] (**) evdev: Power Button: Device: "/dev/input/event1"
[    22.094] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.094] (--) evdev: Power Button: Found keys
[    22.094] (II) evdev: Power Button: Configuring as keyboard
[    22.094] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.094] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.094] (**) Option "xkb_rules" "evdev"
[    22.094] (**) Option "xkb_model" "pc105"
[    22.094] (**) Option "xkb_layout" "be"
[    22.095] (II) XKB: reuse xkmfile /var/lib/xkb/server-BCDBD3DBC93B3E588F97965C4D87FE91FAEC6B41.xkm
[    22.096] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.096] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.096] (II) Using input driver 'evdev' for 'Power Button'
[    22.096] (**) Power Button: always reports core events
[    22.096] (**) evdev: Power Button: Device: "/dev/input/event0"
[    22.096] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.096] (--) evdev: Power Button: Found keys
[    22.096] (II) evdev: Power Button: Configuring as keyboard
[    22.096] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.096] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    22.096] (**) Option "xkb_rules" "evdev"
[    22.096] (**) Option "xkb_model" "pc105"
[    22.096] (**) Option "xkb_layout" "be"
[    22.097] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event2)
[    22.097] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.097] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    22.097] (**) Logitech USB Keyboard: always reports core events
[    22.097] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event2"
[    22.097] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31d
[    22.097] (--) evdev: Logitech USB Keyboard: Found keys
[    22.097] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    22.097] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2/event2"
[    22.097] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 8)
[    22.097] (**) Option "xkb_rules" "evdev"
[    22.097] (**) Option "xkb_model" "pc105"
[    22.097] (**) Option "xkb_layout" "be"
[    22.097] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event3)
[    22.097] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.097] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    22.097] (**) Logitech USB Keyboard: always reports core events
[    22.097] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event3"
[    22.097] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31d
[    22.097] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    22.097] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    22.097] (--) evdev: Logitech USB Keyboard: Found keys
[    22.097] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    22.097] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    22.097] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input3/event3"
[    22.097] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 9)
[    22.097] (**) Option "xkb_rules" "evdev"
[    22.097] (**) Option "xkb_model" "pc105"
[    22.097] (**) Option "xkb_layout" "be"
[    22.098] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    22.098] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    22.098] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    22.098] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    22.098] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    22.098] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
[    22.098] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    22.098] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    22.098] (**) Logitech USB Optical Mouse: always reports core events
[    22.098] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event4"
[    22.098] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    22.098] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    22.098] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    22.098] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    22.098] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    22.098] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    22.098] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    22.098] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    22.098] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.098] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input4/event4"
[    22.098] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 10)
[    22.098] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    22.098] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    22.098] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    22.098] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    22.098] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    22.098] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    22.098] (II) No input driver specified, ignoring this device.
[    22.098] (II) This device may have been added with another device file.
[    22.099] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event5)
[    22.099] (II) No input driver specified, ignoring this device.
[    22.099] (II) This device may have been added with another device file.
[    22.099] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event6)
[    22.099] (II) No input driver specified, ignoring this device.
[    22.099] (II) This device may have been added with another device file.
[    22.099] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event7)
[    22.099] (II) No input driver specified, ignoring this device.
[    22.099] (II) This device may have been added with another device file.
[    22.099] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event8)
[    22.099] (II) No input driver specified, ignoring this device.
[    22.099] (II) This device may have been added with another device file.
[    22.099] (II) config/udev: Adding input device HDA ATI SB Line Out (/dev/input/event9)
[    22.099] (II) No input driver specified, ignoring this device.
[    22.099] (II) This device may have been added with another device file.
[    30.024] (II) RADEON(0): EDID vendor "AOC", prod id 6467
[    30.024] (II) RADEON(0): Using hsync ranges from config file
[    30.024] (II) RADEON(0): Using vrefresh ranges from config file
[    30.024] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.024] (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    30.024] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    30.024] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    30.024] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    30.024] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    30.024] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    30.024] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    30.024] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    30.024] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    30.024] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    30.024] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    30.024] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    30.024] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    30.024] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    30.024] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    30.024] (II) RADEON(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz e)
[    32.641] (II) RADEON(0): EDID vendor "AOC", prod id 6467
[    32.641] (II) RADEON(0): Using hsync ranges from config file
[    32.641] (II) RADEON(0): Using vrefresh ranges from config file
[    32.641] (II) RADEON(0): Printing DDC gathered Modelines:
[    32.641] (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    32.641] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    32.641] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    32.641] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    32.641] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    32.641] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    32.641] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    32.641] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    32.641] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    32.641] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    32.641] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    32.641] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    32.641] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    32.641] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    32.641] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    32.641] (II) RADEON(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz e)
[    46.002] (II) RADEON(0): EDID vendor "AOC", prod id 6467
[    46.002] (II) RADEON(0): Using hsync ranges from config file
[    46.002] (II) RADEON(0): Using vrefresh ranges from config file
[    46.002] (II) RADEON(0): Printing DDC gathered Modelines:
[    46.002] (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    46.002] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    46.002] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    46.002] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    46.002] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    46.002] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    46.002] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    46.002] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    46.002] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    46.002] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    46.002] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    46.002] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    46.002] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    46.002] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    46.002] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    46.002] (II) RADEON(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz e)
[    48.087] (II) RADEON(0): EDID vendor "AOC", prod id 6467
[    48.087] (II) RADEON(0): Using hsync ranges from config file
[    48.087] (II) RADEON(0): Using vrefresh ranges from config file
[    48.087] (II) RADEON(0): Printing DDC gathered Modelines:
[    48.087] (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    48.087] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    48.087] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    48.087] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    48.087] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    48.087] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    48.087] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    48.087] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    48.087] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    48.087] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    48.087] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    48.087] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    48.087] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    48.087] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    48.087] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    48.087] (II) RADEON(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz e)
[    65.083] (II) RADEON(0): EDID vendor "AOC", prod id 6467
[    65.083] (II) RADEON(0): Using hsync ranges from config file
[    65.083] (II) RADEON(0): Using vrefresh ranges from config file
[    65.083] (II) RADEON(0): Printing DDC gathered Modelines:
[    65.083] (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    65.083] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    65.083] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    65.083] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    65.083] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    65.083] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    65.083] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    65.083] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    65.083] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    65.083] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    65.083] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    65.083] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    65.083] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    65.083] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    65.083] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    65.083] (II) RADEON(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz e)
[   790.788] (II) Open ACPI successful (/var/run/acpid.socket)
[   790.818] (II) RADEON(0): EDID vendor "AOC", prod id 6467
[   790.818] (II) RADEON(0): Using hsync ranges from config file
[   790.818] (II) RADEON(0): Using vrefresh ranges from config file
[   790.818] (II) RADEON(0): Printing DDC gathered Modelines:
[   790.818] (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[   790.818] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[   790.818] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   790.818] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   790.818] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   790.818] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   790.818] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   790.818] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   790.818] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   790.818] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   790.818] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   790.818] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   790.818] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   790.818] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   790.818] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   790.818] (II) RADEON(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz e)
```

---

### Post by marc raes on 2012-08-07
Could anybody check my /etc/X11/xorg.conf file please? See if it's all right.
I got my GUI back but it takes a lot of time to start up and it seems to use two phases with the screen telling 'no signal' in the middle of the proces.
If I list X11, I don't see an 'xorg.config' file but tree files (I made a backup as suggested, repeating the procedure twice)
I have 'xorg.config.bak and 'xorg.conf_back' looking like this:
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True" 
EndSection

```
And a 'xorg.conf.dist-upgrade-201204270904' which also looks the same as above and finally a 'xorg.conf.failsafe' which looks like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Three files, saying the same thing, would they slow up the starting up?
NB. Te original file seems to have disappeared... or is it this 'xorg.conf-dist-upgrade' file?

---

### Post by Harry33 on 2012-08-08
> **marc raes said:**
> Although I marked the topic 'solved' I checked the /var/Xorg.0.log as jfernyhough suggested and got the following, which is Chinese to me.
Perhaps there is something in it I should change?


You've got errors there. That is bad. See the lines:

```

X.Org X Server 1.12.1.902 (1.12.2 RC 2)
Release Date: 2012-05-19
....
[    20.898] (II) LoadModule: "fglrx"
[    21.007] (WW) Warning, couldn't open module fglrx
[    21.007] (II) UnloadModule: "fglrx"
[    21.007] (II) Unloading fglrx
[    21.007] (EE) **Failed to load module "fglrx" (module does not exist, 0)**
[    21.007] (II) LoadModule: "ati"

[    21.167] (WW) Warning, couldn't open module fglrx
[    21.167] (II) UnloadModule: "fglrx"
[    21.167] (II) Unloading fglrx

[    21.167] (EE) **Failed to load module "fglrx" (module does not exist, 0)**
[    21.167] (II) LoadModule: "ati"

```

Please see that everything referring to fglrx is completely removed. You better do this with Synaptic.
You are using xserver 1.12 branch and that is correct, but you should only be using open source ati video driver:
- xserver-xorg-video-ati
- xserver-xorg-video-radeon

See that you do not have the proposed repo enabled either. Otherwise you will get xserver 1.13, and with even more trouble.

---

### Post by Harry33 on 2012-08-08
> **marc raes said:**
> Could anybody check my /etc/X11/xorg.conf file please? See if it's all right.
I got my GUI back but it takes a lot of time to start up and it seems to use two phases with the screen telling 'no signal' in the middle of the proces.
If I list X11, I don't see an 'xorg.config' file but tree files (I made a backup as suggested, repeating the procedure twice)
I have 'xorg.config.bak and 'xorg.conf_back' looking like this:
...


The system does not use those *.bak nor "xorg.conf_back" files.
You should use open source ati drivers, so your system does not need a xorg.conf file.
It will automatically detect the hardware.

---

### Post by marc raes on 2012-08-08
> **Harry33 said:**
> The system does not use those *.bak nor "xorg.conf_back" files.
You should use open source ati drivers, so your system does not need a xorg.conf file.
It will automatically detect the hardware.
I made these backup files following the suggestions from other people. As you can see above.
As I may remind you, the original problem was that I upgraded from an existing OS 12.04 to 12.10 resetting the source.list to quantal.
The effect was that my GUI disappeared.
I was instructed to make a backup of the /etc/X11/xorg.conf file and than to remove the fglrx modules with commands that initially didn't seem to work.
On second try, this did work and I got my GUI back but the start-up of the machine is very slow and very strange. That's why I put the question.
Looking at what is installed regarding ati, checking synaptic I see that the open source ati drivers are installed.
I don't know why this file still mentions the fglrx... anyway I removed it completely and didn't open the 'proposed'.
The system starts op very strangely... but it does start up.
We live in hope. At least I was able to get to my work and backed it up.

---

