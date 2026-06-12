---
title: "Remastersys 3.0.2-1 released supporting Ubuntu Lucid up to Precise"
date: 2012-04-28
forum: The Cafe
---

### Post by Fragadelic on 2012-04-28
Most notable changes are:

New official gui that has a log viewer built in.
Gui package now split off from the base cli package.
Precise support.

You can see more details and screenshots on the newly updated website - [http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

Packages you will now see in the repository:

remastersys - base remastersys package cli only - you must install this
remastersys-gui - new gui starting with precise - may not work on older versions prior to 11.10
remastersys-gtk - pygtk gui that should work on lucid and up to and including precise

Splitting them off means you can just install the cli remastersys package as it is the base working package anyway.  If you prefer not to see remastersys on the menu this is all you need.

Installing either remastersys-gui or remastersys-gtk will provide you with the options to customize the live boot background picture, the system grub background pciture, create a simple plymouth theme and copy user settings to /etc/skel so they are default for your system and live iso.

The Manual Method

As root - issue 'sudo su' in the terminal window prior to the following command.

Download and apply the repository gpg key.

wget -O - [http://www.remastersys.com/ubuntu/remastersys.gpg.key](http://www.remastersys.com/ubuntu/remastersys.gpg.key) | apt-key add -

Add the following line that corresponds to your version of Ubuntu to your /etc/apt/sources.list

#Remastersys Lucid
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) lucid main

#Remastersys Maverick
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) maverick main

#Remastersys Natty
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main

#Remastersys Oneiric
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) oneiric main

#Remastersys Precise
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) precise main

Now just apt-get update or reload in Synaptic to have the new Remastersys signed repository ready to use!

Contact me if you would like to translate the new gui into your native language and I will provide you with the po file to translate.  When I get a few more translations I will make a remastersys-gui-translations package that includes the translations and add it to the repository.

---

### Post by Fragadelic on 2012-04-30
IMPORTANT NOTE for Precise users:


I have been notified by Canonical that there is currently a bug in casper - [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/984276](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/984276)

This affects remastersys users as you need casper for the live boot. I'll be keeping an eye on this as they work to correct the situation.

They are working on fixing the issue.

---

### Post by glxtreme on 2012-05-01
Hello Fragadelic, Great Tool, i want to thank you for picking development up again.

To tell you the truth my first encounter with this kind of soft was Relinux, but i could never use it and remastersys was the original and final solution.

I've managed to create my one and only successful dist with remastersys 2.0.18-1 on 11.10.
i couldn't get the dist to boot the installation directly.

I'm still trying to make it work with 3.0.2-1, but can't get it to boot the installation directly and if i install it from the live boot, installation crashes on grub install.

Live CD Works fine!
Thank you again for this magnificent software!:)

---

### Post by Fragadelic on 2012-05-01
Is this a system you have upgraded along the way or was it a regular 11.10 install?  Grub issues tend to happen when you upgrade from older versions and haven't let it upgrade to grub 2.  Ubuntu 10.04(lucid) and newer must have grub2 as that is the only thing the Ubuntu ubiquity installer will setup properly.

Make sure you get the 3.0.2 version from my repo.  You might have to use remastersys-gtk instead of remastersys-gui but you have to first make sure you upgraded the base remastersys to 3.0.2.

---

### Post by glxtreme on 2012-05-01
It's a brand new 11.10, (my first approach to open source :redface:) with the latest updates applied but i haven't upgraded to 12.04 yet.

The only issue i'm experiencing now with 3.0.2 it's that i have to create a new administrator user from the live boot to install the dist since i can't boot the install from the initial splash screen.

When i select install on the splash screen, it takes me directly to the live boot.

Thank you for the quick response.

Regards

---

### Post by Fragadelic on 2012-05-01
Did you by chance set auto login on your original system?  If you did, you'll have to undo that.  Can you post your most recent remastersys.log.  It should be in /home/remastersys/remastersys

---

### Post by glxtreme on 2012-05-01
No, i did not set auto login.
Sure, i'm uploading it right now.
Thanks!

---

### Post by Fragadelic on 2012-05-02
Looking at your remastersys.log leads me to believe you either have too much in /etc/skel or there are config files with user specific permissions in it.

What is the output of "sudo du -sh /etc/skel"

Also post the output of this command - replace username with your user you copied the config files from
sudo grep -R "username" /etc/skel

---

### Post by glxtreme on 2012-05-02
Hi,

Attached is the output of the commands.

Thanks!

---

### Post by Fragadelic on 2012-05-02
You have user specific items in /etc/skel which is making the user creation fail.

What you should do if you want to have more than I normally copy into it with my tool, is to copy your other things over first and then run my user settings copy from the menu which will clean up /etc/skel for you.  Anything that is a problem will be removed by my remastersys-skelcopy.

---

### Post by glxtreme on 2012-05-02
OK Thank you for the tip, i'll try it that way.

So that is what also leads the install option to boot the live?

Thank you Fragadelic for all the help.

---

### Post by Fragadelic on 2012-05-02
If it can't create a live user, there is no user on the system and nothing is run as root so to answer your question, yes.

There may also be something else but you won't be able to tell until the live user is created.

---

### Post by glxtreme on 2012-05-02
OK, I'm going to try create a new Dist without specifying any user to see what happens and get back to you.

Should i change anything to revert any damage i might have done to etc/skel ?

Thank you!

---

### Post by Fragadelic on 2012-05-02
I would remove everything from /etc/skel and just use my skelcopy from the menu to do it for you.  This will keep the skeleton small and only have what is needed for normal configuration options while leaving out config files that will cause issues.

---

### Post by xx58 on 2012-05-02
I make dist DVD and then try to install straight, but it takes and ending in live boot. Then need to user name and password, so I put both and ending up always same: " Invalid password". Just don't know what can be problem?

---

### Post by Fragadelic on 2012-05-03
xx58 - can you post your remastersys.log?

---

