---
title: "Black screen after gui login"
date: 2016-11-28
forum: Ubuntu Development Version
---

### Post by 3-info-x on 2016-11-28
Hello,

I've updated my system to zesty zapus and now i get a black screen after the gui login.
The login window is normal, but after the login i just can see the white mouse. Also there are no task bars, menus and i can't open the terminal from there with the keystroke.

Do you have any suggestions how I can fix this problem?

Thanks in advance

```
root@workstation:~# uname -a
Linux workstation 4.8.0-26-generic #28-Ubuntu SMP Tue Oct 18 14:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

```
root@workstation:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Zesty Zapus (development branch)
Release:    17.04
Codename:    zesty
```


```
root@workstation:~# dpkg -l | grep nvidia
ii  nvidia-304                                      304.132-0ubuntu2                            amd64        NVIDIA legacy binary driver - version 304.132
ii  nvidia-current                                  304.132-0ubuntu2                            amd64        Transitional package for nvidia-current
ii  nvidia-opencl-icd-304                           304.132-0ubuntu2                            amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                 367.35-0ubuntu1                             amd64        Tool for configuring the NVIDIA graphics driver
```

```
root@workstation:~# tailf -n 100 /var/log/syslog.1
Nov 28 09:40:13 workstation click[3798]: QMap<QString, QString> {anonymous}::info_for_app_id(QString) Failed to create Application for "address-book-app"
Nov 28 09:40:13 workstation click[3798]: QMap<QString, QString> {anonymous}::info_for_app_id(QString) Failed to create Application for "address-book-app"
Nov 28 09:40:13 workstation click[3798]: /usr/lib/ubuntu-push-client/click-hook:15: PyGIWarning: Click was imported without specifying a version first. Use gi.require_version('Click', '0.4') before import to ensure that the right version gets loaded.
Nov 28 09:40:13 workstation click[3798]:   from gi.repository import Click
Nov 28 09:40:13 workstation click[3798]: hooks.vala:1216: User-level hook push-helper failed: Hook command '/usr/lib/ubuntu-push-client/click-hook-wrapper' failed: Child process exited with code 1
Nov 28 09:40:13 workstation click[3798]: Nothing to install.
Nov 28 09:40:13 workstation click[3798]: Nothing to update.
Nov 28 09:40:13 workstation click[3798]: Nothing to delete.
Nov 28 09:40:13 workstation click[3798]: Some user-level hooks failed: push-helper
Nov 28 09:40:13 workstation systemd[3775]: click-user-hooks.service: Main process exited, code=exited, status=1/FAILURE
Nov 28 09:40:13 workstation systemd[3775]: Failed to start Run Click user-level hooks.
Nov 28 09:40:13 workstation systemd[3775]: click-user-hooks.service: Unit entered failed state.
Nov 28 09:40:13 workstation systemd[3775]: click-user-hooks.service: Failed with result 'exit-code'.
Nov 28 09:40:13 workstation systemd[3775]: Reached target Default.
Nov 28 09:40:13 workstation systemd[3775]: Startup finished in 465ms.
Nov 28 09:40:13 workstation systemd[1]: Started User Manager for UID 0.
Nov 28 09:40:29 workstation dbus-daemon[2744]: Activating service name='org.gnome.zeitgeist.Engine'
Nov 28 09:40:29 workstation dbus-daemon[2744]: Activating service name='org.gnome.zeitgeist.SimpleIndexer'
Nov 28 09:40:29 workstation dbus-daemon[2744]: Successfully activated service 'org.gnome.zeitgeist.Engine'
Nov 28 09:40:29 workstation zeitgeist-datah[3902]: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Nov 28 09:40:29 workstation dbus-daemon[2744]: Successfully activated service 'org.gnome.zeitgeist.SimpleIndexer'
Nov 28 09:40:29 workstation zeitgeist-datah[3882]: string_strip: assertion 'self != NULL' failed
Nov 28 09:40:29 workstation zeitgeist-datah[3882]: gtk_recent_info_get_application_info: assertion 'app_name != NULL' failed
Nov 28 09:40:29 workstation zeitgeist-datah[3882]: recent-manager-provider.vala:106: (null) was not registered in RecentInfo item 0x5623a2d8a7c0
Nov 28 09:41:00 workstation systemd[1]: Started Session 6 of user root.
Nov 28 09:41:09 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext with direct rendering failed - trying indirect
Nov 28 09:41:09 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext failed
Nov 28 09:41:09 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext with direct rendering failed - trying indirect
Nov 28 09:41:09 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext failed
Nov 28 09:41:12 workstation update-notifier[4026]: GtkDialog mapped without a transient parent. This is discouraged.
Nov 28 09:41:12 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext with direct rendering failed - trying indirect
Nov 28 09:41:12 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext failed
Nov 28 09:41:12 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext with direct rendering failed - trying indirect
Nov 28 09:41:12 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext failed
Nov 28 09:42:47 workstation anacron[966]: Job `cron.daily' started
Nov 28 09:42:47 workstation anacron[4069]: Updated timestamp for job `cron.daily' to 2016-11-28
Nov 28 09:42:47 workstation systemd[2710]: Starting Notification regarding a crash report...
Nov 28 09:42:47 workstation update-notifier-crash[4074]: signon-ui
Nov 28 09:42:47 workstation update-notifier-crash[4074]: pulseaudio
Nov 28 09:42:47 workstation cracklib: no dictionary update necessary.
Nov 28 09:42:47 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext with direct rendering failed - trying indirect
Nov 28 09:42:47 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext failed
Nov 28 09:42:48 workstation system-crash-no[4107]: GtkDialog mapped without a transient parent. This is discouraged.
Nov 28 09:42:48 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext with direct rendering failed - trying indirect
Nov 28 09:42:48 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext failed
Nov 28 09:42:48 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext with direct rendering failed - trying indirect
Nov 28 09:42:48 workstation compiz[3354]: /usr/bin/Compiz (opengl) - Warn: glXCreateContext failed


