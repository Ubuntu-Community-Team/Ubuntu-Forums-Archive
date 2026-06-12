---
title: "Upgraded to 12.04 now my keyboard and mouse don't work...can't get passed the login"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by opasnost on 2012-04-05
Hi,

I upgraded to 12.04 from 11.10 last night using the update-manager -d command. It updated but there were a couple errors and warnings. However now I'm having problems.

After grub I get a string of errors all saying the same thing:

init: Failed to create pty - disabling logging for job

I dont do anything and eventually the ubuntu logo comes on and I get a screen saying:

An error occured while mounting /boot 
press S to skip or M for manual recovery

I press S which takes me to my login screen but my keyboard and mouse do not work so I can't login

If I press M it takes me the maintenance shell. Some more error lines are:

mount: unknown filesystem type 'ext2'
mountall: mount /boot [786] terminated with status 32
mountall: Filesystem could not be mounted: /boot


some additional info. I am using a gateway laptop. /boot is on a separate partition. The keyboard works once in the maintenance shell.


Please help. I will be checking up constantly as I need to fix this as I use this laptop for work....

---

### Post by oldos2er on 2012-04-05
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by opasnost on 2012-04-07
bump....please help. Can anybody tell me what log files i can upload to help diagnose and fix this problem?

---

### Post by cariboo on 2012-04-07
So do your mouse and keyboard not work at all, or does lightdm just koopback to the login screen.

As far as logs go, you might want to paste the output of /var/log/auth.log in your next post. Please remember to use code tags:

> [noparse]```
 
```[/noparse]

---

### Post by swenson on 2012-04-09
+1 for keyboard and mouse not working after 12.04 Beta 2 installed.

My machine has also stopped responding to SSH, so it is very difficult for me to diagnose.

All I see is the login screen with the cursor blinking in the password field under my name.

---

### Post by heald490 on 2012-04-10
+Another one...  I posted a similar thread ([link]("http://ubuntuforums.org/showthread.php?t=1952519&highlight=heald490")) last week in the beginner forum but haven't had any time to mess around with anything until this morning.  I tried Kubuntu 12.04 and the same thing happens.  I've not been actively using Ubuntu, so really I'm just trying out different versions.  Not a huge deal that they aren't working for me at the moment.  Here is the text of my original thread:

> Hi,
I had 11.10 running successfully with no issues on my computer (ASUS P8P67 Deluxe MB, Intel i7/2600k, EVGA GTX580, 8gb ram) everything worked as it was supposed to. I have it setup to dual boot with Windows 7

I decided to try upgrading to 12.04. I did that last night and everything seemed to go as planned until I rebooted, once I got to the login screen, the mouse was extremely unresponsive for about 45 seconds, then finally began to work. Once it started working I tried to enter my password, but the keyboard did not work (it had power, but there was no response to any keypress -- including caps lock). Also, nothing I clicked on with the mouse had any effect.

So, I figured something went wrong with the update and I downloaded the cd image. The same thing occurs when I boot off the CD. Also if I try to install from the CD, when I get to the point of selecting a language, again the keyboard does not work, and mouse clicks do not have any effect.

My keyboard and mouse are both USB, keyboard is a Microsoft Natural Ergo 4000 if that matters.

Any help would be appreciated.. I don't know where to begin or what to do.

Thanks!

---

### Post by swenson on 2012-04-10
I fixed it on my box by doing the following:

Booted to 12.04 CD.

Mounted my partition under /mnt/linux

```

sudo chroot /mnt/linux su
mount /dev
mount /proc
mount /sys
apt-get update
apt-get upgrade
apt-get dist-upgrade

```

This gave me a few error messages, but when I rebooted, everything worked.

Though my system seems to be in a weird state now, but it is bootable, I can SSH into it, and my keyboard and mouse work now.

---

### Post by opasnost on 2012-04-11
Thanks Swenson,

I'm gonna give that a try and let everyone know how it goes...

---

### Post by heald490 on 2012-04-11
Your keyboard / mouse worked fine booting off the CD?  Mine doesn't.. booting off the CD or booting my install does the same thing - no keyboard response and mouse clicks do nothing.

---

### Post by cariboo on 2012-04-11
This problem showed up early on in testing, back then, just unplugging the mouse and keyboard solved the problem. 

If the above solution worked, please report the bug.

---

### Post by lazymanc on 2012-04-12
Exactly the same problem:


[LIST]
[*]Upgrading from a fully-working 11.10 (64-bit) -> 12.04 beta 2
[*]Also have dual boot with Windows 7 on a separate drive
[*]Upgrade process seemed to go ok until the reboot (couple of warnings but it didn't halt or anything).
[*]After reboot, if I pick linux from GRUB, I get an ugly log in screen but no keyboard or mouse input.
[*]If I boot to windows, everything works as normal.
[/LIST]
Will try pulling the cables and re-inserting, if that doesn't work I'll try the recovery method above.

---

### Post by heald490 on 2012-04-12
I had tried unplugging the cables and putting them back, also tried a different keyboard, nothing seemed to help

---

### Post by lazymanc on 2012-04-12
Ok, I followed the instructions here:
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

and managed to get a bootable desktop, but there's clearly broken packages.

I've tried to remedy this with sudo apt-get upgrade and sudo apt-get -f install but I'm now stuck with the following errors:

```

phil@phil-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 gvfs : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu5 is installed
        Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu5 is installed
 gvfs-backends : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu5 is installed
                 Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu5 is installed
 gvfs-daemons : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu5 is installed
                Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu5 is installed
 ubuntu-sso-client-qt : Depends: python-ubuntu-sso-client (= 2.99.92-0ubuntu2) but 3.0.0-0ubuntu1 is installed
                        Depends: ubuntu-sso-client (= 2.99.92-0ubuntu2) but 3.0.0-0ubuntu1 is installed
 ubuntuone-control-panel-qt : Depends: python-ubuntuone-control-panel (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is installed
                              Depends: ubuntuone-control-panel (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is installed
                              Depends: ubuntuone-control-panel-common (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
phil@phil-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libstdc++6:i386 libxfixes3:i386 libaccess-bridge-java libxcomposite1:i386 libldap-2.4-2:i386 libroken18-heimdal:i386 libidn11:i386 libnss3:i386
  libwrap0:i386 nspluginwrapper libsamplerate0:i386 libjpeg-turbo8:i386 libx264-116 libfile-homedir-perl libjpeg8:i386 libmagickcore3 libmagickwand3 libasn1-8-heimdal:i386 libjack-jackd2-0:i386
  libiso9660-7 libnspr4-0d:i386 libcairo2:i386 libgnutls26:i386 libgssapi3-heimdal:i386 libtasn1-3:i386 libfreetype6:i386 python-encutils libexpat1:i386 libdatrie1:i386 libavahi-common-data:i386
  libjson0:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386 libp11-kit0:i386 libaccess-bridge-java-jni libwind0-heimdal:i386 libxau6:i386 python-clientform libpixman-1-0:i386 libcups2:i386 libcurl3:i386
  libxinerama1:i386 libkrb5support0:i386 nspluginviewer:i386 libxft2:i386 libvpx0 python-django libmatroska4 libice6:i386 libspeexdsp1:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386 libkeyutils1:i386
  libasound2:i386 libflac8:i386 libxrender1:i386 libhcrypto4-heimdal:i386 python-cssutils-doc libnspr4:i386 libhx509-5-heimdal:i386 libvorbisenc2:i386 python-django-tagging libasyncns0:i386
  libheimbase1-heimdal:i386 libtiff4:i386 libjasper1:i386 libjpeg62:i386 libattica0 libavahi-client3:i386 libx11-6:i386 libsasl2-2:i386 libid3tag0 libfontconfig1:i386 libpango1.0-0:i386 libsm6:i386
  libmusicbrainz4c2a libpulse0:i386 libmagickcore3-extra libheimntlm0-heimdal:i386 libxdamage1:i386 openoffice.org-common libxcb-render0:i386 librtmp0:i386 libgssapi-krb5-2:i386 libxi6:i386
  libvorbis0a:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386 libxext6:i386 libsasl2-modules:i386 libavahi-common3:i386 libxrandr2:i386 libnss3-1d:i386 libsndfile1:i386 libsqlite3-0:i386
  libgtk2.0-0:i386 libkrb5-26-heimdal:i386 libasound2-plugins:i386 libgpg-error0:i386 libogg0:i386 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gvfs gvfs-backends gvfs-daemons gvfs-fuse ubuntu-sso-client-qt ubuntuone-control-panel-gtk ubuntuone-control-panel-qt
The following packages will be upgraded:
  gvfs gvfs-backends gvfs-daemons gvfs-fuse ubuntu-sso-client-qt ubuntuone-control-panel-gtk ubuntuone-control-panel-qt
7 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
13 not fully installed or removed.
Need to get 0 B/2,682 kB of archives.
After this operation, 23.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of gvfs-daemons:
 gvfs-daemons depends on gvfs-libs (= 1.12.0-0ubuntu4); however:
  Version of gvfs-libs on system is 1.12.0-0ubuntu5.
 gvfs-daemons depends on gvfs-common (= 1.12.0-0ubuntu4); however:
  Version of gvfs-common on system is 1.12.0-0ubuntu5.
dpkg: error processing gvfs-daemons (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gvfs:
 gvfs depends on gvfs-daemons (>= 1.12.0-0ubuntu4); however:
  Package gvfs-daemons is not configured yet.
 gvfs depends on gvfs-daemons (<< 1.12.0-0ubuntu4.1~); however:
  Package gvfs-daemons is not configured yet.
 gvfs depends on gvfs-libs (= 1.12.0-0ubuntu4); however:
  Version of gvfs-libs on system is 1.12.0-0ubuntu5.
 gvfs depends on gvfs-common (= 1.12.0-0ubuntu4); however:
  Version of gvfs-common on system is 1.12.0-0ubuntu5.
dpkg: error processing gvfs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gvfs-fuse:
 gvfs-fuse depends on gvfs (= 1.12.0-0ubuntu4); however:
  Package gvfs is not configured yet.
dpkg: error processing gvfs-fuse (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on gvfs (= 1.12.0-0ubuntu4); however:
  Package gvfs is not configured yet.
 gvfs-backends depends on gvfs-daemons (= 1.12.0-0ubuntu4); however:
  Package gvfs-daemons is not configured yet.
 gvfs-backends depends on gvfs-libs (= 1.12.0-0ubuntu4); however:
  Version of gvfs-libs on system is 1.12.0-0ubuntu5.
 gvfs-backends depends on gvfs-common (= 1.12.0-0ubuntu4); however:
  Version of gvfs-common on system is 1.12.0-0ubuntu5.
dpkg: error processing gvfs-backends (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gvfs; however:
  Package gvfs is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gvfs (>= 1.3.2); however:
  Package gvfs is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on nautilus (>= 1:2.91); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on nautilus-sendto; however:
  Package nautilus-sendto is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-sso-client-qt:
 ubuntu-sso-client-qt depends on python-ubuntu-sso-client (= 2.99.92-0ubuntu2); however:
  Version of python-ubuntu-sso-client on system is 3.0.0-0ubuntu1.
 ubuntu-sso-client-qt depends on ubuntu-sso-client (= 2.99.92-0ubuntu2); however:
  Version of ubuntu-sso-client on system is 3.0.0-0ubuntu1.
dpkg: error processing ubuntu-sso-client-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntuone-control-panel-qt:
 ubuntuone-control-panel-qt depends on python-ubuntuone-control-panel (= 2.99.92-0ubuntu1); however:
  Version of python-ubuntuone-control-panel on system is 3.0.0-0ubuntu1.
 ubuntuone-control-panel-qt depends on ubuntu-sso-client-qt (>= 2.99.92); however:
  Package ubuntu-sso-client-qt is not configured yet.
 ubuntuone-control-panel-qt depends on ubuntuone-control-panel (= 2.99.92-0ubuntu1); however:
  Version of ubuntuone-control-panel on system is 3.0.0-0ubuntu1.
 ubuntuone-control-panel-qt depends on ubuntuone-control-panel-common (= 2.99.92-0ubuntu1); however:
  Version of ubuntuone-control-panel-common on system is 3.0.0-0ubuntu1.
dpkg: error processing ubuntuone-control-panel-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntuone-control-panel-gtk:
 ubuntuone-control-panel-gtk depends on ubuntuone-control-panel-qt (= 2.99.92-0ubuntu1); however:
  Package ubuntuone-control-panel-qt is not configured yet.
dpkg: error processing ubuntuone-control-panel-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 gvfs-daemons
 gvfs
 gvfs-fuse
 gvfs-backends
 brasero
 nautilus
 gnome-session
 nautilus-sendto
 nautilus-share
 ubuntu-desktop
 ubuntu-sso-client-qt
 ubuntuone-control-panel-qt
 ubuntuone-control-panel-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Where do I go from here to fix the rest of the packages?

---

### Post by opasnost on 2012-04-12
> **swenson said:**
> I fixed it on my box by doing the following:

Booted to 12.04 CD.

Mounted my partition under /mnt/linux

```

sudo chroot /mnt/linux su
mount /dev
mount /proc
mount /sys
apt-get update
apt-get upgrade
apt-get dist-upgrade

```This gave me a few error messages, but when I rebooted, everything worked.

Though my system seems to be in a weird state now, but it is bootable, I can SSH into it, and my keyboard and mouse work now.

I'm glad this worked for you swenson but unfortunately this hasn't changed anything keyboard and mouse still not working.

---

### Post by opasnost on 2012-04-12
> **cariboo907 said:**
> So do your mouse and keyboard not work at all, or does lightdm just koopback to the login screen.

As far as logs go, you might want to paste the output of /var/log/auth.log in your next post. Please remember to use code tags:

My mouse and keyboard do not work at all once into lightdm. Here is my auth.log:

```
Apr  2 17:05:48 gateway-ubuntu-sda8 polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:adrian8 to gain TEMPORARY authorization for action com.ubuntu.softwareproperties.applychanges for unix-process:3019:403368 [/usr/bin/python /usr/bin/software-properties-gtk --open-tab 2] (owned by unix-user:adrian8)
Apr  2 17:08:12 gateway-ubuntu-sda8 polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:adrian8 to gain TEMPORARY authorization for action com.ubuntu.softwareproperties.applychanges for unix-process:3160:418727 [/usr/bin/python /usr/bin/software-properties-gtk --open-tab 2] (owned by unix-user:adrian8)
Apr  2 17:13:55 gateway-ubuntu-sda8 polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.54, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8) (disconnected from bus)
Apr  2 17:13:55 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session closed for user adrian8
Apr  2 18:13:37 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  2 18:13:37 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  2 18:13:38 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  2 18:13:38 gateway-ubuntu-sda8 dbus[1033]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.28" (uid=104 pid=1661 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.18" (uid=0 pid=1432 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  2 18:13:42 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session closed for user lightdm
Apr  2 18:13:43 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user adrian8 by (uid=0)
Apr  2 18:13:43 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  2 18:13:45 gateway-ubuntu-sda8 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.48 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8)
Apr  2 18:13:49 gateway-ubuntu-sda8 dbus[1033]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.56" (uid=1000 pid=2030 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.18" (uid=0 pid=1432 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  2 18:17:01 gateway-ubuntu-sda8 CRON[2345]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  2 18:17:01 gateway-ubuntu-sda8 CRON[2345]: pam_unix(cron:session): session closed for user root
Apr  2 19:17:01 gateway-ubuntu-sda8 CRON[2474]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  2 19:17:01 gateway-ubuntu-sda8 CRON[2474]: pam_unix(cron:session): session closed for user root
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2685]: Successful su for adrian8 by root
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2685]: + ??? root:adrian8
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2685]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2685]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2695]: Successful su for adrian8 by root
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2695]: + ??? root:adrian8
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2695]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2695]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2710]: Successful su for adrian8 by root
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2710]: + ??? root:adrian8
Apr  2 19:29:14 gateway-ubuntu-sda8 su[2710]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2710]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2738]: Successful su for adrian8 by root
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2738]: + ??? root:adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2738]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2738]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2748]: Successful su for adrian8 by root
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2748]: + ??? root:adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2748]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2748]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2763]: Successful su for adrian8 by root
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2763]: + ??? root:adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2763]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2763]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2776]: Successful su for adrian8 by root
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2776]: + ??? root:adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2776]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2776]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2789]: Successful su for adrian8 by root
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2789]: + ??? root:adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2789]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2789]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2804]: Successful su for adrian8 by root
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2804]: + ??? root:adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2804]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2804]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2817]: Successful su for adrian8 by root
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2817]: + ??? root:adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2817]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2817]: pam_unix(su:session): session closed for user adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2830]: Successful su for adrian8 by root
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2830]: + ??? root:adrian8
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2830]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 19:29:15 gateway-ubuntu-sda8 su[2830]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3135]: Successful su for adrian8 by root
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3135]: + ??? root:adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3135]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3135]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3151]: Successful su for adrian8 by root
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3151]: + ??? root:adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3151]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3151]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3166]: Successful su for adrian8 by root
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3166]: + ??? root:adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3166]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3166]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3175]: Successful su for adrian8 by root
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3175]: + ??? root:adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3175]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3175]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3196]: Successful su for adrian8 by root
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3196]: + ??? root:adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3196]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3196]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3211]: Successful su for adrian8 by root
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3211]: + ??? root:adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3211]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3211]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3226]: Successful su for adrian8 by root
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3226]: + ??? root:adrian8
Apr  2 20:22:05 gateway-ubuntu-sda8 su[3226]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 20:22:06 gateway-ubuntu-sda8 su[3226]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:06 gateway-ubuntu-sda8 su[3235]: Successful su for adrian8 by root
Apr  2 20:22:06 gateway-ubuntu-sda8 su[3235]: + ??? root:adrian8
Apr  2 20:22:06 gateway-ubuntu-sda8 su[3235]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 20:22:06 gateway-ubuntu-sda8 su[3235]: pam_unix(su:session): session closed for user adrian8
Apr  2 20:22:13 gateway-ubuntu-sda8 gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4751]: Successful su for adrian8 by root
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4751]: + ??? root:adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4751]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4751]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4761]: Successful su for adrian8 by root
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4761]: + ??? root:adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4761]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4761]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4776]: Successful su for adrian8 by root
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4776]: + ??? root:adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4776]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4776]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4804]: Successful su for adrian8 by root
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4804]: + ??? root:adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4804]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4804]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4814]: Successful su for adrian8 by root
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4814]: + ??? root:adrian8
Apr  2 21:00:19 gateway-ubuntu-sda8 su[4814]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4814]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4829]: Successful su for adrian8 by root
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4829]: + ??? root:adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4829]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4829]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4842]: Successful su for adrian8 by root
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4842]: + ??? root:adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4842]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4842]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4855]: Successful su for adrian8 by root
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4855]: + ??? root:adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4855]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4855]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4870]: Successful su for adrian8 by root
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4870]: + ??? root:adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4870]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4870]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4883]: Successful su for adrian8 by root
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4883]: + ??? root:adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4883]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4883]: pam_unix(su:session): session closed for user adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4896]: Successful su for adrian8 by root
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4896]: + ??? root:adrian8
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4896]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  2 21:00:20 gateway-ubuntu-sda8 su[4896]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5201]: Successful su for adrian8 by root
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5201]: + ??? root:adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5201]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5201]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5217]: Successful su for adrian8 by root
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5217]: + ??? root:adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5217]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5217]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5230]: Successful su for adrian8 by root
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5230]: + ??? root:adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5230]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5230]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5241]: Successful su for adrian8 by root
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5241]: + ??? root:adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5241]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5241]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5262]: Successful su for adrian8 by root
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5262]: + ??? root:adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5262]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5262]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5275]: Successful su for adrian8 by root
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5275]: + ??? root:adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5275]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5275]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5292]: Successful su for adrian8 by root
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5292]: + ??? root:adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5292]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5292]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5301]: Successful su for adrian8 by root
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5301]: + ??? root:adrian8
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5301]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 00:31:51 gateway-ubuntu-sda8 su[5301]: pam_unix(su:session): session closed for user adrian8
Apr  3 00:32:51 gateway-ubuntu-sda8 gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr  3 00:44:30 gateway-ubuntu-sda8 polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.48, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8) (disconnected from bus)
Apr  3 00:44:30 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session closed for user adrian8
Apr  3 12:17:17 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  3 12:17:17 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  3 12:17:18 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  3 12:17:18 gateway-ubuntu-sda8 dbus[1016]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.28" (uid=104 pid=1650 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1464 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  3 12:18:53 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session closed for user lightdm
Apr  3 12:18:54 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user adrian8 by (uid=0)
Apr  3 12:18:54 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  3 12:18:57 gateway-ubuntu-sda8 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.51 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8)
Apr  3 12:19:01 gateway-ubuntu-sda8 dbus[1016]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=2024 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1464 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2543]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2543]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2543]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2543]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2553]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2553]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2553]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2553]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2568]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2568]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2568]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2568]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2596]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2596]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2596]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2596]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2606]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2606]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2606]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2606]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2621]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2621]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2621]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2621]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2634]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2634]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2634]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2634]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2647]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2647]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2647]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2647]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2662]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2662]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2662]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2662]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2675]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2675]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2675]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2675]: pam_unix(su:session): session closed for user adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2688]: Successful su for adrian8 by root
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2688]: + ??? root:adrian8
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2688]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 12:52:54 gateway-ubuntu-sda8 su[2688]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[2992]: Successful su for adrian8 by root
Apr  3 14:11:32 gateway-ubuntu-sda8 su[2992]: + ??? root:adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[2992]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 14:11:32 gateway-ubuntu-sda8 su[2992]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3006]: Successful su for adrian8 by root
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3006]: + ??? root:adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3006]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3006]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3023]: Successful su for adrian8 by root
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3023]: + ??? root:adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3023]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3023]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3032]: Successful su for adrian8 by root
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3032]: + ??? root:adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3032]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3032]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3053]: Successful su for adrian8 by root
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3053]: + ??? root:adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3053]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3053]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3068]: Successful su for adrian8 by root
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3068]: + ??? root:adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3068]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3068]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3083]: Successful su for adrian8 by root
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3083]: + ??? root:adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3083]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3083]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3092]: Successful su for adrian8 by root
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3092]: + ??? root:adrian8
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3092]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 14:11:32 gateway-ubuntu-sda8 su[3092]: pam_unix(su:session): session closed for user adrian8
Apr  3 14:11:59 gateway-ubuntu-sda8 gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr  3 14:17:01 gateway-ubuntu-sda8 CRON[3360]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 14:17:01 gateway-ubuntu-sda8 CRON[3360]: pam_unix(cron:session): session closed for user root
Apr  3 15:17:01 gateway-ubuntu-sda8 CRON[3564]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 15:17:01 gateway-ubuntu-sda8 CRON[3564]: pam_unix(cron:session): session closed for user root
Apr  3 16:17:01 gateway-ubuntu-sda8 CRON[3908]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 16:17:01 gateway-ubuntu-sda8 CRON[3908]: pam_unix(cron:session): session closed for user root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4109]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4109]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4109]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4109]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4119]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4119]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4119]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4119]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4134]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4134]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4134]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4134]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4162]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4162]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4162]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4162]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4172]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4172]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4172]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4172]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4187]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4187]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4187]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4187]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4200]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4200]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4200]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4200]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4214]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4214]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4214]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4214]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4228]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4228]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4228]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4228]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4241]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4241]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4241]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4241]: pam_unix(su:session): session closed for user adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4254]: Successful su for adrian8 by root
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4254]: + ??? root:adrian8
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4254]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 16:27:35 gateway-ubuntu-sda8 su[4254]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4557]: Successful su for adrian8 by root
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4557]: + ??? root:adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4557]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4557]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4573]: Successful su for adrian8 by root
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4573]: + ??? root:adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4573]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4573]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4588]: Successful su for adrian8 by root
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4588]: + ??? root:adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4588]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4588]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4597]: Successful su for adrian8 by root
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4597]: + ??? root:adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4597]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4597]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4616]: Successful su for adrian8 by root
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4616]: + ??? root:adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4616]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4616]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4631]: Successful su for adrian8 by root
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4631]: + ??? root:adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4631]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4631]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4648]: Successful su for adrian8 by root
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4648]: + ??? root:adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4648]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4648]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4657]: Successful su for adrian8 by root
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4657]: + ??? root:adrian8
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4657]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:25:01 gateway-ubuntu-sda8 su[4657]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:25:07 gateway-ubuntu-sda8 gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5102]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5102]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5102]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5102]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5112]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5112]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5112]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5112]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5127]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5127]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5127]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5127]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5155]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5155]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5155]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5155]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5165]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5165]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5165]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5165]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5180]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5180]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5180]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5180]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5193]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5193]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5193]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5193]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5206]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5206]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5206]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5206]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5221]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5221]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5221]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5221]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5234]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5234]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5234]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5234]: pam_unix(su:session): session closed for user adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5247]: Successful su for adrian8 by root
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5247]: + ??? root:adrian8
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5247]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 17:26:07 gateway-ubuntu-sda8 su[5247]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5497]: Successful su for adrian8 by root
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5497]: + ??? root:adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5497]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5497]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5513]: Successful su for adrian8 by root
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5513]: + ??? root:adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5513]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5513]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5528]: Successful su for adrian8 by root
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5528]: + ??? root:adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5528]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5528]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5537]: Successful su for adrian8 by root
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5537]: + ??? root:adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5537]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5537]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5558]: Successful su for adrian8 by root
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5558]: + ??? root:adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5558]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5558]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5573]: Successful su for adrian8 by root
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5573]: + ??? root:adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5573]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5573]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5588]: Successful su for adrian8 by root
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5588]: + ??? root:adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5588]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5588]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5597]: Successful su for adrian8 by root
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5597]: + ??? root:adrian8
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5597]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:00:13 gateway-ubuntu-sda8 su[5597]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:00:22 gateway-ubuntu-sda8 unix_chkpwd[5701]: password check failed for user (adrian8)
Apr  3 19:00:22 gateway-ubuntu-sda8 gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=adrian8
Apr  3 19:00:22 gateway-ubuntu-sda8 gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): getting password (0x00000388)
Apr  3 19:00:22 gateway-ubuntu-sda8 gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): pam_get_item returned a password
Apr  3 19:00:22 gateway-ubuntu-sda8 gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Apr  3 19:00:29 gateway-ubuntu-sda8 unix_chkpwd[5760]: password check failed for user (adrian8)
Apr  3 19:00:29 gateway-ubuntu-sda8 gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=adrian8
Apr  3 19:00:29 gateway-ubuntu-sda8 gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): getting password (0x00000388)
Apr  3 19:00:29 gateway-ubuntu-sda8 gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): pam_get_item returned a password
Apr  3 19:00:29 gateway-ubuntu-sda8 gnome-screensaver-dialog: pam_winbind(gnome-screensaver:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Apr  3 19:00:37 gateway-ubuntu-sda8 gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr  3 19:17:01 gateway-ubuntu-sda8 CRON[5852]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  3 19:17:02 gateway-ubuntu-sda8 CRON[5852]: pam_unix(cron:session): session closed for user root
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6002]: Successful su for adrian8 by root
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6002]: + ??? root:adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6002]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6002]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6012]: Successful su for adrian8 by root
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6012]: + ??? root:adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6012]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6012]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6027]: Successful su for adrian8 by root
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6027]: + ??? root:adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6027]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6027]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6055]: Successful su for adrian8 by root
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6055]: + ??? root:adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6055]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6055]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6065]: Successful su for adrian8 by root
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6065]: + ??? root:adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6065]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6065]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6080]: Successful su for adrian8 by root
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6080]: + ??? root:adrian8
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6080]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:14 gateway-ubuntu-sda8 su[6080]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6093]: Successful su for adrian8 by root
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6093]: + ??? root:adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6093]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6093]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6106]: Successful su for adrian8 by root
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6106]: + ??? root:adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6106]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6106]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6121]: Successful su for adrian8 by root
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6121]: + ??? root:adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6121]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6121]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6134]: Successful su for adrian8 by root
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6134]: + ??? root:adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6134]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6134]: pam_unix(su:session): session closed for user adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6147]: Successful su for adrian8 by root
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6147]: + ??? root:adrian8
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6147]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  3 19:21:15 gateway-ubuntu-sda8 su[6147]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:09 gateway-ubuntu-sda8 su[6453]: Successful su for adrian8 by root
Apr  4 13:43:09 gateway-ubuntu-sda8 su[6453]: + ??? root:adrian8
Apr  4 13:43:09 gateway-ubuntu-sda8 su[6453]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6453]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6467]: Successful su for adrian8 by root
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6467]: + ??? root:adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6467]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6467]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6480]: Successful su for adrian8 by root
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6480]: + ??? root:adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6480]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6480]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6493]: Successful su for adrian8 by root
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6493]: + ??? root:adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6493]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6493]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6510]: Successful su for adrian8 by root
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6510]: + ??? root:adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6510]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6510]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6526]: Successful su for adrian8 by root
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6526]: + ??? root:adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6526]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6526]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6540]: Successful su for adrian8 by root
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6540]: + ??? root:adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6540]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6540]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6553]: Successful su for adrian8 by root
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6553]: + ??? root:adrian8
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6553]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 13:43:10 gateway-ubuntu-sda8 su[6553]: pam_unix(su:session): session closed for user adrian8
Apr  4 13:43:32 gateway-ubuntu-sda8 gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr  4 14:17:01 gateway-ubuntu-sda8 CRON[7631]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  4 14:17:01 gateway-ubuntu-sda8 CRON[7631]: pam_unix(cron:session): session closed for user root
Apr  4 15:17:01 gateway-ubuntu-sda8 CRON[7829]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  4 15:17:01 gateway-ubuntu-sda8 CRON[7829]: pam_unix(cron:session): session closed for user root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8032]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8032]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8032]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8032]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8042]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8042]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8042]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8042]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8057]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8057]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8057]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8057]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8085]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8085]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8085]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8085]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8095]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8095]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8095]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8095]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8110]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8110]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8110]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8110]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8123]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8123]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8123]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8123]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8136]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8136]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8136]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8136]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8151]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8151]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8151]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8151]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8164]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8164]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8164]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8164]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8177]: Successful su for adrian8 by root
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8177]: + ??? root:adrian8
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8177]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:48 gateway-ubuntu-sda8 su[8177]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8478]: Successful su for adrian8 by root
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8478]: + ??? root:adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8478]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8478]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8494]: Successful su for adrian8 by root
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8494]: + ??? root:adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8494]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8494]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8509]: Successful su for adrian8 by root
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8509]: + ??? root:adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8509]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8509]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8518]: Successful su for adrian8 by root
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8518]: + ??? root:adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8518]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8518]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8537]: Successful su for adrian8 by root
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8537]: + ??? root:adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8537]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8537]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8552]: Successful su for adrian8 by root
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8552]: + ??? root:adrian8
Apr  4 15:57:55 gateway-ubuntu-sda8 su[8552]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8552]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8569]: Successful su for adrian8 by root
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8569]: + ??? root:adrian8
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8569]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8569]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8578]: Successful su for adrian8 by root
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8578]: + ??? root:adrian8
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8578]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:57:56 gateway-ubuntu-sda8 su[8578]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:10 gateway-ubuntu-sda8 gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr  4 15:58:18 gateway-ubuntu-sda8 su[8979]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[8979]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[8979]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[8979]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[8990]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[8990]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[8990]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[8990]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9004]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9004]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9004]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9004]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9032]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9032]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9032]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9032]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9042]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9042]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9042]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9042]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9057]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9057]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9057]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9057]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9070]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9070]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9070]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9070]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9083]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9083]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9083]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9083]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9098]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9098]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9098]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9098]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9111]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9111]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9111]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9111]: pam_unix(su:session): session closed for user adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9124]: Successful su for adrian8 by root
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9124]: + ??? root:adrian8
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9124]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 15:58:18 gateway-ubuntu-sda8 su[9124]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:52 gateway-ubuntu-sda8 su[9379]: Successful su for adrian8 by root
Apr  4 18:29:52 gateway-ubuntu-sda8 su[9379]: + ??? root:adrian8
Apr  4 18:29:52 gateway-ubuntu-sda8 su[9379]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 18:29:52 gateway-ubuntu-sda8 su[9379]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:52 gateway-ubuntu-sda8 su[9395]: Successful su for adrian8 by root
Apr  4 18:29:52 gateway-ubuntu-sda8 su[9395]: + ??? root:adrian8
Apr  4 18:29:52 gateway-ubuntu-sda8 su[9395]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9395]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9410]: Successful su for adrian8 by root
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9410]: + ??? root:adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9410]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9410]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9419]: Successful su for adrian8 by root
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9419]: + ??? root:adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9419]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9419]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9438]: Successful su for adrian8 by root
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9438]: + ??? root:adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9438]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9438]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9456]: Successful su for adrian8 by root
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9456]: + ??? root:adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9456]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9456]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9470]: Successful su for adrian8 by root
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9470]: + ??? root:adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9470]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9470]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9479]: Successful su for adrian8 by root
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9479]: + ??? root:adrian8
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9479]: pam_unix(su:session): session opened for user adrian8 by (uid=0)
Apr  4 18:29:53 gateway-ubuntu-sda8 su[9479]: pam_unix(su:session): session closed for user adrian8
Apr  4 18:29:59 gateway-ubuntu-sda8 gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr  4 19:17:01 gateway-ubuntu-sda8 CRON[13159]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  4 19:17:01 gateway-ubuntu-sda8 CRON[13159]: pam_unix(cron:session): session closed for user root
Apr  4 20:17:01 gateway-ubuntu-sda8 CRON[13289]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  4 20:17:01 gateway-ubuntu-sda8 CRON[13289]: pam_unix(cron:session): session closed for user root
Apr  4 21:17:01 gateway-ubuntu-sda8 CRON[13484]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  4 21:17:01 gateway-ubuntu-sda8 CRON[13484]: pam_unix(cron:session): session closed for user root
Apr  4 21:44:39 gateway-ubuntu-sda8 polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.51, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8) (disconnected from bus)
Apr  4 21:45:55 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  4 21:45:55 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  4 21:46:01 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  4 21:46:03 gateway-ubuntu-sda8 dbus[1051]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=104 pid=1787 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.21" (uid=0 pid=1520 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  4 21:46:05 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session closed for user lightdm
Apr  4 21:46:06 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user adrian8 by (uid=0)
Apr  4 21:46:06 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  4 21:46:13 gateway-ubuntu-sda8 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.50 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8)
Apr  4 21:46:25 gateway-ubuntu-sda8 dbus[1051]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.58" (uid=1000 pid=2051 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.21" (uid=0 pid=1520 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  4 21:49:18 gateway-ubuntu-sda8 sudo:  adrian8 : TTY=unknown ; PWD=/tmp/update-manager-VZ9I0D ; USER=root ; COMMAND=/tmp/update-manager-VZ9I0D/precise
Apr  4 22:17:01 gateway-ubuntu-sda8 CRON[2725]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  4 22:17:01 gateway-ubuntu-sda8 CRON[2725]: pam_unix(cron:session): session closed for user root
Apr  5 00:40:06 gateway-ubuntu-sda8 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.50 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8)
Apr  5 00:51:28 gateway-ubuntu-sda8 groupadd[20715]: group added to /etc/group: name=whoopsie, GID=127
Apr  5 00:51:28 gateway-ubuntu-sda8 groupadd[20715]: group added to /etc/gshadow: name=whoopsie
Apr  5 00:51:28 gateway-ubuntu-sda8 groupadd[20715]: new group: name=whoopsie, GID=127
Apr  5 00:51:28 gateway-ubuntu-sda8 useradd[20719]: new user: name=whoopsie, UID=114, GID=127, home=/nonexistent, shell=/bin/false
Apr  5 00:51:29 gateway-ubuntu-sda8 usermod[20724]: change user 'whoopsie' password
Apr  5 00:51:29 gateway-ubuntu-sda8 chage[20729]: changed password expiry for whoopsie
Apr  5 00:51:29 gateway-ubuntu-sda8 dbus[1051]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.105" (uid=114 pid=20760 comm="whoopsie ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1121 comm="NetworkManager ")
Apr  5 01:01:15 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  5 01:01:15 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  5 01:01:23 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  5 01:01:24 gateway-ubuntu-sda8 dbus[939]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=104 pid=1854 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.28" (uid=0 pid=1580 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 01:01:25 gateway-ubuntu-sda8 dbus[939]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.43" (uid=104 pid=1894 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.28" (uid=0 pid=1580 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:03:49 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  5 12:03:49 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  5 12:03:58 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  5 12:04:00 gateway-ubuntu-sda8 dbus[963]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=104 pid=1864 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1586 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:04:01 gateway-ubuntu-sda8 dbus[963]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.43" (uid=104 pid=1904 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1586 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:09:15 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  5 12:09:15 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  5 12:09:24 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  5 12:09:25 gateway-ubuntu-sda8 dbus[897]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.34" (uid=104 pid=1775 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.25" (uid=0 pid=1498 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:09:26 gateway-ubuntu-sda8 dbus[897]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.42" (uid=104 pid=1815 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.25" (uid=0 pid=1498 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:45:53 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  5 12:45:53 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  5 12:46:02 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  5 12:46:04 gateway-ubuntu-sda8 dbus[907]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.35" (uid=104 pid=1809 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1533 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:46:05 gateway-ubuntu-sda8 dbus[907]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.44" (uid=104 pid=1849 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1533 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:51:42 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  5 12:51:42 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  5 12:51:50 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  5 12:51:52 gateway-ubuntu-sda8 dbus[907]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=104 pid=1809 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1533 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:51:53 gateway-ubuntu-sda8 dbus[907]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.44" (uid=104 pid=1852 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1533 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:57:51 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr  5 12:57:51 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  5 12:57:57 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr  5 12:57:58 gateway-ubuntu-sda8 dbus[865]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=104 pid=1810 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1537 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr  5 12:58:00 gateway-ubuntu-sda8 dbus[865]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.44" (uid=104 pid=1851 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1537 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Apr 12 12:26:58 gateway-ubuntu-sda8 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Apr 12 12:26:58 gateway-ubuntu-sda8 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 12 12:27:09 gateway-ubuntu-sda8 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "adrian8"
Apr 12 12:27:10 gateway-ubuntu-sda8 dbus[806]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=104 pid=1709 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.26" (uid=0 pid=1436 comm="/usr/sbin/console-kit-daemon --no-daemon ")
```

---

### Post by opasnost on 2012-04-12
I also get and error when booting into ubuntu:

modprob: Fatal: Could not load /lib/modules/3.1.5-1-ARCH/modules.dep: No such file or directory

i googled this and only thing related to arch linux came up. I do have Archlinux intalled I wonder if this is causing a problem?

---

### Post by krige on 2012-04-14
I had the same problem on two different computers. My keyboard and mouse are both USB. Unplugging the mouse and keyboard didn't work; swenson solution worked.

These are the full detailed steps I followed:

[LIST=1]
[*] boot from an external 12.04 installation disk (or USB drive);
[*] open a terminal and run:
```
sudo mkdir /mnt/linux
sudo fdisk -l
```
[*] identify your Linux partition (in my case it was sda6) and run:
```
sudo mount /dev/sda6 /mnt/linux
sudo chroot /mnt/linux su
mount /dev
mount /proc
mount /sys
apt-get update
apt-get -f upgrade
```
[*] I had to use the -f option because some packages had unmet dependencies (took a while to complete this step). Then run:
```
apt-get dist-upgrade
```
[*] reboot, login and run:
```
sudo rm -fr /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get autoclean
```
[/LIST]

---

### Post by unibroker on 2012-04-15
I have been using 12.04 for about a month now.  My mouse/keyboard will freeze if I don't move my mouse upon initial boot up (I shutdown every night) and the cursor first appears on the screen.  This is just before the logon screen and after the initial Ubuntu splash screen.  Following this procedure has never failed.  I am dual boot with Win XP.

---

### Post by krige on 2012-04-16
After running:
```
sudo chroot /mnt/linux su
```

I get the following error:
```
chroot: failed to run command `su': No such file or directory
```

/mnt/linux after mounted contains only the following file:
```
EFI/ubuntu/grubx64.efi
```

I am stuck.

The output of "sudo fdisk -l" follows:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   156301487    78150743+  ee  GPT
```

---

### Post by krige on 2012-04-18
> **krige said:**
> ```
chroot: failed to run command `su': No such file or directory
```

/mnt/linux after mounted contains only the following file:
```
EFI/ubuntu/grubx64.efi
```

I mounted the wrong partition, my bad. Using GParted Partition Editor I was able to see that the actual partition was sda2, not sda1. Weirdly enough though, fdisk showed only sda1 partition.

---

### Post by krige on 2012-04-18
There are still problems. The upgrade gets interrupted with the following error:

```
  language-pack-en-base:amd64 conflicts with language-pack-en:amd64
  language-pack-gnome-en-base:amd64 conflicts with language-pack-gnome-en:amd64
Can not write log, openpty() failed (/dev/pts not mounted?)
dpkg: error processing libgdk-pixbuf2.0-0:i386 (--configure):
 libgdk-pixbuf2.0-0:i386 2.26.0-1 cannot be configured because libgdk-pixbuf2.0-0:amd64 is in a different version (2.26.1-1)
dpkg: error processing libgdk-pixbuf2.0-0 (--configure):
 libgdk-pixbuf2.0-0:amd64 2.26.1-1 cannot be configured because libgdk-pixbuf2.0-0:i386 is in a different version (2.26.0-1)
dpkg: error processing libfontconfig1 (--configure):
 libfontconfig1:amd64 2.8.0-3ubuntu9 cannot be configured because libfontconfig1:i386 is in a different version (2.8.0-3ubuntu8)
dpkg: error processing libfontconfig1:i386 (--configure):
 libfontconfig1:i386 2.8.0-3ubuntu8 cannot be configured because libfontconfig1:amd64 is in a different version (2.8.0-3ubuntu9)
dpkg: dependency problems prevent configuration of fontconfig:
 fontconfig depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing fontconfig (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libpango1.0-0 (--configure):
 libpango1.0-0:amd64 1.30.0-0ubuntu2 cannot be configured because libpango1.0-0:i386 is in a different version (1.30.0-0ubuntu1)
dpkg: dependency problems prevent configuration of libcairo2:i386:
 libcairo2:i386 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1:i386 is not configured yet.
dpkg: error processing libcairo2:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached alreadydpkg: dependency problems prevent configuration of libxft2:i386:
 libxft2:i386 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1:i386 is not configured yet.
dpkg: error processing libxft2:i386 (--configure):
 dependency problems - leaving unconfigured

dpkg: error processing libpango1.0-0:i386 (--configure):
 libpango1.0-0:i386 1.30.0-0ubuntu1 cannot be configured because libpango1.0-0:amd64 is in a different version (1.30.0-0ubuntu2)
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 libgtk2.0-0 depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 libgtk2.0-0 depends on libpango1.0-0 (>= 1.28.3); however:
  Package libpango1.0-0 is not configured yet.
No apport report written because MaxReports is reached already
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing librsvg2-2:i386 (--configure):
 librsvg2-2:i386 2.36.0-0ubuntu1 cannot be configured because librsvg2-2:amd64 is in a different version (2.36.1-0ubuntu1)
dpkg: error processing librsvg2-2 (--configure):
 librsvg2-2:amd64 2.36.1-0ubuntu1 cannot be configured because librsvg2-2:i386 is in a different version (2.36.0-0ubuntu1)
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 libgdk-pixbuf2.0-0:i386
 libgdk-pixbuf2.0-0
 libfontconfig1
 libfontconfig1:i386
 fontconfig
 libpango1.0-0
 libcairo2:i386
 libxft2:i386
 libpango1.0-0:i386
 libgtk2.0-0
 librsvg2-2:i386
 librsvg2-2
E: Internal Error, No file name for libgdk-pixbuf2.0-0
E: Internal Error, No file name for libgtk2.0-0
E: Internal Error, No file name for librsvg2-2
E: Internal Error, No file name for libgnome-keyring0
E: Internal Error, No file name for libgdu0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by kkoouu on 2012-04-20
exactly same problem here :(

---

### Post by kkoouu on 2012-04-20
I have managed to get through the problem. 

1) Boot from CD and enter chroot

Problematic packages have to be installed by:

```
dpkg -i /var/cache/apt/archives/<package>.deb
```

then running:
```
apt-get -f install
apt-get -f upgrade
```

sometimes:
```
dpkg --configure <package>
```

Once I ended up with circular depency, this was solved by
```
dpkg --ignore-depends <package1> --install/configure <package2>
```

I had to install manually around 30 packages, running apt-get after each is moving forward a bit, errors are the solved by mentioned commands above.


After I saw that kernel was configured and grub installed, I tried to reboot, system is working including USB mouse/keyboard, there are still errors, but the system is usable, I will go on the same way as before to solve these.

---

### Post by krige on 2012-04-20
> **kkoouu said:**
> I have managed to get through the problem.

Wonderful! Thanks a lot :) I can't test if that works because I have found another workaround (installed on another hard disk and copied the data from the broken system), but this will definitely help somebody else to overcome this problem.

---

### Post by BigCityCat on 2012-04-21
I am reading this thread and I don't understand why the live cd. If you can open the run dialog by using ctrl alt t and then type konsol in kubuntu or terminal in ubuntu then the terminal will open and you can type these commands directly into the terminal without the live cd. Am I missing something? just wondering.

---

### Post by BigCityCat on 2012-04-21
and maybe it's just an update that is fixing the problem. Just wondering.

---

### Post by krige on 2012-04-21
> **BigCityCat said:**
> I am reading this thread and I don't understand why the live cd. If you can open the run dialog by using ctrl alt t and then type konsol in kubuntu or terminal in ubuntu then the terminal will open and you can type these commands directly into the terminal without the live cd. Am I missing something? just wondering.

We can't press CTRL+ALT+T because the keyboard is not responding.

---

### Post by heald490 on 2012-04-22
I can't do anything because my keyboard and mouse don't work from the live cd either;  I'm now waiting for the release.. hopefully that will work for me.

---