### Post by xx58 on 2012-05-03
Distribution Mode Selected  
 Enabling remastersys-firstboot  
 Checking filesystem type of the Working Folder  
 /home/remastersys/remastersys is on a ext4 filesystem  
 Making sure popularity contest is not installed  
 Installing the Ubiquity GTK frontend  
 Checking if the /home/remastersys/remastersys folder has been created  
 Creating /home/remastersys/remastersys folder tree  
 Creating /home/remastersys/remastersys/ISOTMP folder tree  
 Copying /var and /etc to temp area and excluding extra files  ... this will take a while so be patient  
 Cleaning up files not needed for the live in /home/remastersys/remastersys/dummysys  
 Cleaning up passwd, group, shadow and gshadow files for the live system  
 Making sure adduser and autologin functions of casper are set properly  
 Copying memtest86+ for the live system  
 Creating isolinux setup for the live system  
 Checking the ARCH of the system and setting the README.diskdefines file  
 Creating filesystem.manifest and filesystem.manifest-desktop  
 Creating the casper.conf file.  
 Checking and setting user-setup-apply for the live system  
 Setting up casper and ubiquity options for dist mode  
 Creating a new initial ramdisk for the live system  
 Copying your kernel and initrd for the livecd  
 Creating filesystem.squashfs   ... this will take a while so be patient  
 Adding stage 1 files/folders that the livecd requires  
 Adding stage 2 files/folders that the livecd requires  
 ------------------------------------------------------ 
 Mount information  
 /dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr)  
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
 gvfs-fuse-daemon on /home/alain/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alain)  
 /dev/mmcblk0p1 on /media/B5D2-D5BA type vfat (ro,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks) 
 ------------------------------------------------------ 
 Disk size information  
 Filesystem      Size  Used Avail Use% Mounted on  
 /dev/sda1       108G   33G   70G  32% / 
 udev            2.0G  4.0K  2.0G   1% /dev  
 tmpfs           804M  908K  803M   1% /run  
 none            5.0M     0  5.0M   0% /run/lock  
 none            2.0G  260K  2.0G   1% /run/shm  
 /dev/mmcblk0p1  963M   91M  873M  10% /media/B5D2-D5BA  
 ------------------------------------------------------ 
 Casper Script info  
 total 148  
 -rwxr-xr-x 1 root root  297 Apr 18 12:17 01integrity_check  
 -rwxr-xr-x 1 root root  467 Apr 18 12:17 05mountpoints  
 -rwxr-xr-x 1 root root  571 Apr 18 12:17 07remove_oem_config  
 -rwxr-xr-x 1 root root  400 Apr 18 12:17 12fstab  
 -rwxr-xr-x 1 root root  830 Apr 18 12:17 13swap  
 -rwxr-xr-x 1 root root 1221 Apr 18 12:17 14locales  
 -rwxr-xr-x 1 root root 2920 Apr 18 12:17 15autologin  
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
 -rwxr-xr-x 1 root root 3939 Apr 18 12:17 25adduser  
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
 LIVEUSER="custom"  
 

 

 # Here you can change the name of the livecd/dvd label  
 LIVECDLABEL="Custom Live CD"  
 

 

 # Here you can change the name of the ISO file that is created  
 CUSTOMISO="custom-$1.iso"  
 

 

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
 

 export USERNAME="custom"  
 export USERFULLNAME="Live session user"  
 export HOST="custom"  
 export BUILD_SYSTEM="Ubuntu"  
 ------------------------------------------------------ 
 /etc/passwd info  
 root:0:0:root:/root:/bin/bash  
 daemon:1:1:daemon:/usr/sbin:/bin/sh  
 bin:2:2:bin:/bin:/bin/sh  
 sys:3:3:sys:/dev:/bin/sh  
 sync:4:65534:sync:/bin:/bin/sync  
 games:5:60:games:/usr/games:/bin/sh  
 man:6:12:man:/var/cache/man:/bin/sh  
 lp:7:7:lp:/var/spool/lpd:/bin/sh  
 mail:8:8:mail:/var/mail:/bin/sh  
 news:9:9:news:/var/spool/news:/bin/sh 
 uucp:10:10:uucp:/var/spool/uucp:/bin/sh 
 proxy:13:13roxy:/bin:/bin/sh  
 www-data:33:33:www-data:/var/www:/bin/sh 
 backup:34:34:backup:/var/backups:/bin/sh 
 list:38:38:Mailing List Manager:/var/list:/bin/sh  
 irc:39:39:ircd:/var/run/ircd:/bin/sh  
 gnats:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh  
 libuuid:100:101::/var/lib/libuuid:/bin/sh 
 syslog:101:103::/home/syslog:/bin/false 
 messagebus:102:104::/var/run/dbus:/bin/false 
 colord:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false  
 lightdm:104:109:Light Display Manager:/var/lib/lightdm:/bin/false  
 avahi-autoipd:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false  
 avahi:106:114:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false  
 usbmux:107:46:usbmux daemon,,,:/home/usbmux:/bin/false  
 kernoops:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false  
 pulse:109:118ulseAudio daemon,,,:/var/run/pulse:/bin/false  
 rtkit:110:121:RealtimeKit,,,:/proc:/bin/false 
 saned:111:122::/home/saned:/bin/false 
 speech-dispatcher:112:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh  
 hplip:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false  
 whoopsie:114:124::/nonexistent:/bin/false 
 gdm:115:127:Gnome Display Manager:/var/lib/gdm:/bin/false  
 debian-xfs:116:128::/nonexistent:/bin/false 
 nobody:65534:65534:nobody:/nonexistent:/bin/sh 
 ------------------------------------------------------ 
 /etc/group info  
 root:0:  
 daemon:1:  
 bin:2:  
 sys:3:  
 adm:4:  
 tty:5:  
 disk:6:  
 lp:7:  
 mail:8:  
 news:9:  
 uucp:10:  
 man:12:  
 proxy:13:  
 kmem:15:  
 dialout:20:  
 fax:21:  
 voice:22:  
 cdrom:24:  
 floppy:25:  
 tape:26:  
 sudo:27:  
 audio:29ulse  
 dip:30:  
 www-data:33:  
 backup:34:  
 operator:37:  
 list:38:  
 irc:39:  
 src:40:  
 gnats:41:  
 shadow:42:  
 utmp:43:  
 video:44:  
 sasl:45:  
 plugdev:46:  
 staff:50:  
 games:60:  
 users:100:  
 libuuid:101:  
 crontab:102:  
 syslog:103:  
 messagebus:104:  
 fuse:105:  
 bluetooth:106:  
 scanner:107:  
 colord:108:  
 lightdm:109:  
 nopasswdlogin:110:  
 mlocate:111:  
 ssh:112:  
 avahi-autoipd:113:  
 avahi:114:  
 netdev:115:  
 lpadmin:116:  
 ssl-cert:117:  
 pulse:118:  
 pulse-access:119:  
 utempter:120:  
 rtkit:121:  
 saned:122:  
 sambashare:123:  
 whoopsie:124:  
 winbindd_priv:125:  
 pcscd:126:  
 gdm:127:  
 debian-xfs:128:  
 nogroup:65534:  
 ------------------------------------------------------ 
 /etc/X11/default-display-manager info  
 /usr/sbin/lightdm  
 ------------------------------------------------------ 
 /etc/skel info  
 /etc/skel  
 /etc/skel/.local  
 /etc/skel/.local/share  
 /etc/skel/.local/share/gsettings-data-convert 
 /etc/skel/.local/share/vlc  
 /etc/skel/.local/share/vlc/ml.xspf  
 /etc/skel/.local/share/icons  
 /etc/skel/.local/share/icons/hicolor  
 /etc/skel/.local/share/icons/hicolor/48x48 
 /etc/skel/.local/share/icons/hicolor/48x48/apps 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/application-x-shockwave-flash.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/application-x-wine-extension-its.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/8ADA_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/AF10_Terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/0FB9_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/3457_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/FB4C_iexplore.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/02FD_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/1690_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/AB7B_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/C4FC_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/AEA6_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/A35F_hh.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/A53A_ppicon.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/DFE9_Icon.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/109E_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/5B5A_Terminal.2.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/application-x-wine-extension-msp.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/1E64_notepad.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/07BE_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/2081_SmartInstaller.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/4137_winhlp32.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/7A71_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/39FA_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/EBE1_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/15F6_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/1CD8_rundll32.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/2EF4_wordpad.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/AE33_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/7765_winebrowser.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/DBB8_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/1091_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/4365_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32 
 /etc/skel/.local/share/icons/hicolor/32x32/apps 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/application-x-shockwave-flash.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/application-x-wine-extension-its.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/8ADA_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/AF10_Terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/0FB9_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/3457_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/FB4C_iexplore.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/CF7E_Uninstall.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/02FD_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/1690_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/AB7B_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/C4FC_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/AEA6_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/A35F_hh.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/A53A_ppicon.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/DFE9_Icon.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/109E_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/5B5A_Terminal.2.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/22AB_Uninstall.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/application-x-wine-extension-msp.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/1E64_notepad.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/07BE_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/2081_SmartInstaller.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/4137_winhlp32.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/7A71_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/39FA_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/EBE1_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/15F6_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/88EB_Uninstall.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/1CD8_rundll32.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/2EF4_wordpad.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/AE33_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/7765_winebrowser.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/DBB8_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/1091_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/4365_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16 
 /etc/skel/.local/share/icons/hicolor/16x16/apps 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/application-x-shockwave-flash.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/application-x-wine-extension-its.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/8ADA_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/AF10_Terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/0FB9_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/3457_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/FB4C_iexplore.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/CF7E_Uninstall.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/02FD_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/1690_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/AB7B_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/C4FC_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/AEA6_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/A35F_hh.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/A53A_ppicon.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/DFE9_Icon.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/109E_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/5B5A_Terminal.2.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/22AB_Uninstall.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/application-x-wine-extension-msp.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/1E64_notepad.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/07BE_homepage.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/4137_winhlp32.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/7A71_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/39FA_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/EBE1_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/15F6_dde-sample.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/88EB_Uninstall.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/1CD8_rundll32.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/2EF4_wordpad.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/AE33_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/7765_winebrowser.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/DBB8_logs.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/1091_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/4365_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/24x24 
 /etc/skel/.local/share/icons/hicolor/24x24/apps 
 /etc/skel/.local/share/icons/hicolor/24x24/apps/0FB9_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/24x24/apps/5B5A_Terminal.2.png 
 /etc/skel/.local/share/icons/hicolor/64x64 
 /etc/skel/.local/share/icons/hicolor/64x64/apps 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/AF10_Terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/0FB9_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/02FD_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/1690_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/1091_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/4365_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/128x128 
 /etc/skel/.local/share/icons/hicolor/128x128/apps 
 /etc/skel/.local/share/icons/hicolor/128x128/apps/A53A_ppicon.0.png 
 /etc/skel/.local/share/zeitgeist  
 /etc/skel/.local/share/zeitgeist/fts.index 
 /etc/skel/.local/share/zeitgeist/fts.index/position.DB 
 /etc/skel/.local/share/zeitgeist/fts.index/termlist.baseA 
 /etc/skel/.local/share/zeitgeist/fts.index/position.baseB 
 /etc/skel/.local/share/zeitgeist/fts.index/postlist.baseB 
 /etc/skel/.local/share/zeitgeist/fts.index/postlist.baseA 
 /etc/skel/.local/share/zeitgeist/fts.index/iamchert 
 /etc/skel/.local/share/zeitgeist/fts.index/record.DB 
 /etc/skel/.local/share/zeitgeist/fts.index/record.baseB 
 /etc/skel/.local/share/zeitgeist/fts.index/position.baseA 
 /etc/skel/.local/share/zeitgeist/fts.index/termlist.baseB 
 /etc/skel/.local/share/zeitgeist/fts.index/flintlock 
 /etc/skel/.local/share/zeitgeist/fts.index/termlist.DB 
 /etc/skel/.local/share/zeitgeist/fts.index/record.baseA 
 /etc/skel/.local/share/zeitgeist/bb.fts.index 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/position.DB 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/termlist.baseA 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/position.baseB 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/postlist.baseB 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/postlist.baseA 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/iamchert 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/record.DB 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/postlist.DB 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/record.baseB 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/position.baseA 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/termlist.baseB 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/flintlock 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/termlist.DB 
 /etc/skel/.local/share/zeitgeist/bb.fts.index/record.baseA 
 /etc/skel/.local/share/zeitgeist/activity.sqlite-shm 
 /etc/skel/.local/share/zeitgeist/activity.sqlite.bck 
 /etc/skel/.local/share/.converted-launchers 
 /etc/skel/.local/share/icc  
 /etc/skel/.local/share/icc/edid-d97503083b4f8eecadb82407c8a2000b.icc 
 /etc/skel/.local/share/icc/edid-8b0ff841a2c836e4522824f3522ee8a7.icc 
 /etc/skel/.local/share/eog-wallpaper.jpg 
 /etc/skel/.local/share/mime  
 /etc/skel/.local/share/mime/globs  
 /etc/skel/.local/share/mime/version  
 /etc/skel/.local/share/mime/icons  
 /etc/skel/.local/share/mime/globs2  
 /etc/skel/.local/share/mime/types  
 /etc/skel/.local/share/mime/subclasses  
 /etc/skel/.local/share/mime/aliases  
 /etc/skel/.local/share/mime/generic-icons 
 /etc/skel/.local/share/mime/treemagic  
 /etc/skel/.local/share/mime/XMLnamespaces 
 /etc/skel/.local/share/mime/text  
 /etc/skel/.local/share/mime/text/x-component.xml 
 /etc/skel/.local/share/mime/text/plain.xml 
 /etc/skel/.local/share/mime/packages  
 /etc/skel/.local/share/mime/packages/x-wine-extension-dll.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-its.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-sol.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-sor.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-htc.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-jfif.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-ini.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-vbs.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-msp.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-mfp.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-inf.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-dxr.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-cpl.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-hlp.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-dib.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-dir.xml 
 /etc/skel/.local/share/mime/image  
 /etc/skel/.local/share/mime/image/jpeg.xml 
 /etc/skel/.local/share/mime/image/bmp.xml 
 /etc/skel/.local/share/mime/application 
 /etc/skel/.local/share/mime/application/x-wine-extension-its.xml 
 /etc/skel/.local/share/mime/application/x-director.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-ini.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-vbs.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-msp.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-inf.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-cpl.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-hlp.xml 
 /etc/skel/.local/share/mime/application/x-shockwave-flash.xml 
 /etc/skel/.local/share/mime/application/x-msdownload.xml 
 /etc/skel/.local/share/mime/magic  
 /etc/skel/.local/share/telepathy  
 /etc/skel/.local/share/telepathy/mission-control 
 /etc/skel/.local/share/telepathy/mission-control/accounts-goa.cfg 
 /etc/skel/.local/share/rhythmbox  
 /etc/skel/.local/share/rhythmbox/podcast-timestamp 
 /etc/skel/.local/share/rhythmbox/playlists.xml 
 /etc/skel/.local/share/ubuntuone  
 /etc/skel/.local/share/ubuntuone/syncdaemon 
 /etc/skel/.local/share/ubuntuone/syncdaemon/fsm 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1332986027939601.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1335868995146378.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1332985477196525.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1331410857245452.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1335859161343404.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1333771012983479.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1334166009269956.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1333910274082903.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1331410857369151.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1334234889343081.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1335947944697574.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/metadata_version 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm/shared 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm/.version 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm/udfs 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm/shares 
 /etc/skel/.local/share/ubuntuone/shares 
 /etc/skel/.local/share/desktop-directories 
 /etc/skel/.local/share/desktop-directories/wine-Programs-FX Solutions - MetaTrader.directory  
 /etc/skel/.local/share/desktop-directories/wine-Programs.directory 
 /etc/skel/.local/share/desktop-directories/wine-Programs-PartyPoker.directory 
 /etc/skel/.local/share/desktop-directories/wine-Programs-FX Solutions UK - MetaTrader.directory  
 /etc/skel/.local/share/desktop-directories/wine-wine.directory 
 /etc/skel/.local/share/desktop-directories/X-GNOME-Other.directory 
 /etc/skel/.local/share/desktop-directories/wine-Programs-FXCM MetaTrader 4.directory  
 /etc/skel/.local/share/desktop-directories/wine-Programs-Games.directory 
 /etc/skel/.local/share/desktop-directories/wine-Programs-Luvin Poker.directory  
 /etc/skel/.local/share/desktop-directories/wine-Programs-MetaTrader 4 at FOREX.com.directory  
 /etc/skel/.local/share/applications  
 /etc/skel/.local/share/applications/ubuntu-software-center.desktop 
 /etc/skel/.local/share/applications/mimeapps.list 
 /etc/skel/.local/share/applications/wine 
 /etc/skel/.local/share/applications/wine/Programs 
 /etc/skel/.local/share/applications/wine/Programs/PartyPoker 
 /etc/skel/.local/share/applications/wine/Programs/PartyPoker/Uninstall PartyPoker.desktop  
 /etc/skel/.local/share/applications/wine/Programs/Games 
 /etc/skel/.local/share/applications/wine/Programs/FXCM MetaTrader 4  
 /etc/skel/.local/share/applications/wine/Programs/MetaTrader 4 at FOREX.com  
 /etc/skel/.local/share/applications/wine/Programs/MetaTrader 4 at FOREX.com/MetaEditor.desktop  
 /etc/skel/.local/share/applications/wine/Programs/MetaTrader 4 at FOREX.com/DDE Sample.desktop  
 /etc/skel/.local/share/applications/wine/Programs/MetaTrader 4 at FOREX.com/Journals.desktop  
 /etc/skel/.local/share/applications/wine/Programs/MetaTrader 4 at FOREX.com/Home Page.desktop  
 /etc/skel/.local/share/applications/wine/Programs/MetaTrader 4 at FOREX.com/Uninstall.desktop  
 /etc/skel/.local/share/applications/wine/Programs/MetaTrader 4 at FOREX.com/MetaTrader 4 at FOREX.com.desktop  
 /etc/skel/.local/share/applications/wine/Programs/FX Solutions - MetaTrader  
 /etc/skel/.local/share/applications/wine/Programs/FX Solutions UK - MetaTrader  
 /etc/skel/.local/share/applications/wine/Programs/FX Solutions UK - MetaTrader/FX Solutions UK - MetaTrader.desktop  
 /etc/skel/.local/share/applications/wine/Programs/FX Solutions UK - MetaTrader/MetaEditor.desktop  
 /etc/skel/.local/share/applications/wine/Programs/FX Solutions UK - MetaTrader/DDE Sample.desktop  
 /etc/skel/.local/share/applications/wine/Programs/FX Solutions UK - MetaTrader/Journals.desktop  
 /etc/skel/.local/share/applications/wine/Programs/FX Solutions UK - MetaTrader/Home Page.desktop  
 /etc/skel/.local/share/applications/wine/Programs/FX Solutions UK - MetaTrader/Uninstall.desktop  
 /etc/skel/.local/share/applications/wine/Programs/Luvin Poker  
 /etc/skel/.local/share/applications/wine/Programs/Luvin Poker/Uninstall Luvin Poker.desktop  
 /etc/skel/.local/share/applications/wine/Programs/Luvin Poker/Luvin Poker.desktop  
 /etc/skel/.local/share/applications/wine/Programs/Luvin Poker/Website.desktop  
 /etc/skel/.gconf  
 /etc/skel/.gconf/desktop  
 /etc/skel/.gconf/desktop/unity-2d  
 /etc/skel/.gconf/desktop/unity-2d/launcher 
 /etc/skel/.gconf/desktop/unity-2d/launcher/%gconf.xml 
 /etc/skel/.gconf/desktop/unity-2d/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome  
 /etc/skel/.gconf/desktop/gnome/url-handlers 
 /etc/skel/.gconf/desktop/gnome/url-handlers/mailto 
 /etc/skel/.gconf/desktop/gnome/url-handlers/mailto/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/url-handlers/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/background 
 /etc/skel/.gconf/desktop/gnome/background/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/peripherals 
 /etc/skel/.gconf/desktop/gnome/peripherals/keyboard 
 /etc/skel/.gconf/desktop/gnome/peripherals/keyboard/kbd 
 /etc/skel/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/peripherals/keyboard/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/peripherals/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/%gconf.xml 
 /etc/skel/.gconf/desktop/%gconf.xml  
 /etc/skel/.gconf/desktop/pgp  
 /etc/skel/.gconf/desktop/pgp/keyservers 
 /etc/skel/.gconf/desktop/pgp/keyservers/%gconf.xml 
 /etc/skel/.gconf/desktop/pgp/%gconf.xml 
 /etc/skel/.gconf/apps  
 /etc/skel/.gconf/apps/compiz-1  
 /etc/skel/.gconf/apps/compiz-1/plugins  
 /etc/skel/.gconf/apps/compiz-1/plugins/move 
 /etc/skel/.gconf/apps/compiz-1/plugins/move/screen0 
 /etc/skel/.gconf/apps/compiz-1/plugins/move/screen0/options 
 /etc/skel/.gconf/apps/compiz-1/plugins/move/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/plugins/move/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/plugins/move/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/plugins/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/general  
 /etc/skel/.gconf/apps/compiz-1/general/screen0 
 /etc/skel/.gconf/apps/compiz-1/general/screen0/options 
 /etc/skel/.gconf/apps/compiz-1/general/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/general/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/general/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/%gconf.xml 
 /etc/skel/.gconf/apps/onboard  
 /etc/skel/.gconf/apps/onboard/%gconf.xml 
 /etc/skel/.gconf/apps/update-notifier  
 /etc/skel/.gconf/apps/update-notifier/%gconf.xml 
 /etc/skel/.gconf/apps/deja-dup  
 /etc/skel/.gconf/apps/deja-dup/s3  
 /etc/skel/.gconf/apps/deja-dup/s3/%gconf.xml 
 /etc/skel/.gconf/apps/deja-dup/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus  
 /etc/skel/.gconf/apps/nautilus/desktop  
 /etc/skel/.gconf/apps/nautilus/desktop/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus/preferences 
 /etc/skel/.gconf/apps/nautilus/preferences/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus/icon_view 
 /etc/skel/.gconf/apps/nautilus/icon_view/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus/list_view 
 /etc/skel/.gconf/apps/nautilus/list_view/%gconf.xml 
 /etc/skel/.gconf/apps/eog  
 /etc/skel/.gconf/apps/eog/ui  
 /etc/skel/.gconf/apps/eog/ui/%gconf.xml 
 /etc/skel/.gconf/apps/eog/view  
 /etc/skel/.gconf/apps/eog/view/%gconf.xml 
 /etc/skel/.gconf/apps/eog/%gconf.xml  
 /etc/skel/.gconf/apps/gnome-system-log  
 /etc/skel/.gconf/apps/gnome-system-log/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1  
 /etc/skel/.gconf/apps/compizconfig-1/profiles 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2  
 /etc/skel/.gconf/apps/gedit-2/plugins  
 /etc/skel/.gconf/apps/gedit-2/plugins/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2/preferences 
 /etc/skel/.gconf/apps/gedit-2/preferences/ui 
 /etc/skel/.gconf/apps/gedit-2/preferences/ui/statusbar 
 /etc/skel/.gconf/apps/gedit-2/preferences/ui/statusbar/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2/preferences/ui/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2/preferences/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2/%gconf.xml 
 /etc/skel/.gconf/apps/nm-applet  
 /etc/skel/.gconf/apps/nm-applet/%gconf.xml 
 /etc/skel/.gconf/apps/panel3-applets  
 /etc/skel/.gconf/apps/panel3-applets/object_8 
 /etc/skel/.gconf/apps/panel3-applets/object_8/%gconf.xml 
 /etc/skel/.gconf/apps/panel3-applets/object_16 
 /etc/skel/.gconf/apps/panel3-applets/object_16/%gconf.xml 
 /etc/skel/.gconf/apps/panel3-applets/%gconf.xml 
 /etc/skel/.gconf/apps/evolution  
 /etc/skel/.gconf/apps/evolution/calendar 
 /etc/skel/.gconf/apps/evolution/calendar/notify 
 /etc/skel/.gconf/apps/evolution/calendar/notify/%gconf.xml 
 /etc/skel/.gconf/apps/evolution/calendar/%gconf.xml 
 /etc/skel/.gconf/apps/evolution/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash  
 /etc/skel/.gconf/apps/gnucash/window  
 /etc/skel/.gconf/apps/gnucash/window/pages 
 /etc/skel/.gconf/apps/gnucash/window/pages/register 
 /etc/skel/.gconf/apps/gnucash/window/pages/register/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/window/pages/account_tree 
 /etc/skel/.gconf/apps/gnucash/window/pages/account_tree/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/window/pages/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/window/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/history  
 /etc/skel/.gconf/apps/gnucash/history/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/dialogs  
 /etc/skel/.gconf/apps/gnucash/dialogs/new_user 
 /etc/skel/.gconf/apps/gnucash/dialogs/new_user/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/dialogs/tip_of_the_day 
 /etc/skel/.gconf/apps/gnucash/dialogs/tip_of_the_day/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/dialogs/open_save 
 /etc/skel/.gconf/apps/gnucash/dialogs/open_save/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/dialogs/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/%gconf.xml 
 /etc/skel/.gconf/apps/update-manager  
 /etc/skel/.gconf/apps/update-manager/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-settings  
 /etc/skel/.gconf/apps/gnome-settings/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-settings/gnome-search-tool 
 /etc/skel/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml 
 /etc/skel/.gconf/apps/%gconf.xml  
 /etc/skel/.gconf/apps/file-roller  
 /etc/skel/.gconf/apps/file-roller/listing 
 /etc/skel/.gconf/apps/file-roller/listing/%gconf.xml 
 /etc/skel/.gconf/apps/file-roller/ui  
 /etc/skel/.gconf/apps/file-roller/ui/%gconf.xml 
 /etc/skel/.gconf/apps/file-roller/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-terminal  
 /etc/skel/.gconf/apps/gnome-terminal/profiles 
 /etc/skel/.gconf/apps/gnome-terminal/profiles/Default 
 /etc/skel/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-terminal/profiles/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-terminal/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-search-tool 
 /etc/skel/.gconf/apps/gnome-search-tool/select 
 /etc/skel/.gconf/apps/gnome-search-tool/select/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-search-tool/%gconf.xml 
 /etc/skel/.gconf/apps/metacity  
 /etc/skel/.gconf/apps/metacity/window_keybindings 
 /etc/skel/.gconf/apps/metacity/window_keybindings/%gconf.xml 
 /etc/skel/.gconf/apps/metacity/global_keybindings 
 /etc/skel/.gconf/apps/metacity/global_keybindings/%gconf.xml 
 /etc/skel/.gconf/apps/metacity/general  
 /etc/skel/.gconf/apps/metacity/general/%gconf.xml 
 /etc/skel/.gconf/apps/metacity/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-screenshot  
 /etc/skel/.bashrc  
 /etc/skel/.profile  
 /etc/skel/.kde  
 /etc/skel/.kde/tmp-ubuntu  
 /etc/skel/.kde/share  
 /etc/skel/.kde/share/apps  
 /etc/skel/.kde/share/apps/kfileplaces  
 /etc/skel/.kde/share/apps/k3b  
 /etc/skel/.kde/share/apps/k3b/lastlog.log 
 /etc/skel/.kde/share/apps/kconf_update  
 /etc/skel/.kde/share/apps/kconf_update/log 
 /etc/skel/.kde/share/config  
 /etc/skel/.kde/share/config/phonondevicesrc 
 /etc/skel/.kde/share/config/kio_httprc  
 /etc/skel/.kde/share/config/katerc  
 /etc/skel/.kde/share/config/nepomukserverrc 
 /etc/skel/.kde/share/config/kuriikwsfilterrc 
 /etc/skel/.kde/share/config/kdedrc  
 /etc/skel/.kde/share/config/kcookiejarrc 
 /etc/skel/.kde/share/config/kdebugrc  
 /etc/skel/.kde/share/config/kdeglobals  
 /etc/skel/.kde/share/config/kioslaverc  
 /etc/skel/.kde/share/config/emaildefaults 
 /etc/skel/.kde/share/config/kconf_updaterc 
 /etc/skel/.kde/share/kde4  
 /etc/skel/.kde/share/kde4/services  
 /etc/skel/.gnome2  
 /etc/skel/.gnome2/accels  
 /etc/skel/.gnome2/accels/nautilus  
 /etc/skel/.gnome2/accels/gconf-editor  
 /etc/skel/.gnome2/nautilus-scripts  
 /etc/skel/.gnome2/keyrings  
 /etc/skel/.config  
 /etc/skel/.config/menus  
 /etc/skel/.config/menus/applications-merged 
 /etc/skel/.config/menus/applications-merged/wine-Programs-MetaTrader 4 at FOREX.com-MetaEditor.menu  
 /etc/skel/.config/menus/applications-merged/wine-PartyPoker.menu 
 /etc/skel/.config/menus/applications-merged/wine-Programs-FX Solutions UK - MetaTrader-Uninstall.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-FX Solutions UK - MetaTrader-Journals.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-Luvin Poker-Uninstall Luvin Poker.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-MetaTrader 4 at FOREX.com-Uninstall.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-PartyPoker-Uninstall PartyPoker.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-Games-PartyPoker.menu 
 /etc/skel/.config/menus/applications-merged/wine-Programs-FX Solutions UK - MetaTrader-DDE Sample.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-FX Solutions UK - MetaTrader-FX Solutions UK - MetaTrader.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-Luvin Poker-Website.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-Luvin Poker-Luvin Poker.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-MetaTrader 4 at FOREX.com-Journals.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-MetaTrader 4 at FOREX.com-Home Page.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-FX Solutions UK - MetaTrader-MetaEditor.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-MetaTrader 4 at FOREX.com-MetaTrader 4 at FOREX.com.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-MetaTrader 4 at FOREX.com-DDE Sample.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-PartyPoker-PartyPoker.menu 
 /etc/skel/.config/menus/applications-merged/wine-Programs-FX Solutions UK - MetaTrader-Home Page.menu  
 /etc/skel/.config/compiz-1  
 /etc/skel/.config/compiz-1/compizconfig 
 /etc/skel/.config/compiz-1/compizconfig/config 
 /etc/skel/.config/compiz-1/compizconfig/done_upgrades 
 /etc/skel/.config/gnome-disk-utility  
 /etc/skel/.config/gnome-disk-utility/ata-smart-ignore 
 /etc/skel/.config/update-notifier  
 /etc/skel/.config/update-notifier/hooks_seen 
 /etc/skel/.config/gnome-session  
 /etc/skel/.config/gnome-session/saved-session 
 /etc/skel/.config/vlc  
 /etc/skel/.config/vlc/vlcrc  
 /etc/skel/.config/nautilus  
 /etc/skel/.config/nautilus/desktop-metadata.M1V0DW 
 /etc/skel/.config/nautilus/desktop-metadata 
 /etc/skel/.config/software-center  
 /etc/skel/.config/software-center/softwarecenter.cfg 
 /etc/skel/.config/ibus  
 /etc/skel/.config/ibus/bus  
 /etc/skel/.config/eog  
 /etc/skel/.config/eog/accels  
 /etc/skel/.config/dconf  
 /etc/skel/.config/gnome-mplayer  
 /etc/skel/.config/gnome-mplayer/cover_art 
 /etc/skel/.config/gnome-mplayer/plugin  
 /etc/skel/.config/libreoffice  
 /etc/skel/.config/libreoffice/3  
 /etc/skel/.config/libreoffice/3/user  
 /etc/skel/.config/libreoffice/3/user/autocorr 
 /etc/skel/.config/libreoffice/3/user/template 
 /etc/skel/.config/libreoffice/3/user/database 
 /etc/skel/.config/libreoffice/3/user/database/biblio.odb 
 /etc/skel/.config/libreoffice/3/user/database/biblio 
 /etc/skel/.config/libreoffice/3/user/database/biblio/biblio.dbt 
 /etc/skel/.config/libreoffice/3/user/database/biblio/biblio.dbf 
 /etc/skel/.config/libreoffice/3/user/config 
 /etc/skel/.config/libreoffice/3/user/config/libreoffice.soc 
 /etc/skel/.config/libreoffice/3/user/config/modern.sog 
 /etc/skel/.config/libreoffice/3/user/config/html.soc 
 /etc/skel/.config/libreoffice/3/user/config/standard.sod 
 /etc/skel/.config/libreoffice/3/user/config/arrowhd.soe 
 /etc/skel/.config/libreoffice/3/user/config/palette.soc 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/menubar 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/statusbar 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/images 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/images/Bitmaps 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/toolbar 
 /etc/skel/.config/libreoffice/3/user/config/autotbl.fmt 
 /etc/skel/.config/libreoffice/3/user/config/gallery.soc 
 /etc/skel/.config/libreoffice/3/user/config/standard.sog 
 /etc/skel/.config/libreoffice/3/user/config/hatching.soh 
 /etc/skel/.config/libreoffice/3/user/config/javasettings_Linux_x86.xml 
 /etc/skel/.config/libreoffice/3/user/config/standard.soh 
 /etc/skel/.config/libreoffice/3/user/config/tango.soc 
 /etc/skel/.config/libreoffice/3/user/config/cmyk.soc 
 /etc/skel/.config/libreoffice/3/user/config/styles.sod 
 /etc/skel/.config/libreoffice/3/user/config/standard.sob 
 /etc/skel/.config/libreoffice/3/user/config/web.soc 
 /etc/skel/.config/libreoffice/3/user/config/classic.sog 
 /etc/skel/.config/libreoffice/3/user/config/standard.soe 
 /etc/skel/.config/libreoffice/3/user/config/standard.soc 
 /etc/skel/.config/libreoffice/3/user/config/scribus.soc 
 /etc/skel/.config/libreoffice/3/user/autotext 
 /etc/skel/.config/libreoffice/3/user/autotext/mytexts.bau 
 /etc/skel/.config/libreoffice/3/user/gallery 
 /etc/skel/.config/libreoffice/3/user/gallery/sg30.thm 
 /etc/skel/.config/libreoffice/3/user/gallery/sg100.thm 
 /etc/skel/.config/libreoffice/3/user/gallery/sg100.sdv 
 /etc/skel/.config/libreoffice/3/user/gallery/sg30.sdv 
 /etc/skel/.config/libreoffice/3/user/extensions 
 /etc/skel/.config/libreoffice/3/user/extensions/shared 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/lastsynchronized 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/extensions.db 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend/unorc 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/lastsynchronized 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/extensions.db 
 /etc/skel/.config/libreoffice/3/user/uno_packages 
 /etc/skel/.config/libreoffice/3/user/psprint 
 /etc/skel/.config/libreoffice/3/user/psprint/driver 
 /etc/skel/.config/libreoffice/3/user/psprint/fontmetric 
 /etc/skel/.config/libreoffice/3/user/temp 
 /etc/skel/.config/libreoffice/3/user/store 
 /etc/skel/.config/libreoffice/3/user/wordbook 
 /etc/skel/.config/libreoffice/3/user/Scripts 
 /etc/skel/.config/libreoffice/3/user/basic 
 /etc/skel/.config/libreoffice/3/user/basic/Standard 
 /etc/skel/.config/libreoffice/3/user/basic/Standard/dialog.xlb 
 /etc/skel/.config/libreoffice/3/user/basic/Standard/script.xlb 
 /etc/skel/.config/libreoffice/3/user/basic/Standard/Module1.xba 
 /etc/skel/.config/libreoffice/3/user/basic/script.xlc 
 /etc/skel/.config/libreoffice/3/user/basic/dialog.xlc 
 /etc/skel/.config/libreoffice/3/user/backup 
 /etc/skel/.config/gnome-panel  
 /etc/skel/.config/gnome-panel/launchers 
 /etc/skel/.config/gnome-panel/launchers/onboard.desktop 
 /etc/skel/.config/gnome-panel/launchers/gnucash.desktop 
 /etc/skel/.config/Bitcoin  
 /etc/skel/.config/Bitcoin/Bitcoin-Qt.conf 
 /etc/skel/.config/gedit  
 /etc/skel/.config/gedit/accels  
 /etc/skel/.config/alarm-clock  
 /etc/skel/.config/alarm-clock/alarms.conf 
 /etc/skel/.config/alarm-clock/global.conf 
 /etc/skel/.config/alarm-clock/birthdays.conf 
 /etc/skel/.config/alarm-clock/missed.conf 
 /etc/skel/.config/alarm-clock/templates.conf 
 /etc/skel/.config/goa-1.0  
 /etc/skel/.config/autostart  
 /etc/skel/.config/autostart/pidgin.desktop 
 /etc/skel/.config/autostart/libcanberra-login-sound.desktop 
 /etc/skel/.config/autostart/dropbox.desktop 
 /etc/skel/.config/autostart/skype.desktop 
 /etc/skel/.config/autostart/alarm-clock.desktop 
 /etc/skel/.config/Trolltech.conf  
 /etc/skel/.config/ubuntuone  
 /etc/skel/.config/enchant  
 /etc/skel/.config/enchant/en_US.exc  
 /etc/skel/.config/enchant/en_US.dic  
 /etc/skel/.config/transmission  
 /etc/skel/.config/transmission/resume  
 /etc/skel/.config/transmission/torrents 
 /etc/skel/.config/transmission/stats.json 
 /etc/skel/.config/transmission/dht.dat  
 /etc/skel/.config/transmission/blocklists 
 /etc/skel/.config/gnome-control-center  
 /etc/skel/.config/gnome-control-center/backgrounds 
 /etc/skel/.config/gnome-control-center/backgrounds/last-edited.xml 
 ------------------------------------------------------ 
 lsb-release info  
 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=12.04  
 DISTRIB_CODENAME=precise  
 DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"  
 ------------------------------------------------------ 
 remastersys version info  
 REMASTERSYSVERSION="3.0.2-1"  
   
 ------------------------------------------------------ 
 ISOTMP info  
 /home/remastersys/remastersys/ISOTMP:  
 total 20  
 drwxr-xr-x 2 root root 4096 May  3 18:50 casper  
 drwxr-xr-x 2 root root 4096 May  3 18:46 install  
 drwxr-xr-x 2 root root 4096 May  3 18:49 isolinux  
 drwxr-xr-x 2 root root 4096 May  3 18:46 preseed  
 -rw-r--r-- 1 root root  195 May  3 18:49 README.diskdefines  
 

 /home/remastersys/remastersys/ISOTMP/casper: 
 total 1978092  
 -rw-r--r-- 1 root root      61071 May  3 18:49 filesystem.manifest  
 -rw-r--r-- 1 root root      61007 May  3 18:49 filesystem.manifest-desktop  
 -rw-r--r-- 1 root root 1999884288 May  3 19:10 filesystem.squashfs  
 -rw-r--r-- 1 root root   20532599 May  3 18:50 initrd.gz  
 -rw-r--r-- 1 root root        195 May  3 18:49 README.diskdefines  
 -rw------- 1 root root    5015872 May  3 18:50 vmlinuz  
 

 /home/remastersys/remastersys/ISOTMP/install: 
 total 176  
 -rw-r--r-- 1 root root 176764 May  3 18:46 memtest  
 

 /home/remastersys/remastersys/ISOTMP/isolinux: 
 total 184  
 -rw-r--r-- 1 root root  24576 May  3 18:48 isolinux.bin  
 -rw-r--r-- 1 root root    896 May  3 18:49 isolinux.cfg  
 -rwxr-xr-x 1 root root      0 May  3 18:49 splash.png  
 -rw-r--r-- 1 root root 155792 May  3 18:49 vesamenu.c32  
 

 /home/remastersys/remastersys/ISOTMP/preseed: 
 total 4  
 -rwxr-xr-x 1 root root 212 May  3 18:46 custom.seed  
 ------------------------------------------------------ 
 /home/remastersys/remastersys/tmpusers info  
 alain  
 ------------------------------------------------------ 
 Command-line options = dist  
 ------------------------------------------------------ 
 Removing the ubiquity frontend as it has been included and is not needed on the normal system  
 Calculating the installed filesystem size for the installer  
 Removing remastersys-firstboot from system startup  
 Making disk compatible with Ubuntu Startup Disk Creator.  
 Creating md5sum.txt for the livecd/dvd  
 Creating custom-dist.iso in /home/remastersys/remastersys  
 Creating custom-dist.iso.md5 in /home/remastersys/remastersys  
 /home/remastersys/remastersys/custom-dist.iso which is 1.9G in size is ready to be burned or tested in a virtual machine.