```
```
root@workstation:~# unity --reset
WARNING: no DISPLAY variable set, setting it to :0
The --reset option is deprecated, You should run with no options instead.
A dependency job for unity7.service failed. See 'journalctl -xe' for details.

```
```
root@workstation:~#journalctl -xe
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit UNIT has failed.
--
-- The result is failed.
Nov 28 09:47:53 workstation systemd[3775]: indicator-printers.service: Unit entered failed state.
Nov 28 09:47:53 workstation systemd[3775]: indicator-printers.service: Failed with result 'exit-code'.
Nov 28 09:47:53 workstation systemd[3775]: Stopped Backing Service for the Unity Panel.
-- Subject: Unit UNIT has finished shutting down
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit UNIT has finished shutting down.
Nov 28 09:47:53 workstation systemd[3775]: Stopped Unity Shell v7.
-- Subject: Unit UNIT has finished shutting down
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit UNIT has finished shutting down.
Nov 28 09:47:53 workstation systemd[3775]: Stopped Unity Settings Daemon.
-- Subject: Unit UNIT has finished shutting down
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit UNIT has finished shutting down.
Nov 28 09:47:53 workstation systemd[3775]: unity-settings-daemon.service: Start request repeated too quickly.
Nov 28 09:47:53 workstation systemd[3775]: Failed to start Unity Settings Daemon.
-- Subject: Unit UNIT has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit UNIT has failed.
--
-- The result is failed.
Nov 28 09:47:53 workstation systemd[3775]: Dependency failed for Unity Shell v7.
-- Subject: Unit UNIT has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit UNIT has failed.
--
-- The result is dependency.
Nov 28 09:47:53 workstation systemd[3775]: unity7.service: Job unity7.service/start failed with result 'dependency'.
Nov 28 09:47:53 workstation systemd[3775]: unity-settings-daemon.service: Unit entered failed state.
Nov 28 09:47:53 workstation systemd[3775]: unity-settings-daemon.service: Failed with result 'exit-code'.
Nov 28 09:47:53 workstation systemd[3775]: unity-panel-service.service: Start request repeated too quickly.
Nov 28 09:47:53 workstation systemd[3775]: Failed to start Backing Service for the Unity Panel.
-- Subject: Unit UNIT has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit UNIT has failed.
--
-- The result is failed.
```

---

### Post by howefield on 2016-11-28
Moved to the "*Ubuntu Development Version*" forum.

---

### Post by dino99 on 2016-11-28
ZZ has 4.9 kernel now, but it does not work without the nvidia-driver from 'graphics-drivers' ppa; so use 4.8 till fixing your issue.

First be sure of /etc/apt/sources.list only setting genuine ZZ archives (deactivate everything else in case)
Then clean the system: 'sudo apt-get clean' same with autoclean & autoremove. Also run gtkorphan to get rid of possible orphans.
After that done, update the packages, run 'sudo apt-get -f install' & 'sudo dpkg --configure -a'   & 'sudo reboot now'

---

### Post by 3-info-x on 2016-11-28
I'm currently using the 4.8 kernel.

```
root@workstation:~# uname -r
4.8.0-26-generic
```

This is my sources.list: There are just ZZ archives 
```
# deb cdrom:[Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner

```

After the cleaning: 
```
root@workstation:~# gtkorphan
Gtk-WARNING **: cannot open display:  at /usr/lib/x86_64-linux-gnu/perl5/5.24/Gtk2.pm line 126.


root@workstation:~# echo $DISPLAY


root@workstation:~# export DISPLAY=:0
root@workstation:~# gtkorphan
No protocol specified
Gtk-WARNING **: cannot open display: :0 at /usr/lib/x86_64-linux-gnu/perl5/5.24/Gtk2.pm line 126.
```

Updating the packages went fine. Could this be a display problem?
After the reboot it is not working.

```
root@workstation:~# glxinfo
Error: unable to open display
root@workstation:~# echo $DISPLAY


root@workstation:~#

