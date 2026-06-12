---
title: "New Remastersys Test packages 3.0.2-1 supporting Ubuntu 12.04"
date: 2012-04-06
forum: The Cafe
---

### Post by Fragadelic on 2012-04-06
Supports versions 10.04 to 12.04 Ubuntu and variants.

I have posted up some new test packages for remastersys 3.0.2-1.

I have split off the gui to its own package and this one has a brand new gui created in BaCon - [http://www.basic-converter.org](http://www.basic-converter.org) with the HUG gui.

Added ubiquity-frontend-debconf as a dependency to prevent synaptic from installing ALL of the frontends causing a lot of packages to be installed that aren't needed.

Code cleanup and fixes for Ubuntu 12.04.

The gui now lets you view the log file directly making it easier to copy and paste it here to the forum.  I believe the gui now makes more sense and should be easier to use for users new to remastersys.

You can set the default grub background for your system with remastersys-gui.

You can create a simple plymouth theme for your system with remastersys-gui.

You can preview the newly created plymouth theme with remastersys-gui.

You can select which plymouth theme is set to be the default for your system with remastersys-gui.

You can set the live system boot menu background picture with remastersys-gui.

You can copy your user settings to be the default for the live system - copies certain folders and files from your chosen user to /etc/skel which is the new user folder skeleton and removes config files or folders that would cause user creation to fail.


Please try it out and post feedback in this thread.


[http://www.remastersys.com/forums/index.php?topic=2161.0](http://www.remastersys.com/forums/index.php?topic=2161.0)

---

### Post by Fragadelic on 2012-04-10
I had to abandon the new gui due to problems with 64-bit.  The gtk gui is back as the default gui.

I have put the packages also for direct download at [http://www.remastersys.com/downloads](http://www.remastersys.com/downloads) right now and when this is tested enough I'll add a precise signed repository.

If you installed the remastersys-gui, uninstall it prior to installing remastersys-gtk.

---

### Post by Megaptera on 2012-04-11
Many thanks for this update. Will follow progress.

---

### Post by Fragadelic on 2012-04-11
I will have to recompile the gui for 64-bit but I'm not ready for that yet.  That might make it back into the package for 3.0.3-1

---

### Post by Fragadelic on 2012-04-13
I decided to setup a 64-bit partition and compiled the gui in 64-bit as well so now it works as intended on 64-bit(amd64).

New packages are up with the new gui.  If you don't want to go to my forum, you can get them from this downloads folder on my website.

[http://www.remastersys.com/downloads](http://www.remastersys.com/downloads)

The gui will be in i386 and amd64 from now on and the main base cli package will work for either architecture.

---

### Post by Megaptera on 2012-04-14
I'll give 64 bit a try with 12.04, thanks!

---

### Post by Fragadelic on 2012-04-14
Let me know how it works for you.  I have been testing in 64-bit myself for a few days and it seems to be behaving properly.

---

### Post by Megaptera on 2012-04-15
Hi,
Downloaded .deb from the link in 

Double-clicked the .deb and Ubuntu Software Centre gave this I'm afraid to say:

(Reading database ... 253637 files and directories currently installed.)
Unpacking remastersys-gui (from .../remastersys-gui_3.0.2-1_amd64.deb) ...
dpkg: error processing /home/richard/Downloads/remastersys-gui_3.0.2-1_amd64.deb (--install):
 trying to overwrite '/usr/bin/plymouth-preview', which is also in package remastersys 3.0.0-1
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /home/richard/Downloads/remastersys-gui_3.0.2-1_amd64.deb

---

### Post by Fragadelic on 2012-04-15
You need to install the new base remastersys 3.0.2-1 first and then the gui.

I split the main off from the gui so if folks don't want a gui or anything remastersys to show up in the menu they can still use just the base remastersys cli package.  When upgrading from the older version you must install the base package first which will upgrade to the new version and then the gui.

---

### Post by Megaptera on 2012-04-15
Thanks for that (note to self - read posts carefully!!) GUI now opens properly and all looks familiar.
 I'll try running a backup in the next day or so.

---

### Post by Fragadelic on 2012-04-21
I have created a thread for the translations.

[http://www.remastersys.com/forums/index.php?topic=2195.0](http://www.remastersys.com/forums/index.php?topic=2195.0)

If you would like remastersys to have your translation, please check the thread.

---

### Post by Fragadelic on 2012-04-25
I put some fixes in the gui and the base package for live user creation.  The new packages are here - [http://www.remastersys.com/downloads](http://www.remastersys.com/downloads)

I accidentally introduced a bug in the 3.0.x series relating to live user creation during live boot that would prevent the live user from being created.  This was introduced as a result of trying to fix the issue with the recovery mode.  I put the recovery mode fix in the remastersys-firstboot and pulled it from remastersys so it doesn't interfere with the live user creation.

If everything goes as planned these packages will be the final that I will be releasing at the end of this week.

You need to install the remastersys_3.0.2-1_all.deb first for either i386 or amd64 and then the appropriate gui for your arch - remastersys-gui_3.0.2-1_i386.deb for i386 and remastersys-gui_3.0.2-1_amd64.deb for amd64.

Many thanks to everyone that helped track down and help me find the bugs.

---

### Post by sanitarium616 on 2012-04-25
this maybe me being stupid but i cant find the gui for it

---

### Post by Fragadelic on 2012-04-25
Do you mean you can't find it in my downloads folder on my website or you can't find it in your menu?

If it is in your menu, what desktop are you using?

Also, the base 3.0.2 package must be installed prior to installing the gui package as the old base package had everything and your system will prevent you from installing another package with overlapping files.  Once you install the new base package it will get rid of everything from the old one and update the files needed.  At this point the gui can be installed and should show up in your menu.

---

### Post by sanitarium616 on 2012-04-25
I'm using ubuntu 11.10 and i downloaded the remastersys 3.0.2-1 all.deb file and am confused as to where the gui files are located in order to download and install them

---

### Post by sanitarium616 on 2012-04-25
doh i just noticed my problem. should really read links better.

---

### Post by oberworld on 2012-04-30
Hello, thanks for your great work.

I'm using ubuntu 12.04.

Can't install gui:

> (Reading database ... 100%
(Reading database ... 185920 files and directories currently installed.)
Unpacking remastersys-gui (from .../remastersys-gui_3.0.2-1_i386.deb) ...
dpkg: error processing /home/toni/Escritorio/remastersys-gui_3.0.2-1_i386.deb (--install):
 trying to overwrite '/usr/bin/plymouth-preview', which is also in package remastersys-gtk 3.0.2-1
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /home/myuser/Escritorio/remastersys-gui_3.0.2-1_i386.deb

Also, without using the gui the program works perfect, when I run my backup boots fine, but when I try to install it boots to desktop and give me an error:

[[IMG]http://img11.imageshack.us/img11/6584/seleccin001r.png[/IMG]](http://imageshack.us/photo/my-images/11/seleccin001r.png/)

Help, please.

Sorry for my english is not my native languaje.

Thanks in advance.

Here is the log file.

---

### Post by josephmills on 2012-04-30
This is all great news I love remastersys

---

### Post by Fragadelic on 2012-04-30
You have to install the base remastersys package before installing the gui.

up to 3.0.1-1 the gui and base cli were one package.  Starting with 3.0.2-1 they are split off separately so you have to install the base first and then the gui.

This also means that if you don't want to the gui you don't have to have it.  All the files are contained in the base cli package.  This is also so that the remastersys-gtk gui can still be used with remastersys.

---

### Post by oberworld on 2012-04-30
I have installed the base package first.

I dont mind to install the gui.

But I can't use my backups since it don't install.

This is my Big problem.

When I select install in grub menu its boot to desktop and gives me the error above.

Thanks anyway.

---

### Post by Fragadelic on 2012-04-30
What happens when you bring up the desktop and then try to install?

---

### Post by oberworld on 2012-04-30
I don't have install icon on desktop in my live-CD backup.

Only way to try to install is in grub menu before live CD starts.

Anyway, if I select install, it's boot to desktop & gives me the error in the snapshot.

Thank you again for be here and help me.

---

### Post by Fragadelic on 2012-04-30
Did you have internet access when you remastered?  That is the only time the frontend is downloaded and installed.

---

### Post by oberworld on 2012-05-01
No, I disconnect internet connection before the program starts.

Must I make the backup with internet connection on?

I have disconnected because the program says "close all windows & internet connections".

Regards.

EDIT: extract of remastersys.log:

> ------------------------------------------------------
Command-line options = backup
------------------------------------------------------
Cleaning up the install icon from the user desktops
Removing the ubiquity frontend as it has been included and is not needed on the normal system

---

### Post by Fragadelic on 2012-05-01
The frontend is removed at the end as you don't need it on the installed system but you need internet access.

The message is regarding network shares.

You must be using the remastersys-gtk frontend as I do not have that message on the remastersys-gui.

---

### Post by oberworld on 2012-05-01
Yes, it's  the remastersys-gtk frontend since I can't install  the remastersys-gui.

I'll try later with internet connection and then i'll post here later if it works.

Thank you very much for give me your help.

I'm very thankful to you.

---

### Post by Fragadelic on 2012-05-01
You are very welcome.

What problem did you have with remastersys-gui?

---

### Post by oberworld on 2012-05-01
Here's a quote of one of my previous post:

> **oberworld said:**
> Hello, thanks for your great work.

I'm using ubuntu 12.04.

Can't install gui:

> (Reading database ... 100%
(Reading database ... 185920 files and directories currently installed.)
Unpacking remastersys-gui (from .../remastersys-gui_3.0.2-1_i386.deb) ...
dpkg: error processing /home/toni/Escritorio/remastersys-gui_3.0.2-1_i386.deb (--install):
trying to overwrite '/usr/bin/plymouth-preview', which is also in package remastersys-gtk 3.0.2-1
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
/home/toni/Escritorio/remastersys-gui_3.0.2-1_i386.deb



---

### Post by Fragadelic on 2012-05-01
You have to uninstall remastersys-gtk before you install remastersys-gui.

---

### Post by pelerin21 on 2012-05-01
I make a backup on my fresh install of Ubuntu 12.04. But when I use open the backup on live mode when log in to desktop Software center, chromium and glipper gives crash error. I can use these apps properly but why I get these messages?

thank you!

---

### Post by oberworld on 2012-05-01
All works fine now, if I make my backup connected to internet it works fine, I haven't icon to install on desktop, but can install ok by grub menu install option.

Also I have unnistalled remastersys-gtk and installed remastersys-gui sucefully.

Thankyou very much for your help.

Im so so happy now.

Regards.

---

### Post by pelerin21 on 2012-05-03
> **oberworld said:**
> All works fine now, if I make my backup connected to internet it works fine, I haven't icon to install on desktop, but can install ok by grub menu install option.

Also I have unnistalled remastersys-gtk and installed remastersys-gui sucefully.

Thankyou very much for your help.

Im so so happy now.

Regards.

I make the same think but it does not work :mad: :(

---

### Post by Fragadelic on 2012-05-03
> **pelerin21 said:**
> I make the same think but it does not work :mad: :(
Can you post your remastersys.log?

---

### Post by pelerin21 on 2012-05-05
> **Fragadelic said:**
> Can you post your remastersys.log?

Here it is:

```


System Backup Mode Selected
Checking filesystem type of the Working Folder as it must be a valid linux filesystem for permissions
/home/remastersys/remastersys is on an ext4 filesystem
Making sure popularity contest is not installed
Installing the proper Ubiquity frontend
Checking if the /home/remastersys/remastersys folder has been created
Creating /home/remastersys/remastersys folder tree
Creating /home/remastersys/remastersys/ISOTMP folder tree
Copying /var and /etc to temp area and excluding extra files  ... this will take a while so be patient
Cleaning up files not needed for the live in /home/remastersys/remastersys/dummysys
Making sure adduser and autologin functions of casper are set properly
Copying memtest86+ for the live system
Creating isolinux setup for the live system
Checking the ARCH of the system and setting the README.diskdefines file
Creating filesystem.manifest and filesystem.manifest-desktop
Excluding folder from the backup that will cause issues
Copying the install icon to the desktop of dave
Creating the casper.conf file.
Checking and setting user-setup-apply for the live system
Setting up casper and ubiquity options for backup mode
Creating a new initial ramdisk for the live system
Copying your kernel and initrd for the livecd
Creating filesystem.squashfs   ... this will take a while so be patient
Adding stage 1 files/folders that the livecd requires
Adding stage 2 files/folders that the livecd requires
------------------------------------------------------
Mount information
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
------------------------------------------------------
Disk size information
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        21G  6.4G   14G  33% /
udev            414M  4.0K  414M   1% /dev
tmpfs           170M  904K  169M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            424M  104K  424M   1% /run/shm
------------------------------------------------------
Casper Script info
total 148
-rwxr-xr-x 1 root root  297 Apr 18 12:17 01integrity_check
-rwxr-xr-x 1 root root  467 Apr 18 12:17 05mountpoints
-rwxr-xr-x 1 root root  571 Apr 18 12:17 07remove_oem_config
-rwxr-xr-x 1 root root  400 Apr 18 12:17 12fstab
-rwxr-xr-x 1 root root  830 Apr 18 12:17 13swap
-rwxr-xr-x 1 root root 1221 Apr 18 12:17 14locales
-rw-r--r-- 1 root root 2920 Apr 18 12:17 15autologin
-rwxr-xr-x 1 root root  577 Apr 18 12:17 18hostname
-rwxr-xr-x 1 root root 8878 Apr 18 12:17 19keyboard
-rwxr-xr-x 1 root root  546 Apr 18 12:17 20xconfig
-rwxr-xr-x 1 root root  624 Apr 18 12:17 22gnome_panel_data
-rwxr-xr-x 1 root root  867 Apr 18 12:17 22screensaver
-rwxr-xr-x 1 root root  577 Apr 18 12:17 22serialtty
-rwxr-xr-x 1 root root  410 Apr 18 12:17 22sslcert
-rwxr-xr-x 1 root root  380 Apr 18 12:17 23etc_modules
-rwxr-xr-x 1 root root 3786 Apr 18 12:33 23networking
-rwxr-xr-x 1 root root 2102 Apr 18 12:17 24preseed
-rw-r--r-- 1 root root 3939 Apr 18 12:17 25adduser
-rwxr-xr-x 1 root root 1996 Apr 18 12:17 25configure_init
-rwxr-xr-x 1 root root  644 Apr 18 12:17 26disable_user_menu
-rwxr-xr-x 1 root root 1421 Apr 18 12:17 30accessibility
-rwxr-xr-x 1 root root 1152 Apr 18 12:17 31disable_update_notifier
-rwxr-xr-x 1 root root  463 Apr 18 12:17 32disable_hibernation
-rwxr-xr-x 1 root root  650 Apr 18 12:17 33enable_apport_crashes
-rwxr-xr-x 1 root root  928 Apr 18 12:17 34disable_kde_services
-rwxr-xr-x 1 root root  562 Apr 18 12:17 35fix_language_selector
-rwxr-xr-x 1 root root  407 Apr 18 12:17 36disable_trackerd
-rwxr-xr-x 1 root root  908 Apr 18 12:17 40install_driver_updates
-rwxr-xr-x 1 root root  561 Apr 18 12:17 41apt_cdrom
-rwxr-xr-x 1 root root  847 Apr 18 12:17 43disable_updateinitramfs
-rwxr-xr-x 1 root root  640 Apr 18 12:17 44pk_allow_ubuntu
-rwxr-xr-x 1 root root  594 Apr 18 12:17 45jackd2
-rwxr-xr-x 1 root root  215 Apr 18 12:17 48kubuntu_disable_restart_notifications
-rwxr-xr-x 1 root root  169 Apr 18 12:17 49kubuntu_mobile_session
-rwxr-xr-x 1 root root  346 Apr 18 12:17 50ubiquity-bluetooth-agent
------------------------------------------------------
/etc/remastersys.conf info

#Remastersys Global Configuration File


# This is the temporary working directory and won't be included on the cd/dvd
WORKDIR="/home/remastersys"


# Here you can add any other files or directories to be excluded from the live filesystem
# Separate each entry with a space
EXCLUDES=""


# Here you can change the livecd/dvd username
LIVEUSER="dave"


# Here you can change the name of the livecd/dvd label
LIVECDLABEL="Ubuntu1204Custom"


# Here you can change the name of the ISO file that is created
CUSTOMISO="Ubuntu1204Custom.iso"

# Here you can change the mksquashfs options
SQUASHFSOPTS="-no-recovery -always-use-fragments -b 1M -no-duplicates"


# Here you can prevent the Install icon from showing up on the desktop in backup mode. 0 - to not show 1 - to show 
BACKUPSHOWINSTALL="1"


# Here you can change the url for the usb-creator info
LIVECDURL="http://www.remastersys.com"
------------------------------------------------------
/etc/casper.conf info
# This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM
 
export USERNAME="dave"
export USERFULLNAME="Live session user"
export HOST="dave"
export BUILD_SYSTEM="Ubuntu"
------------------------------------------------------
/etc/passwd info
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
colord:x:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false
whoopsie:x:105:114::/nonexistent:/bin/false
avahi-autoipd:x:106:117:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:108:46:usbmux daemon,,,:/home/usbmux:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:122:RealtimeKit,,,:/proc:/bin/false
speech-dispatcher:x:112:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:114:123::/home/saned:/bin/false
dave:x:1000:1000:dave,,,:/home/dave:/bin/bash
gdm:x:115:125:Gnome Display Manager:/var/lib/gdm:/bin/false
mysql:x:104:111:MySQL Server,,,:/nonexistent:/bin/false
ntp:x:116:126::/home/ntp:/bin/false
mythtv:x:117:127::/home/mythtv:/bin/sh
------------------------------------------------------
/etc/group info
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:dave
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:mythtv
fax:x:21:
voice:x:22:
cdrom:x:24:dave,mythtv
floppy:x:25:
tape:x:26:
sudo:x:27:dave
audio:x:29:pulse,mythtv
dip:x:30:dave
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:mythtv
sasl:x:45:
plugdev:x:46:dave
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
bluetooth:x:106:
scanner:x:107:
colord:x:108:
lpadmin:x:109:dave
ssl-cert:x:110:
nopasswdlogin:x:112:
netdev:x:113:
whoopsie:x:114:
mlocate:x:115:
ssh:x:116:
avahi-autoipd:x:117:
avahi:x:118:
pulse:x:119:
pulse-access:x:120:
utempter:x:121:
rtkit:x:122:
saned:x:123:
dave:x:1000:
sambashare:x:124:dave
gdm:x:125:
mysql:x:111:
ntp:x:126:
mythtv:x:127:
vboxusers:x:128:
------------------------------------------------------
/etc/X11/default-display-manager info
/usr/sbin/gdm
------------------------------------------------------
lsb-release info
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
------------------------------------------------------
remastersys version info
REMASTERSYSVERSION="3.0.0-1"
 
------------------------------------------------------
ISOTMP info
/home/remastersys/remastersys/ISOTMP:
total 20
drwxr-xr-x 2 root root 4096 Apr 29 20:34 casper
drwxr-xr-x 2 root root 4096 Apr 29 20:33 install
drwxr-xr-x 2 root root 4096 Apr 29 20:34 isolinux
drwxr-xr-x 2 root root 4096 Apr 29 20:33 preseed
-rw-r--r-- 1 root root  197 Apr 29 20:34 README.diskdefines

/home/remastersys/remastersys/ISOTMP/casper:
total 1573636
-rw-r--r-- 1 root root      56233 Apr 29 20:34 filesystem.manifest
-rw-r--r-- 1 root root      56203 Apr 29 20:34 filesystem.manifest-desktop
-rw-r--r-- 1 root root 1585709056 Apr 29 20:45 filesystem.squashfs
-rw-r--r-- 1 root root   20550838 Apr 29 20:34 initrd.gz
-rw-r--r-- 1 root root        197 Apr 29 20:34 README.diskdefines
-rw------- 1 root root    5015872 Apr 29 20:34 vmlinuz

/home/remastersys/remastersys/ISOTMP/install:
total 176
-rw-r--r-- 1 root root 176764 Apr 29 20:33 memtest

/home/remastersys/remastersys/ISOTMP/isolinux:
total 604
-rw-r--r-- 1 root root  24576 Apr 29 20:33 isolinux.bin
-rw-r--r-- 1 root root    898 Apr 29 20:34 isolinux.cfg
-rwxr-xr-x 1 root root 429403 Apr 29 20:34 splash.png
-rw-r--r-- 1 root root 155792 Apr 29 20:34 vesamenu.c32

/home/remastersys/remastersys/ISOTMP/preseed:
total 4
-rwxr-xr-x 1 root root 212 Apr 29 20:33 custom.seed
------------------------------------------------------
/home/remastersys/remastersys/tmpusers info
------------------------------------------------------
Command-line options = backup
------------------------------------------------------
Cleaning up the install icon from the user desktop
Removing the ubiquity frontend as it has been included and is not needed on the normal system
Calculating the installed filesystem size for the installer
Making disk compatible with Ubuntu Startup Disk Creator.
Creating md5sum.txt for the livecd/dvd
Creating Ubuntu1204Custom.iso in /home/remastersys/remastersys
Creating Ubuntu1204Custom.iso.md5 in /home/remastersys/remastersys
/home/remastersys/remastersys/Ubuntu1204Custom.iso which is 1.6G in size is ready to be burned or tested in a virtual machine.


```

---

### Post by Fragadelic on 2012-05-05
> **pelerin21 said:**
> Here it is:

```


System Backup Mode Selected
Checking filesystem type of the Working Folder as it must be a valid linux filesystem for permissions
/home/remastersys/remastersys is on an ext4 filesystem
Making sure popularity contest is not installed
Installing the proper Ubiquity frontend
Checking if the /home/remastersys/remastersys folder has been created
Creating /home/remastersys/remastersys folder tree
Creating /home/remastersys/remastersys/ISOTMP folder tree
Copying /var and /etc to temp area and excluding extra files  ... this will take a while so be patient
Cleaning up files not needed for the live in /home/remastersys/remastersys/dummysys
Making sure adduser and autologin functions of casper are set properly
Copying memtest86+ for the live system
Creating isolinux setup for the live system
Checking the ARCH of the system and setting the README.diskdefines file
Creating filesystem.manifest and filesystem.manifest-desktop
Excluding folder from the backup that will cause issues
Copying the install icon to the desktop of dave
Creating the casper.conf file.
Checking and setting user-setup-apply for the live system
Setting up casper and ubiquity options for backup mode
Creating a new initial ramdisk for the live system
Copying your kernel and initrd for the livecd
Creating filesystem.squashfs   ... this will take a while so be patient
Adding stage 1 files/folders that the livecd requires
Adding stage 2 files/folders that the livecd requires
------------------------------------------------------
Mount information
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
------------------------------------------------------
Disk size information
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        21G  6.4G   14G  33% /
udev            414M  4.0K  414M   1% /dev
tmpfs           170M  904K  169M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            424M  104K  424M   1% /run/shm
------------------------------------------------------
Casper Script info
total 148
-rwxr-xr-x 1 root root  297 Apr 18 12:17 01integrity_check
-rwxr-xr-x 1 root root  467 Apr 18 12:17 05mountpoints
-rwxr-xr-x 1 root root  571 Apr 18 12:17 07remove_oem_config
-rwxr-xr-x 1 root root  400 Apr 18 12:17 12fstab
-rwxr-xr-x 1 root root  830 Apr 18 12:17 13swap
-rwxr-xr-x 1 root root 1221 Apr 18 12:17 14locales
-rw-r--r-- 1 root root 2920 Apr 18 12:17 15autologin
-rwxr-xr-x 1 root root  577 Apr 18 12:17 18hostname
-rwxr-xr-x 1 root root 8878 Apr 18 12:17 19keyboard
-rwxr-xr-x 1 root root  546 Apr 18 12:17 20xconfig
-rwxr-xr-x 1 root root  624 Apr 18 12:17 22gnome_panel_data
-rwxr-xr-x 1 root root  867 Apr 18 12:17 22screensaver
-rwxr-xr-x 1 root root  577 Apr 18 12:17 22serialtty
-rwxr-xr-x 1 root root  410 Apr 18 12:17 22sslcert
-rwxr-xr-x 1 root root  380 Apr 18 12:17 23etc_modules
-rwxr-xr-x 1 root root 3786 Apr 18 12:33 23networking
-rwxr-xr-x 1 root root 2102 Apr 18 12:17 24preseed
-rw-r--r-- 1 root root 3939 Apr 18 12:17 25adduser
-rwxr-xr-x 1 root root 1996 Apr 18 12:17 25configure_init
-rwxr-xr-x 1 root root  644 Apr 18 12:17 26disable_user_menu
-rwxr-xr-x 1 root root 1421 Apr 18 12:17 30accessibility
-rwxr-xr-x 1 root root 1152 Apr 18 12:17 31disable_update_notifier
-rwxr-xr-x 1 root root  463 Apr 18 12:17 32disable_hibernation
-rwxr-xr-x 1 root root  650 Apr 18 12:17 33enable_apport_crashes
-rwxr-xr-x 1 root root  928 Apr 18 12:17 34disable_kde_services
-rwxr-xr-x 1 root root  562 Apr 18 12:17 35fix_language_selector
-rwxr-xr-x 1 root root  407 Apr 18 12:17 36disable_trackerd
-rwxr-xr-x 1 root root  908 Apr 18 12:17 40install_driver_updates
-rwxr-xr-x 1 root root  561 Apr 18 12:17 41apt_cdrom
-rwxr-xr-x 1 root root  847 Apr 18 12:17 43disable_updateinitramfs
-rwxr-xr-x 1 root root  640 Apr 18 12:17 44pk_allow_ubuntu
-rwxr-xr-x 1 root root  594 Apr 18 12:17 45jackd2
-rwxr-xr-x 1 root root  215 Apr 18 12:17 48kubuntu_disable_restart_notifications
-rwxr-xr-x 1 root root  169 Apr 18 12:17 49kubuntu_mobile_session
-rwxr-xr-x 1 root root  346 Apr 18 12:17 50ubiquity-bluetooth-agent
------------------------------------------------------
/etc/remastersys.conf info

#Remastersys Global Configuration File


# This is the temporary working directory and won't be included on the cd/dvd
WORKDIR="/home/remastersys"


# Here you can add any other files or directories to be excluded from the live filesystem
# Separate each entry with a space
EXCLUDES=""


# Here you can change the livecd/dvd username
LIVEUSER="dave"


# Here you can change the name of the livecd/dvd label
LIVECDLABEL="Ubuntu1204Custom"


# Here you can change the name of the ISO file that is created
CUSTOMISO="Ubuntu1204Custom.iso"

# Here you can change the mksquashfs options
SQUASHFSOPTS="-no-recovery -always-use-fragments -b 1M -no-duplicates"


# Here you can prevent the Install icon from showing up on the desktop in backup mode. 0 - to not show 1 - to show 
BACKUPSHOWINSTALL="1"


# Here you can change the url for the usb-creator info
LIVECDURL="http://www.remastersys.com"
------------------------------------------------------
/etc/casper.conf info
# This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM
 
export USERNAME="dave"
export USERFULLNAME="Live session user"
export HOST="dave"
export BUILD_SYSTEM="Ubuntu"
------------------------------------------------------
/etc/passwd info
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
colord:x:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false
whoopsie:x:105:114::/nonexistent:/bin/false
avahi-autoipd:x:106:117:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:108:46:usbmux daemon,,,:/home/usbmux:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:122:RealtimeKit,,,:/proc:/bin/false
speech-dispatcher:x:112:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:114:123::/home/saned:/bin/false
dave:x:1000:1000:dave,,,:/home/dave:/bin/bash
gdm:x:115:125:Gnome Display Manager:/var/lib/gdm:/bin/false
mysql:x:104:111:MySQL Server,,,:/nonexistent:/bin/false
ntp:x:116:126::/home/ntp:/bin/false
mythtv:x:117:127::/home/mythtv:/bin/sh
------------------------------------------------------
/etc/group info
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:dave
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:mythtv
fax:x:21:
voice:x:22:
cdrom:x:24:dave,mythtv
floppy:x:25:
tape:x:26:
sudo:x:27:dave
audio:x:29:pulse,mythtv
dip:x:30:dave
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:mythtv
sasl:x:45:
plugdev:x:46:dave
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
bluetooth:x:106:
scanner:x:107:
colord:x:108:
lpadmin:x:109:dave
ssl-cert:x:110:
nopasswdlogin:x:112:
netdev:x:113:
whoopsie:x:114:
mlocate:x:115:
ssh:x:116:
avahi-autoipd:x:117:
avahi:x:118:
pulse:x:119:
pulse-access:x:120:
utempter:x:121:
rtkit:x:122:
saned:x:123:
dave:x:1000:
sambashare:x:124:dave
gdm:x:125:
mysql:x:111:
ntp:x:126:
mythtv:x:127:
vboxusers:x:128:
------------------------------------------------------
/etc/X11/default-display-manager info
/usr/sbin/gdm
------------------------------------------------------
lsb-release info
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
------------------------------------------------------
remastersys version info
REMASTERSYSVERSION="3.0.0-1"
 
------------------------------------------------------
ISOTMP info
/home/remastersys/remastersys/ISOTMP:
total 20
drwxr-xr-x 2 root root 4096 Apr 29 20:34 casper
drwxr-xr-x 2 root root 4096 Apr 29 20:33 install
drwxr-xr-x 2 root root 4096 Apr 29 20:34 isolinux
drwxr-xr-x 2 root root 4096 Apr 29 20:33 preseed
-rw-r--r-- 1 root root  197 Apr 29 20:34 README.diskdefines

/home/remastersys/remastersys/ISOTMP/casper:
total 1573636
-rw-r--r-- 1 root root      56233 Apr 29 20:34 filesystem.manifest
-rw-r--r-- 1 root root      56203 Apr 29 20:34 filesystem.manifest-desktop
-rw-r--r-- 1 root root 1585709056 Apr 29 20:45 filesystem.squashfs
-rw-r--r-- 1 root root   20550838 Apr 29 20:34 initrd.gz
-rw-r--r-- 1 root root        197 Apr 29 20:34 README.diskdefines
-rw------- 1 root root    5015872 Apr 29 20:34 vmlinuz

/home/remastersys/remastersys/ISOTMP/install:
total 176
-rw-r--r-- 1 root root 176764 Apr 29 20:33 memtest

/home/remastersys/remastersys/ISOTMP/isolinux:
total 604
-rw-r--r-- 1 root root  24576 Apr 29 20:33 isolinux.bin
-rw-r--r-- 1 root root    898 Apr 29 20:34 isolinux.cfg
-rwxr-xr-x 1 root root 429403 Apr 29 20:34 splash.png
-rw-r--r-- 1 root root 155792 Apr 29 20:34 vesamenu.c32

/home/remastersys/remastersys/ISOTMP/preseed:
total 4
-rwxr-xr-x 1 root root 212 Apr 29 20:33 custom.seed
------------------------------------------------------
/home/remastersys/remastersys/tmpusers info
------------------------------------------------------
Command-line options = backup
------------------------------------------------------
Cleaning up the install icon from the user desktop
Removing the ubiquity frontend as it has been included and is not needed on the normal system
Calculating the installed filesystem size for the installer
Making disk compatible with Ubuntu Startup Disk Creator.
Creating md5sum.txt for the livecd/dvd
Creating Ubuntu1204Custom.iso in /home/remastersys/remastersys
Creating Ubuntu1204Custom.iso.md5 in /home/remastersys/remastersys
/home/remastersys/remastersys/Ubuntu1204Custom.iso which is 1.6G in size is ready to be burned or tested in a virtual machine.


```
You should upgrade to the newest 3.0.2 version of remastersys.  More details on it can be found on my website or on the thread in this forum area on the official release of it.  In 12.04 Canonical added another "FLAVOUR" option in the casper.conf file which, if not set, takes the name of your distro and your name is quite long so this may be the issue.

---

### Post by pelerin21 on 2012-05-05
> **Fragadelic said:**
> You should upgrade to the newest 3.0.2 version of remastersys.  More details on it can be found on my website or on the thread in this forum area on the official release of it.  In 12.04 Canonical added another "FLAVOUR" option in the casper.conf file which, if not set, takes the name of your distro and your name is quite long so this may be the issue.

I could not find any 3.0.2 version of remastersys on sub-links of this:

[http://www.remastersys.com/repository/](http://www.remastersys.com/repository/)
(I want a .deb to install)


Also for name that you say possible long is the link of iso? Ubuntu1204Custom.iso?

---

### Post by Fragadelic on 2012-05-05
Please check my website for the info you need.  The repository link you provided is old.  I have long since created signed repositories and there is inof for precise there.

---

### Post by traditionalist on 2012-05-09
Well, I finally got a version downloaded from the repository on the website, ( The GtK version), but it doesn't work. The discs wont boot.  The version I had before worked but I seem unable to obtain it. I must be doing something wrong, but what?

Regards....Trad

---

### Post by traditionalist on 2012-05-09
No matter what I do I can not get the gui version, all I get is this;

[[IMG]http://img152.imageshack.us/img152/4844/selection001v.th.png[/IMG]](http://img152.imageshack.us/i/selection001v.png/)

Regards....Trad

---

### Post by Fragadelic on 2012-05-09
Traditionalist - you need to get the 3.0.2 version as that is the only one that officially supports 12.04 and this is also the first version where the gui is split off from the base cli package.  Prior to this version, remastersys cli and gui was always a single package.

You can get info on adding my repository for precise on [http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html) or directly download it from [http://www.remastersys.com/downloads/](http://www.remastersys.com/downloads/)

---

### Post by traditionalist on 2012-05-09
> **Fragadelic said:**
> Traditionalist - you need to get the 3.0.2 version as that is the only one that officially supports 12.04 and this is also the first version where the gui is split off from the base cli package.  Prior to this version, remastersys cli and gui was always a single package.

You can get info on adding my repository for precise on [http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html) or directly download it from [http://www.remastersys.com/downloads/](http://www.remastersys.com/downloads/)

I tried all the ways described on your site. None of them worked. I just downloaded the versions here;

[http://www.remastersys.com/downloads/](http://www.remastersys.com/downloads/)

saved them to disc ( Doesn't work if you try to open in Ubuntu Software Center), double clicked on the downloads.  ( You have to click on the main package first, if you try to install the GUI first it wont work).  They opened and ran in Ubuntu Software Centre.  

So, I finally got the complete setup again.  I am running a backup now, just as a test. I know it wont work because there is too much data in there right now.  Once I am sure it works I will get rid of some stuff and run it for real;

[[IMG]http://img99.imageshack.us/img99/7193/selection002x.th.png[/IMG]]("http://img99.imageshack.us/i/selection002x.png/")

Regards....Trad

---

### Post by traditionalist on 2012-05-09
Well, that didn't work either. I removed all excess data. Ran the backup and it told me it was successful, but the disc wouldn't boot. Hangs at "Isolinux.....".

So, I assume there is some sort of error on my system. I am going to reinstall the whole lot from scratch and see where that gets me.

Regards....Trad

---

### Post by Fragadelic on 2012-05-09
Before you do that, post you remastersys.log so I can see if something sticks out.

---

### Post by traditionalist on 2012-05-09
> **Fragadelic said:**
> Before you do that, post you remastersys.log so I can see if something sticks out.

Already did it!  There were a couple of things I wanted to change anyway. I am restoring data now.  When finished I will try remastersys again. This MUST work, because it is the last successful backup I made using remastersys.

I will let you know how I get on.

Regards....Trad

---

### Post by traditionalist on 2012-05-09
I think I found the major error, Remastersys is not excluding the /Home  folder.  Still playing around with it.

Despite all these problems it is a really great program once it runs.  The only thing allowing me to do a lot of these things is the baseline backup I made with it after I had set things up. 

Without that,  most things would simply not have been possible at all in any reasonable timeframe.

I will get it working eventually.

Regards....Trad

---

### Post by traditionalist on 2012-05-10
Just for people reading this. The problem was caused by the "tracker" indexer.  After removing it remastersys once again worked perfectly.  The indexer was also causing very considerable other problems.

Regards....Trad

---

### Post by pelerin21 on 2012-05-14
> **traditionalist said:**
> Just for people reading this. The problem was caused by the "tracker" indexer.  After removing it remastersys once again worked perfectly.  The indexer was also causing very considerable other problems.

Regards....Trad

Hi,

Which tracker do you talking about? I search on software center "tracker" and "indexer" but nothing installed on my system. I use Ubuntu 12.04 32 bit.

@[Fragadelic]("http://ubuntuforums.org/member.php?u=386921") I need also GUI. Which should I install from this link: [http://www.remastersys.com/downloads/](http://www.remastersys.com/downloads/)

Thanks

---

### Post by Fragadelic on 2012-05-16
> **pelerin21 said:**
> Hi,

Which tracker do you talking about? I search on software center "tracker" and "indexer" but nothing installed on my system. I use Ubuntu 12.04 32 bit.

@[Fragadelic]("http://ubuntuforums.org/member.php?u=386921") I need also GUI. Which should I install from this link: [http://www.remastersys.com/downloads/](http://www.remastersys.com/downloads/)

Thanks

What version of Ubuntu are you running?  Check the READMD.txt file in that folder for details.

---

### Post by pelerin21 on 2012-05-16
> **Fragadelic said:**
> What version of Ubuntu are you running?  Check the READMD.txt file in that folder for details.

I am using Ubuntu 12.04.

---

### Post by Fragadelic on 2012-05-16
You can use either remastersys-gtk or the new official gui - remastersys-gui.  When you download remastersys-gui, just make sure to get the right one for your architecture.

---

### Post by nm_geo on 2012-05-16
Hi Fragadelic,

Been awhile, I think it was during the Beta 1 Precise roll out before Lubuntu & Xubuntu went to a non-pae kernel as I recall. 

I will probably be trying out the new Remastersys on Lubuntu and Xubuntu anything specific you need tested let me know.

Hope you are doing well.

---

### Post by Fragadelic on 2012-05-16
You might as well wait a day or two as I have another update coming to fix the usb startup disk creator issue.

I will try to push the update tonight if I get a chance.

---

### Post by pelerin21 on 2012-05-16
@Fragadelic I downloaded the remastersys and I make my own iso. Thank you!

I need to ask you something different. I can open Ubuntu from USB by writing it with unetbootin (or alternatives). But **some **of my USB could not open by **some **computers. I will buy a new USB. But I don't know if it will open by all machines. Can you please tell me about these issue...

Thank you again!

---

### Post by Fragadelic on 2012-05-16
pelerin21 - that issue is usually due to the bios on the computers that have an issue.

What you can try is to delete all partitions on the usb key and create a partition #4.

More info can be found here - [http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/](http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/)

---

### Post by pelerin21 on 2012-05-19
@Fragadelic I solved the boot problem. Thank you!

No I make a backup of my Ubuntu 12.04 with the latest version of remastersys. 

But on the installation process of my custom Ubuntu I get this error from ubiguity:

```
The username you entered is invalid. Note that usernames must start with a lower-case letter, which can be followed by any combination of numbers and more lower-case letters.
```At the same time it gives this error too:

```
ubi-partman failed wtih exit code 10. Further information may found in var/log/syslog
```I send you also my syslog file:

```
May 19 18:58:01 dave kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 19 18:58:01 dave rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1057" x-info="http://www.rsyslog.com"] start
May 19 18:58:01 dave rsyslogd: rsyslogd's groupid changed to 103
May 19 18:58:01 dave rsyslogd: rsyslogd's userid changed to 101
May 19 18:58:01 dave rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May 19 18:58:01 dave kernel: [    0.000000] Initializing cgroup subsys cpuset
May 19 18:58:01 dave kernel: [    0.000000] Initializing cgroup subsys cpu
May 19 18:58:01 dave kernel: [    0.000000] Linux version 3.2.0-24-generic-pae (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 (Ubuntu 3.2.0-24.37-generic-pae 3.2.14)
May 19 18:58:01 dave kernel: [    0.000000] KERNEL supported cpus:
May 19 18:58:01 dave kernel: [    0.000000]   Intel GenuineIntel
May 19 18:58:01 dave kernel: [    0.000000]   AMD AuthenticAMD
May 19 18:58:01 dave kernel: [    0.000000]   NSC Geode by NSC
May 19 18:58:01 dave kernel: [    0.000000]   Cyrix CyrixInstead
May 19 18:58:01 dave kernel: [    0.000000]   Centaur CentaurHauls
May 19 18:58:01 dave kernel: [    0.000000]   Transmeta GenuineTMx86
May 19 18:58:01 dave kernel: [    0.000000]   Transmeta TransmetaCPU
May 19 18:58:01 dave kernel: [    0.000000]   UMC UMC UMC UMC
May 19 18:58:01 dave kernel: [    0.000000] BIOS-provided physical RAM map:
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
May 19 18:58:01 dave kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
May 19 18:58:01 dave kernel: [    0.000000] NX (Execute Disable) protection: active
May 19 18:58:01 dave kernel: [    0.000000] DMI 2.4 present.
May 19 18:58:01 dave kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. P35-S3G/P35-S3G, BIOS F2 11/30/2007
May 19 18:58:01 dave kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
May 19 18:58:01 dave kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
May 19 18:58:01 dave kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x1000000
May 19 18:58:01 dave kernel: [    0.000000] MTRR default type: uncachable
May 19 18:58:01 dave kernel: [    0.000000] MTRR fixed ranges enabled:
May 19 18:58:01 dave kernel: [    0.000000]   00000-9FFFF write-back
May 19 18:58:01 dave kernel: [    0.000000]   A0000-BFFFF uncachable
May 19 18:58:01 dave kernel: [    0.000000]   C0000-CEFFF write-protect
May 19 18:58:01 dave kernel: [    0.000000]   CF000-EFFFF uncachable
May 19 18:58:01 dave kernel: [    0.000000]   F0000-FFFFF write-through
May 19 18:58:01 dave kernel: [    0.000000] MTRR variable ranges enabled:
May 19 18:58:01 dave kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
May 19 18:58:01 dave kernel: [    0.000000]   1 base 07FF00000 mask FFFF00000 write-through
May 19 18:58:01 dave kernel: [    0.000000]   2 disabled
May 19 18:58:01 dave kernel: [    0.000000]   3 disabled
May 19 18:58:01 dave kernel: [    0.000000]   4 disabled
May 19 18:58:01 dave kernel: [    0.000000]   5 disabled
May 19 18:58:01 dave kernel: [    0.000000]   6 disabled
May 19 18:58:01 dave kernel: [    0.000000]   7 disabled
May 19 18:58:01 dave kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May 19 18:58:01 dave kernel: [    0.000000] found SMP MP-table at [c00f51b0] f51b0
May 19 18:58:01 dave kernel: [    0.000000] initial memory mapped : 0 - 02000000
May 19 18:58:01 dave kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
May 19 18:58:01 dave kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
May 19 18:58:01 dave kernel: [    0.000000]  0000000000 - 0000200000 page 4k
May 19 18:58:01 dave kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
May 19 18:58:01 dave kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
May 19 18:58:01 dave kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
May 19 18:58:01 dave kernel: [    0.000000] RAMDISK: 7eb46000 - 7fedf000
May 19 18:58:01 dave kernel: [    0.000000] Allocated new RAMDISK: 36865000 - 37bfded3
May 19 18:58:01 dave kernel: [    0.000000] Move RAMDISK from 000000007eb46000 - 000000007fedeed2 to 36865000 - 37bfded2
May 19 18:58:01 dave kernel: [    0.000000] ACPI: RSDP 000f6b60 00014 (v00 GBT   )
May 19 18:58:01 dave kernel: [    0.000000] ACPI: RSDT 7fee3040 00034 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: FACP 7fee30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: DSDT 7fee3180 04C6D (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: FACS 7fee0000 00040
May 19 18:58:01 dave kernel: [    0.000000] ACPI: HPET 7fee7f40 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: MCFG 7fee7fc0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: APIC 7fee7e40 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 19 18:58:01 dave kernel: [    0.000000] 1154MB HIGHMEM available.
May 19 18:58:01 dave kernel: [    0.000000] 891MB LOWMEM available.
May 19 18:58:01 dave kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
May 19 18:58:01 dave kernel: [    0.000000]   low ram: 0 - 37bfe000
May 19 18:58:01 dave kernel: [    0.000000] Zone PFN ranges:
May 19 18:58:01 dave kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May 19 18:58:01 dave kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
May 19 18:58:01 dave kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0007fee0
May 19 18:58:01 dave kernel: [    0.000000] Movable zone start PFN for each node
May 19 18:58:01 dave kernel: [    0.000000] early_node_map[2] active PFN ranges
May 19 18:58:01 dave kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
May 19 18:58:01 dave kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
May 19 18:58:01 dave kernel: [    0.000000] On node 0 totalpages: 523887
May 19 18:58:01 dave kernel: [    0.000000] free_area_init_node: node 0, pgdat c186b480, node_mem_map f5864200
May 19 18:58:01 dave kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 19 18:58:01 dave kernel: [    0.000000]   DMA zone: 0 pages reserved
May 19 18:58:01 dave kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
May 19 18:58:01 dave kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
May 19 18:58:01 dave kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
May 19 18:58:01 dave kernel: [    0.000000]   HighMem zone: 2310 pages used for memmap
May 19 18:58:01 dave kernel: [    0.000000]   HighMem zone: 293340 pages, LIFO batch:31
May 19 18:58:01 dave kernel: [    0.000000] Using APIC driver default
May 19 18:58:01 dave kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May 19 18:58:01 dave kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 19 18:58:01 dave kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May 19 18:58:01 dave kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
May 19 18:58:01 dave kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
May 19 18:58:01 dave kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
May 19 18:58:01 dave kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May 19 18:58:01 dave kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May 19 18:58:01 dave kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 19 18:58:01 dave kernel: [    0.000000] ACPI: IRQ0 used by override.
May 19 18:58:01 dave kernel: [    0.000000] ACPI: IRQ2 used by override.
May 19 18:58:01 dave kernel: [    0.000000] ACPI: IRQ9 used by override.
May 19 18:58:01 dave kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 19 18:58:01 dave kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
May 19 18:58:01 dave kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
May 19 18:58:01 dave kernel: [    0.000000] nr_irqs_gsi: 40
May 19 18:58:01 dave kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May 19 18:58:01 dave kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May 19 18:58:01 dave kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May 19 18:58:01 dave kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:70100000)
May 19 18:58:01 dave kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May 19 18:58:01 dave kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
May 19 18:58:01 dave kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f5600000 s34240 r0 d23104 u524288
May 19 18:58:01 dave kernel: [    0.000000] pcpu-alloc: s34240 r0 d23104 u524288 alloc=1*2097152
May 19 18:58:01 dave kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
May 19 18:58:01 dave kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
May 19 18:58:01 dave kernel: [    0.000000] Kernel command line: initrd=/ubninit file=/cdrom/preseed/custom.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
May 19 18:58:01 dave kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
May 19 18:58:01 dave kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 19 18:58:01 dave kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 19 18:58:01 dave kernel: [    0.000000] Initializing CPU#0
May 19 18:58:01 dave kernel: [    0.000000] allocated 8383744 bytes of page_cgroup
May 19 18:58:01 dave kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May 19 18:58:01 dave kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007fee0)
May 19 18:58:01 dave kernel: [    0.000000] Memory: 2039456k/2096000k available (5825k kernel code, 56092k reserved, 2850k data, 740k init, 1182600k highmem)
May 19 18:58:01 dave kernel: [    0.000000] virtual kernel memory layout:
May 19 18:58:01 dave kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
May 19 18:58:01 dave kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
May 19 18:58:01 dave kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
May 19 18:58:01 dave kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
May 19 18:58:01 dave kernel: [    0.000000]       .init : 0xc1879000 - 0xc1932000   ( 740 kB)
May 19 18:58:01 dave kernel: [    0.000000]       .data : 0xc15b04bc - 0xc1878d00   (2850 kB)
May 19 18:58:01 dave kernel: [    0.000000]       .text : 0xc1000000 - 0xc15b04bc   (5825 kB)
May 19 18:58:01 dave kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May 19 18:58:01 dave kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May 19 18:58:01 dave kernel: [    0.000000] Hierarchical RCU implementation.
May 19 18:58:01 dave kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
May 19 18:58:01 dave kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712 16
May 19 18:58:01 dave kernel: [    0.000000] CPU 0 irqstacks, hard=f480a000 soft=f480c000
May 19 18:58:01 dave kernel: [    0.000000] Console: colour VGA+ 80x25
May 19 18:58:01 dave kernel: [    0.000000] console [tty0] enabled
May 19 18:58:01 dave kernel: [    0.000000] hpet clockevent registered
May 19 18:58:01 dave kernel: [    0.000000] Fast TSC calibration using PIT
May 19 18:58:01 dave kernel: [    0.000000] Detected 2399.845 MHz processor.
May 19 18:58:01 dave kernel: [    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.69 BogoMIPS (lpj=9599380)
May 19 18:58:01 dave kernel: [    0.004009] pid_max: default: 32768 minimum: 301
May 19 18:58:01 dave kernel: [    0.004038] Security Framework initialized
May 19 18:58:01 dave kernel: [    0.004058] AppArmor: AppArmor initialized
May 19 18:58:01 dave kernel: [    0.004060] Yama: becoming mindful.
May 19 18:58:01 dave kernel: [    0.004130] Mount-cache hash table entries: 512
May 19 18:58:01 dave kernel: [    0.004296] Initializing cgroup subsys cpuacct
May 19 18:58:01 dave kernel: [    0.004304] Initializing cgroup subsys memory
May 19 18:58:01 dave kernel: [    0.004314] Initializing cgroup subsys devices
May 19 18:58:01 dave kernel: [    0.004318] Initializing cgroup subsys freezer
May 19 18:58:01 dave kernel: [    0.004321] Initializing cgroup subsys blkio
May 19 18:58:01 dave kernel: [    0.004329] Initializing cgroup subsys perf_event
May 19 18:58:01 dave kernel: [    0.004362] CPU: Physical Processor ID: 0
May 19 18:58:01 dave kernel: [    0.004365] CPU: Processor Core ID: 0
May 19 18:58:01 dave kernel: [    0.004369] mce: CPU supports 6 MCE banks
May 19 18:58:01 dave kernel: [    0.004379] CPU0: Thermal monitoring enabled (TM2)
May 19 18:58:01 dave kernel: [    0.004383] using mwait in idle threads.
May 19 18:58:01 dave kernel: [    0.007159] ACPI: Core revision 20110623
May 19 18:58:01 dave kernel: [    0.012031] ftrace: allocating 26594 entries in 53 pages
May 19 18:58:01 dave kernel: [    0.016050] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 19 18:58:01 dave kernel: [    0.016419] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May 19 18:58:01 dave kernel: [    0.059491] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
May 19 18:58:01 dave kernel: [    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
May 19 18:58:01 dave kernel: [    0.060003] PEBS disabled due to CPU errata.
May 19 18:58:01 dave kernel: [    0.060003] ... version:                2
May 19 18:58:01 dave kernel: [    0.060003] ... bit width:              40
May 19 18:58:01 dave kernel: [    0.060003] ... generic registers:      2
May 19 18:58:01 dave kernel: [    0.060003] ... value mask:             000000ffffffffff
May 19 18:58:01 dave kernel: [    0.060003] ... max period:             000000007fffffff
May 19 18:58:01 dave kernel: [    0.060003] ... fixed-purpose events:   3
May 19 18:58:01 dave kernel: [    0.060003] ... event mask:             0000000700000003
May 19 18:58:01 dave kernel: [    0.060003] NMI watchdog enabled, takes one hw-pmu counter.
May 19 18:58:01 dave kernel: [    0.060003] CPU 1 irqstacks, hard=f48f2000 soft=f48f4000
May 19 18:58:01 dave kernel: [    0.060003] Booting Node   0, Processors  #1
May 19 18:58:01 dave kernel: [    0.060003] smpboot cpu 1: start_ip = 9b000
May 19 18:58:01 dave kernel: [    0.008000] Initializing CPU#1
May 19 18:58:01 dave kernel: [    0.148031] NMI watchdog enabled, takes one hw-pmu counter.
May 19 18:58:01 dave kernel: [    0.148140] CPU 2 irqstacks, hard=f4920000 soft=f4922000
May 19 18:58:01 dave kernel: [    0.148143]  #2
May 19 18:58:01 dave kernel: [    0.148145] smpboot cpu 2: start_ip = 9b000
May 19 18:58:01 dave kernel: [    0.008000] Initializing CPU#2
May 19 18:58:01 dave kernel: [    0.240056] NMI watchdog enabled, takes one hw-pmu counter.
May 19 18:58:01 dave kernel: [    0.240192] CPU 3 irqstacks, hard=f492e000 soft=f4938000
May 19 18:58:01 dave kernel: [    0.240195]  #3 Ok.
May 19 18:58:01 dave kernel: [    0.240198] smpboot cpu 3: start_ip = 9b000
May 19 18:58:01 dave kernel: [    0.008000] Initializing CPU#3
May 19 18:58:01 dave kernel: [    0.332048] NMI watchdog enabled, takes one hw-pmu counter.
May 19 18:58:01 dave kernel: [    0.332091] Brought up 4 CPUs
May 19 18:58:01 dave kernel: [    0.332094] Total of 4 processors activated (19199.66 BogoMIPS).
May 19 18:58:01 dave kernel: [    0.336222] devtmpfs: initialized
May 19 18:58:01 dave kernel: [    0.336222] EVM: security.selinux
May 19 18:58:01 dave kernel: [    0.336222] EVM: security.SMACK64
May 19 18:58:01 dave kernel: [    0.336222] EVM: security.capability
May 19 18:58:01 dave kernel: [    0.336359] PM: Registering ACPI NVS region at 7fee0000 (12288 bytes)
May 19 18:58:01 dave kernel: [    0.337517] print_constraints: dummy: 
May 19 18:58:01 dave kernel: [    0.337550] RTC time: 15:57:45, date: 05/19/12
May 19 18:58:01 dave kernel: [    0.337602] NET: Registered protocol family 16
May 19 18:58:01 dave kernel: [    0.337634] Trying to unpack rootfs image as initramfs...
May 19 18:58:01 dave kernel: [    0.337771] EISA bus registered
May 19 18:58:01 dave kernel: [    0.337793] ACPI: bus type pci registered
May 19 18:58:01 dave kernel: [    0.337882] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
May 19 18:58:01 dave kernel: [    0.337887] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
May 19 18:58:01 dave kernel: [    0.337890] PCI: Using MMCONFIG for extended config space
May 19 18:58:01 dave kernel: [    0.337892] PCI: Using configuration type 1 for base access
May 19 18:58:01 dave kernel: [    0.341221] bio: create slab <bio-0> at 0
May 19 18:58:01 dave kernel: [    0.341221] ACPI: Added _OSI(Module Device)
May 19 18:58:01 dave kernel: [    0.341221] ACPI: Added _OSI(Processor Device)
May 19 18:58:01 dave kernel: [    0.341221] ACPI: Added _OSI(3.0 _SCP Extensions)
May 19 18:58:01 dave kernel: [    0.341221] ACPI: Added _OSI(Processor Aggregator Device)
May 19 18:58:01 dave kernel: [    0.341368] ACPI: EC: Look up EC in DSDT
May 19 18:58:01 dave kernel: [    0.348359] ACPI: Interpreter enabled
May 19 18:58:01 dave kernel: [    0.348384] ACPI: (supports S0 S3 S4 S5)
May 19 18:58:01 dave kernel: [    0.348413] ACPI: Using IOAPIC for interrupt routing
May 19 18:58:01 dave kernel: [    0.355370] ACPI: No dock devices found.
May 19 18:58:01 dave kernel: [    0.355374] HEST: Table not found.
May 19 18:58:01 dave kernel: [    0.355382] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
May 19 18:58:01 dave kernel: [    0.355459] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
May 19 18:58:01 dave kernel: [    0.355631] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
May 19 18:58:01 dave kernel: [    0.355636] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
May 19 18:58:01 dave kernel: [    0.355640] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
May 19 18:58:01 dave kernel: [    0.355644] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
May 19 18:58:01 dave kernel: [    0.355648] pci_root PNP0A03:00: host bridge window [mem 0x7ff00000-0xfebfffff] (ignored)
May 19 18:58:01 dave kernel: [    0.355663] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
May 19 18:58:01 dave kernel: [    0.355723] pci 0000:00:01.0: [8086:29c1] type 1 class 0x000604
May 19 18:58:01 dave kernel: [    0.355779] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
May 19 18:58:01 dave kernel: [    0.355784] pci 0000:00:01.0: PME# disabled
May 19 18:58:01 dave kernel: [    0.355831] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
May 19 18:58:01 dave kernel: [    0.355881] pci 0000:00:1a.0: reg 20: [io  0xe000-0xe01f]
May 19 18:58:01 dave kernel: [    0.355941] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
May 19 18:58:01 dave kernel: [    0.355990] pci 0000:00:1a.1: reg 20: [io  0xe100-0xe11f]
May 19 18:58:01 dave kernel: [    0.356063] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
May 19 18:58:01 dave kernel: [    0.356112] pci 0000:00:1a.2: reg 20: [io  0xe500-0xe51f]
May 19 18:58:01 dave kernel: [    0.356178] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
May 19 18:58:01 dave kernel: [    0.356197] pci 0000:00:1a.7: reg 10: [mem 0xf9004000-0xf90043ff]
May 19 18:58:01 dave kernel: [    0.356300] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
May 19 18:58:01 dave kernel: [    0.356319] pci 0000:00:1b.0: reg 10: [mem 0xf9000000-0xf9003fff 64bit]
May 19 18:58:01 dave kernel: [    0.356398] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May 19 18:58:01 dave kernel: [    0.356403] pci 0000:00:1b.0: PME# disabled
May 19 18:58:01 dave kernel: [    0.356427] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
May 19 18:58:01 dave kernel: [    0.356509] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
May 19 18:58:01 dave kernel: [    0.356514] pci 0000:00:1c.0: PME# disabled
May 19 18:58:01 dave kernel: [    0.356543] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
May 19 18:58:01 dave kernel: [    0.356625] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
May 19 18:58:01 dave kernel: [    0.356630] pci 0000:00:1c.4: PME# disabled
May 19 18:58:01 dave kernel: [    0.356656] pci 0000:00:1c.5: [8086:294a] type 1 class 0x000604
May 19 18:58:01 dave kernel: [    0.356737] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
May 19 18:58:01 dave kernel: [    0.356742] pci 0000:00:1c.5: PME# disabled
May 19 18:58:01 dave kernel: [    0.356770] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
May 19 18:58:01 dave kernel: [    0.356819] pci 0000:00:1d.0: reg 20: [io  0xe200-0xe21f]
May 19 18:58:01 dave kernel: [    0.356879] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
May 19 18:58:01 dave kernel: [    0.356928] pci 0000:00:1d.1: reg 20: [io  0xe300-0xe31f]
May 19 18:58:01 dave kernel: [    0.356989] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
May 19 18:58:01 dave kernel: [    0.357038] pci 0000:00:1d.2: reg 20: [io  0xe400-0xe41f]
May 19 18:58:01 dave kernel: [    0.357104] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
May 19 18:58:01 dave kernel: [    0.357124] pci 0000:00:1d.7: reg 10: [mem 0xf9005000-0xf90053ff]
May 19 18:58:01 dave kernel: [    0.357222] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
May 19 18:58:01 dave kernel: [    0.357295] pci 0000:00:1f.0: [8086:2918] type 0 class 0x000601
May 19 18:58:01 dave kernel: [    0.357385] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
May 19 18:58:01 dave kernel: [    0.357391] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
May 19 18:58:01 dave kernel: [    0.357445] pci 0000:00:1f.2: [8086:2921] type 0 class 0x000101
May 19 18:58:01 dave kernel: [    0.357463] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
May 19 18:58:01 dave kernel: [    0.357473] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
May 19 18:58:01 dave kernel: [    0.357483] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
May 19 18:58:01 dave kernel: [    0.357493] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
May 19 18:58:01 dave kernel: [    0.357504] pci 0000:00:1f.2: reg 20: [io  0xf000-0xf00f]
May 19 18:58:01 dave kernel: [    0.357514] pci 0000:00:1f.2: reg 24: [io  0xfc00-0xfc0f]
May 19 18:58:01 dave kernel: [    0.357569] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
May 19 18:58:01 dave kernel: [    0.357587] pci 0000:00:1f.3: reg 10: [mem 0xf9006000-0xf90060ff 64bit]
May 19 18:58:01 dave kernel: [    0.357612] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
May 19 18:58:01 dave kernel: [    0.357652] pci 0000:00:1f.5: [8086:2926] type 0 class 0x000101
May 19 18:58:01 dave kernel: [    0.357671] pci 0000:00:1f.5: reg 10: [io  0xe700-0xe707]
May 19 18:58:01 dave kernel: [    0.357681] pci 0000:00:1f.5: reg 14: [io  0xe800-0xe803]
May 19 18:58:01 dave kernel: [    0.357691] pci 0000:00:1f.5: reg 18: [io  0xe900-0xe907]
May 19 18:58:01 dave kernel: [    0.357701] pci 0000:00:1f.5: reg 1c: [io  0xea00-0xea03]
May 19 18:58:01 dave kernel: [    0.357711] pci 0000:00:1f.5: reg 20: [io  0xeb00-0xeb0f]
May 19 18:58:01 dave kernel: [    0.357721] pci 0000:00:1f.5: reg 24: [io  0xec00-0xec0f]
May 19 18:58:01 dave kernel: [    0.357818] pci 0000:01:00.0: [1002:9505] type 0 class 0x000300
May 19 18:58:01 dave kernel: [    0.357836] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xefffffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.357850] pci 0000:01:00.0: reg 18: [mem 0xf5000000-0xf500ffff 64bit]
May 19 18:58:01 dave kernel: [    0.357860] pci 0000:01:00.0: reg 20: [io  0xa000-0xa0ff]
May 19 18:58:01 dave kernel: [    0.357876] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
May 19 18:58:01 dave kernel: [    0.357916] pci 0000:01:00.0: supports D1 D2
May 19 18:58:01 dave kernel: [    0.357940] pci 0000:01:00.1: [1002:aa18] type 0 class 0x000403
May 19 18:58:01 dave kernel: [    0.357957] pci 0000:01:00.1: reg 10: [mem 0xf5010000-0xf5013fff 64bit]
May 19 18:58:01 dave kernel: [    0.358030] pci 0000:01:00.1: supports D1 D2
May 19 18:58:01 dave kernel: [    0.358067] pci 0000:00:01.0: PCI bridge to [bus 01-01]
May 19 18:58:01 dave kernel: [    0.358072] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
May 19 18:58:01 dave kernel: [    0.358077] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf5ffffff]
May 19 18:58:01 dave kernel: [    0.358083] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.358130] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
May 19 18:58:01 dave kernel: [    0.358135] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
May 19 18:58:01 dave kernel: [    0.358208] pci 0000:03:00.0: [197b:2368] type 0 class 0x000101
May 19 18:58:01 dave kernel: [    0.358242] pci 0000:03:00.0: reg 10: [io  0xb000-0xb007]
May 19 18:58:01 dave kernel: [    0.358258] pci 0000:03:00.0: reg 14: [io  0xb100-0xb103]
May 19 18:58:01 dave kernel: [    0.358274] pci 0000:03:00.0: reg 18: [io  0xb200-0xb207]
May 19 18:58:01 dave kernel: [    0.358290] pci 0000:03:00.0: reg 1c: [io  0xb300-0xb303]
May 19 18:58:01 dave kernel: [    0.358306] pci 0000:03:00.0: reg 20: [io  0xb400-0xb40f]
May 19 18:58:01 dave kernel: [    0.358409] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
May 19 18:58:01 dave kernel: [    0.358422] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
May 19 18:58:01 dave kernel: [    0.358427] pci 0000:00:1c.4:   bridge window [io  0xb000-0xbfff]
May 19 18:58:01 dave kernel: [    0.358433] pci 0000:00:1c.4:   bridge window [mem 0xf6000000-0xf6ffffff]
May 19 18:58:01 dave kernel: [    0.358509] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
May 19 18:58:01 dave kernel: [    0.358530] pci 0000:04:00.0: reg 10: [io  0xc000-0xc0ff]
May 19 18:58:01 dave kernel: [    0.358565] pci 0000:04:00.0: reg 18: [mem 0xf8000000-0xf8000fff 64bit]
May 19 18:58:01 dave kernel: [    0.358606] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
May 19 18:58:01 dave kernel: [    0.358696] pci 0000:04:00.0: supports D1 D2
May 19 18:58:01 dave kernel: [    0.358699] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
May 19 18:58:01 dave kernel: [    0.358706] pci 0000:04:00.0: PME# disabled
May 19 18:58:01 dave kernel: [    0.358732] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
May 19 18:58:01 dave kernel: [    0.358744] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
May 19 18:58:01 dave kernel: [    0.358749] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
May 19 18:58:01 dave kernel: [    0.358755] pci 0000:00:1c.5:   bridge window [mem 0xf7000000-0xf8ffffff]
May 19 18:58:01 dave kernel: [    0.358797] pci 0000:05:01.0: [1102:0007] type 0 class 0x000401
May 19 18:58:01 dave kernel: [    0.358817] pci 0000:05:01.0: reg 10: [io  0xd000-0xd01f]
May 19 18:58:01 dave kernel: [    0.358901] pci 0000:05:01.0: supports D1 D2
May 19 18:58:01 dave kernel: [    0.358952] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
May 19 18:58:01 dave kernel: [    0.358958] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
May 19 18:58:01 dave kernel: [    0.358968] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
May 19 18:58:01 dave kernel: [    0.358972] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
May 19 18:58:01 dave kernel: [    0.358997] pci_bus 0000:00: on NUMA node 0
May 19 18:58:01 dave kernel: [    0.359002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 19 18:58:01 dave kernel: [    0.359238] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
May 19 18:58:01 dave kernel: [    0.359310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
May 19 18:58:01 dave kernel: [    0.359385] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
May 19 18:58:01 dave kernel: [    0.359446] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May 19 18:58:01 dave kernel: [    0.359713]  pci0000:00: Requesting ACPI _OSC control (0x1d)
May 19 18:58:01 dave kernel: [    0.359717]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
May 19 18:58:01 dave kernel: [    0.359720] ACPI _OSC control for PCIe not granted, disabling ASPM
May 19 18:58:01 dave kernel: [    0.375346] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
May 19 18:58:01 dave kernel: [    0.375418] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
May 19 18:58:01 dave kernel: [    0.375487] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 19 18:58:01 dave kernel: [    0.375555] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May 19 18:58:01 dave kernel: [    0.375623] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
May 19 18:58:01 dave kernel: [    0.375692] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
May 19 18:58:01 dave kernel: [    0.375759] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May 19 18:58:01 dave kernel: [    0.375827] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
May 19 18:58:01 dave kernel: [    0.375971] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
May 19 18:58:01 dave kernel: [    0.376030] vgaarb: loaded
May 19 18:58:01 dave kernel: [    0.376033] vgaarb: bridge control possible 0000:01:00.0
May 19 18:58:01 dave kernel: [    0.376205] i2c-core: driver [aat2870] using legacy suspend method
May 19 18:58:01 dave kernel: [    0.376208] i2c-core: driver [aat2870] using legacy resume method
May 19 18:58:01 dave kernel: [    0.376319] SCSI subsystem initialized
May 19 18:58:01 dave kernel: [    0.376360] libata version 3.00 loaded.
May 19 18:58:01 dave kernel: [    0.376360] usbcore: registered new interface driver usbfs
May 19 18:58:01 dave kernel: [    0.376360] usbcore: registered new interface driver hub
May 19 18:58:01 dave kernel: [    0.376360] usbcore: registered new device driver usb
May 19 18:58:01 dave kernel: [    0.376360] PCI: Using ACPI for IRQ routing
May 19 18:58:01 dave kernel: [    0.377648] PCI: pci_cache_line_size set to 64 bytes
May 19 18:58:01 dave kernel: [    0.377766] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
May 19 18:58:01 dave kernel: [    0.377770] reserve RAM buffer: 000000007fee0000 - 000000007fffffff 
May 19 18:58:01 dave kernel: [    0.377909] NetLabel: Initializing
May 19 18:58:01 dave kernel: [    0.377911] NetLabel:  domain hash size = 128
May 19 18:58:01 dave kernel: [    0.377914] NetLabel:  protocols = UNLABELED CIPSOv4
May 19 18:58:01 dave kernel: [    0.377928] NetLabel:  unlabeled traffic allowed by default
May 19 18:58:01 dave kernel: [    0.377959] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
May 19 18:58:01 dave kernel: [    0.377959] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
May 19 18:58:01 dave kernel: [    0.377959] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
May 19 18:58:01 dave kernel: [    0.392355] Switching to clocksource hpet
May 19 18:58:01 dave kernel: [    0.403479] AppArmor: AppArmor Filesystem Enabled
May 19 18:58:01 dave kernel: [    0.403514] pnp: PnP ACPI init
May 19 18:58:01 dave kernel: [    0.403537] ACPI: bus type pnp registered
May 19 18:58:01 dave kernel: [    0.403655] pnp 00:00: [bus 00-3f]
May 19 18:58:01 dave kernel: [    0.403660] pnp 00:00: [io  0x0cf8-0x0cff]
May 19 18:58:01 dave kernel: [    0.403663] pnp 00:00: [io  0x0000-0x0cf7 window]
May 19 18:58:01 dave kernel: [    0.403667] pnp 00:00: [io  0x0d00-0xffff window]
May 19 18:58:01 dave kernel: [    0.403670] pnp 00:00: [mem 0x000a0000-0x000bffff window]
May 19 18:58:01 dave kernel: [    0.403674] pnp 00:00: [mem 0x000c0000-0x000dffff window]
May 19 18:58:01 dave kernel: [    0.403677] pnp 00:00: [mem 0x7ff00000-0xfebfffff window]
May 19 18:58:01 dave kernel: [    0.403769] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
May 19 18:58:01 dave kernel: [    0.403889] pnp 00:01: [io  0x0010-0x001f]
May 19 18:58:01 dave kernel: [    0.403893] pnp 00:01: [io  0x0022-0x003f]
May 19 18:58:01 dave kernel: [    0.403896] pnp 00:01: [io  0x0044-0x005f]
May 19 18:58:01 dave kernel: [    0.403898] pnp 00:01: [io  0x0062-0x0063]
May 19 18:58:01 dave kernel: [    0.403901] pnp 00:01: [io  0x0065-0x006f]
May 19 18:58:01 dave kernel: [    0.403904] pnp 00:01: [io  0x0074-0x007f]
May 19 18:58:01 dave kernel: [    0.403907] pnp 00:01: [io  0x0091-0x0093]
May 19 18:58:01 dave kernel: [    0.403910] pnp 00:01: [io  0x00a2-0x00bf]
May 19 18:58:01 dave kernel: [    0.403912] pnp 00:01: [io  0x00e0-0x00ef]
May 19 18:58:01 dave kernel: [    0.403915] pnp 00:01: [io  0x04d0-0x04d1]
May 19 18:58:01 dave kernel: [    0.403918] pnp 00:01: [io  0x0290-0x029f]
May 19 18:58:01 dave kernel: [    0.403921] pnp 00:01: [io  0x0800-0x087f]
May 19 18:58:01 dave kernel: [    0.403924] pnp 00:01: [io  0x0290-0x0294]
May 19 18:58:01 dave kernel: [    0.403927] pnp 00:01: [io  0x0880-0x088f]
May 19 18:58:01 dave kernel: [    0.404056] system 00:01: [io  0x04d0-0x04d1] has been reserved
May 19 18:58:01 dave kernel: [    0.404060] system 00:01: [io  0x0290-0x029f] has been reserved
May 19 18:58:01 dave kernel: [    0.404064] system 00:01: [io  0x0800-0x087f] has been reserved
May 19 18:58:01 dave kernel: [    0.404068] system 00:01: [io  0x0290-0x0294] has been reserved
May 19 18:58:01 dave kernel: [    0.404072] system 00:01: [io  0x0880-0x088f] has been reserved
May 19 18:58:01 dave kernel: [    0.404077] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
May 19 18:58:01 dave kernel: [    0.404095] pnp 00:02: [dma 4]
May 19 18:58:01 dave kernel: [    0.404099] pnp 00:02: [io  0x0000-0x000f]
May 19 18:58:01 dave kernel: [    0.404102] pnp 00:02: [io  0x0080-0x0090]
May 19 18:58:01 dave kernel: [    0.404104] pnp 00:02: [io  0x0094-0x009f]
May 19 18:58:01 dave kernel: [    0.404107] pnp 00:02: [io  0x00c0-0x00df]
May 19 18:58:01 dave kernel: [    0.404155] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
May 19 18:58:01 dave kernel: [    0.404225] pnp 00:03: [irq 0 disabled]
May 19 18:58:01 dave kernel: [    0.404239] pnp 00:03: [irq 8]
May 19 18:58:01 dave kernel: [    0.404243] pnp 00:03: [mem 0xfed00000-0xfed003ff]
May 19 18:58:01 dave kernel: [    0.404296] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
May 19 18:58:01 dave kernel: [    0.404333] pnp 00:04: [io  0x0070-0x0073]
May 19 18:58:01 dave kernel: [    0.404383] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
May 19 18:58:01 dave kernel: [    0.404397] pnp 00:05: [io  0x0061]
May 19 18:58:01 dave kernel: [    0.404445] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
May 19 18:58:01 dave kernel: [    0.404459] pnp 00:06: [io  0x00f0-0x00ff]
May 19 18:58:01 dave kernel: [    0.404466] pnp 00:06: [irq 13]
May 19 18:58:01 dave kernel: [    0.404517] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
May 19 18:58:01 dave kernel: [    0.404810] pnp 00:07: [io  0x03f8-0x03ff]
May 19 18:58:01 dave kernel: [    0.404818] pnp 00:07: [irq 4]
May 19 18:58:01 dave kernel: [    0.404915] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
May 19 18:58:01 dave kernel: [    0.405150] pnp 00:08: [io  0x0378-0x037f]
May 19 18:58:01 dave kernel: [    0.405158] pnp 00:08: [irq 7]
May 19 18:58:01 dave kernel: [    0.405241] pnp 00:08: Plug and Play ACPI device, IDs PNP0400 (active)
May 19 18:58:01 dave kernel: [    0.405360] pnp 00:09: [io  0x0060]
May 19 18:58:01 dave kernel: [    0.405364] pnp 00:09: [io  0x0064]
May 19 18:58:01 dave kernel: [    0.405370] pnp 00:09: [irq 1]
May 19 18:58:01 dave kernel: [    0.405427] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
May 19 18:58:01 dave kernel: [    0.405472] pnp 00:0a: [io  0x0400-0x04bf]
May 19 18:58:01 dave kernel: [    0.405556] system 00:0a: [io  0x0400-0x04bf] has been reserved
May 19 18:58:01 dave kernel: [    0.405561] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
May 19 18:58:01 dave kernel: [    0.405839] pnp 00:0b: [mem 0xf0000000-0xf3ffffff]
May 19 18:58:01 dave kernel: [    0.405938] system 00:0b: [mem 0xf0000000-0xf3ffffff] has been reserved
May 19 18:58:01 dave kernel: [    0.405944] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
May 19 18:58:01 dave kernel: [    0.406162] pnp 00:0c: [mem 0x000cf400-0x000cffff]
May 19 18:58:01 dave kernel: [    0.406166] pnp 00:0c: [mem 0x000f0000-0x000f7fff]
May 19 18:58:01 dave kernel: [    0.406169] pnp 00:0c: [mem 0x000f8000-0x000fbfff]
May 19 18:58:01 dave kernel: [    0.406172] pnp 00:0c: [mem 0x000fc000-0x000fffff]
May 19 18:58:01 dave kernel: [    0.406175] pnp 00:0c: [mem 0x7fee0000-0x7fefffff]
May 19 18:58:01 dave kernel: [    0.406178] pnp 00:0c: [mem 0x00000000-0x0009ffff]
May 19 18:58:01 dave kernel: [    0.406182] pnp 00:0c: [mem 0x00100000-0x7fedffff]
May 19 18:58:01 dave kernel: [    0.406185] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
May 19 18:58:01 dave kernel: [    0.406188] pnp 00:0c: [mem 0xfed10000-0xfed1dfff]
May 19 18:58:01 dave kernel: [    0.406191] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
May 19 18:58:01 dave kernel: [    0.406194] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
May 19 18:58:01 dave kernel: [    0.406197] pnp 00:0c: [mem 0xffb00000-0xffb7ffff]
May 19 18:58:01 dave kernel: [    0.406200] pnp 00:0c: [mem 0xfff00000-0xffffffff]
May 19 18:58:01 dave kernel: [    0.406203] pnp 00:0c: [mem 0x000e0000-0x000effff]
May 19 18:58:01 dave kernel: [    0.406313] system 00:0c: [mem 0x000cf400-0x000cffff] has been reserved
May 19 18:58:01 dave kernel: [    0.406318] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
May 19 18:58:01 dave kernel: [    0.406322] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
May 19 18:58:01 dave kernel: [    0.406326] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
May 19 18:58:01 dave kernel: [    0.406330] system 00:0c: [mem 0x7fee0000-0x7fefffff] could not be reserved
May 19 18:58:01 dave kernel: [    0.406334] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
May 19 18:58:01 dave kernel: [    0.406339] system 00:0c: [mem 0x00100000-0x7fedffff] could not be reserved
May 19 18:58:01 dave kernel: [    0.406343] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
May 19 18:58:01 dave kernel: [    0.406347] system 00:0c: [mem 0xfed10000-0xfed1dfff] has been reserved
May 19 18:58:01 dave kernel: [    0.406351] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
May 19 18:58:01 dave kernel: [    0.406355] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
May 19 18:58:01 dave kernel: [    0.406360] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
May 19 18:58:01 dave kernel: [    0.406364] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
May 19 18:58:01 dave kernel: [    0.406368] system 00:0c: [mem 0x000e0000-0x000effff] has been reserved
May 19 18:58:01 dave kernel: [    0.406373] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
May 19 18:58:01 dave kernel: [    0.406401] pnp 00:0d: [mem 0xffb80000-0xffbfffff]
May 19 18:58:01 dave kernel: [    0.406475] pnp 00:0d: Plug and Play ACPI device, IDs INT0800 (active)
May 19 18:58:01 dave kernel: [    0.406484] pnp: PnP ACPI: found 14 devices
May 19 18:58:01 dave kernel: [    0.406487] ACPI: ACPI bus type pnp unregistered
May 19 18:58:01 dave kernel: [    0.406493] PnPBIOS: Disabled by ACPI PNP
May 19 18:58:01 dave kernel: [    0.444695] PCI: max bus depth: 1 pci_try_num: 2
May 19 18:58:01 dave kernel: [    0.444753] pci 0000:00:1c.5: BAR 15: assigned [mem 0x80000000-0x800fffff pref]
May 19 18:58:01 dave kernel: [    0.444760] pci 0000:00:1c.5: BAR 15: assigned [mem 0x80000000-0x802fffff pref]
May 19 18:58:01 dave kernel: [    0.444765] pci 0000:00:1c.4: BAR 15: assigned [mem 0x80300000-0x804fffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.444770] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80500000-0x806fffff]
May 19 18:58:01 dave kernel: [    0.444774] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80700000-0x808fffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.444780] pci 0000:01:00.0: BAR 6: assigned [mem 0xf4000000-0xf401ffff pref]
May 19 18:58:01 dave kernel: [    0.444785] pci 0000:00:01.0: PCI bridge to [bus 01-01]
May 19 18:58:01 dave kernel: [    0.444789] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
May 19 18:58:01 dave kernel: [    0.444794] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf5ffffff]
May 19 18:58:01 dave kernel: [    0.444799] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.444806] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
May 19 18:58:01 dave kernel: [    0.444810] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
May 19 18:58:01 dave kernel: [    0.444816] pci 0000:00:1c.0:   bridge window [mem 0x80500000-0x806fffff]
May 19 18:58:01 dave kernel: [    0.444821] pci 0000:00:1c.0:   bridge window [mem 0x80700000-0x808fffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.444829] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
May 19 18:58:01 dave kernel: [    0.444834] pci 0000:00:1c.4:   bridge window [io  0xb000-0xbfff]
May 19 18:58:01 dave kernel: [    0.444840] pci 0000:00:1c.4:   bridge window [mem 0xf6000000-0xf6ffffff]
May 19 18:58:01 dave kernel: [    0.444845] pci 0000:00:1c.4:   bridge window [mem 0x80300000-0x804fffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.444854] pci 0000:04:00.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
May 19 18:58:01 dave kernel: [    0.444858] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
May 19 18:58:01 dave kernel: [    0.444862] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
May 19 18:58:01 dave kernel: [    0.444868] pci 0000:00:1c.5:   bridge window [mem 0xf7000000-0xf8ffffff]
May 19 18:58:01 dave kernel: [    0.444873] pci 0000:00:1c.5:   bridge window [mem 0x80000000-0x802fffff pref]
May 19 18:58:01 dave kernel: [    0.444881] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
May 19 18:58:01 dave kernel: [    0.444885] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
May 19 18:58:01 dave kernel: [    0.444916] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 19 18:58:01 dave kernel: [    0.444922] pci 0000:00:01.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.444932] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 19 18:58:01 dave kernel: [    0.444937] pci 0000:00:1c.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.444945] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 19 18:58:01 dave kernel: [    0.444950] pci 0000:00:1c.4: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.444963] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May 19 18:58:01 dave kernel: [    0.444968] pci 0000:00:1c.5: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.444977] pci 0000:00:1e.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.444982] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
May 19 18:58:01 dave kernel: [    0.444986] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
May 19 18:58:01 dave kernel: [    0.444989] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
May 19 18:58:01 dave kernel: [    0.444993] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf5ffffff]
May 19 18:58:01 dave kernel: [    0.444997] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.445001] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
May 19 18:58:01 dave kernel: [    0.445004] pci_bus 0000:02: resource 1 [mem 0x80500000-0x806fffff]
May 19 18:58:01 dave kernel: [    0.445008] pci_bus 0000:02: resource 2 [mem 0x80700000-0x808fffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.445011] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
May 19 18:58:01 dave kernel: [    0.445015] pci_bus 0000:03: resource 1 [mem 0xf6000000-0xf6ffffff]
May 19 18:58:01 dave kernel: [    0.445018] pci_bus 0000:03: resource 2 [mem 0x80300000-0x804fffff 64bit pref]
May 19 18:58:01 dave kernel: [    0.445022] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
May 19 18:58:01 dave kernel: [    0.445025] pci_bus 0000:04: resource 1 [mem 0xf7000000-0xf8ffffff]
May 19 18:58:01 dave kernel: [    0.445029] pci_bus 0000:04: resource 2 [mem 0x80000000-0x802fffff pref]
May 19 18:58:01 dave kernel: [    0.445033] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
May 19 18:58:01 dave kernel: [    0.445036] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]
May 19 18:58:01 dave kernel: [    0.445040] pci_bus 0000:05: resource 5 [mem 0x00000000-0xfffffffff]
May 19 18:58:01 dave kernel: [    0.445094] NET: Registered protocol family 2
May 19 18:58:01 dave kernel: [    0.445193] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May 19 18:58:01 dave kernel: [    0.445496] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 19 18:58:01 dave kernel: [    0.445944] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May 19 18:58:01 dave kernel: [    0.446157] TCP: Hash tables configured (established 131072 bind 65536)
May 19 18:58:01 dave kernel: [    0.446160] TCP reno registered
May 19 18:58:01 dave kernel: [    0.446163] UDP hash table entries: 512 (order: 2, 16384 bytes)
May 19 18:58:01 dave kernel: [    0.446174] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
May 19 18:58:01 dave kernel: [    0.446263] NET: Registered protocol family 1
May 19 18:58:01 dave kernel: [    0.446292] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 19 18:58:01 dave kernel: [    0.446311] pci 0000:00:1a.0: PCI INT A disabled
May 19 18:58:01 dave kernel: [    0.446328] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May 19 18:58:01 dave kernel: [    0.446345] pci 0000:00:1a.1: PCI INT B disabled
May 19 18:58:01 dave kernel: [    0.446360] pci 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 19 18:58:01 dave kernel: [    0.446378] pci 0000:00:1a.2: PCI INT C disabled
May 19 18:58:01 dave kernel: [    0.446389] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 19 18:58:01 dave kernel: [    0.446417] pci 0000:00:1a.7: PCI INT C disabled
May 19 18:58:01 dave kernel: [    0.446442] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 19 18:58:01 dave kernel: [    0.446459] pci 0000:00:1d.0: PCI INT A disabled
May 19 18:58:01 dave kernel: [    0.446472] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 19 18:58:01 dave kernel: [    0.446490] pci 0000:00:1d.1: PCI INT B disabled
May 19 18:58:01 dave kernel: [    0.446499] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 19 18:58:01 dave kernel: [    0.446516] pci 0000:00:1d.2: PCI INT C disabled
May 19 18:58:01 dave kernel: [    0.446526] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 19 18:58:01 dave kernel: [    0.446543] pci 0000:00:1d.7: PCI INT A disabled
May 19 18:58:01 dave kernel: [    0.446564] pci 0000:01:00.0: Boot video device
May 19 18:58:01 dave kernel: [    0.446580] PCI: CLS 32 bytes, default 64
May 19 18:58:01 dave kernel: [    0.447197] audit: initializing netlink socket (disabled)
May 19 18:58:01 dave kernel: [    0.447208] type=2000 audit(1337443065.440:1): initialized
May 19 18:58:01 dave kernel: [    0.482360] highmem bounce pool size: 64 pages
May 19 18:58:01 dave kernel: [    0.482368] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May 19 18:58:01 dave kernel: [    0.491449] VFS: Disk quotas dquot_6.5.2
May 19 18:58:01 dave kernel: [    0.491545] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 19 18:58:01 dave kernel: [    0.492380] fuse init (API version 7.17)
May 19 18:58:01 dave kernel: [    0.492522] msgmni has been set to 1673
May 19 18:58:01 dave kernel: [    0.493028] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May 19 18:58:01 dave kernel: [    0.493068] io scheduler noop registered
May 19 18:58:01 dave kernel: [    0.493071] io scheduler deadline registered
May 19 18:58:01 dave kernel: [    0.493081] io scheduler cfq registered (default)
May 19 18:58:01 dave kernel: [    0.493245] pcieport 0000:00:01.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.493285] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
May 19 18:58:01 dave kernel: [    0.493351] pcieport 0000:00:1c.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.493395] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
May 19 18:58:01 dave kernel: [    0.493467] pcieport 0000:00:1c.4: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.493510] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
May 19 18:58:01 dave kernel: [    0.493582] pcieport 0000:00:1c.5: setting latency timer to 64
May 19 18:58:01 dave kernel: [    0.493626] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
May 19 18:58:01 dave kernel: [    0.493737] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 19 18:58:01 dave kernel: [    0.493772] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 19 18:58:01 dave kernel: [    0.493908] intel_idle: MWAIT substates: 0x20
May 19 18:58:01 dave kernel: [    0.493911] intel_idle: does not run on family 6 model 15
May 19 18:58:01 dave kernel: [    0.494017] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
May 19 18:58:01 dave kernel: [    0.494024] ACPI: Power Button [PWRB]
May 19 18:58:01 dave kernel: [    0.494103] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May 19 18:58:01 dave kernel: [    0.494108] ACPI: Power Button [PWRF]
May 19 18:58:01 dave kernel: [    0.506279] ERST: Table is not found!
May 19 18:58:01 dave kernel: [    0.506283] GHES: HEST is not enabled!
May 19 18:58:01 dave kernel: [    0.506373] isapnp: Scanning for PnP cards...
May 19 18:58:01 dave kernel: [    0.506412] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May 19 18:58:01 dave kernel: [    0.526785] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 19 18:58:01 dave kernel: [    0.859489] isapnp: No Plug & Play device found
May 19 18:58:01 dave kernel: [    0.938182] Freeing initrd memory: 20068k freed
May 19 18:58:01 dave kernel: [    1.072580] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 19 18:58:01 dave kernel: [    1.108439] Linux agpgart interface v0.103
May 19 18:58:01 dave kernel: [    1.111040] brd: module loaded
May 19 18:58:01 dave kernel: [    1.112245] loop: module loaded
May 19 18:58:01 dave kernel: [    1.112491] ata_piix 0000:00:1f.2: version 2.13
May 19 18:58:01 dave kernel: [    1.112509] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 19 18:58:01 dave kernel: [    1.112516] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
May 19 18:58:01 dave kernel: [    1.112569] ata_piix 0000:00:1f.2: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.112926] scsi0 : ata_piix
May 19 18:58:01 dave kernel: [    1.113039] scsi1 : ata_piix
May 19 18:58:01 dave kernel: [    1.113718] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May 19 18:58:01 dave kernel: [    1.113723] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May 19 18:58:01 dave kernel: [    1.113749] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 19 18:58:01 dave kernel: [    1.113755] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
May 19 18:58:01 dave kernel: [    1.113804] ata_piix 0000:00:1f.5: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.114138] scsi2 : ata_piix
May 19 18:58:01 dave kernel: [    1.114242] scsi3 : ata_piix
May 19 18:58:01 dave kernel: [    1.114789] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
May 19 18:58:01 dave kernel: [    1.114794] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
May 19 18:58:01 dave kernel: [    1.114867] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 19 18:58:01 dave kernel: [    1.114905] pata_acpi 0000:03:00.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.114924] pata_acpi 0000:03:00.0: PCI INT A disabled
May 19 18:58:01 dave kernel: [    1.115421] Fixed MDIO Bus: probed
May 19 18:58:01 dave kernel: [    1.115451] tun: Universal TUN/TAP device driver, 1.6
May 19 18:58:01 dave kernel: [    1.115455] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May 19 18:58:01 dave kernel: [    1.115527] PPP generic driver version 2.4.2
May 19 18:58:01 dave kernel: [    1.115676] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May 19 18:58:01 dave kernel: [    1.115696] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 19 18:58:01 dave kernel: [    1.115711] ehci_hcd 0000:00:1a.7: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.115716] ehci_hcd 0000:00:1a.7: EHCI Host Controller
May 19 18:58:01 dave kernel: [    1.115782] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
May 19 18:58:01 dave kernel: [    1.119701] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
May 19 18:58:01 dave kernel: [    1.119720] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9004000
May 19 18:58:01 dave kernel: [    1.132018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
May 19 18:58:01 dave kernel: [    1.132213] hub 1-0:1.0: USB hub found
May 19 18:58:01 dave kernel: [    1.132219] hub 1-0:1.0: 6 ports detected
May 19 18:58:01 dave kernel: [    1.132325] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 19 18:58:01 dave kernel: [    1.132339] ehci_hcd 0000:00:1d.7: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.132344] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May 19 18:58:01 dave kernel: [    1.132412] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
May 19 18:58:01 dave kernel: [    1.136308] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
May 19 18:58:01 dave kernel: [    1.136326] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9005000
May 19 18:58:01 dave kernel: [    1.152017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
May 19 18:58:01 dave kernel: [    1.152185] hub 2-0:1.0: USB hub found
May 19 18:58:01 dave kernel: [    1.152191] hub 2-0:1.0: 6 ports detected
May 19 18:58:01 dave kernel: [    1.152301] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May 19 18:58:01 dave kernel: [    1.152322] uhci_hcd: USB Universal Host Controller Interface driver
May 19 18:58:01 dave kernel: [    1.152343] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 19 18:58:01 dave kernel: [    1.152354] uhci_hcd 0000:00:1a.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.152358] uhci_hcd 0000:00:1a.0: UHCI Host Controller
May 19 18:58:01 dave kernel: [    1.152423] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
May 19 18:58:01 dave kernel: [    1.152459] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
May 19 18:58:01 dave kernel: [    1.152640] hub 3-0:1.0: USB hub found
May 19 18:58:01 dave kernel: [    1.152646] hub 3-0:1.0: 2 ports detected
May 19 18:58:01 dave kernel: [    1.152742] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May 19 18:58:01 dave kernel: [    1.152751] uhci_hcd 0000:00:1a.1: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.152755] uhci_hcd 0000:00:1a.1: UHCI Host Controller
May 19 18:58:01 dave kernel: [    1.152826] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
May 19 18:58:01 dave kernel: [    1.152864] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e100
May 19 18:58:01 dave kernel: [    1.153041] hub 4-0:1.0: USB hub found
May 19 18:58:01 dave kernel: [    1.153047] hub 4-0:1.0: 2 ports detected
May 19 18:58:01 dave kernel: [    1.153139] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 19 18:58:01 dave kernel: [    1.153148] uhci_hcd 0000:00:1a.2: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.153152] uhci_hcd 0000:00:1a.2: UHCI Host Controller
May 19 18:58:01 dave kernel: [    1.153224] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
May 19 18:58:01 dave kernel: [    1.153249] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e500
May 19 18:58:01 dave kernel: [    1.153424] hub 5-0:1.0: USB hub found
May 19 18:58:01 dave kernel: [    1.153430] hub 5-0:1.0: 2 ports detected
May 19 18:58:01 dave kernel: [    1.153521] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 19 18:58:01 dave kernel: [    1.153530] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.153534] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May 19 18:58:01 dave kernel: [    1.153599] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
May 19 18:58:01 dave kernel: [    1.153624] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
May 19 18:58:01 dave kernel: [    1.153799] hub 6-0:1.0: USB hub found
May 19 18:58:01 dave kernel: [    1.153804] hub 6-0:1.0: 2 ports detected
May 19 18:58:01 dave kernel: [    1.153896] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 19 18:58:01 dave kernel: [    1.153905] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.153909] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May 19 18:58:01 dave kernel: [    1.153972] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
May 19 18:58:01 dave kernel: [    1.153996] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
May 19 18:58:01 dave kernel: [    1.154176] hub 7-0:1.0: USB hub found
May 19 18:58:01 dave kernel: [    1.154181] hub 7-0:1.0: 2 ports detected
May 19 18:58:01 dave kernel: [    1.154273] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 19 18:58:01 dave kernel: [    1.154282] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May 19 18:58:01 dave kernel: [    1.154286] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May 19 18:58:01 dave kernel: [    1.154348] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
May 19 18:58:01 dave kernel: [    1.154373] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
May 19 18:58:01 dave kernel: [    1.154548] hub 8-0:1.0: USB hub found
May 19 18:58:01 dave kernel: [    1.154553] hub 8-0:1.0: 2 ports detected
May 19 18:58:01 dave kernel: [    1.154726] usbcore: registered new interface driver libusual
May 19 18:58:01 dave kernel: [    1.154799] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May 19 18:58:01 dave kernel: [    1.154802] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May 19 18:58:01 dave kernel: [    1.155009] serio: i8042 KBD port at 0x60,0x64 irq 1
May 19 18:58:01 dave kernel: [    1.155166] mousedev: PS/2 mouse device common for all mice
May 19 18:58:01 dave kernel: [    1.155383] rtc_cmos 00:04: RTC can wake from S4
May 19 18:58:01 dave kernel: [    1.155508] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
May 19 18:58:01 dave kernel: [    1.155534] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
May 19 18:58:01 dave kernel: [    1.155611] device-mapper: uevent: version 1.0.3
May 19 18:58:01 dave kernel: [    1.155716] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
May 19 18:58:01 dave kernel: [    1.155765] EISA: Probing bus 0 at eisa.0
May 19 18:58:01 dave kernel: [    1.155797] EISA: Detected 0 cards.
May 19 18:58:01 dave kernel: [    1.155809] cpufreq-nforce2: No nForce2 chipset.
May 19 18:58:01 dave kernel: [    1.155813] cpuidle: using governor ladder
May 19 18:58:01 dave kernel: [    1.155815] cpuidle: using governor menu
May 19 18:58:01 dave kernel: [    1.155818] EFI Variables Facility v0.08 2004-May-17
May 19 18:58:01 dave kernel: [    1.156198] TCP cubic registered
May 19 18:58:01 dave kernel: [    1.156383] NET: Registered protocol family 10
May 19 18:58:01 dave kernel: [    1.157175] NET: Registered protocol family 17
May 19 18:58:01 dave kernel: [    1.157195] Registering the dns_resolver key type
May 19 18:58:01 dave kernel: [    1.157222] Using IPI No-Shortcut mode
May 19 18:58:01 dave kernel: [    1.157380] PM: Hibernation image not present or could not be loaded.
May 19 18:58:01 dave kernel: [    1.157396] registered taskstats version 1
May 19 18:58:01 dave kernel: [    1.169772]   Magic number: 12:454:993
May 19 18:58:01 dave kernel: [    1.169863] rtc_cmos 00:04: setting system clock to 2012-05-19 15:57:46 UTC (1337443066)
May 19 18:58:01 dave kernel: [    1.169897] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 19 18:58:01 dave kernel: [    1.169900] EDD information not available.
May 19 18:58:01 dave kernel: [    1.174723] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
May 19 18:58:01 dave kernel: [    1.442654] ata3: SATA link down (SStatus 0 SControl 300)
May 19 18:58:01 dave kernel: [    1.444016] Refined TSC clocksource calibration: 2399.970 MHz.
May 19 18:58:01 dave kernel: [    1.444022] Switching to clocksource tsc
May 19 18:58:01 dave kernel: [    1.453305] ata4: SATA link down (SStatus 0 SControl 300)
May 19 18:58:01 dave kernel: [    1.508016] usb 2-5: new high-speed USB device number 2 using ehci_hcd
May 19 18:58:01 dave kernel: [    1.588046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 19 18:58:01 dave kernel: [    1.588148] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 19 18:58:01 dave kernel: [    1.596192] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB04, max UDMA/100
May 19 18:58:01 dave kernel: [    1.597219] ata2.00: HPA detected: current 490232639, native 490234752
May 19 18:58:01 dave kernel: [    1.597227] ata2.00: ATA-7: Maxtor 6L250S0, BACE1G20, max UDMA/133
May 19 18:58:01 dave kernel: [    1.597231] ata2.00: 490232639 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 19 18:58:01 dave kernel: [    1.612192] ata1.00: configured for UDMA/100
May 19 18:58:01 dave kernel: [    1.613227] ata2.00: configured for UDMA/133
May 19 18:58:01 dave kernel: [    1.613489] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB04 PQ: 0 ANSI: 5
May 19 18:58:01 dave kernel: [    1.616113] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May 19 18:58:01 dave kernel: [    1.616117] cdrom: Uniform CD-ROM driver Revision: 3.20
May 19 18:58:01 dave kernel: [    1.616279] sr 0:0:0:0: Attached scsi CD-ROM sr0
May 19 18:58:01 dave kernel: [    1.616374] sr 0:0:0:0: Attached scsi generic sg0 type 5
May 19 18:58:01 dave kernel: [    1.616583] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6L250S0   BACE PQ: 0 ANSI: 5
May 19 18:58:01 dave kernel: [    1.616771] sd 1:0:0:0: [sda] 490232639 512-byte logical blocks: (250 GB/233 GiB)
May 19 18:58:01 dave kernel: [    1.616799] sd 1:0:0:0: Attached scsi generic sg1 type 0
May 19 18:58:01 dave kernel: [    1.616868] sd 1:0:0:0: [sda] Write Protect is off
May 19 18:58:01 dave kernel: [    1.616873] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 19 18:58:01 dave kernel: [    1.616911] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 19 18:58:01 dave kernel: [    1.645867] Initializing USB Mass Storage driver...
May 19 18:58:01 dave kernel: [    1.646001] scsi4 : usb-storage 2-5:1.0
May 19 18:58:01 dave kernel: [    1.646092] usbcore: registered new interface driver usb-storage
May 19 18:58:01 dave kernel: [    1.646095] USB Mass Storage support registered.
May 19 18:58:01 dave kernel: [    1.699478]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
May 19 18:58:01 dave kernel: [    1.699715] sda: p6 size 51329024 extends beyond EOD, enabling native capacity
May 19 18:58:01 dave kernel: [    1.699740] ata2: hard resetting link
May 19 18:58:01 dave kernel: [    1.880017] usb 5-1: new low-speed USB device number 2 using uhci_hcd
May 19 18:58:01 dave kernel: [    2.172047] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 19 18:58:01 dave kernel: [    2.204124] ata2.00: n_sectors mismatch 490232639 != 490234752
May 19 18:58:01 dave kernel: [    2.204127] ata2.00: new n_sectors matches native, probably late HPA unlock, n_sectors updated
May 19 18:58:01 dave kernel: [    2.221081] ata2.00: configured for UDMA/133
May 19 18:58:01 dave kernel: [    2.221086] ata2: EH complete
May 19 18:58:01 dave kernel: [    2.221133] sd 1:0:0:0: [sda] 490234752 512-byte logical blocks: (251 GB/233 GiB)
May 19 18:58:01 dave kernel: [    2.221598] sda: detected capacity change from 250999111168 to 251000193024
May 19 18:58:01 dave kernel: [    2.289837]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
May 19 18:58:01 dave kernel: [    2.290471] sd 1:0:0:0: [sda] Attached SCSI disk
May 19 18:58:01 dave kernel: [    2.290566] Freeing unused kernel memory: 740k freed
May 19 18:58:01 dave kernel: [    2.290843] Write protecting the kernel text: 5828k
May 19 18:58:01 dave kernel: [    2.290869] Write protecting the kernel read-only data: 2376k
May 19 18:58:01 dave kernel: [    2.290871] NX-protecting the kernel data: 4412k
May 19 18:58:01 dave kernel: [    2.357686] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 19 18:58:01 dave kernel: [    2.357728] pata_jmicron 0000:03:00.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    2.362132] [drm] Initialized drm 1.1.0 20060810
May 19 18:58:01 dave kernel: [    2.366213] scsi5 : pata_jmicron
May 19 18:58:01 dave kernel: [    2.366500] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May 19 18:58:01 dave kernel: [    2.366531] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May 19 18:58:01 dave kernel: [    2.366574] r8169 0000:04:00.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    2.366660] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
May 19 18:58:01 dave kernel: [    2.367296] scsi6 : pata_jmicron
May 19 18:58:01 dave kernel: [    2.367689] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xf840a000, 00:1f:d0:8b:fd:2e, XID 18000000 IRQ 44
May 19 18:58:01 dave kernel: [    2.367695] r8169 0000:04:00.0: eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
May 19 18:58:01 dave kernel: [    2.368191] ata5: PATA max UDMA/100 cmd 0xb000 ctl 0xb100 bmdma 0xb400 irq 16
May 19 18:58:01 dave kernel: [    2.368196] ata6: PATA max UDMA/100 cmd 0xb200 ctl 0xb300 bmdma 0xb408 irq 16
May 19 18:58:01 dave kernel: [    2.384770] [drm] radeon defaulting to kernel modesetting.
May 19 18:58:01 dave kernel: [    2.384773] [drm] radeon kernel modesetting enabled.
May 19 18:58:01 dave kernel: [    2.384860] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 19 18:58:01 dave kernel: [    2.384867] radeon 0000:01:00.0: setting latency timer to 64
May 19 18:58:01 dave kernel: [    2.387636] [drm] initializing kernel modesetting (RV670 0x1002:0x9505 0x1787:0x2245).
May 19 18:58:01 dave kernel: [    2.387667] [drm] register mmio base: 0xF5000000
May 19 18:58:01 dave kernel: [    2.387670] [drm] register mmio size: 65536
May 19 18:58:01 dave kernel: [    2.387862] ATOM BIOS: RV670
May 19 18:58:01 dave kernel: [    2.387883] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
May 19 18:58:01 dave kernel: [    2.387888] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
May 19 18:58:01 dave kernel: [    2.393637] [drm] Detected VRAM RAM=1024M, BAR=256M
May 19 18:58:01 dave kernel: [    2.393641] [drm] RAM width 256bits DDR
May 19 18:58:01 dave kernel: [    2.395743] [TTM] Zone  kernel: Available graphics memory: 438832 kiB.
May 19 18:58:01 dave kernel: [    2.395748] [TTM] Zone highmem: Available graphics memory: 1030132 kiB.
May 19 18:58:01 dave kernel: [    2.395751] [TTM] Initializing pool allocator.
May 19 18:58:01 dave kernel: [    2.395780] [drm] radeon: 1024M of VRAM memory ready
May 19 18:58:01 dave kernel: [    2.395785] [drm] radeon: 512M of GTT memory ready.
May 19 18:58:01 dave kernel: [    2.395806] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
May 19 18:58:01 dave kernel: [    2.395809] [drm] Driver supports precise vblank timestamp query.
May 19 18:58:01 dave kernel: [    2.395967] radeon 0000:01:00.0: irq 45 for MSI/MSI-X
May 19 18:58:01 dave kernel: [    2.395976] radeon 0000:01:00.0: radeon: using MSI.
May 19 18:58:01 dave kernel: [    2.396029] [drm] radeon: irq initialized.
May 19 18:58:01 dave kernel: [    2.396036] [drm] GART: num cpu pages 131072, num gpu pages 131072
May 19 18:58:01 dave kernel: [    2.396918] [drm] Loading RV670 Microcode
May 19 18:58:01 dave kernel: [    2.428917] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
May 19 18:58:01 dave kernel: [    2.429056] radeon 0000:01:00.0: WB enabled
May 19 18:58:01 dave kernel: [    2.460315] [drm] ring test succeeded in 1 usecs
May 19 18:58:01 dave kernel: [    2.460511] [drm] radeon: ib pool ready.
May 19 18:58:01 dave kernel: [    2.460595] [drm] ib test succeeded in 0 usecs
May 19 18:58:01 dave kernel: [    2.460979] [drm] Radeon Display Connectors
May 19 18:58:01 dave kernel: [    2.460982] [drm] Connector 0:
May 19 18:58:01 dave kernel: [    2.460984] [drm]   DVI-I
May 19 18:58:01 dave kernel: [    2.460986] [drm]   HPD1
May 19 18:58:01 dave kernel: [    2.460990] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
May 19 18:58:01 dave kernel: [    2.460992] [drm]   Encoders:
May 19 18:58:01 dave kernel: [    2.460994] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
May 19 18:58:01 dave kernel: [    2.460997] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
May 19 18:58:01 dave kernel: [    2.460999] [drm] Connector 1:
May 19 18:58:01 dave kernel: [    2.461001] [drm]   DIN
May 19 18:58:01 dave kernel: [    2.461003] [drm]   Encoders:
May 19 18:58:01 dave kernel: [    2.461005] [drm]     TV1: INTERNAL_KLDSCP_DAC2
May 19 18:58:01 dave kernel: [    2.461007] [drm] Connector 2:
May 19 18:58:01 dave kernel: [    2.461009] [drm]   DVI-I
May 19 18:58:01 dave kernel: [    2.461011] [drm]   HPD2
May 19 18:58:01 dave kernel: [    2.461013] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
May 19 18:58:01 dave kernel: [    2.461016] [drm]   Encoders:
May 19 18:58:01 dave kernel: [    2.461018] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
May 19 18:58:01 dave kernel: [    2.461020] [drm]     DFP2: INTERNAL_LVTM1
May 19 18:58:01 dave kernel: [    2.461030] [drm] Internal thermal controller with fan control
May 19 18:58:01 dave kernel: [    2.461090] [drm] radeon: power management initialized
May 19 18:58:01 dave kernel: [    2.544832] [drm] fb mappable at 0xE0142000
May 19 18:58:01 dave kernel: [    2.544836] [drm] vram apper at 0xE0000000
May 19 18:58:01 dave kernel: [    2.544838] [drm] size 7299072
May 19 18:58:01 dave kernel: [    2.544840] [drm] fb depth is 24
May 19 18:58:01 dave kernel: [    2.544842] [drm]    pitch is 6912
May 19 18:58:01 dave kernel: [    2.544930] fbcon: radeondrmfb (fb0) is primary device
May 19 18:58:01 dave kernel: [    2.645033] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler G3  PMAP PQ: 0 ANSI: 0 CCS
May 19 18:58:01 dave kernel: [    2.645920] sd 4:0:0:0: Attached scsi generic sg2 type 0
May 19 18:58:01 dave kernel: [    2.646767] sd 4:0:0:0: [sdb] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
May 19 18:58:01 dave kernel: [    2.648394] sd 4:0:0:0: [sdb] Write Protect is off
May 19 18:58:01 dave kernel: [    2.648398] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
May 19 18:58:01 dave kernel: [    2.650015] sd 4:0:0:0: [sdb] No Caching mode page present
May 19 18:58:01 dave kernel: [    2.650018] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 19 18:58:01 dave kernel: [    2.655262] sd 4:0:0:0: [sdb] No Caching mode page present
May 19 18:58:01 dave kernel: [    2.655266] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 19 18:58:01 dave kernel: [    2.656211]  sdb: sdb1
May 19 18:58:01 dave kernel: [    2.661265] sd 4:0:0:0: [sdb] No Caching mode page present
May 19 18:58:01 dave kernel: [    2.661269] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 19 18:58:01 dave kernel: [    2.661273] sd 4:0:0:0: [sdb] Attached SCSI removable disk
May 19 18:58:01 dave kernel: [    2.693888] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
May 19 18:58:01 dave kernel: [    2.694033] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.2-1/input0
May 19 18:58:01 dave kernel: [    2.694057] usbcore: registered new interface driver usbhid
May 19 18:58:01 dave kernel: [    2.694059] usbhid: USB HID core driver
May 19 18:58:01 dave kernel: [    2.969527] Console: switching to colour frame buffer device 210x65
May 19 18:58:01 dave kernel: [    2.978924] fb0: radeondrmfb frame buffer device
May 19 18:58:01 dave kernel: [    2.978927] drm: registered panic notifier
May 19 18:58:01 dave kernel: [    2.978944] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
May 19 18:58:01 dave kernel: [    3.435863] Btrfs loaded
May 19 18:58:01 dave kernel: [    3.443634] xor: automatically using best checksumming function: pIII_sse
May 19 18:58:01 dave kernel: [    3.460004]    pIII_sse  :  5949.000 MB/sec
May 19 18:58:01 dave kernel: [    3.460008] xor: using function: pIII_sse (5949.000 MB/sec)
May 19 18:58:01 dave kernel: [    3.460777] device-mapper: dm-raid45: initialized v0.2594b
May 19 18:58:01 dave kernel: [    4.560821] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
May 19 18:58:01 dave kernel: [    4.767942] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
May 19 18:58:01 dave kernel: [    6.406782] squashfs: version 4.0 (2009/01/31) Phillip Lougher
May 19 18:58:01 dave kernel: [   15.410245] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 19 18:58:01 dave kernel: [   15.936830] lp: driver loaded but no devices found
May 19 18:58:01 dave kernel: [   16.207905] parport_pc 00:08: reported by Plug and Play ACPI
May 19 18:58:01 dave kernel: [   16.207952] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May 19 18:58:01 dave kernel: [   16.308244] lp0: using parport0 (interrupt-driven).
May 19 18:58:01 dave kernel: [   16.376094] device-mapper: multipath: version 1.3.0 loaded
May 19 18:58:01 dave bluetoothd[1324]: Bluetooth daemon 4.98
May 19 18:58:01 dave kernel: [   16.454450] ppdev: user-space parallel port driver
May 19 18:58:01 dave bluetoothd[1324]: Starting SDP server
May 19 18:58:01 dave failsafe: Failsafe of 120 seconds reached.
May 19 18:58:01 dave kernel: [   16.618284] Bluetooth: Core ver 2.16
May 19 18:58:01 dave kernel: [   16.618368] NET: Registered protocol family 31
May 19 18:58:01 dave kernel: [   16.618371] Bluetooth: HCI device and connection manager initialized
May 19 18:58:01 dave kernel: [   16.618375] Bluetooth: HCI socket layer initialized
May 19 18:58:01 dave kernel: [   16.618378] Bluetooth: L2CAP socket layer initialized
May 19 18:58:01 dave kernel: [   16.618385] Bluetooth: SCO socket layer initialized
May 19 18:58:02 dave kernel: [   16.797003] Bluetooth: RFCOMM TTY layer initialized
May 19 18:58:02 dave kernel: [   16.797011] Bluetooth: RFCOMM socket layer initialized
May 19 18:58:02 dave kernel: [   16.797014] Bluetooth: RFCOMM ver 1.11
May 19 18:58:02 dave bluetoothd[1324]: Failed to init alert plugin
May 19 18:58:02 dave bluetoothd[1324]: Failed to init time plugin
May 19 18:58:02 dave bluetoothd[1324]: Failed to init proximity plugin
May 19 18:58:02 dave kernel: [   17.048572] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 19 18:58:02 dave kernel: [   17.048577] Bluetooth: BNEP filters: protocol multicast
May 19 18:58:02 dave bluetoothd[1324]: Failed to init gatt_example plugin
May 19 18:58:02 dave mtp-probe: checking bus 5, device 2: "/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1"
May 19 18:58:02 dave mtp-probe: checking bus 2, device 2: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5"
May 19 18:58:02 dave mtp-probe: bus: 5, device: 2 was not an MTP device
May 19 18:58:02 dave mtp-probe: bus: 2, device: 2 was not an MTP device
May 19 18:58:02 dave avahi-daemon[1503]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
May 19 18:58:02 dave avahi-daemon[1503]: Successfully dropped root privileges.
May 19 18:58:02 dave avahi-daemon[1503]: avahi-daemon 0.6.30 starting up.
May 19 18:58:02 dave avahi-daemon[1503]: Successfully called chroot().
May 19 18:58:02 dave avahi-daemon[1503]: Successfully dropped remaining capabilities.
May 19 18:58:02 dave modem-manager[1241]: <info>  ModemManager (version 0.5.2.0) starting...
May 19 18:58:02 dave avahi-daemon[1505]: chroot.c: open() failed: No such file or directory
May 19 18:58:02 dave avahi-daemon[1503]: Failed to open /etc/resolv.conf: Invalid argument
May 19 18:58:02 dave avahi-daemon[1503]: Loading service file /services/udisks.service.
May 19 18:58:02 dave kernel: [   17.554280] init: failsafe main process (1331) killed by TERM signal
May 19 18:58:02 dave modem-manager[1241]: <info>  Loaded plugin AnyData
May 19 18:58:02 dave avahi-daemon[1503]: Network interface enumeration completed.
May 19 18:58:02 dave avahi-daemon[1503]: Registering HINFO record with values 'I686'/'LINUX'.
May 19 18:58:02 dave avahi-daemon[1503]: Server startup complete. Host name is dave.local. Local service cookie is 2868969984.
May 19 18:58:02 dave avahi-daemon[1503]: Service "dave" (/services/udisks.service) successfully established.
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Generic
May 19 18:58:03 dave kernel: [   17.713526] snd_ca0106 0000:05:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
May 19 18:58:03 dave kernel: [   17.713550] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Gobi
May 19 18:58:03 dave kernel: [   17.809694] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May 19 18:58:03 dave kernel: [   17.809758] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
May 19 18:58:03 dave kernel: [   17.809793] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Option High-Speed
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Huawei
May 19 18:58:03 dave kernel: [   17.933027] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input4
May 19 18:58:03 dave kernel: [   17.933158] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input5
May 19 18:58:03 dave kernel: [   17.933269] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input6
May 19 18:58:03 dave kernel: [   17.933378] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input7
May 19 18:58:03 dave kernel: [   17.933486] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
May 19 18:58:03 dave kernel: [   17.933919] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May 19 18:58:03 dave kernel: [   17.933987] snd_hda_intel 0000:01:00.1: irq 47 for MSI/MSI-X
May 19 18:58:03 dave kernel: [   17.934016] snd_hda_intel 0000:01:00.1: setting latency timer to 64
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Linktop
May 19 18:58:03 dave kernel: [   18.011404] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
May 19 18:58:03 dave kernel: [   18.011514] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input9
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Longcheer
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Ericsson MBM
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin MotoC
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Nokia
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Novatel
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Option
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Samsung
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Sierra
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin SimTech
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin Wavecom
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin X22X
May 19 18:58:03 dave modem-manager[1241]: <info>  Loaded plugin ZTE
May 19 18:58:03 dave udev-configure-printer: add /module/lp
May 19 18:58:03 dave udev-configure-printer: Failed to get parent
May 19 18:58:03 dave udev-configure-printer: add /devices/pnp0/00:08/printer/lp0
May 19 18:58:03 dave udev-configure-printer: Failed to get parent
May 19 18:58:03 dave NetworkManager[1595]: <info> NetworkManager (version 0.9.4.0) is starting...
May 19 18:58:03 dave NetworkManager[1595]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
May 19 18:58:04 dave NetworkManager[1595]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
May 19 18:58:04 dave NetworkManager[1595]: <info> DNS: loaded plugin dnsmasq
May 19 18:58:04 dave dbus[1081]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
May 19 18:58:04 dave polkitd[1617]: started daemon version 0.104 using authority implementation `local' version `0.104'
May 19 18:58:04 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: init!
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: update_system_hostname
May 19 18:58:04 dave NetworkManager[1595]:    SCPluginIfupdown: management mode: unmanaged
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/eth0, iface: eth0)
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: end _init.
May 19 18:58:04 dave NetworkManager[1595]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May 19 18:58:04 dave NetworkManager[1595]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May 19 18:58:04 dave NetworkManager[1595]:    Ifupdown: get unmanaged devices count: 0
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: (158861136) ... get_connections.
May 19 18:58:04 dave NetworkManager[1595]:    SCPlugin-Ifupdown: (158861136) ... get_connections (managed=false): return empty list.
May 19 18:58:04 dave NetworkManager[1595]:    Ifupdown: get unmanaged devices count: 0
May 19 18:58:04 dave NetworkManager[1595]: <info> modem-manager is now available
May 19 18:58:04 dave NetworkManager[1595]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 19 18:58:04 dave NetworkManager[1595]: <info> WiFi enabled by radio killswitch; enabled by state file
May 19 18:58:04 dave NetworkManager[1595]: <info> WWAN enabled by radio killswitch; enabled by state file
May 19 18:58:04 dave NetworkManager[1595]: <info> WiMAX enabled by radio killswitch; enabled by state file
May 19 18:58:04 dave NetworkManager[1595]: <info> Networking is enabled by state file
May 19 18:58:04 dave NetworkManager[1595]: <warn> failed to allocate link cache: (-10) Operation not supported
May 19 18:58:04 dave NetworkManager[1595]: <info> (eth0): carrier is OFF
May 19 18:58:04 dave NetworkManager[1595]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
May 19 18:58:04 dave NetworkManager[1595]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May 19 18:58:04 dave NetworkManager[1595]: <info> (eth0): now managed
May 19 18:58:04 dave NetworkManager[1595]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 19 18:58:04 dave NetworkManager[1595]: <info> (eth0): bringing up device.
May 19 18:58:04 dave NetworkManager[1595]: <info> (eth0): preparing device.
May 19 18:58:04 dave NetworkManager[1595]: <info> (eth0): deactivating device (reason 'managed') [2]
May 19 18:58:04 dave NetworkManager[1595]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/eth0
May 19 18:58:04 dave kernel: [   19.432495] r8169 0000:04:00.0: eth0: link down
May 19 18:58:04 dave kernel: [   19.432504] r8169 0000:04:00.0: eth0: link down
May 19 18:58:04 dave kernel: [   19.432769] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 19 18:58:04 dave kernel: [   19.433150] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 19 18:58:04 dave cron[1657]: (CRON) INFO (pidfile fd = 3)
May 19 18:58:04 dave acpid: starting up with proc fs
May 19 18:58:04 dave cron[1674]: (CRON) STARTUP (fork ok)
May 19 18:58:05 dave cron[1674]: (CRON) INFO (Running @reboot jobs)
May 19 18:58:05 dave acpid: 35 rules loaded
May 19 18:58:05 dave acpid: waiting for events: event logging is off
May 19 18:58:05 dave kernel: [   19.987230] init: alsa-restore main process (1656) terminated with status 99
May 19 18:58:05 dave gdm-binary[1701]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May 19 18:58:06 dave kernel: [   20.728122] vboxdrv: Found 4 processor cores.
May 19 18:58:06 dave kernel: [   20.728873] vboxdrv: fAsync=0 offMin=0x357 offMax=0x1722
May 19 18:58:06 dave kernel: [   20.728961] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May 19 18:58:06 dave kernel: [   20.728964] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
May 19 18:58:06 dave gdm-simple-slave[1729]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May 19 18:58:06 dave kernel: [   20.929224] vboxpci: IOMMU not found (not registered)
May 19 18:58:06 dave ntpd[2267]: ntpd 4.2.6p3@1.2290 Tue Mar  6 15:03:21 UTC 2012 (1)
May 19 18:58:06 dave ntpd[2329]: proto: precision = 0.608 usec
May 19 18:58:06 dave ntpd[2329]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
May 19 18:58:06 dave ntpd[2329]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
May 19 18:58:06 dave ntpd[2329]: Listen and drop on 1 v6wildcard :: UDP 123
May 19 18:58:06 dave ntpd[2329]: Listen normally on 2 lo 127.0.0.1 UDP 123
May 19 18:58:06 dave ntpd[2329]: Listen normally on 3 lo ::1 UDP 123
May 19 18:58:06 dave ntpd[2329]: peers refreshed
May 19 18:58:06 dave ntpd[2329]: Listening on routing socket on fd #20 for interface updates
May 19 18:58:06 dave dbus[1081]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
May 19 18:58:06 dave acpid: client connected from 1765[0:0]
May 19 18:58:06 dave acpid: 1 client rule loaded
May 19 18:58:06 dave NetworkManager[1595]: <info> (eth0): carrier now ON (device state 20)
May 19 18:58:06 dave ntpd[2329]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
May 19 18:58:06 dave NetworkManager[1595]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May 19 18:58:06 dave ntpd[2329]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
May 19 18:58:06 dave kernel: [   21.445749] r8169 0000:04:00.0: eth0: link up
May 19 18:58:06 dave kernel: [   21.445987] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 19 18:58:06 dave NetworkManager[1595]: <info> Auto-activating connection 'Wired connection 1'.
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) starting connection 'Wired connection 1'
May 19 18:58:06 dave NetworkManager[1595]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 19 18:58:06 dave ntpd[2329]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 19 18:58:06 dave ntpd[2329]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May 19 18:58:06 dave NetworkManager[1595]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 19 18:58:06 dave NetworkManager[1595]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 19 18:58:06 dave ntpd[2329]: Deferring DNS for ntp.ubuntu.com 1
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 19 18:58:06 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
May 19 18:58:06 dave NetworkManager[1595]: <info> dhclient started with pid 2429
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Beginning IP6 addrconf.
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 19 18:58:06 dave dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 19 18:58:06 dave dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 19 18:58:06 dave dhclient: All rights reserved.
May 19 18:58:06 dave dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 19 18:58:06 dave dhclient: 
May 19 18:58:06 dave NetworkManager[1595]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 19 18:58:06 dave dhclient: Listening on LPF/eth0/00:1f:d0:8b:fd:2e
May 19 18:58:06 dave dhclient: Sending on   LPF/eth0/00:1f:d0:8b:fd:2e
May 19 18:58:06 dave dhclient: Sending on   Socket/fallback
May 19 18:58:06 dave dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 19 18:58:06 dave dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May 19 18:58:06 dave dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May 19 18:58:06 dave dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May 19 18:58:06 dave dhclient: bound to 192.168.1.101 -- renewal in 3125 seconds.
May 19 18:58:06 dave NetworkManager[1595]: <info> (eth0): DHCPv4 state changed preinit -> bound
May 19 18:58:06 dave NetworkManager[1595]: <info>   address 192.168.1.101
May 19 18:58:06 dave NetworkManager[1595]: <info>   prefix 24 (255.255.255.0)
May 19 18:58:06 dave NetworkManager[1595]: <info>   gateway 192.168.1.1
May 19 18:58:06 dave NetworkManager[1595]: <info>   nameserver '192.168.1.1'
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 19 18:58:06 dave NetworkManager[1595]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May 19 18:58:06 dave avahi-daemon[1503]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May 19 18:58:06 dave avahi-daemon[1503]: New relevant interface eth0.IPv4 for mDNS.
May 19 18:58:06 dave avahi-daemon[1503]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May 19 18:58:08 dave NetworkManager[1595]: <info> DNS: starting dnsmasq...
May 19 18:58:08 dave kernel: [   22.687422] radeon 0000:01:00.0: texture bo too small (1680 1050 26 0 -> 7299072 have 7258112)
May 19 18:58:08 dave kernel: [   22.687428] radeon 0000:01:00.0: alignments 1728 64 8 256
May 19 18:58:08 dave kernel: [   22.687432] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
May 19 18:58:08 dave NetworkManager[1595]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
May 19 18:58:08 dave NetworkManager[1595]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 19 18:58:08 dave NetworkManager[1595]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May 19 18:58:08 dave NetworkManager[1595]: <info> Activation (eth0) successful, device activated.
May 19 18:58:08 dave dbus[1081]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 19 18:58:08 dave NetworkManager[1595]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May 19 18:58:08 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 19 18:58:08 dave /etc/mysql/debian-start[2688]: Upgrading MySQL tables if necessary.
May 19 18:58:08 dave dnsmasq[2662]: started, version 2.59 cache disabled
May 19 18:58:08 dave dnsmasq[2662]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 19 18:58:08 dave dnsmasq[2662]: using nameserver 192.168.1.1#53
May 19 18:58:08 dave avahi-daemon[1503]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21f:d0ff:fe8b:fd2e.
May 19 18:58:08 dave avahi-daemon[1503]: New relevant interface eth0.IPv6 for mDNS.
May 19 18:58:08 dave avahi-daemon[1503]: Registering new address record for fe80::21f:d0ff:fe8b:fd2e on eth0.*.
May 19 18:58:08 dave ntpd[2329]: ntpd exiting on signal 15
May 19 18:58:08 dave ntpd_intres[2425]: parent died before we finished, exiting
May 19 18:58:08 dave /etc/mysql/debian-start[2691]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
May 19 18:58:08 dave /etc/mysql/debian-start[2691]: Looking for 'mysql' as: /usr/bin/mysql
May 19 18:58:08 dave /etc/mysql/debian-start[2691]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
May 19 18:58:08 dave /etc/mysql/debian-start[2691]: This installation of MySQL is already upgraded to 5.5.22, use --force if you still need to run mysql_upgrade
May 19 18:58:08 dave /etc/mysql/debian-start[2903]: Checking for insecure root accounts.
May 19 18:58:08 dave /etc/mysql/debian-start[2908]: WARNING: mysql.user contains 4 root accounts without password!
May 19 18:58:08 dave /etc/mysql/debian-start[2909]: Triggering myisam-recover for all MyISAM tables
May 19 18:58:08 dave gdm-simple-slave[1729]: CRITICAL: gdm_session_direct_get_username: assertion `session != NULL' failed
May 19 18:58:11 dave gnome-session[3009]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/lib/at-spi/at-spi-registryd" (No such file or directory)
May 19 18:58:11 dave dbus[1081]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
May 19 18:58:11 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.UPower'
May 19 18:58:13 dave kernel: [   27.991891] init: mythtv-backend main process (2969) terminated with status 138
May 19 18:58:13 dave kernel: [   27.991926] init: mythtv-backend main process ended, respawning
May 19 18:58:13 dave kernel: [   28.257320] init: mythtv-backend main process (3707) terminated with status 138
May 19 18:58:13 dave kernel: [   28.257356] init: mythtv-backend main process ended, respawning
May 19 18:58:13 dave kernel: [   28.458030] init: mythtv-backend main process (3922) terminated with status 138
May 19 18:58:13 dave kernel: [   28.458066] init: mythtv-backend respawning too fast, stopped
May 19 18:58:13 dave dbus[1081]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
May 19 18:58:14 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.ColorManager'
May 19 18:58:14 dave dbus[1081]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
May 19 18:58:14 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
May 19 18:58:14 dave rtkit-daemon[3973]: Successfully called chroot.
May 19 18:58:14 dave rtkit-daemon[3973]: Successfully dropped privileges.
May 19 18:58:14 dave rtkit-daemon[3973]: Successfully limited resources.
May 19 18:58:14 dave rtkit-daemon[3973]: Running.
May 19 18:58:14 dave rtkit-daemon[3973]: Watchdog thread running.
May 19 18:58:14 dave rtkit-daemon[3973]: Canary thread running.
May 19 18:58:14 dave rtkit-daemon[3973]: Successfully made thread 3971 of process 3971 (n/a) owned by '115' high priority at nice level -11.
May 19 18:58:14 dave rtkit-daemon[3973]: Supervising 1 threads of 1 processes of 1 users.
May 19 18:58:14 dave gnome-session[3009]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
May 19 18:58:14 dave rtkit-daemon[3973]: Successfully made thread 3980 of process 3971 (n/a) owned by '115' RT at priority 5.
May 19 18:58:14 dave rtkit-daemon[3973]: Supervising 2 threads of 1 processes of 1 users.
May 19 18:58:14 dave gdm-session-worker[3981]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May 19 18:58:14 dave gdm-session-worker[3981]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May 19 18:58:14 dave dbus[1081]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
May 19 18:58:14 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.Accounts'
May 19 18:58:14 dave accounts-daemon[3984]: started daemon version 0.6.15
May 19 18:58:14 dave rtkit-daemon[3973]: Successfully made thread 3990 of process 3971 (n/a) owned by '115' RT at priority 5.
May 19 18:58:14 dave rtkit-daemon[3973]: Supervising 3 threads of 1 processes of 1 users.
May 19 18:58:14 dave rtkit-daemon[3973]: Successfully made thread 3991 of process 3971 (n/a) owned by '115' RT at priority 5.
May 19 18:58:14 dave rtkit-daemon[3973]: Supervising 4 threads of 1 processes of 1 users.
May 19 18:58:15 dave rtkit-daemon[3973]: Successfully made thread 3992 of process 3971 (n/a) owned by '115' RT at priority 5.
May 19 18:58:15 dave rtkit-daemon[3973]: Supervising 5 threads of 1 processes of 1 users.
May 19 18:58:15 dave rtkit-daemon[3973]: Successfully made thread 3993 of process 3971 (n/a) owned by '115' RT at priority 5.
May 19 18:58:15 dave rtkit-daemon[3973]: Supervising 6 threads of 1 processes of 1 users.
May 19 18:58:15 dave rtkit-daemon[3973]: Successfully made thread 3996 of process 3996 (n/a) owned by '115' high priority at nice level -11.
May 19 18:58:15 dave rtkit-daemon[3973]: Supervising 7 threads of 2 processes of 1 users.
May 19 18:58:15 dave pulseaudio[3996]: [pulseaudio] pid.c: Daemon already running.
May 19 18:58:15 dave gdm-simple-greeter[3976]: Gtk-WARNING: Overriding tab label for notebook
May 19 18:58:15  gdm-simple-greeter[3976]: last message repeated 4 times
May 19 18:58:15 dave gdm-simple-greeter[3976]: Gtk-WARNING: /build/buildd/gtk+3.0-3.4.1/./gtk/gtkwidget.c:7117: widget not within a GtkWindow
May 19 18:58:16 dave gdm-simple-greeter[3976]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
May 19 18:58:16 dave gdm-simple-greeter[3976]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
May 19 18:58:16 dave gdm-simple-greeter[3976]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
May 19 18:58:16 dave gdm-simple-greeter[3976]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
May 19 18:58:16 dave gdm-simple-greeter[3976]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
May 19 18:58:16 dave gdm-simple-greeter[3976]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
May 19 18:58:16 dave gdm-simple-greeter[3976]: CRITICAL: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed
May 19 18:58:16 dave gdm-simple-greeter[3976]: CRITICAL: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed
May 19 18:58:17 dave kernel: [   32.208009] eth0: no IPv6 routers present
May 19 15:58:20 dave ntpdate[2877]: step time server 212.175.18.126 offset -10799.566449 sec
May 19 15:58:20 dave ntpd[4024]: ntpd 4.2.6p3@1.2290 Tue Mar  6 15:03:21 UTC 2012 (1)
May 19 15:58:20 dave ntpd[4025]: proto: precision = 0.611 usec
May 19 15:58:20 dave ntpd[4025]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
May 19 15:58:20 dave ntpd[4025]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
May 19 15:58:20 dave ntpd[4025]: Listen and drop on 1 v6wildcard :: UDP 123
May 19 15:58:20 dave ntpd[4025]: Listen normally on 2 lo 127.0.0.1 UDP 123
May 19 15:58:20 dave ntpd[4025]: Listen normally on 3 eth0 192.168.1.101 UDP 123
May 19 15:58:20 dave ntpd[4025]: Listen normally on 4 eth0 fe80::21f:d0ff:fe8b:fd2e UDP 123
May 19 15:58:20 dave ntpd[4025]: Listen normally on 5 lo ::1 UDP 123
May 19 15:58:20 dave ntpd[4025]: peers refreshed
May 19 15:58:20 dave ntpd[4025]: Listening on routing socket on fd #22 for interface updates
May 19 15:58:22 dave rtkit-daemon[3973]: Successfully made thread 4134 of process 4134 (n/a) owned by '1000' high priority at nice level -11.
May 19 15:58:22 dave rtkit-daemon[3973]: Supervising 7 threads of 2 processes of 2 users.
May 19 15:58:23 dave rtkit-daemon[3973]: Successfully made thread 4135 of process 4134 (n/a) owned by '1000' RT at priority 5.
May 19 15:58:23 dave rtkit-daemon[3973]: Supervising 8 threads of 2 processes of 2 users.
May 19 15:58:23 dave rtkit-daemon[3973]: Successfully made thread 4139 of process 4134 (n/a) owned by '1000' RT at priority 5.
May 19 15:58:23 dave rtkit-daemon[3973]: Supervising 9 threads of 2 processes of 2 users.
May 19 15:58:23 dave rtkit-daemon[3973]: Successfully made thread 4141 of process 4134 (n/a) owned by '1000' RT at priority 5.
May 19 15:58:23 dave rtkit-daemon[3973]: Supervising 10 threads of 2 processes of 2 users.
May 19 15:58:23 dave rtkit-daemon[3973]: Successfully made thread 4144 of process 4134 (n/a) owned by '1000' RT at priority 5.
May 19 15:58:23 dave rtkit-daemon[3973]: Supervising 11 threads of 2 processes of 2 users.
May 19 15:58:23 dave rtkit-daemon[3973]: Successfully made thread 4145 of process 4134 (n/a) owned by '1000' RT at priority 5.
May 19 15:58:23 dave rtkit-daemon[3973]: Supervising 12 threads of 2 processes of 2 users.
May 19 15:58:23 dave rtkit-daemon[3973]: Successfully made thread 4150 of process 4150 (n/a) owned by '1000' high priority at nice level -11.
May 19 15:58:23 dave rtkit-daemon[3973]: Supervising 13 threads of 3 processes of 2 users.
May 19 15:58:23 dave pulseaudio[4150]: [pulseaudio] pid.c: Daemon already running.
May 19 15:58:24 dave dbus[1081]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
May 19 15:58:24 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.UDisks'
May 19 15:58:26 dave goa[4191]: goa-daemon version 3.4.0 starting [main.c:112, main()]
May 19 15:58:27 dave NetworkManager[1595]: <info> (eth0): IP6 addrconf timed out or failed.
May 19 15:58:27 dave NetworkManager[1595]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 19 15:58:27 dave NetworkManager[1595]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 19 15:58:27 dave NetworkManager[1595]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 19 15:58:36 dave ubiquity[4212]: Ubiquity 2.10.16
May 19 15:58:37 dave ubiquity[4212]: log-output -t ubiquity laptop-detect
May 19 15:58:44 dave ubiquity[4212]: switched to page language
May 19 15:58:46 dave ubiquity[4212]: switched to page language
May 19 15:58:55 dave localechooser: info: Language = 'en'
May 19 15:58:55 dave localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
May 19 15:58:55 dave localechooser: info: Set debian-installer/language = 'en'
May 19 15:58:55 dave localechooser: info: Default country = 'US'
May 19 15:58:55 dave localechooser: info: Default locale = 'en_US.UTF-8'
May 19 15:58:55 dave localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
May 19 15:58:55 dave localechooser: info: Set debian-installer/country = 'US'
May 19 15:58:55 dave localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May 19 15:58:55 dave localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
May 19 15:58:56 dave ubiquity[4212]: debconffilter_done: ubi-language (current: ubi-language)
May 19 15:58:56 dave ubiquity[4212]: Step_before = stepLanguage
May 19 15:58:57 dave ubiquity[4212]: switched to page prepare
May 19 15:58:58 dave ubiquity[4212]: debconffilter_done: ubi-prepare (current: ubi-prepare)
May 19 15:58:59 dave localechooser: info: debian-installer/language preseeded to 'en' (seen: false)
May 19 15:58:59 dave localechooser: info: debian-installer/country preseeded to 'US' (seen: false)
May 19 15:58:59 dave localechooser: info: debian-installer/locale preseeded to 'en_US.UTF-8' (seen: false)
May 19 15:58:59 dave localechooser: info: Preseeded language ignored: unknown language code
May 19 15:58:59 dave ubiquity[4212]: switched to page language
May 19 15:59:21 dave dbus[1081]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
May 19 15:59:21 dave dbus[1081]: [system] Successfully activated service 'org.freedesktop.locale1'
May 19 15:59:36 dave localechooser: info: Language = 'en'
May 19 15:59:36 dave localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
May 19 15:59:36 dave localechooser: info: Set debian-installer/language = 'en'
May 19 15:59:36 dave localechooser: info: Default country = 'US'
May 19 15:59:36 dave localechooser: info: Default locale = 'en_US.UTF-8'
May 19 15:59:36 dave localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
May 19 15:59:36 dave localechooser: info: Set debian-installer/country = 'US'
May 19 15:59:36 dave localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May 19 15:59:36 dave localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
May 19 15:59:38 dave ubiquity[4212]: debconffilter_done: ubi-language (current: ubi-language)
May 19 15:59:38 dave ubiquity[4212]: Step_before = stepLanguage
May 19 15:59:39 dave ubiquity[4212]: switched to page prepare
May 19 15:59:46 dave ubiquity[4212]: debconffilter_done: ubi-prepare (current: ubi-prepare)
May 19 15:59:46 dave ubiquity[4212]: Step_before = stepPrepare
May 19 15:59:46 dave ubiquity[4212]: Step_before = stepPrepare
May 19 15:59:46 dave activate-dmraid: No Serial ATA RAID disks detected
May 19 15:59:47 dave kernel: [  121.240773] JFS: nTxBlock = 8192, nTxLock = 65536
May 19 15:59:47 dave kernel: [  121.343149] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
May 19 15:59:47 dave kernel: [  121.344817] SGI XFS Quota Management subsystem
May 19 15:59:54 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 15:59:54 dave ntfsresize: Device name        : /dev/sda2
May 19 15:59:54 dave ntfsresize: NTFS volume version: 3.1
May 19 15:59:54 dave ntfsresize: Cluster size       : 4096 bytes
May 19 15:59:54 dave ntfsresize: Current volume size: 83783315968 bytes (83784 MB)
May 19 15:59:54 dave ntfsresize: Current device size: 83783319552 bytes (83784 MB)
May 19 15:59:54 dave ntfsresize: Checking filesystem consistency ...
May 19 15:59:54 dave ntfsresize: Accounting clusters ...
May 19 15:59:54 dave ntfsresize: Space in use       : 34128 MB (40.7%)
May 19 15:59:54 dave ntfsresize: Collecting resizing constraints ...
May 19 15:59:54 dave ntfsresize: You might resize at 34127597568 bytes or 34128 MB (freeing 49656 MB).
May 19 15:59:54 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 15:59:58 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 15:59:58 dave ntfsresize: Device name        : /dev/sda5
May 19 15:59:58 dave ntfsresize: NTFS volume version: 3.1
May 19 15:59:58 dave ntfsresize: Cluster size       : 4096 bytes
May 19 15:59:58 dave ntfsresize: Current volume size: 125830300160 bytes (125831 MB)
May 19 15:59:58 dave ntfsresize: Current device size: 125830301184 bytes (125831 MB)
May 19 15:59:58 dave ntfsresize: Checking filesystem consistency ...
May 19 15:59:58 dave ntfsresize: Accounting clusters ...
May 19 15:59:58 dave ntfsresize: Space in use       : 85634 MB (68.1%)
May 19 15:59:58 dave ntfsresize: Collecting resizing constraints ...
May 19 15:59:58 dave ntfsresize: You might resize at 85633314816 bytes or 85634 MB (freeing 40197 MB).
May 19 15:59:58 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 15:59:58 dave ntfs-3g[7270]: Version 2012.1.15AR.1 external FUSE 28
May 19 15:59:58 dave ntfs-3g[7270]: Mounted /dev/sda1 (Read-Only, label "System Reserved", NTFS 3.1)
May 19 15:59:58 dave ntfs-3g[7270]: Cmdline options: ro
May 19 15:59:58 dave ntfs-3g[7270]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
May 19 15:59:58 dave ntfs-3g[7270]: Ownership and permissions disabled, configuration type 7
May 19 15:59:58 dave ntfs-3g[7270]: Unmounting /dev/sda1 (System Reserved)
May 19 15:59:58 dave ntfs-3g[7284]: Version 2012.1.15AR.1 external FUSE 28
May 19 15:59:58 dave ntfs-3g[7284]: Mounted /dev/sda2 (Read-Only, label "", NTFS 3.1)
May 19 15:59:58 dave ntfs-3g[7284]: Cmdline options: ro
May 19 15:59:58 dave ntfs-3g[7284]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
May 19 15:59:58 dave ntfs-3g[7284]: Ownership and permissions disabled, configuration type 7
May 19 15:59:58 dave ntfs-3g[7284]: Unmounting /dev/sda2 ()
May 19 15:59:59 dave ntfs-3g[7293]: Version 2012.1.15AR.1 external FUSE 28
May 19 15:59:59 dave ntfs-3g[7293]: Mounted /dev/sda5 (Read-Only, label "", NTFS 3.1)
May 19 15:59:59 dave ntfs-3g[7293]: Cmdline options: ro
May 19 15:59:59 dave ntfs-3g[7293]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096
May 19 15:59:59 dave ntfs-3g[7293]: Ownership and permissions disabled, configuration type 7
May 19 15:59:59 dave ntfs-3g[7293]: Unmounting /dev/sda5 ()
May 19 15:59:59 dave kernel: [  133.392905] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
May 19 15:59:59 dave kernel: [  133.593187] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
May 19 15:59:59 dave ubiquity: umount: /tmp/tmp.gh9YKGF6I3: not mounted
May 19 15:59:59 dave ntfs-3g[7353]: Version 2012.1.15AR.1 external FUSE 28
May 19 15:59:59 dave ntfs-3g[7353]: Mounted /dev/sda1 (Read-Only, label "System Reserved", NTFS 3.1)
May 19 15:59:59 dave ntfs-3g[7353]: Cmdline options: ro
May 19 15:59:59 dave ntfs-3g[7353]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
May 19 15:59:59 dave ntfs-3g[7353]: Ownership and permissions disabled, configuration type 7
May 19 15:59:59 dave ntfs-3g[7353]: Unmounting /dev/sda1 (System Reserved)
May 19 15:59:59 dave ntfs-3g[7362]: Version 2012.1.15AR.1 external FUSE 28
May 19 15:59:59 dave ntfs-3g[7362]: Mounted /dev/sda2 (Read-Only, label "", NTFS 3.1)
May 19 15:59:59 dave ntfs-3g[7362]: Cmdline options: ro
May 19 15:59:59 dave ntfs-3g[7362]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
May 19 15:59:59 dave ntfs-3g[7362]: Ownership and permissions disabled, configuration type 7
May 19 15:59:59 dave ntfs-3g[7362]: Unmounting /dev/sda2 ()
May 19 16:00:00 dave ntfs-3g[7371]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:00 dave ntfs-3g[7371]: Mounted /dev/sda5 (Read-Only, label "", NTFS 3.1)
May 19 16:00:00 dave ntfs-3g[7371]: Cmdline options: ro
May 19 16:00:00 dave ntfs-3g[7371]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096
May 19 16:00:00 dave ntfs-3g[7371]: Ownership and permissions disabled, configuration type 7
May 19 16:00:00 dave ntfs-3g[7371]: Unmounting /dev/sda5 ()
May 19 16:00:00 dave kernel: [  134.365753] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:00 dave kernel: [  134.541071] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:00 dave ubiquity: umount: /tmp/tmp.4mCxyordcv: not mounted
May 19 16:00:05 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 16:00:05 dave ntfsresize: Device name        : /dev/sda2
May 19 16:00:05 dave ntfsresize: NTFS volume version: 3.1
May 19 16:00:05 dave ntfsresize: Cluster size       : 4096 bytes
May 19 16:00:05 dave ntfsresize: Current volume size: 83783315968 bytes (83784 MB)
May 19 16:00:05 dave ntfsresize: Current device size: 83783319552 bytes (83784 MB)
May 19 16:00:05 dave ntfsresize: Checking filesystem consistency ...
May 19 16:00:05 dave ntfsresize: Accounting clusters ...
May 19 16:00:05 dave ntfsresize: Space in use       : 34128 MB (40.7%)
May 19 16:00:05 dave ntfsresize: Collecting resizing constraints ...
May 19 16:00:05 dave ntfsresize: You might resize at 34127597568 bytes or 34128 MB (freeing 49656 MB).
May 19 16:00:05 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 16:00:06 dave ntfs-3g[7620]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:06 dave ntfs-3g[7620]: Mounted /dev/sda1 (Read-Only, label "System Reserved", NTFS 3.1)
May 19 16:00:06 dave ntfs-3g[7620]: Cmdline options: ro
May 19 16:00:06 dave ntfs-3g[7620]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
May 19 16:00:06 dave ntfs-3g[7620]: Ownership and permissions disabled, configuration type 7
May 19 16:00:06 dave ntfs-3g[7620]: Unmounting /dev/sda1 (System Reserved)
May 19 16:00:06 dave ntfs-3g[7629]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:06 dave ntfs-3g[7629]: Mounted /dev/sda2 (Read-Only, label "", NTFS 3.1)
May 19 16:00:06 dave ntfs-3g[7629]: Cmdline options: ro
May 19 16:00:06 dave ntfs-3g[7629]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
May 19 16:00:06 dave ntfs-3g[7629]: Ownership and permissions disabled, configuration type 7
May 19 16:00:06 dave ntfs-3g[7629]: Unmounting /dev/sda2 ()
May 19 16:00:06 dave ntfs-3g[7643]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:06 dave ntfs-3g[7643]: Mounted /dev/sda5 (Read-Only, label "", NTFS 3.1)
May 19 16:00:06 dave ntfs-3g[7643]: Cmdline options: ro
May 19 16:00:06 dave ntfs-3g[7643]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096
May 19 16:00:06 dave ntfs-3g[7643]: Ownership and permissions disabled, configuration type 7
May 19 16:00:06 dave ntfs-3g[7643]: Unmounting /dev/sda5 ()
May 19 16:00:06 dave kernel: [  140.959676] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:06 dave kernel: [  141.143296] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:06 dave ubiquity: umount: /tmp/tmp.SQq3Ik1Wts: not mounted
May 19 16:00:07 dave ntfs-3g[7703]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:07 dave ntfs-3g[7703]: Mounted /dev/sda1 (Read-Only, label "System Reserved", NTFS 3.1)
May 19 16:00:07 dave ntfs-3g[7703]: Cmdline options: ro
May 19 16:00:07 dave ntfs-3g[7703]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
May 19 16:00:07 dave ntfs-3g[7703]: Ownership and permissions disabled, configuration type 7
May 19 16:00:07 dave ntfs-3g[7703]: Unmounting /dev/sda1 (System Reserved)
May 19 16:00:07 dave ntfs-3g[7712]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:07 dave ntfs-3g[7712]: Mounted /dev/sda2 (Read-Only, label "", NTFS 3.1)
May 19 16:00:07 dave ntfs-3g[7712]: Cmdline options: ro
May 19 16:00:07 dave ntfs-3g[7712]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
May 19 16:00:07 dave ntfs-3g[7712]: Ownership and permissions disabled, configuration type 7
May 19 16:00:07 dave ntfs-3g[7712]: Unmounting /dev/sda2 ()
May 19 16:00:07 dave ntfs-3g[7721]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:07 dave ntfs-3g[7721]: Mounted /dev/sda5 (Read-Only, label "", NTFS 3.1)
May 19 16:00:07 dave ntfs-3g[7721]: Cmdline options: ro
May 19 16:00:07 dave ntfs-3g[7721]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096
May 19 16:00:07 dave ntfs-3g[7721]: Ownership and permissions disabled, configuration type 7
May 19 16:00:07 dave ntfs-3g[7721]: Unmounting /dev/sda5 ()
May 19 16:00:07 dave kernel: [  141.899207] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:07 dave kernel: [  142.074583] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:07 dave ubiquity: umount: /tmp/tmp.e49svGhFej: not mounted
May 19 16:00:07 dave ubiquity: 
May 19 16:00:08 dave ntfs-3g[7864]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:08 dave ntfs-3g[7864]: Mounted /dev/sda1 (Read-Only, label "System Reserved", NTFS 3.1)
May 19 16:00:08 dave ntfs-3g[7864]: Cmdline options: ro
May 19 16:00:08 dave ntfs-3g[7864]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
May 19 16:00:08 dave ntfs-3g[7864]: Ownership and permissions disabled, configuration type 7
May 19 16:00:08 dave ntfs-3g[7864]: Unmounting /dev/sda1 (System Reserved)
May 19 16:00:08 dave ntfs-3g[7873]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:08 dave ntfs-3g[7873]: Mounted /dev/sda2 (Read-Only, label "", NTFS 3.1)
May 19 16:00:08 dave ntfs-3g[7873]: Cmdline options: ro
May 19 16:00:08 dave ntfs-3g[7873]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
May 19 16:00:08 dave ntfs-3g[7873]: Ownership and permissions disabled, configuration type 7
May 19 16:00:08 dave ntfs-3g[7873]: Unmounting /dev/sda2 ()
May 19 16:00:08 dave ntfs-3g[7882]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:08 dave ntfs-3g[7882]: Mounted /dev/sda5 (Read-Only, label "", NTFS 3.1)
May 19 16:00:08 dave ntfs-3g[7882]: Cmdline options: ro
May 19 16:00:08 dave ntfs-3g[7882]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096
May 19 16:00:08 dave ntfs-3g[7882]: Ownership and permissions disabled, configuration type 7
May 19 16:00:08 dave ntfs-3g[7882]: Unmounting /dev/sda5 ()
May 19 16:00:08 dave kernel: [  142.880474] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:08 dave kernel: [  143.055734] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:08 dave ubiquity: umount: /tmp/tmp.q5YUFmDeut: not mounted
May 19 16:00:08 dave ubiquity: 
May 19 16:00:09 dave ntfs-3g[7942]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:09 dave ntfs-3g[7942]: Mounted /dev/sda1 (Read-Only, label "System Reserved", NTFS 3.1)
May 19 16:00:09 dave ntfs-3g[7942]: Cmdline options: ro
May 19 16:00:09 dave ntfs-3g[7942]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
May 19 16:00:09 dave ntfs-3g[7942]: Ownership and permissions disabled, configuration type 7
May 19 16:00:09 dave ntfs-3g[7942]: Unmounting /dev/sda1 (System Reserved)
May 19 16:00:09 dave ntfs-3g[7951]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:09 dave ntfs-3g[7951]: Mounted /dev/sda2 (Read-Only, label "", NTFS 3.1)
May 19 16:00:09 dave ntfs-3g[7951]: Cmdline options: ro
May 19 16:00:09 dave ntfs-3g[7951]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
May 19 16:00:09 dave ntfs-3g[7951]: Ownership and permissions disabled, configuration type 7
May 19 16:00:09 dave ntfs-3g[7951]: Unmounting /dev/sda2 ()
May 19 16:00:09 dave ntfs-3g[7960]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:00:09 dave ntfs-3g[7960]: Mounted /dev/sda5 (Read-Only, label "", NTFS 3.1)
May 19 16:00:09 dave ntfs-3g[7960]: Cmdline options: ro
May 19 16:00:09 dave ntfs-3g[7960]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096
May 19 16:00:09 dave ntfs-3g[7960]: Ownership and permissions disabled, configuration type 7
May 19 16:00:09 dave ntfs-3g[7960]: Unmounting /dev/sda5 ()
May 19 16:00:09 dave kernel: [  143.728583] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:09 dave kernel: [  143.895573] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
May 19 16:00:09 dave ubiquity: umount: /tmp/tmp.MGUVBemsV9: not mounted
May 19 16:00:09 dave kernel: [  144.102219] NTFS driver 2.1.30 [Flags: R/O MODULE].
May 19 16:00:09 dave kernel: [  144.166378] QNX4 filesystem 0.2.3 registered.
May 19 16:00:10 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
May 19 16:00:10 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:00:10 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:00:10 dave 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
May 19 16:00:10 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:00:10 dave 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
May 19 16:00:10 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:00:10 dave macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
May 19 16:00:10 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:00:10 dave 20microsoft: debug: /dev/sda1 is a NTFS partition
May 19 16:00:10 dave 20microsoft: result: /dev/sda1:Windows 7 (loader):Windows:chain
May 19 16:00:10 dave 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:00:10 dave os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 19 16:00:10 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
May 19 16:00:11 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:00:11 dave 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:00:11 dave 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:00:11 dave macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:00:11 dave 20microsoft: debug: /dev/sda2 is a NTFS partition
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:00:11 dave 30utility: debug: /dev/sda2 is not a FAT partition: exiting
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:00:11 dave 83haiku: debug: /dev/sda2 is not a BeFS partition: exiting
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:00:11 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:00:11 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
May 19 16:00:11 dave 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
May 19 16:00:11 dave os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 19 16:00:11 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
May 19 16:00:12 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:00:12 dave 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:00:12 dave 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:00:12 dave macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:00:12 dave 20microsoft: debug: /dev/sda5 is a NTFS partition
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:00:12 dave 30utility: debug: /dev/sda5 is not a FAT partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:00:12 dave 83haiku: debug: /dev/sda5 is not a BeFS partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:00:12 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
May 19 16:00:12 dave 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:00:12 dave 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:00:12 dave 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:00:12 dave macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:00:12 dave 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:00:12 dave 30utility: debug: /dev/sda6 is not a FAT partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:00:12 dave 83haiku: debug: /dev/sda6 is not a BeFS partition: exiting
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:00:12 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:00:12 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda7
May 19 16:00:13 dave 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
May 19 16:00:13 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:00:13 dave 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
May 19 16:00:13 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:00:13 dave 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
May 19 16:00:13 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:00:13 dave macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
May 19 16:00:13 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:00:13 dave 20microsoft: debug: /dev/sda7 is not a MS partition: exiting
May 19 16:00:13 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:00:13 dave 30utility: debug: /dev/sda7 is not a FAT partition: exiting
May 19 16:00:13 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:00:13 dave 40lsb: result: /dev/sda7:Ubuntu 12.04 LTS (12.04):Ubuntu:linux
May 19 16:00:13 dave 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:00:13 dave os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
May 19 16:00:13 dave 10freedos: debug: /dev/sdb1 is a FAT32 partition
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
May 19 16:00:13 dave 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
May 19 16:00:13 dave macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
May 19 16:00:13 dave 20microsoft: debug: /dev/sdb1 is a FAT32 partition
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
May 19 16:00:13 dave 30utility: debug: /dev/sdb1 is a FAT32 partition
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
May 19 16:00:13 dave 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/90bsd-distro on mounted /dev/sdb1
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
May 19 16:00:13 dave os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
May 19 16:00:13 dave ubiquity[4212]: Device /dev/sda2 not found in os-prober output
May 19 16:00:13 dave ubiquity[4212]: Device /dev/sda5 not found in os-prober output
May 19 16:00:13 dave ubiquity[4212]: Device /dev/sda6 not found in os-prober output
May 19 16:00:13 dave ubiquity[4212]: switched to page partman
May 19 16:00:18  ubiquity[4212]: last message repeated 2 times
May 19 16:00:18 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 16:00:18 dave ntfsresize: Device name        : /dev/sda1
May 19 16:00:18 dave ntfsresize: NTFS volume version: 3.1
May 19 16:00:18 dave ntfsresize: Cluster size       : 4096 bytes
May 19 16:00:18 dave ntfsresize: Current volume size: 104854016 bytes (105 MB)
May 19 16:00:18 dave ntfsresize: Current device size: 104857600 bytes (105 MB)
May 19 16:00:18 dave ntfsresize: Checking filesystem consistency ...
May 19 16:00:18 dave ntfsresize: Accounting clusters ...
May 19 16:00:18 dave ntfsresize: Space in use       : 26 MB (24.6%)
May 19 16:00:18 dave ntfsresize: Collecting resizing constraints ...
May 19 16:00:18 dave ntfsresize: You might resize at 34971648 bytes or 35 MB (freeing 70 MB).
May 19 16:00:18 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 16:00:19 dave ubiquity[4212]: switched to page partman
May 19 16:00:25 dave ubiquity[4212]: switched to page partman
May 19 16:00:25 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 16:00:25 dave ntfsresize: Device name        : /dev/sda1
May 19 16:00:25 dave ntfsresize: NTFS volume version: 3.1
May 19 16:00:25 dave ntfsresize: Cluster size       : 4096 bytes
May 19 16:00:25 dave ntfsresize: Current volume size: 104854016 bytes (105 MB)
May 19 16:00:25 dave ntfsresize: Current device size: 104857600 bytes (105 MB)
May 19 16:00:25 dave ntfsresize: Checking filesystem consistency ...
May 19 16:00:25 dave ntfsresize: Accounting clusters ...
May 19 16:00:25 dave ntfsresize: Space in use       : 26 MB (24.6%)
May 19 16:00:25 dave ntfsresize: Collecting resizing constraints ...
May 19 16:00:25 dave ntfsresize: You might resize at 34971648 bytes or 35 MB (freeing 70 MB).
May 19 16:00:25 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 16:00:31 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 16:00:31 dave ntfsresize: Device name        : /dev/sda2
May 19 16:00:31 dave ntfsresize: NTFS volume version: 3.1
May 19 16:00:31 dave ntfsresize: Cluster size       : 4096 bytes
May 19 16:00:31 dave ntfsresize: Current volume size: 83783315968 bytes (83784 MB)
May 19 16:00:31 dave ntfsresize: Current device size: 83783319552 bytes (83784 MB)
May 19 16:00:31 dave ntfsresize: Checking filesystem consistency ...
May 19 16:00:31 dave ntfsresize: Accounting clusters ...
May 19 16:00:31 dave ntfsresize: Space in use       : 34128 MB (40.7%)
May 19 16:00:31 dave ntfsresize: Collecting resizing constraints ...
May 19 16:00:31 dave ntfsresize: You might resize at 34127597568 bytes or 34128 MB (freeing 49656 MB).
May 19 16:00:31 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 16:00:35 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 16:00:35 dave ntfsresize: Device name        : /dev/sda5
May 19 16:00:35 dave ntfsresize: NTFS volume version: 3.1
May 19 16:00:35 dave ntfsresize: Cluster size       : 4096 bytes
May 19 16:00:35 dave ntfsresize: Current volume size: 125830300160 bytes (125831 MB)
May 19 16:00:35 dave ntfsresize: Current device size: 125830301184 bytes (125831 MB)
May 19 16:00:35 dave ntfsresize: Checking filesystem consistency ...
May 19 16:00:35 dave ntfsresize: Accounting clusters ...
May 19 16:00:35 dave ntfsresize: Space in use       : 85634 MB (68.1%)
May 19 16:00:35 dave ntfsresize: Collecting resizing constraints ...
May 19 16:00:35 dave ntfsresize: You might resize at 85633314816 bytes or 85634 MB (freeing 40197 MB).
May 19 16:00:35 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 16:00:35 dave ubiquity[4212]: switched to page partman
May 19 16:00:42 dave ubiquity[4212]: switched to page partman
May 19 16:00:43 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 16:00:43 dave ntfsresize: Device name        : /dev/sda1
May 19 16:00:43 dave ntfsresize: NTFS volume version: 3.1
May 19 16:00:43 dave ntfsresize: Cluster size       : 4096 bytes
May 19 16:00:43 dave ntfsresize: Current volume size: 104854016 bytes (105 MB)
May 19 16:00:43 dave ntfsresize: Current device size: 104857600 bytes (105 MB)
May 19 16:00:43 dave ntfsresize: Checking filesystem consistency ...
May 19 16:00:43 dave ntfsresize: Accounting clusters ...
May 19 16:00:43 dave ntfsresize: Space in use       : 26 MB (24.6%)
May 19 16:00:43 dave ntfsresize: Collecting resizing constraints ...
May 19 16:00:43 dave ntfsresize: You might resize at 34971648 bytes or 35 MB (freeing 70 MB).
May 19 16:00:43 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 16:00:48 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 16:00:48 dave ntfsresize: Device name        : /dev/sda2
May 19 16:00:48 dave ntfsresize: NTFS volume version: 3.1
May 19 16:00:48 dave ntfsresize: Cluster size       : 4096 bytes
May 19 16:00:48 dave ntfsresize: Current volume size: 83783315968 bytes (83784 MB)
May 19 16:00:48 dave ntfsresize: Current device size: 83783319552 bytes (83784 MB)
May 19 16:00:48 dave ntfsresize: Checking filesystem consistency ...
May 19 16:00:48 dave ntfsresize: Accounting clusters ...
May 19 16:00:48 dave ntfsresize: Space in use       : 34128 MB (40.7%)
May 19 16:00:48 dave ntfsresize: Collecting resizing constraints ...
May 19 16:00:48 dave ntfsresize: You might resize at 34127597568 bytes or 34128 MB (freeing 49656 MB).
May 19 16:00:48 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 16:00:52 dave ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 19 16:00:52 dave ntfsresize: Device name        : /dev/sda5
May 19 16:00:52 dave ntfsresize: NTFS volume version: 3.1
May 19 16:00:52 dave ntfsresize: Cluster size       : 4096 bytes
May 19 16:00:52 dave ntfsresize: Current volume size: 125830300160 bytes (125831 MB)
May 19 16:00:52 dave ntfsresize: Current device size: 125830301184 bytes (125831 MB)
May 19 16:00:52 dave ntfsresize: Checking filesystem consistency ...
May 19 16:00:52 dave ntfsresize: Accounting clusters ...
May 19 16:00:52 dave ntfsresize: Space in use       : 85634 MB (68.1%)
May 19 16:00:52 dave ntfsresize: Collecting resizing constraints ...
May 19 16:00:52 dave ntfsresize: You might resize at 85633314816 bytes or 85634 MB (freeing 40197 MB).
May 19 16:00:52 dave ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 19 16:00:53 dave ubiquity[4212]: switched to page partman
May 19 16:01:02  ubiquity[4212]: last message repeated 2 times
May 19 16:01:02 dave ubiquity[4212]: debconffilter_done: ubi-partman (current: ubi-partman)
May 19 16:01:02 dave ubiquity[4212]: Step_before = stepPartAdvanced
May 19 16:01:03 dave clock-setup: Sat May 19 16:01:03 EEST 2012
May 19 16:01:03 dave clock-setup: rdate: adjust local clock by -0.028686 seconds
May 19 16:01:04 dave ubiquity[4212]: switched to page timezone
May 19 16:01:05 dave partman: mke2fs 1.42 (29-Nov-2011)
May 19 16:01:09 dave kernel: [  203.631311] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: errors=remount-ro
May 19 16:01:09 dave ubiquity[4212]: debconffilter_done: ubiquity.components.partman_commit (current: ubi-timezone)
May 19 16:01:10 dave install.py: keeping packages due to preseeding: 
May 19 16:01:10 dave install.py: keeping language packs for: en_US.UTF-8
May 19 16:01:41 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
May 19 16:01:43 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:01:43 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:01:43 dave 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
May 19 16:01:43 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:01:43 dave 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
May 19 16:01:43 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:01:43 dave macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
May 19 16:01:43 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:01:43 dave 20microsoft: debug: /dev/sda1 is a NTFS partition
May 19 16:01:43 dave 20microsoft: result: /dev/sda1:Windows 7 (loader):Windows:chain
May 19 16:01:43 dave 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:01:43 dave os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 19 16:01:43 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
May 19 16:01:44 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:01:44 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:01:44 dave 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
May 19 16:01:44 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:01:44 dave 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
May 19 16:01:44 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:01:44 dave macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
May 19 16:01:44 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:01:44 dave 20microsoft: debug: /dev/sda2 is a NTFS partition
May 19 16:01:45 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:01:45 dave 30utility: debug: /dev/sda2 is not a FAT partition: exiting
May 19 16:01:45 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:01:45 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:01:45 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:01:45 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:01:45 dave 83haiku: debug: /dev/sda2 is not a BeFS partition: exiting
May 19 16:01:45 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:01:45 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:01:45 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:01:45 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
May 19 16:01:45 dave 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
May 19 16:01:45 dave os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 19 16:01:45 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
May 19 16:01:46 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:01:46 dave 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:01:46 dave 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:01:46 dave macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:01:46 dave 20microsoft: debug: /dev/sda5 is a NTFS partition
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:01:46 dave 30utility: debug: /dev/sda5 is not a FAT partition: exiting
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:01:46 dave 83haiku: debug: /dev/sda5 is not a BeFS partition: exiting
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:01:46 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:01:46 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
May 19 16:01:47 dave 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:01:47 dave 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:01:47 dave 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:01:47 dave macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:01:47 dave 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:01:47 dave 30utility: debug: /dev/sda6 is not a FAT partition: exiting
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:01:47 dave 83haiku: debug: /dev/sda6 is not a BeFS partition: exiting
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:01:47 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
May 19 16:01:47 dave 10freedos: debug: /dev/sdb1 is a FAT32 partition
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
May 19 16:01:47 dave 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
May 19 16:01:47 dave macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
May 19 16:01:47 dave 20microsoft: debug: /dev/sdb1 is a FAT32 partition
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
May 19 16:01:47 dave 30utility: debug: /dev/sdb1 is a FAT32 partition
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
May 19 16:01:47 dave 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/90bsd-distro on mounted /dev/sdb1
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
May 19 16:01:47 dave os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
May 19 16:01:47 dave ubiquity[4212]: debconffilter_done: ubi-timezone (current: ubi-timezone)
May 19 16:01:47 dave ubiquity[4212]: Step_before = stepLocation
May 19 16:01:48 dave ubiquity[4212]: switched to page console_setup
May 19 16:01:49 dave ubiquity[4212]: log-output -t ubiquity setxkbmap -model pc105 -layout tr -option  -option lv3:ralt_switch
May 19 16:01:58 dave ubiquity: Your console font configuration will be updated the next time your system
May 19 16:01:58 dave ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
May 19 16:01:58 dave ubiquity[4212]: log-output -t ubiquity setxkbmap -model pc105 -layout tr -option 
May 19 16:01:58 dave ubiquity[4212]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
May 19 16:01:58 dave ubiquity[4212]: Step_before = stepKeyboardConf
May 19 16:01:58 dave ubiquity[4212]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
May 19 16:01:58 dave ubiquity[4212]: Step_before = stepKeyboardConf
May 19 16:01:59 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
May 19 16:02:00 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:02:00 dave 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:02:00 dave 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:02:00 dave macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:02:00 dave 20microsoft: debug: /dev/sda1 is a NTFS partition
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:02:00 dave 30utility: debug: /dev/sda1 is not a FAT partition: exiting
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:02:00 dave 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:02:00 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:02:00 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
May 19 16:02:01 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:02:01 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:02:01 dave 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
May 19 16:02:01 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:02:01 dave 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
May 19 16:02:01 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:02:01 dave macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
May 19 16:02:01 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:02:01 dave 20microsoft: debug: /dev/sda2 is a NTFS partition
May 19 16:02:02 dave 20microsoft: result: /dev/sda2:Windows 7 (data):Windows:chain
May 19 16:02:02 dave 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:02:02 dave os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 19 16:02:02 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
May 19 16:02:02 dave 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
May 19 16:02:02 dave os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 19 16:02:02 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
May 19 16:02:03 dave 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:02:03 dave 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:02:03 dave 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:02:03 dave macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:02:03 dave 20microsoft: debug: /dev/sda5 is a NTFS partition
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:02:03 dave 30utility: debug: /dev/sda5 is not a FAT partition: exiting
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:02:03 dave 83haiku: debug: /dev/sda5 is not a BeFS partition: exiting
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:02:03 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:02:03 dave os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
May 19 16:02:04 dave 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
May 19 16:02:04 dave 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
May 19 16:02:04 dave 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
May 19 16:02:04 dave macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
May 19 16:02:04 dave 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
May 19 16:02:04 dave 30utility: debug: /dev/sda6 is not a FAT partition: exiting
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
May 19 16:02:04 dave 83haiku: debug: /dev/sda6 is not a BeFS partition: exiting
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
May 19 16:02:04 dave 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
May 19 16:02:05 dave 10freedos: debug: /dev/sdb1 is a FAT32 partition
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
May 19 16:02:05 dave 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
May 19 16:02:05 dave macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
May 19 16:02:05 dave 20microsoft: debug: /dev/sdb1 is a FAT32 partition
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
May 19 16:02:05 dave 30utility: debug: /dev/sdb1 is a FAT32 partition
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
May 19 16:02:05 dave 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/90bsd-distro on mounted /dev/sdb1
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
May 19 16:02:05 dave os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
May 19 16:02:05 dave migration-assistant: info: setting ostype from: '/dev/sda2:Windows 7 (data):Windows:chain'
May 19 16:02:05 dave migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
May 19 16:02:05 dave ntfs-3g[16763]: Version 2012.1.15AR.1 external FUSE 28
May 19 16:02:05 dave ntfs-3g[16763]: Mounted /dev/sda2 (Read-Write, label "", NTFS 3.1)
May 19 16:02:05 dave ntfs-3g[16763]: Cmdline options: rw,umask=0022,nls=utf8
May 19 16:02:05 dave ntfs-3g[16763]: Mount options: rw,nls=utf8,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sda2,blkdev,blksize=4096
May 19 16:02:05 dave ntfs-3g[16763]: Global ownership and permissions enforced, configuration type 7
profilesdir: /mnt/migrationassistant/Users
profilesdir: /mnt/migrationassistant/Users
May 19 16:02:29 dave ubiquity[4212]: Reverting lockdown of the desktop environment.
May 19 16:02:30 dave activate-dmraid: No Serial ATA RAID disks detected
May 19 16:02:32 dave ubiquity: umount: /target: device is busy.
May 19 16:02:32 dave ubiquity:         (In some cases useful info about processes that use
May 19 16:02:32 dave ubiquity:          the device is found by lsof(8) or fuser(1))
May 19 16:02:32 dave ubiquity[4212]: debconffilter_done: ubi-partman (current: ubi-partman)
May 19 16:02:36 dave ubiquity[4212]: dbfilter_handle_status: ('ubi-partman', 10)
May 19 16:04:15 dave ubiquity[4212]: debconffilter_done: ubiquity.components.install (current: None)
```

My username on Ubuntu is "dave".

I also upload my all log files ( var/log ) here : h t t p s : / / r a p i d s h a r e.com/files/862826057/log.7z (psw: 123456789)

---

### Post by Fragadelic on 2012-05-19
According to your log it looks like gdm wasn't setup correctly.  Can you post your gdm config files?

---

### Post by pelerin21 on 2012-05-20
> **Fragadelic said:**
> According to your log it looks like gdm wasn't setup correctly.  Can you post your gdm config files?

My all gdm config files (before create backup) are here: h t t p s : / / r a p i d s h a r e . c om/files/1903168253/configiles.7z (psw: 123456789)

You are talking about Gnome, so I need to say that I did all thinks here before make a backup (the system works perfect):

[http://linux-software-news-tutorials.blogspot.com/2012/04/totally-remove-unity-from-ubuntu-1204.html](http://linux-software-news-tutorials.blogspot.com/2012/04/totally-remove-unity-from-ubuntu-1204.html)

[http://blog.linuxhaber.com/unityye-veda-veya-ubuntu-12-04-altinda-unity-temizligi/](http://blog.linuxhaber.com/unityye-veda-veya-ubuntu-12-04-altinda-unity-temizligi/)

I try to start the installation of custom Ubuntu from Gnome Shell, Gnome (without effect), gnome normally session. But I face the same problem (on two machines).

---

### Post by Fragadelic on 2012-05-20
With gdm, you will need to setup your default xsession so the system knows which one to use.

It is set in /etc/alternatives and is the x-session-manager link.  You can change it by using update-alternatives.

---

### Post by traditionalist on 2012-05-24
Well, remastersys stopped working.  I think I found the reason, it is not loading the right Isolinux package.

I posted on your forum with some results.  I can force an image to boot properly by changing the isolinux on the disk, but that does not work properly, it merely makes the image bootable.

Any ideas would be most welcome. This software is brilliant  and I would like to have it working again.

---

### Post by Fragadelic on 2012-05-24
Check my latest 3.0.3 package as there is a fix in there for usb booting due to isolinux.

---

### Post by pelerin21 on 2012-05-24
> **Fragadelic said:**
> With gdm, you will need to setup your default xsession so the system knows which one to use.

It is set in /etc/alternatives and is the x-session-manager link.  You can change it by using update-alternatives.

update-alternatives command asks me about thinks which have alternatives. But some of them does not have any alternatives. One of them was x-session-manager:

```
There is only one alternative in link group x-session-manager: /usr/bin/gnome-session
Nothing to configure.
```

---

### Post by pelerin21 on 2012-05-28
@Fragadelic Are you sure my problem is about GDM? I am waiting for you help :confused:

---

### Post by Fragadelic on 2012-05-28
No I'm not sure.  I've been working with traditionlist on his issue and he has made a successful remaster from a regular install with only the basics.  I've asked him to document each step mto see where he went wrong.

I've used remastersys on all the major desktops in 12.04 - lxde, xfce, kde, gnome3, unity, and mate and all were fully successful so we need to figure out where you went wrong.

You could also try replacing gdm with lightdm and see if that helps.  It could be that the casper code for gdm is bad which wouldn't surprise my since ubuntu by default uses lightdm now and they probably haven't tested gdm compatibility but this is only my speculation.

---

### Post by pelerin21 on 2012-06-04
> **Fragadelic said:**
> Check my latest 3.0.3 package as there is a fix in there for usb booting due to isolinux.

There is no 3.0.3 here: [http://www.remastersys.com/downloads/](http://www.remastersys.com/downloads/)

---

### Post by Fragadelic on 2012-06-04
You'll have to get it from my repository.

---

### Post by pelerin21 on 2012-06-05
> **Fragadelic said:**
> You'll have to get it from my repository.

I re-install Ubuntu 12.04. This time I did not remove Unity. But I face exactly the same problem.

I try this: [http://fir3net.com/Debian-/-Ubuntu/ubuntu-ubiquity-error-qthe-username-you-entered-is-invalidq.html](http://fir3net.com/Debian-/-Ubuntu/ubuntu-ubiquity-error-qthe-username-you-entered-is-invalidq.html)

But It does not work. This time the installation strted but the windows size was very small that I even could not click anything.

----------------------

I make the remastersys backup from inside of VirtualBox (4.1.x). I try the custom-backup.iso on my other desktop machine. It gives me the error that I explain it.

But today I try the iso if it will install on the VirtualBox. And it worked.

I could not understand why the iso does not work on other machines? I remeber that my old (11.10, 11.04, 10.10...) backups worked on all machines perfect.

---

### Post by Fragadelic on 2012-06-05
You have something messed up on your system.  Please explain everything you did after the initial install so we can figure out what you did wrong.

---

### Post by pelerin21 on 2012-06-05
> **Fragadelic said:**
> You have something messed up on your system.  Please explain everything you did after the initial install so we can figure out what you did wrong.

I format the parttion and I install Ubuntu 12.04. Aftr the installation I did all updates.
I remove the packages from synaptic:

```

rhythmbox
all games
ubuntu one

```

I install these packages from synaptic:

```

bleachbit
calibre
cheese
chromium-browser
fbreader
gimp
glipper
gnome-shell
gnome-tweak-tool
gparted
grabc
hardinfo
k3b
kalgebra
libreoffice-base
mythtv
numlockx
openjdk 7
pyrenamer
recol
skanlite
subtitleeditor
tesseract-ocr
tesseract-ocr-eng
testdisk
transmageddon
ultracopier
unetbootin
virtualbox
vlc

```

And I install these from deb packages (not from synaptic):

```

bleachbit bonuspack
ubuntu tweak

```

I install the remastersys at the end. And I get a backup. 

I restart every time after installation of any step. Nothing else. I did not change anything on system. I even did not change the wallpaper. 

I use also bleachbit to clena the system. But with bleachbit latest version I had use 11.10 + 11.04 and olders versions of Ubuntu, and I had a perfect remastered backup which works on my all machines.

My Ubuntu was inside on VirtualBox 4.x. When I put the backup iso inside a USB, the USB starts properly and the installation is properly inside on VirtualBox. The USB also starts properly on my other machine (which works with 11.10 remastered backup iso and 12.04(clean) ) but it gives the error on startup of installation (which we had disccuss it on our older messages).

Additional note: I was making exactly the same steps, I was install exactly the same apps before making a backup wtih remastersys on my Ubuntu 11.10 + 11.04 and older versions...

---

### Post by Fragadelic on 2012-06-07
What ppa's do you have on your system?  I just recently found out that there are some ppa's that have caused problems as they contain apps/libs that cause casper/ubiquity to fail.

---

### Post by pelerin21 on 2012-06-08
> **Fragadelic said:**
> What ppa's do you have on your system?  I just recently found out that there are some ppa's that have caused problems as they contain apps/libs that cause casper/ubiquity to fail.

I did not add any ppa on my system. I don't know even what is ppa exactly. I write what did to system on my last meesage (I did not do anything extra what did I write). I did not change even the wallpaper of system.

---

### Post by pelerin21 on 2012-06-15
Any news :confused:

---

### Post by Fragadelic on 2012-06-15
I have no idea what is wrong on your system.  Put the iso up somewhere so I can download it and try.  That is about the only way I can help you now.  I'll actually have to take a look at it myself.

You can also try running ubiquity in debug mode to see what other messages it pops up.

Do me a favour as well, if you are going to ask ahgain about stuff like this please post your current status including the problem you are having.  I don't have time to go reading old posts and I'm working on a pile of things at the same time so I have no idea what your original issue is.

If you post on my forum with a proper thread title that would make it much easier for me.

---

### Post by pelerin21 on 2012-06-16
> **Fragadelic said:**
> 
Do me a favour as well, if you are going to ask ahgain about stuff like this please post your current status including the problem you are having.  I don't have time to go reading old posts and I'm working on a pile of things at the same time so I have no idea what your original issue is.

If you post on my forum with a proper thread title that would make it much easier for me.

Okey...

---

### Post by pelerin21 on 2012-06-24
Hi Fragadelic,

I solve the problem using --no-migration-assistant parameter for ubiquity.

Now I have a different problem: 

I can not click "continue" button because it is always disabled on "choose a picture" step of installation.

The same iso does not asked "chose a picture" step on my desktop, but the same iso asks on my laptop :(

---