---

### Post by Fragadelic on 2012-05-03
It looks like you might be using one of the test version of 3.0.2-1.  Did you get it from my official repo or the direct download?

It is missing the FLAVOUR variable in the /etc/casper.conf.

I uploaded the final 3.0.2 to the direct download when I setup the repository so if you got it earlier than that, please update the to final 3.0.2-1.

---

### Post by xx58 on 2012-05-03
Can you give me web site, where is right place to download this 3 packages? Thank you up front.
Sincerely

---

### Post by Fragadelic on 2012-05-03
You can either get them from my repo and the info for the repo is on this webpage - [http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

Or you can download directly from [http://www.remastersys.com/downloads](http://www.remastersys.com/downloads)

If you are running precise 32-bit:
Download remasterys_3.0.2-1_all.deb and remastersys-gui_3.0.2-1_i386.deb

If you are running precise 64-bit:
Download remasterys_3.0.2-1_all.deb and remastersys-gui_3.0.2-1_amd64.deb

If you are running lucid to natty 32 or 64 bit:
Download remasterys_3.0.2-1_all.deb and remastersys-gtk_3.0.2-1_all.deb

You MUST install remastersys_3.0.2-1_all.deb first and then install the gui or gtk package especially if you are upgrading from an older version of remastersys like 3.0.1 or earlier.  I know this part doesn't apply to you directly but I though I'd put it up in case anyone else sees this so it saves them time to properly install it.

---

### Post by xx58 on 2012-05-03
Start Installer Directly. [COLOR=#ff0000]Not work[/COLOR]. Will take to Login Screen. Sign in like Guest Session. Cannot use other option, don't know user name and password. Then find Install Custom Live. Enter your password to preform administrative task. Then , [COLOR=#ff0000]Incorrect password..... try again.[/COLOR]
 

 [COLOR=#000000]2nd problem.[/COLOR]
 

 [COLOR=#000000]Every time I install new program, I make backup with Clonezilla. So, if I install Remastersys and try make backup, I will have next message:[/COLOR]
 

 [COLOR=#ff0000]Something wrong. This partition in the image is broken:sda1, Broken partition image were found, or some of them are not checkable in this image.[/COLOR]

---

### Post by xx58 on 2012-05-03
Distribution Mode Selected  
 Enabling remastersys-firstboot  
 Checking filesystem type of the Working Folder  
 /home/remastersys/remastersys is on a ext4 filesystem  
 Making sure popularity contest is not installed  
 Installing the Ubiquity GTK frontend  
 Checking if the /home/remastersys/remastersys folder has been created  
 Creating /home/remastersys/remastersys folder tree  
 Creating /home/remastersys/remastersys/ISOTMP folder tree  
 Copying /var and /etc to temp area and excluding extra files  ... this will take a while so be patient  
 Cleaning up files not needed for the live in /home/remastersys/remastersys/dummysys  
 Cleaning up passwd, group, shadow and gshadow files for the live system  
 Making sure adduser and autologin functions of casper are set properly  
 Copying memtest86+ for the live system  
 Creating isolinux setup for the live system  
 Checking the ARCH of the system and setting the README.diskdefines file  
 Creating filesystem.manifest and filesystem.manifest-desktop  
 Creating the casper.conf file.  
 Checking and setting user-setup-apply for the live system  
 Setting up casper and ubiquity options for dist mode  
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
 gvfs-fuse-daemon on /home/alain/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alain)  
 /dev/sdb1 on /media/New Volume type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks) 
 ------------------------------------------------------ 
 Disk size information  
 Filesystem      Size  Used Avail Use% Mounted on  
 /dev/sda1       110G   15G   90G  15% / 
 udev            992M  4.0K  992M   1% /dev  
 tmpfs           401M  912K  400M   1% /run  
 none            5.0M     0  5.0M   0% /run/lock  
 none           1003M  1.4M 1001M   1% /run/shm  
 /dev/sdb1       147G  125G   23G  85% /media/New Volume  
 ------------------------------------------------------ 
 Casper Script info  
 total 148  
 -rwxr-xr-x 1 root root  297 Apr 18 12:17 01integrity_check  
 -rwxr-xr-x 1 root root  467 Apr 18 12:17 05mountpoints  
 -rwxr-xr-x 1 root root  571 Apr 18 12:17 07remove_oem_config  
 -rwxr-xr-x 1 root root  400 Apr 18 12:17 12fstab  
 -rwxr-xr-x 1 root root  830 Apr 18 12:17 13swap  
 -rwxr-xr-x 1 root root 1221 Apr 18 12:17 14locales  
 -rwxr-xr-x 1 root root 2920 Apr 18 12:17 15autologin  
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
 -rwxr-xr-x 1 root root 3939 Apr 18 12:17 25adduser  
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
 LIVEUSER="custom"  
 

 

 # Here you can change the name of the livecd/dvd label  
 LIVECDLABEL="Custom Live CD"  
 

 

 # Here you can change the name of the ISO file that is created  
 CUSTOMISO="custom-$1.iso"  
 

 

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
 

 export USERNAME="custom"  
 export USERFULLNAME="Live session user"  
 export HOST="custom"  
 export BUILD_SYSTEM="Ubuntu"  
 export FLAVOUR="custom"  
 ------------------------------------------------------ 
 /etc/passwd info  
 root:0:0:root:/root:/bin/bash  
 daemon:1:1:daemon:/usr/sbin:/bin/sh  
 bin:2:2:bin:/bin:/bin/sh  
 sys:3:3:sys:/dev:/bin/sh  
 sync:4:65534:sync:/bin:/bin/sync  
 games:5:60:games:/usr/games:/bin/sh  
 man:6:12:man:/var/cache/man:/bin/sh  
 lp:7:7:lp:/var/spool/lpd:/bin/sh  
 mail:8:8:mail:/var/mail:/bin/sh  
 news:9:9:news:/var/spool/news:/bin/sh 
 uucp:10:10:uucp:/var/spool/uucp:/bin/sh 
 proxy:13:13roxy:/bin:/bin/sh  
 www-data:33:33:www-data:/var/www:/bin/sh 
 backup:34:34:backup:/var/backups:/bin/sh 
 list:38:38:Mailing List Manager:/var/list:/bin/sh  
 irc:39:39:ircd:/var/run/ircd:/bin/sh  
 gnats:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh  
 libuuid:100:101::/var/lib/libuuid:/bin/sh 
 syslog:101:103::/home/syslog:/bin/false 
 messagebus:102:105::/var/run/dbus:/bin/false 
 colord:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false  
 lightdm:104:111:Light Display Manager:/var/lib/lightdm:/bin/false  
 whoopsie:105:114::/nonexistent:/bin/false 
 avahi-autoipd:106:117:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false  
 avahi:107:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false  
 usbmux:108:46:usbmux daemon,,,:/home/usbmux:/bin/false  
 kernoops:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false  
 pulse:110:119ulseAudio daemon,,,:/var/run/pulse:/bin/false  
 rtkit:111:122:RealtimeKit,,,:/proc:/bin/false 
 speech-dispatcher:112:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh  
 hplip:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false  
 saned:114:123::/home/saned:/bin/false 
 kdm:115:65534::/home/kdm:/bin/false  
 nobody:65534:65534:nobody:/nonexistent:/bin/sh 
 ------------------------------------------------------ 
 /etc/group info  
 root:0:  
 daemon:1:  
 bin:2:  
 sys:3:  
 adm:4:  
 tty:5:  
 disk:6:  
 lp:7:  
 mail:8:  
 news:9:  
 uucp:10:  
 man:12:  
 proxy:13:  
 kmem:15:  
 dialout:20:  
 fax:21:  
 voice:22:  
 cdrom:24:  
 floppy:25:  
 tape:26:  
 sudo:27:  
 audio:29ulse  
 dip:30:  
 www-data:33:  
 backup:34:  
 operator:37:  
 list:38:  
 irc:39:  
 src:40:  
 gnats:41:  
 shadow:42:  
 utmp:43:  
 video:44:  
 sasl:45:  
 plugdev:46:  
 staff:50:  
 games:60:  
 users:100:  
 libuuid:101:  
 crontab:102:  
 syslog:103:  
 fuse:104:  
 messagebus:105:  
 bluetooth:106:  
 scanner:107:  
 colord:108:  
 lpadmin:109:  
 ssl-cert:110:  
 lightdm:111:  
 nopasswdlogin:112:  
 netdev:113:  
 whoopsie:114:  
 mlocate:115:  
 ssh:116:  
 avahi-autoipd:117:  
 avahi:118:  
 pulse:119:  
 pulse-access:120:  
 utempter:121:  
 rtkit:122:  
 saned:123:  
 sambashare:124:  
 winbindd_priv:125:  
 pcscd:126:  
 nogroup:65534:  
 ------------------------------------------------------ 
 /etc/X11/default-display-manager info  
 /usr/sbin/lightdm  
 ------------------------------------------------------ 
 /etc/skel info  
 /etc/skel  
 /etc/skel/.kde  
 /etc/skel/.kde/tmp-alan  
 /etc/skel/.kde/share  
 /etc/skel/.kde/share/config  
 /etc/skel/.kde/share/config/phonondevicesrc 
 /etc/skel/.kde/share/config/ksmserverrc 
 /etc/skel/.kde/share/config/emaildefaults 
 /etc/skel/.kde/share/config/katerc  
 /etc/skel/.kde/share/config/kwinrulesrc 
 /etc/skel/.kde/share/config/kcookiejarrc 
 /etc/skel/.kde/share/config/kglobalshortcutsrc 
 /etc/skel/.kde/share/config/kdeglobals  
 /etc/skel/.kde/share/config/kwinrc  
 /etc/skel/.kde/share/config/mailtransports 
 /etc/skel/.kde/share/config/kconf_updaterc 
 /etc/skel/.kde/share/config/kmailrc  
 /etc/skel/.kde/share/config/kcmdisplayrc 
 /etc/skel/.kde/share/config/kdebugrc  
 /etc/skel/.kde/share/config/kcminputrc  
 /etc/skel/.kde/share/config/klipperrc  
 /etc/skel/.kde/share/config/knoderc  
 /etc/skel/.kde/share/config/nepomukserverrc 
 /etc/skel/.kde/share/config/kdedrc  
 /etc/skel/.kde/share/config/kio_httprc  
 /etc/skel/.kde/share/config/kioslaverc  
 /etc/skel/.kde/share/config/kwin.eventsrc 
 /etc/skel/.kde/share/config/kuriikwsfilterrc 
 /etc/skel/.kde/share/kde4  
 /etc/skel/.kde/share/kde4/services  
 /etc/skel/.kde/share/apps  
 /etc/skel/.kde/share/apps/kfileplaces  
 /etc/skel/.kde/share/apps/k3b  
 /etc/skel/.kde/share/apps/k3b/lastlog.log 
 /etc/skel/.kde/share/apps/kconf_update  
 /etc/skel/.kde/share/apps/kconf_update/log 
 /etc/skel/.profile  
 /etc/skel/examples.desktop  
 /etc/skel/.config  
 /etc/skel/.config/menus  
 /etc/skel/.config/menus/applications-merged 
 /etc/skel/.config/menus/applications-merged/wine-Programs-PartyPoker-Uninstall PartyPoker.menu  
 /etc/skel/.config/menus/applications-merged/wine-Programs-Games-PartyPoker.menu 
 /etc/skel/.config/menus/applications-merged/wine-PartyPoker.menu 
 /etc/skel/.config/menus/applications-merged/wine-Programs-PartyPoker-PartyPoker.menu 
 /etc/skel/.config/enchant  
 /etc/skel/.config/enchant/en_AU.exc  
 /etc/skel/.config/enchant/en_AU.dic  
 /etc/skel/.config/ibus  
 /etc/skel/.config/ibus/bus  
 /etc/skel/.config/compiz-1  
 /etc/skel/.config/compiz-1/compizconfig 
 /etc/skel/.config/compiz-1/compizconfig/config 
 /etc/skel/.config/compiz-1/compizconfig/done_upgrades 
 /etc/skel/.config/gnome-disk-utility  
 /etc/skel/.config/gnome-disk-utility/ata-smart-ignore 
 /etc/skel/.config/yelp  
 /etc/skel/.config/gnome-session  
 /etc/skel/.config/gnome-session/saved-session 
 /etc/skel/.config/gedit  
 /etc/skel/.config/gedit/accels  
 /etc/skel/.config/nautilus  
 /etc/skel/.config/nautilus/desktop-metadata 
 /etc/skel/.config/alarm-clock  
 /etc/skel/.config/alarm-clock/global.conf 
 /etc/skel/.config/alarm-clock/alarms.conf 
 /etc/skel/.config/alarm-clock/templates.conf 
 /etc/skel/.config/alarm-clock/missed.conf 
 /etc/skel/.config/alarm-clock/birthdays.conf 
 /etc/skel/.config/autostart  
 /etc/skel/.config/autostart/canberra-gtk-play.desktop 
 /etc/skel/.config/autostart/alarm-clock.desktop 
 /etc/skel/.config/autostart/dropbox.desktop 
 /etc/skel/.config/autostart/indicator-weather.desktop 
 /etc/skel/.config/Trolltech.conf  
 /etc/skel/.config/update-notifier  
 /etc/skel/.config/update-notifier/hooks_seen 
 /etc/skel/.config/gnome-panel  
 /etc/skel/.config/gnome-panel/launchers 
 /etc/skel/.config/gnome-panel/launchers/onboard.desktop 
 /etc/skel/.config/Bitcoin  
 /etc/skel/.config/Bitcoin/Bitcoin-Qt.conf 
 /etc/skel/.config/software-center  
 /etc/skel/.config/software-center/softwarecenter.cfg 
 /etc/skel/.config/dconf  
 /etc/skel/.config/gnome-control-center  
 /etc/skel/.config/gnome-control-center/backgrounds 
 /etc/skel/.config/libreoffice  
 /etc/skel/.config/libreoffice/3  
 /etc/skel/.config/libreoffice/3/user  
 /etc/skel/.config/libreoffice/3/user/temp 
 /etc/skel/.config/libreoffice/3/user/config 
 /etc/skel/.config/libreoffice/3/user/config/standard.soe 
 /etc/skel/.config/libreoffice/3/user/config/standard.sob 
 /etc/skel/.config/libreoffice/3/user/config/gallery.soc 
 /etc/skel/.config/libreoffice/3/user/config/styles.sod 
 /etc/skel/.config/libreoffice/3/user/config/autotbl.fmt 
 /etc/skel/.config/libreoffice/3/user/config/scribus.soc 
 /etc/skel/.config/libreoffice/3/user/config/javasettings_Linux_x86.xml 
 /etc/skel/.config/libreoffice/3/user/config/arrowhd.soe 
 /etc/skel/.config/libreoffice/3/user/config/standard.sog 
 /etc/skel/.config/libreoffice/3/user/config/standard.sod 
 /etc/skel/.config/libreoffice/3/user/config/modern.sog 
 /etc/skel/.config/libreoffice/3/user/config/standard.soh 
 /etc/skel/.config/libreoffice/3/user/config/tango.soc 
 /etc/skel/.config/libreoffice/3/user/config/libreoffice.soc 
 /etc/skel/.config/libreoffice/3/user/config/hatching.soh 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/statusbar 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/images 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/images/Bitmaps 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/toolbar 
 /etc/skel/.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/menubar 
 /etc/skel/.config/libreoffice/3/user/config/palette.soc 
 /etc/skel/.config/libreoffice/3/user/config/standard.soc 
 /etc/skel/.config/libreoffice/3/user/config/cmyk.soc 
 /etc/skel/.config/libreoffice/3/user/config/classic.sog 
 /etc/skel/.config/libreoffice/3/user/config/html.soc 
 /etc/skel/.config/libreoffice/3/user/config/web.soc 
 /etc/skel/.config/libreoffice/3/user/extensions 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/lastsynchronized 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/extensions.db 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend/unorc 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/shared 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/lastsynchronized 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/extensions.db 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml 
 /etc/skel/.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend 
 /etc/skel/.config/libreoffice/3/user/backup 
 /etc/skel/.config/libreoffice/3/user/uno_packages 
 /etc/skel/.config/libreoffice/3/user/autocorr 
 /etc/skel/.config/libreoffice/3/user/psprint 
 /etc/skel/.config/libreoffice/3/user/psprint/fontmetric 
 /etc/skel/.config/libreoffice/3/user/psprint/driver 
 /etc/skel/.config/libreoffice/3/user/gallery 
 /etc/skel/.config/libreoffice/3/user/gallery/sg30.thm 
 /etc/skel/.config/libreoffice/3/user/gallery/sg30.sdv 
 /etc/skel/.config/libreoffice/3/user/gallery/sg100.thm 
 /etc/skel/.config/libreoffice/3/user/gallery/sg100.sdv 
 /etc/skel/.config/libreoffice/3/user/autotext 
 /etc/skel/.config/libreoffice/3/user/autotext/mytexts.bau 
 /etc/skel/.config/libreoffice/3/user/wordbook 
 /etc/skel/.config/libreoffice/3/user/store 
 /etc/skel/.config/libreoffice/3/user/basic 
 /etc/skel/.config/libreoffice/3/user/basic/dialog.xlc 
 /etc/skel/.config/libreoffice/3/user/basic/script.xlc 
 /etc/skel/.config/libreoffice/3/user/basic/Standard 
 /etc/skel/.config/libreoffice/3/user/basic/Standard/dialog.xlb 
 /etc/skel/.config/libreoffice/3/user/basic/Standard/Module1.xba 
 /etc/skel/.config/libreoffice/3/user/basic/Standard/script.xlb 
 /etc/skel/.config/libreoffice/3/user/template 
 /etc/skel/.config/libreoffice/3/user/Scripts 
 /etc/skel/.config/libreoffice/3/user/database 
 /etc/skel/.config/libreoffice/3/user/database/biblio 
 /etc/skel/.config/libreoffice/3/user/database/biblio/biblio.dbt 
 /etc/skel/.config/libreoffice/3/user/database/biblio/biblio.dbf 
 /etc/skel/.config/libreoffice/3/user/database/biblio.odb 
 /etc/skel/.config/eog  
 /etc/skel/.config/eog/accels  
 /etc/skel/.config/goa-1.0  
 /etc/skel/.config/ubuntuone  
 /etc/skel/.bash_logout  
 /etc/skel/.bashrc  
 /etc/skel/.gconf  
 /etc/skel/.gconf/desktop  
 /etc/skel/.gconf/desktop/%gconf.xml  
 /etc/skel/.gconf/desktop/gnome  
 /etc/skel/.gconf/desktop/gnome/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/peripherals 
 /etc/skel/.gconf/desktop/gnome/peripherals/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/peripherals/keyboard 
 /etc/skel/.gconf/desktop/gnome/peripherals/keyboard/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/peripherals/keyboard/kbd 
 /etc/skel/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/background 
 /etc/skel/.gconf/desktop/gnome/url-handlers 
 /etc/skel/.gconf/desktop/gnome/url-handlers/%gconf.xml 
 /etc/skel/.gconf/desktop/gnome/url-handlers/mailto 
 /etc/skel/.gconf/desktop/gnome/url-handlers/mailto/%gconf.xml 
 /etc/skel/.gconf/apps  
 /etc/skel/.gconf/apps/deja-dup  
 /etc/skel/.gconf/apps/deja-dup/%gconf.xml 
 /etc/skel/.gconf/apps/deja-dup/s3  
 /etc/skel/.gconf/apps/deja-dup/s3/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1  
 /etc/skel/.gconf/apps/compizconfig-1/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/move/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitydialog/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/place/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/screen0 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/screen0/options 
 /etc/skel/.gconf/apps/compizconfig-1/profiles/unity/general/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/%gconf.xml  
 /etc/skel/.gconf/apps/file-roller  
 /etc/skel/.gconf/apps/file-roller/%gconf.xml 
 /etc/skel/.gconf/apps/file-roller/listing 
 /etc/skel/.gconf/apps/file-roller/listing/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1  
 /etc/skel/.gconf/apps/compiz-1/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/general  
 /etc/skel/.gconf/apps/compiz-1/general/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/general/screen0 
 /etc/skel/.gconf/apps/compiz-1/general/screen0/%gconf.xml 
 /etc/skel/.gconf/apps/compiz-1/general/screen0/options 
 /etc/skel/.gconf/apps/compiz-1/general/screen0/options/%gconf.xml 
 /etc/skel/.gconf/apps/metacity  
 /etc/skel/.gconf/apps/metacity/%gconf.xml 
 /etc/skel/.gconf/apps/metacity/window_keybindings 
 /etc/skel/.gconf/apps/metacity/window_keybindings/%gconf.xml 
 /etc/skel/.gconf/apps/metacity/global_keybindings 
 /etc/skel/.gconf/apps/metacity/global_keybindings/%gconf.xml 
 /etc/skel/.gconf/apps/metacity/general  
 /etc/skel/.gconf/apps/metacity/general/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus  
 /etc/skel/.gconf/apps/nautilus/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus/icon_view 
 /etc/skel/.gconf/apps/nautilus/icon_view/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus/preferences 
 /etc/skel/.gconf/apps/nautilus/preferences/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus/desktop  
 /etc/skel/.gconf/apps/nautilus/desktop/%gconf.xml 
 /etc/skel/.gconf/apps/nautilus/list_view 
 /etc/skel/.gconf/apps/nautilus/list_view/%gconf.xml 
 /etc/skel/.gconf/apps/onboard  
 /etc/skel/.gconf/apps/onboard/%gconf.xml 
 /etc/skel/.gconf/apps/panel3-applets  
 /etc/skel/.gconf/apps/panel3-applets/%gconf.xml 
 /etc/skel/.gconf/apps/panel3-applets/object_12 
 /etc/skel/.gconf/apps/panel3-applets/object_12/%gconf.xml 
 /etc/skel/.gconf/apps/panel3-applets/object_1 
 /etc/skel/.gconf/apps/panel3-applets/object_1/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2  
 /etc/skel/.gconf/apps/gedit-2/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2/plugins  
 /etc/skel/.gconf/apps/gedit-2/plugins/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2/preferences 
 /etc/skel/.gconf/apps/gedit-2/preferences/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2/preferences/ui 
 /etc/skel/.gconf/apps/gedit-2/preferences/ui/%gconf.xml 
 /etc/skel/.gconf/apps/gedit-2/preferences/ui/statusbar 
 /etc/skel/.gconf/apps/gedit-2/preferences/ui/statusbar/%gconf.xml 
 /etc/skel/.gconf/apps/update-notifier  
 /etc/skel/.gconf/apps/update-notifier/%gconf.xml 
 /etc/skel/.gconf/apps/nm-applet  
 /etc/skel/.gconf/apps/nm-applet/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash  
 /etc/skel/.gconf/apps/gnucash/history  
 /etc/skel/.gconf/apps/gnucash/history/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/dialogs  
 /etc/skel/.gconf/apps/gnucash/dialogs/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/dialogs/tip_of_the_day 
 /etc/skel/.gconf/apps/gnucash/dialogs/tip_of_the_day/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/dialogs/open_save 
 /etc/skel/.gconf/apps/gnucash/dialogs/open_save/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/dialogs/new_user 
 /etc/skel/.gconf/apps/gnucash/dialogs/new_user/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/window  
 /etc/skel/.gconf/apps/gnucash/window/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/window/pages 
 /etc/skel/.gconf/apps/gnucash/window/pages/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/window/pages/register 
 /etc/skel/.gconf/apps/gnucash/window/pages/register/%gconf.xml 
 /etc/skel/.gconf/apps/gnucash/window/pages/account_tree 
 /etc/skel/.gconf/apps/gnucash/window/pages/account_tree/%gconf.xml 
 /etc/skel/.gconf/apps/update-manager  
 /etc/skel/.gconf/apps/update-manager/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-terminal  
 /etc/skel/.gconf/apps/gnome-terminal/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-terminal/profiles 
 /etc/skel/.gconf/apps/gnome-terminal/profiles/%gconf.xml 
 /etc/skel/.gconf/apps/gnome-terminal/profiles/Default 
 /etc/skel/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml 
 /etc/skel/.gconf/apps/eog  
 /etc/skel/.gconf/apps/eog/%gconf.xml  
 /etc/skel/.gconf/apps/eog/ui  
 /etc/skel/.gconf/apps/eog/ui/%gconf.xml 
 /etc/skel/.gconf/apps/eog/view  
 /etc/skel/.gconf/apps/eog/view/%gconf.xml 
 /etc/skel/.gconf/system  
 /etc/skel/.gconf/system/%gconf.xml  
 /etc/skel/.gconf/system/http_proxy  
 /etc/skel/.gconf/system/http_proxy/%gconf.xml 
 /etc/skel/.local  
 /etc/skel/.local/share  
 /etc/skel/.local/share/icons  
 /etc/skel/.local/share/icons/hicolor  
 /etc/skel/.local/share/icons/hicolor/64x64 
 /etc/skel/.local/share/icons/hicolor/64x64/apps 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/88EB_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/FCE4_Terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/64x64/apps/4365_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16 
 /etc/skel/.local/share/icons/hicolor/16x16/apps 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/application-x-wine-extension-msp.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/08AE_Terminal.2.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/7765_winebrowser.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/1CD8_rundll32.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/C4FC_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/2EF4_wordpad.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/88EB_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/A35F_hh.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/1E64_notepad.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/application-x-wine-extension-its.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/A53A_ppicon.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/FCE4_Terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/FB4C_iexplore.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/4365_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/16x16/apps/4137_winhlp32.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32 
 /etc/skel/.local/share/icons/hicolor/32x32/apps 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/application-x-wine-extension-msp.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/08AE_Terminal.2.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/7765_winebrowser.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/1CD8_rundll32.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/C4FC_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/2EF4_wordpad.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/88EB_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/A35F_hh.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/2081_SmartInstaller.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/1E64_notepad.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/application-x-wine-extension-its.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/A53A_ppicon.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/FCE4_Terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/FB4C_iexplore.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/4365_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/32x32/apps/4137_winhlp32.0.png 
 /etc/skel/.local/share/icons/hicolor/128x128 
 /etc/skel/.local/share/icons/hicolor/128x128/apps 
 /etc/skel/.local/share/icons/hicolor/128x128/apps/A53A_ppicon.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48 
 /etc/skel/.local/share/icons/hicolor/48x48/apps 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/application-x-wine-extension-msp.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/08AE_Terminal.2.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/7765_winebrowser.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/1CD8_rundll32.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/C4FC_MetaEditor.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/2EF4_wordpad.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/88EB_Uninstall.1.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/A35F_hh.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/2081_SmartInstaller.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/1E64_notepad.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/application-x-wine-extension-its.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/A53A_ppicon.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/FCE4_Terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/FB4C_iexplore.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/4365_terminal.0.png 
 /etc/skel/.local/share/icons/hicolor/48x48/apps/4137_winhlp32.0.png 
 /etc/skel/.local/share/icons/hicolor/24x24 
 /etc/skel/.local/share/icons/hicolor/24x24/apps 
 /etc/skel/.local/share/icons/hicolor/24x24/apps/08AE_Terminal.2.png 
 /etc/skel/.local/share/icons/hicolor/24x24/apps/88EB_Uninstall.1.png 
 /etc/skel/.local/share/applications  
 /etc/skel/.local/share/applications/wine 
 /etc/skel/.local/share/applications/wine/Programs 
 /etc/skel/.local/share/applications/wine/Programs/Games 
 /etc/skel/.local/share/applications/wine/Programs/PartyPoker 
 /etc/skel/.local/share/applications/wine/Programs/PartyPoker/Uninstall PartyPoker.desktop  
 /etc/skel/.local/share/applications/wine/Programs/MetaTrader 4 at FOREX.com  
 /etc/skel/.local/share/applications/mimeapps.list 
 /etc/skel/.local/share/zeitgeist  
 /etc/skel/.local/share/zeitgeist/activity.sqlite-shm 
 /etc/skel/.local/share/zeitgeist/fts.index 
 /etc/skel/.local/share/zeitgeist/fts.index/position.baseA 
 /etc/skel/.local/share/zeitgeist/fts.index/postlist.baseB 
 /etc/skel/.local/share/zeitgeist/fts.index/position.DB 
 /etc/skel/.local/share/zeitgeist/fts.index/termlist.baseB 
 /etc/skel/.local/share/zeitgeist/fts.index/record.DB 
 /etc/skel/.local/share/zeitgeist/fts.index/record.baseB 
 /etc/skel/.local/share/zeitgeist/fts.index/termlist.baseA 
 /etc/skel/.local/share/zeitgeist/fts.index/flintlock 
 /etc/skel/.local/share/zeitgeist/fts.index/position.baseB 
 /etc/skel/.local/share/zeitgeist/fts.index/termlist.DB 
 /etc/skel/.local/share/zeitgeist/fts.index/record.baseA 
 /etc/skel/.local/share/zeitgeist/fts.index/postlist.baseA 
 /etc/skel/.local/share/zeitgeist/fts.index/iamchert 
 /etc/skel/.local/share/icc  
 /etc/skel/.local/share/icc/edid-4efa08efc8761c60d76be27f2a068fca.icc 
 /etc/skel/.local/share/mime  
 /etc/skel/.local/share/mime/types  
 /etc/skel/.local/share/mime/application 
 /etc/skel/.local/share/mime/application/x-wine-extension-cpl.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-its.xml 
 /etc/skel/.local/share/mime/application/x-msdownload.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-vbs.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-inf.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-hlp.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-msp.xml 
 /etc/skel/.local/share/mime/application/x-wine-extension-ini.xml 
 /etc/skel/.local/share/mime/globs2  
 /etc/skel/.local/share/mime/icons  
 /etc/skel/.local/share/mime/XMLnamespaces 
 /etc/skel/.local/share/mime/aliases  
 /etc/skel/.local/share/mime/text  
 /etc/skel/.local/share/mime/text/x-component.xml 
 /etc/skel/.local/share/mime/subclasses  
 /etc/skel/.local/share/mime/treemagic  
 /etc/skel/.local/share/mime/image  
 /etc/skel/.local/share/mime/image/bmp.xml 
 /etc/skel/.local/share/mime/image/jpeg.xml 
 /etc/skel/.local/share/mime/globs  
 /etc/skel/.local/share/mime/version  
 /etc/skel/.local/share/mime/magic  
 /etc/skel/.local/share/mime/packages  
 /etc/skel/.local/share/mime/packages/x-wine-extension-cpl.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-its.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-jfif.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-vbs.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-dll.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-inf.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-hlp.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-msp.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-dib.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-ini.xml 
 /etc/skel/.local/share/mime/packages/x-wine-extension-htc.xml 
 /etc/skel/.local/share/mime/generic-icons 
 /etc/skel/.local/share/gsettings-data-convert 
 /etc/skel/.local/share/telepathy  
 /etc/skel/.local/share/telepathy/mission-control 
 /etc/skel/.local/share/telepathy/mission-control/accounts-goa.cfg 
 /etc/skel/.local/share/.converted-launchers 
 /etc/skel/.local/share/ubuntuone  
 /etc/skel/.local/share/ubuntuone/syncdaemon 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm/udfs 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm/shares 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm/shared 
 /etc/skel/.local/share/ubuntuone/syncdaemon/vm/.version 
 /etc/skel/.local/share/ubuntuone/syncdaemon/fsm 
 /etc/skel/.local/share/ubuntuone/syncdaemon/metadata_version 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336051917542238.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336079539085333.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336015891809809.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336016860069463.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336077541643632.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336015891947737.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336021082392401.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336026402823926.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336048299641960.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/syncdaemon/tritcask/1336022749258435.inactive.tritcask-v1.data.hint 
 /etc/skel/.local/share/ubuntuone/shares 
 /etc/skel/.local/share/desktop-directories 
 /etc/skel/.local/share/desktop-directories/wine-Programs.directory 
 /etc/skel/.local/share/desktop-directories/wine-Programs-MetaTrader 4 at FOREX.com.directory  
 /etc/skel/.local/share/desktop-directories/wine-wine.directory 
 /etc/skel/.local/share/desktop-directories/wine-Programs-PartyPoker.directory 
 /etc/skel/.local/share/desktop-directories/wine-Programs-Games.directory 
 /etc/skel/.gnome2  
 /etc/skel/.gnome2/nautilus-scripts  
 /etc/skel/.gnome2/accels  
 /etc/skel/.gnome2/accels/nautilus  
 /etc/skel/.gnome2/keyrings  
 ------------------------------------------------------ 
 lsb-release info  
 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=12.04  
 DISTRIB_CODENAME=precise  
 DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"  
 ------------------------------------------------------ 
 remastersys version info  
 REMASTERSYSVERSION="3.0.2-1"  
   
 ------------------------------------------------------ 
 ISOTMP info  
 /home/remastersys/remastersys/ISOTMP:  
 total 20  
 drwxr-xr-x 2 root root 4096 May  4 01:16 casper  
 drwxr-xr-x 2 root root 4096 May  4 01:14 install  
 drwxr-xr-x 2 root root 4096 May  4 01:15 isolinux  
 drwxr-xr-x 2 root root 4096 May  4 01:14 preseed  
 -rw-r--r-- 1 root root  195 May  4 01:15 README.diskdefines  
 

 /home/remastersys/remastersys/ISOTMP/casper: 
 total 1575536  
 -rw-r--r-- 1 root root      59282 May  4 01:16 filesystem.manifest  
 -rw-r--r-- 1 root root      59218 May  4 01:16 filesystem.manifest-desktop  
 -rw-r--r-- 1 root root 1587654656 May  4 01:29 filesystem.squashfs  
 -rw-r--r-- 1 root root   20541801 May  4 01:16 initrd.gz  
 -rw-r--r-- 1 root root        195 May  4 01:15 README.diskdefines  
 -rw------- 1 root root    5015872 May  4 01:16 vmlinuz  
 

 /home/remastersys/remastersys/ISOTMP/install: 
 total 176  
 -rw-r--r-- 1 root root 176764 May  4 01:14 memtest  
 

 /home/remastersys/remastersys/ISOTMP/isolinux: 
 total 400  
 -rw-r--r-- 1 root root  24576 May  4 01:14 isolinux.bin  
 -rw-r--r-- 1 root root    896 May  4 01:15 isolinux.cfg  
 -rwxr-xr-x 1 root root 220583 May  4 01:15 splash.png  
 -rw-r--r-- 1 root root 155792 May  4 01:15 vesamenu.c32  
 

 /home/remastersys/remastersys/ISOTMP/preseed: 
 total 4  
 -rwxr-xr-x 1 root root 212 May  4 01:14 custom.seed  
 ------------------------------------------------------ 
 /home/remastersys/remastersys/tmpusers info  
 alain  
 ------------------------------------------------------ 
 Command-line options = dist  
 ------------------------------------------------------ 
 Removing the ubiquity frontend as it has been included and is not needed on the normal system  
 Calculating the installed filesystem size for the installer  
 Removing remastersys-firstboot from system startup  
 Making disk compatible with Ubuntu Startup Disk Creator.  
 Creating md5sum.txt for the livecd/dvd  
 Creating custom-dist.iso in /home/remastersys/remastersys  
 Creating custom-dist.iso.md5 in /home/remastersys/remastersys  
 /home/remastersys/remastersys/custom-dist.iso which is 1.6G in size is ready to be burned or tested in a virtual machine.

---

### Post by Fragadelic on 2012-05-03
> **xx58 said:**
> Start Installer Directly. [COLOR=#ff0000]Not work[/COLOR]. Will take to Login Screen. Sign in like Guest Session. Cannot use other option, don't know user name and password. Then find Install Custom Live. Enter your password to preform administrative task. Then , [COLOR=#ff0000]Incorrect password..... try again.[/COLOR]
 

 [COLOR=#000000]2nd problem.[/COLOR]
 

 [COLOR=#000000]Every time I install new program, I make backup with Clonezilla. So, if I install Remastersys and try make backup, I will have next message:[/COLOR]
 

 [COLOR=#ff0000]Something wrong. This partition in the image is broken:sda1, Broken partition image were found, or some of them are not checkable in this image.[/COLOR]

Where are you backing up your clonezilla files?

Remastersys makes no changes to your system.  The changes happen in the temp folder /home/remastersys/remastersys/dummysys which is where /var and /etc are copied to before changing only the files in the temp folder.

Try removing your stuff from /etc/skel and remaster again.

---

### Post by Fragadelic on 2012-05-04
Some info regarding the casper issue for some folks.

This ONLY affects those using the iso image on USB and using persistence.  If you use it this way, DO NOT INSTALL IT TO A HARD DRIVE or you will have problems upgrading the kernel and initial ramdisk.

My official recommendation as it has always been, if you are planning to install your remaster, only use the usb mode WITHOUT persistence or use a cd/dvdrom.

---

### Post by xx58 on 2012-05-04
From Ubuntu 11.04 and previous versions, there was Remastersys work without problems. Was able to install it from any position like Direct Installation, from live DVD . Ubuntu 11.10 I was able to install only with Direct installation option. This time Ubuntu 12.04 I cannot install at all. 
So, only option is start from scratch and install Ubuntu 12.04 from from 0. I think it is my fault and don't know what do too rightly. Anyway I try, but I have 4 computers to load with Ubuntu 12.04 and have not time.

---

### Post by Fragadelic on 2012-05-04
Did you upgrade an older version to 12.04?  If you did, make sure everything upgraded properly. Usually issues arise if the upgrade wasn't clean and there are things left over from the older version.

Also try installing metacity to see if it helps with direct install.  Metacity used to be what was used for direct install from the menu.  I will do some testing maybe this weekend to see if there is something missing in remastersys for this.

---

### Post by xx58 on 2012-05-04
Clean Ubuntu 12.04

---

### Post by xx58 on 2012-05-04
OK, let say I put Remastersys DVD in CD/DVD ROM. Process start and now I am in Login screen.
1. Choice

Guest - do I use this option

2. Username and password  - do I use that options

so from that moment - need exact guide.

My system sign in is 
Username Alain
And password 1234

so if I sign in with that Alain and 1234 - will be invalid password
if I sign in like Guest - i will come to desktop, BUT anything I like to changer or start Custom Live DVD installation - need password - id I use password 1234 - invalid
So, where is solution
Thanks

---

### Post by firekage on 2012-05-06
> **xx58 said:**
> OK, let say I put Remastersys DVD in CD/DVD ROM. 

How to make Remaster DVD, or live version?

---

### Post by Fragadelic on 2012-05-06
> **xx58 said:**
> OK, let say I put Remastersys DVD in CD/DVD ROM. Process start and now I am in Login screen.
1. Choice

Guest - do I use this option

2. Username and password  - do I use that options

so from that moment - need exact guide.

My system sign in is 
Username Alain
And password 1234

so if I sign in with that Alain and 1234 - will be invalid password
if I sign in like Guest - i will come to desktop, BUT anything I like to changer or start Custom Live DVD installation - need password - id I use password 1234 - invalid
So, where is solution
Thanks

I see your issue.  You have kdm installed but lightdm is the default.  When kdm is installed, casper will modify it and then skip the rest of the login manager setups so lightdm isn't going to be setup.  Either use kdm or remove it cause it is the first choice in the casper scripts to configure and lightdm is never being setup.

---

### Post by bsad on 2012-05-07
> **Fragadelic said:**
> Some info regarding the casper issue for some folks.

This ONLY affects those using the iso image on USB and using persistence.  If you use it this way, DO NOT INSTALL IT TO A HARD DRIVE or you will have problems upgrading the kernel and initial ramdisk.

My official recommendation as it has always been, if you are planning to install your remaster, only use the usb mode WITHOUT persistence or use a cd/dvdrom.
I am using the ISO to USB without persistence. However, I am unable to launch the Ubiquity installer that appears on the desktop when remastering Lubuntu Precise. When I try to launch it manually from the command prompt (ubiquity --desktop %k gtk_ui) it quits after a few seconds. No user interface is seen at all.

I have confirmed that ubiquity and ubiquity-frontend-gtk are installed.

Any ideas? Although the icon now appears I have never been able to get Remastersys to work with previous Lubuntu releases either. Works great with LXDE on Debian Squeeze, though.

BTW this is a Lubuntu-minimal install.

---

### Post by traditionalist on 2012-05-07
Seems to work fine for me on 12.04 64 BIT.  I checked the custom distro by burning it to a CD. Seemed OK.  I am going to check if the complete personal backup works now from a DVD.  I have automatic boot enabled, and the custom distro worked OK

I am a newbie with Ubuntu, ( only been running it a couple of weeks), and this seems to be the best backup  system I have tried yet.  I tried a few others and they simply didn't work. I had a lot of problems setting my system up so that it was stable, but it seems OK now.  I am running Gnome classic, and everything settled down when I removed unity completely. 

Am burning my last backup to disc now and will try a boot with it.

Regards....Trad

---

### Post by Fragadelic on 2012-05-07
bsad - run ubiquity from a terminal window and see what error messages are showing up.

When you open up the terminal window, suod to root:

sudo su

Then run the ubiquity command:

ubiquity --desktop %k gtk_ui

If nothing is showing up, then you may be missing some app/library that isn't listed as a normal dependency for ubiquity and casper but should be.

It should show you something in the terminal window though especially if it is failing.

If that still doesn't show anything, run ubiquity in debugging mode to see what is going on.

ubiquity -d

---

### Post by bsad on 2012-05-07
> **Fragadelic said:**
> bsad - run ubiquity from a terminal window and see what error messages are showing up.

When you open up the terminal window, suod to root:

sudo su

Then run the ubiquity command:

ubiquity --desktop %k gtk_ui

If nothing is showing up, then you may be missing some app/library that isn't listed as a normal dependency for ubiquity and casper but should be.
Yea that is what I was trying... no return of anything even with -d. Maybe I'll try reinstalling Ubiquity. Very odd.

---

### Post by traditionalist on 2012-05-07
OK. Burned my last backup iso to DVD.  Booted the live system with that DVD.  PERFECT!   All my settings, menus, etc etc.  No problems whatsoever.  I am very pleased indeed with that.

Regards....Trad

---

### Post by Fragadelic on 2012-05-07
traditionalist - glad it worked as you expected!

bsad - that is really odd.  It should throw something up especially if it fails.  Can you post your remastersys.log for me to see?

---

### Post by bsad on 2012-05-08
> **Fragadelic said:**
> traditionalist - glad it worked as you expected!

bsad - that is really odd.  It should throw something up especially if it fails.  Can you post your remastersys.log for me to see?
After reinstalling Ubiquity I noted that ubiquity-frontend-gtk did not get installed by default this time, I installed it manually. I was able to launch the Ubuquity installer and proceed with the installation.

Is ubiquity-frontend-gtk a dependency of remastersys-gui? I am using it instead of remastersys-gtk as per your web site recommendations that -gtk is depreciated.

Thanks for your considerable time and effort toward developing this app!

---

### Post by Fragadelic on 2012-05-08
The frontends are not deps for any remastersys package(other than ubiquity-frontend-debconf which is a cli only minimal frontend for oem that I use to keep remastersys installed).  They are installed during the remastersys run which is why you need to have internet access so it can be downloaded and installed from the repository.

---

### Post by traditionalist on 2012-05-09
Hmmm....no idea what went wrong, but after reinstalling my system the package no longer works and I am unable to download it. Have tried since yesterday, just gives me errors.  It was working perfectly, so I know it does work.  No idea what to do right now.


EDIT: Finally got it to work again. For some reason it kept reverting to an old package before. Burning another  backup now.

EDIT. Doesn't work.  Just made another unbootable coaster. I will leave it for the time being and come back to it later.



Regards....Trad

---

### Post by xx58 on 2012-05-11
All I want is:
Download and install Remastersys and then make Dist DVD or Flash . Run and install and have easy transfer customer program. Is that much to ask. 
I DON'T WANT try, maybe or maybe not. It don't work for me, so I did all my 4 computers one by one without Remastersys, because it just don't work like I accept. 
I want DVD  put DVD Rom, start and install direct installation and thats all. IS THAT CLEAR.

---

### Post by Fragadelic on 2012-05-13
> **xx58 said:**
> All I want is:
Download and install Remastersys and then make Dist DVD or Flash . Run and install and have easy transfer customer program. Is that much to ask. 
I DON'T WANT try, maybe or maybe not. It don't work for me, so I did all my 4 computers one by one without Remastersys, because it just don't work like I accept. 
I want DVD  put DVD Rom, start and install direct installation and thats all. IS THAT CLEAR.

I'm trying to help you and you are being rude.  For what its worth, direct install from the boot menu works fine on ALL of my remasters so there is something wrong with your system setup.  Do as you please.

---

### Post by Fragadelic on 2012-05-13
**Important note regarding a recent update to syslinux on 12.04 and remastersys created iso's.**

I have found an issue when trying to boot on usb media.  It hangs at the isolinux boot: prompt.  If this affects you, please use only real cd/dvd media for the time being.

---

### Post by Fragadelic on 2012-05-13
**UPDATE** - there is a fix for this but it is manual.

If you use usb-creator(Startup Disk Creator) you must put the usb key back in after it finishes and do this at the command line:

sudo syslinux --install /dev/sdb1

Where sdb1 is the usb key partition you are installing it to.

Apparently it is using syslinux-legacy(3.63) which is very limited and remastersys iso's need the new syslinux(4.05)

---

### Post by Fragadelic on 2012-05-13
SECOND UPDATE - found the issue

The new usb-creator checks the ubuntu version from the .disk/info file from the iso.  What I have done for the new remastersys that will be released in a few days is that I took the first word from the LIVECDLABEL and then DISTRIB_RELEASE from /etc/lsb-release as it needs to see the ubuntu version from position 2 of the info contents.

I will be doing some testing over the next few days to ensure this works properly and then I'll release an update.

---

### Post by Éderson on 2012-05-17
I made a custom iso with remastersys for precise but the internet does not work. I tried wireless and cable but nothing worked. Is there anyone to help?

---

### Post by Fragadelic on 2012-05-17
Your issue is most likely related to dnsmasq. You could try disabling dnsmasq on your original system.  Check the link for instructions - [http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html)

---

### Post by Éderson on 2012-05-17
> **Fragadelic said:**
> Your issue is most likely related to dnsmasq. You could try disabling dnsmasq on your original system.  Check the link for instructions - [http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html)

I tried what you said but it still doesn't work. I connect normally at my wireless but the internet doesn't work.

---

### Post by Fragadelic on 2012-05-17
Try pinging [www.ubuntu.com](www.ubuntu.com) from a terminal window.  If it doesn't resolve then your issue is still with dnsmasq.  You probably are getting connected but you aren't getting name resolution due to dnsmasq.  If it is something else, post again.

---

### Post by Éderson on 2012-05-18
> **Fragadelic said:**
> Try pinging [www.ubuntu.com](www.ubuntu.com) from a terminal window.  If it doesn't resolve then your issue is still with dnsmasq.  You probably are getting connected but you aren't getting name resolution due to dnsmasq.  If it is something else, post again.

As you said, I tried to ping but I still haven't internet. I made a new iso on my wife's computer and the problem is the same. Anyone posted this before? Two differente computers with this problem and only I have it? :O

If you can help me, I'll be thankfull.

---

### Post by Fragadelic on 2012-05-18
Post the output of the following from one of the one you are having problems with:

sudo ifconfig

sudo netstat -r

---

### Post by Éderson on 2012-05-18
> **Fragadelic said:**
> Post the output of the following from one of the one you are having problems with:

sudo ifconfig

sudo netstat -r

Well, this is mine after change dnsmasq with the link instructions:


ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:c5:39:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16052 (16.0 KB)  TX bytes:16052 (16.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:99:6f:fe  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe99:6ffe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1486 (1.4 KB)  TX bytes:14016 (14.0 KB)

###################################################################

ubuntu@ubuntu:~$ sudo netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
192.168.0.0     *               255.255.255.0   U         0 0          0 wlan0

---

### Post by Éderson on 2012-05-18
This is without change the dnsmasq (My wife's laptop)

ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:be:7c:46:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11308 (11.3 KB)  TX bytes:11308 (11.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:34:6d:d4  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe34:6dd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1486 (1.4 KB)  TX bytes:16737 (16.7 KB)


#######################################################################################

ubuntu@ubuntu:~$ sudo netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

default         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
192.168.0.0     *               255.255.255.0   U         0 0          0 wlan0

---

### Post by Fragadelic on 2012-05-18
Everything I am seeing is pointing to a dnsmasq issue.  Show me everything you did to disable dnsmasq.

---

### Post by Fragadelic on 2012-05-18
The funny thing is that I use NetworkManager on my home remasters with wireless and dnsmasq is running fine.

Not sure what is different about your setup though.  What desktop are you running?

Post your remastersys.log so I can look at it.

---

### Post by Éderson on 2012-05-18
I'd like to tell that I always remaster my ubuntu to friends and this never happened


That's what I made:
edited /etc/NetworkManager/NetworkManager.conf file with:
gksudo gedit /etc/NetworkManager/NetworkManager.conf
changed dns=dnsmasq to #dns=dnsmasq
and sudo restart network-manager

I made as above but it continued without work so I removed the # and remastered again.
It's good to tell that when I run the iso with virtualbox, everything work well, even internet but when I burn the CD or flashdrive, no internet again, even with the wireless conected.
I use Ubuntu 12.04 (Precise).

I can't paste the log file here cause it's too big. I it's really needed, I can put it in with a link.

---

### Post by Éderson on 2012-05-20
I discovered more people with the same problem:
[http://www.remastersys.com/forums/index.php?topic=2065.0](http://www.remastersys.com/forums/index.php?topic=2065.0)

---

### Post by Fragadelic on 2012-05-20
Right but you just mentioned that the same iso works fine on virtual box and not on your regular systems.  This tells me something on your home network setup is causing issues with dnsmasq/NetworkManager.

---

### Post by Éderson on 2012-05-22
Solved. Follow this link: [http://www.remastersys.com/forums/index.php?topic=2065.0](http://www.remastersys.com/forums/index.php?topic=2065.0)

---

### Post by cataclop on 2012-05-23
Hello,

Just a detail for those who would be interrested : I had problems building a live of my ubuntu, because I had too many things on it and the size of the squashfs was too big. I added "-*comp xz"  *at the end of SQUASHFSOPTS, and saved about 20% of the space, at the cost of a (quite) longer build.

Hope this will be usefull.

---

### Post by Fragadelic on 2012-05-24
Just be aware that if you share this with others there are folks who may have issues with it not being able to boot properly.

---

### Post by HalfNote5 on 2012-05-25
Hi everyone! I posed the following question the other day in a different part of the forum, but was helpfully redirected here.

> I think you would be best to ask here -

[http://ubuntuforums.org/showthread.p...light=remaster]("http://ubuntuforums.org/showthread.php?t=1967865&highlight=remaster")

Rodney
 		                   		  		  		 		 			 				__________________
				Asus P5Q Pro MB, Intel Core 2 Duo CPU E8400 3.00GHz 
GSkill DDR2 8Gig Ram, Asus 9600GT Video 

Toshiba Satellite L500/08P Laptop 			


My original question was as follows:

> **Remastersys works great. Then uninstalls itself completely!?** 			
 			 			 		   		 		 		Hi everyone! I'm just loading up a copy of Xubuntu with all the goodies we wanna carry around in our pockets on a daily basis. 

As usual, I'm using Remastersys to wrap it all up into an ISO. 

Now, Remastersys is working great, AND Remastersys is appearing IN the ISO image.... so far so good.

Now... we make a few tweaks on the original machine, and try to run Remastersys again and...... it's GONE. Poof. Thin air. Nada.

Oh sure, apt-get install remastersys puts it back, but it's a little  wierd for a program to just up and disappear every time you use it, eh?

Anyone have any idea what's going on with it? Is this an intentional  behavior of the new version? ( I don't see why it would be...)

Thanks! ):P


---

### Post by Fragadelic on 2012-05-25
You are using an old version of remastersys.  Please upgrade to 3.0.3-1.

---

### Post by HalfNote5 on 2012-05-25
> **Fragadelic said:**
> You are using an old version of remastersys.  Please upgrade to 3.0.3-1.


Thanks! Quick question, though;  what should I have in my sources.list file as the repository?  I'm using Precise. and:
 [http://www.remastersys.com/repository](http://www.remastersys.com/repository)
and also,
[http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository)

By the way, your software is awesome. Remastersys has saved our clients' tails at numerous times.

---

### Post by Fragadelic on 2012-05-25
That is really old.  I have a new signed repository.  You can find the info on my Ubuntu page on my website.

---

### Post by Fragadelic on 2012-05-25
Really busy and forgot to say thanks for the nice endorsement!

---

### Post by HalfNote5 on 2012-05-25
> **Fragadelic said:**
> Really busy and forgot to say thanks for the nice endorsement!

It is I who should be thanking you. You've created one of the single most useful software packages I've ever had. Can't wait to check out the new version.  = )

Cheers!

---

### Post by rupertocowo on 2012-07-24
Thanks for reviving remastersys
It installs fine on precise but remastersys-gui cannot open from the menu except from the terminal as super user. After editing menu I noticed it has gksu before the program to run. Do I really need to download gksu or should I just change the words. I tried sudo, sudo su, and sudo su root but none works ... I also tried it with no words but it says it has to be run as root. Plz help

** should have been kdesudo remastersys-gui instead of gksu remastersys-gui to the command in menu edit

---