```

---

### Post by dino99 on 2016-11-28
the sources.list entries does not have the "/" at the end ; you probably get some missing updates.

mine for example:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-proposed main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety partner

[http://www.ubuntugeek.com/cleaning-up-a-ubuntu-gnulinux-system-updated-with-ubuntu-14-10-and-more-tools-added.html](http://www.ubuntugeek.com/cleaning-up-a-ubuntu-gnulinux-system-updated-with-ubuntu-14-10-and-more-tools-added.html)

and: NEVER set ROOT for working; use your user login, and 'sudo' from the terminal to execute commands. Using root is the worst thing to do (and you may have broken your system that way)

---

### Post by 3-info-x on 2016-11-28
Thanks for your answer.

I have removed the / at the end and cleaned my system (your link).
Now i also use sudo ;)
After the cleaning up I rebooted my system but i still get a black screen.

```
mathias@workstation:~$mathias@workstation:~$ sudo apt-get clean
mathias@workstation:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mathias@workstation:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
mathias@workstation:~$ gtkorphan
Gtk-WARNING **: cannot open display:  at /usr/lib/x86_64-linux-gnu/perl5/5.24/Gtk2.pm line 126.
mathias@workstation:~$ sudo apt-get update
Get:1 http://security.ubuntu.com/ubuntu zesty-security InRelease [102 kB]
Hit:2 http://de.archive.ubuntu.com/ubuntu zesty InRelease
Hit:3 http://de.archive.ubuntu.com/ubuntu zesty-updates InRelease
Hit:4 http://de.archive.ubuntu.com/ubuntu zesty-backports InRelease
Fetched 102 kB in 0s (261 kB/s)
Reading package lists... Done
mathias@workstation:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mathias@workstation:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mathias@workstation:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
mathias@workstation:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mathias@workstation:~$ sudo dpkg --configure -a
mathias@workstation:~$ uname -r
4.8.0-26-generic
mathias@workstation:~$ cat /etc/apt/sources.list
deb http://de.archive.ubuntu.com/ubuntu zesty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu zesty main restricted


deb http://de.archive.ubuntu.com/ubuntu zesty-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu zesty-updates main restricted


deb http://de.archive.ubuntu.com/ubuntu zesty universe
deb-src http://de.archive.ubuntu.com/ubuntu zesty universe
deb http://de.archive.ubuntu.com/ubuntu zesty-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu zesty-updates universe


deb http://de.archive.ubuntu.com/ubuntu zesty multiverse
deb-src http://de.archive.ubuntu.com/ubuntu zesty multiverse
deb http://de.archive.ubuntu.com/ubuntu zesty-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu zesty-updates multiverse


deb http://de.archive.ubuntu.com/ubuntu zesty-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu zesty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu zesty-security main restricted
deb-src http://security.ubuntu.com/ubuntu zesty-security main restricted
deb http://security.ubuntu.com/ubuntu zesty-security universe
deb-src http://security.ubuntu.com/ubuntu zesty-security universe
deb http://security.ubuntu.com/ubuntu zesty-security multiverse
deb-src http://security.ubuntu.com/ubuntu zesty-security multiverse
```

---

### Post by dino99 on 2016-11-28
What you have not said:
- before setting Zesty on that workstation, which was the distro/flavour used ?
- have you made some custom change(s) ? (like with lightdm, or changing the DE (gnome-shell, unity,...)
- if you select 'upstart' boot entry from boot menu, do you also get a black screen ?
- is your system encrypted ? all the device or only system partition ? 

You can also purge nvidia and try booting with 'nouveau' (to get a working gui)  (it is installed by default, but nvidia is choosen when both are installed)
At last, from the command line (get it via ctrl+alt+F3) run:
> sudo apt-get purge nvidia*
sudo apt-get install nvidia-367 

---

### Post by 3-info-x on 2016-11-28
1) Before zesty i had 16.10 yakkety yak. I've upgraded by a mistake, wanted to downgrade over the sources.list but this don't worked
2) I didn't made changes. I just want to the the standard gui unity
3) The upstart boot failed -> upstart failed to spawn plymouth-upstart-bridge main process: unable to execute: no such file or directory
4) Standard encryption is active:
sdb                       8:16   0 223.6G  0 disk
&#9500;&#9472;sdb1                    8:17   0   512M  0 part  /boot/efi
&#9500;&#9472;sdb2                    8:18   0   244M  0 part  /boot
&#9492;&#9472;sdb3                    8:19   0 222.9G  0 part
  &#9492;&#9472;sdb3_crypt          252:0    0 222.8G  0 crypt
    &#9500;&#9472;ubuntu--vg-root   252:1    0 214.9G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 252:2    0     8G  0 lvm   [SWAP]

nvidia* was purged and i have installed nvidia-367

After a reboot it worked. Thanks!!!!!!!!

---

### Post by dino99 on 2016-11-28
Good news
now think to add the graphics-drivers ppa to get nvidia-375 which works with 4.9 kernels (if the proposed archive is activated)  ):P

---

