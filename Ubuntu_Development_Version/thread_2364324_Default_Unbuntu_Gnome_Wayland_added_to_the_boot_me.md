---
title: "Default Unbuntu Gnome Wayland added to the boot menu"
date: 2017-06-21
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2017-06-21
Greetings,
Login menu now has Ubuntu Gnome Wayland as Default


rrnbtter@rrnbtter-110-15ISK:~$ loginctl
   SESSION        UID USER             SEAT             TTY             
        c6       1000 rrnbtter         seat0                            
        c5        111 lightdm          seat0                            


2 sessions listed.

rrnbtter@rrnbtter-110-15ISK:~$ loginctl show-session c5 -p Type
Type=x11
rrnbtter@rrnbtter-110-15ISK:~$ loginctl show-session c6 -p Type
Type=wayland



rrnbtter@rrnbtter-110-15ISK:
inxi -Sxx && $DESKTOP_SESSION
System:    Host: rrnbtter-110-15ISK Kernel: 4.11.0-8-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu2) dm: lightdm
           Distro: Ubuntu Artful Aardvark (development branch)
ubuntu-wayland


PS Still can't run X11 super user with Wayland.

---

### Post by Chanath on 2017-06-22
The default is Ubuntu, and there is another Ubuntu Wayland, all together 4 entries. From Ubuntu I can logout, but from Ubuntu Wayland I can't, just get a black screen. Btw, after such a long time with Unity, it looks quite Unbuntu as you've mentioned in the heading.

---

### Post by Nand0 on 2017-06-22
Hi, after last update i can't login with any login, gnome, ubuntu, wayland... The screen set black and back to login menu.

---

### Post by P-I H on 2017-06-24
After boot and grub menu the system showed a black screen instead of the login menu. Managed to get to the login menu by pressing Ctrl+Alt+F7 and Ctrl+Alt+F3 a couple of times.

Decided to reinstall.
The installation went OK.
Made an update
```
Start-Date: 2017-06-24  10:46:33
Commandline: /usr/sbin/synaptic
Requested-By: p-i (1000)
Install: ubuntu-session:amd64 (3.24.1-0ubuntu5, automatic)
Upgrade: libunity-settings-daemon1:amd64 (15.04.1+17.04.20170418-0ubuntu1, 15.04.1+17.04.20170619-0ubuntu1), libqmi-proxy:amd64 (1.16.2-1, 1.18.0-1ubuntu1), suru-icon-theme:amd64 (16.10+17.10.20170518-0ubuntu1, 16.10+17.10.20170619-0ubuntu1), libgles2-mesa:amd64 (17.1.2-1ubuntu1, 17.1.2-2ubuntu2), gnome-session:amd64 (3.24.1-0ubuntu2, 3.24.1-0ubuntu5), publicsuffix:amd64 (20170424.0717-1, 20170616.1637-1), gnome-session-common:amd64 (3.24.1-0ubuntu2, 3.24.1-0ubuntu5), xserver-common:amd64 (2:1.19.3-1ubuntu1, 2:1.19.3-1ubuntu2), xserver-xorg-core:amd64 (2:1.19.3-1ubuntu1, 2:1.19.3-1ubuntu2), libgrilo-0.3-0:amd64 (0.3.3-1, 0.3.3-2), update-notifier-common:amd64 (3.179, 3.180), libwbclient0:amd64 (2:4.5.8+dfsg-2ubuntu1, 2:4.5.8+dfsg-2ubuntu2), fonts-guru-extra:amd64 (2.0-3, 2.0-4), libsystemd0:amd64 (233-6ubuntu3, 233-8ubuntu1), gstreamer1.0-tools:amd64 (1.12.0-2, 1.12.1-1), libraw16:amd64 (0.18.2-1, 0.18.2-2), libgjs0f:amd64 (1.48.4-0ubuntu1, 1.48.5-0ubuntu1), cpp-6:amd64 (6.3.0-18ubuntu2, 6.3.0-19ubuntu1), libglapi-mesa:amd64 (17.1.2-1ubuntu1, 17.1.2-2ubuntu2), printer-driver-foo2zjs:amd64 (20160902dfsg0-2, 20170320dfsg0-2), binutils:amd64 (2.28-4ubuntu1, 2.28-6ubuntu1), libqmi-glib5:amd64 (1.16.2-1, 1.18.0-1ubuntu1), sudo:amd64 (1.8.19p1-1ubuntu1, 1.8.20p2-1ubuntu1), ubuntu-standard:amd64 (1.388, 1.389), gcc-7-base:amd64 (7.1.0-6ubuntu2, 7.1.0-7ubuntu1), ubuntu-desktop:amd64 (1.388, 1.389), gdb:amd64 (7.99.90.20170502-0ubuntu1, 8.0-0ubuntu1), xserver-xorg-legacy:amd64 (2:1.19.3-1ubuntu1, 2:1.19.3-1ubuntu2), gjs:amd64 (1.48.4-0ubuntu1, 1.48.5-0ubuntu1), libxatracker2:amd64 (17.1.2-1ubuntu1, 17.1.2-2ubuntu2), python3:amd64 (3.5.3-1, 3.5.3-1ubuntu3), udev:amd64 (233-6ubuntu3, 233-8ubuntu1), hud:amd64 (14.10+17.10.20170618-0ubuntu1, 14.10+17.10.20170619-0ubuntu1), libegl1-mesa:amd64 (17.1.2-1ubuntu1, 17.1.2-2ubuntu2), gcc-6-base:amd64 (6.3.0-18ubuntu2, 6.3.0-19ubuntu1), libwavpack1:amd64 (5.0.0-2, 5.1.0-1), libdfu1:amd64 (0.9.2-5, 0.9.4-1ubuntu1), libexpat1:amd64 (2.2.0-2, 2.2.1-1), libudev1:amd64 (233-6ubuntu3, 233-8ubuntu1), libtalloc2:amd64 (2.1.8-1, 2.1.9-2), libio-socket-ssl-perl:amd64 (2.044-1, 2.049-1), libgbm1:amd64 (17.1.2-1ubuntu1, 17.1.2-2ubuntu2), python-talloc:amd64 (2.1.8-1, 2.1.9-2), libgcc1:amd64 (1:7.1.0-6ubuntu2, 1:7.1.0-7ubuntu1), libllvm4.0:amd64 (1:4.0.1~+rc3-1, 1:4.0.1-1), samba-libs:amd64 (2:4.5.8+dfsg-2ubuntu1, 2:4.5.8+dfsg-2ubuntu2), ubuntu-minimal:amd64 (1.388, 1.389), apport:amd64 (2.20.5-0ubuntu4, 2.20.5-0ubuntu5), libinput-bin:amd64 (1.6.3-1ubuntu1, 1.7.3-1ubuntu1), cups-filters:amd64 (1.14.0-1, 1.14.0-2), python3-minimal:amd64 (3.5.3-1, 3.5.3-1ubuntu3), libhud2:amd64 (14.10+17.10.20170618-0ubuntu1, 14.10+17.10.20170619-0ubuntu1), python3-apport:amd64 (2.20.5-0ubuntu4, 2.20.5-0ubuntu5), libnss-myhostname:amd64 (233-6ubuntu3, 233-8ubuntu1), libpython3-stdlib:amd64 (3.5.3-1, 3.5.3-1ubuntu3), libcupsfilters1:amd64 (1.14.0-1, 1.14.0-2), systemd-sysv:amd64 (233-6ubuntu3, 233-8ubuntu1), libwayland-egl1-mesa:amd64 (17.1.2-1ubuntu1, 17.1.2-2ubuntu2), libgcrypt20:amd64 (1.7.6-2, 1.7.7-2), python3-markupsafe:amd64 (0.23-3build1, 1.0-1), printer-driver-gutenprint:amd64 (5.2.12-1, 5.2.12-2), lintian:amd64 (2.5.50.4, 2.5.51), gnome-shell-common:amd64 (3.24.2-0ubuntu6, 3.24.2-0ubuntu7), libmm-glib0:amd64 (1.6.4-1, 1.6.8-1), libpam-systemd:amd64 (233-6ubuntu3, 233-8ubuntu1), xwayland:amd64 (2:1.19.3-1ubuntu1, 2:1.19.3-1ubuntu2), libsndfile1:amd64 (1.0.27-3, 1.0.28-2), python3-yaml:amd64 (3.12-1, 3.12-1build1), python3-pkg-resources:amd64 (33.1.1-1, 36.0.1-1), systemd:amd64 (233-6ubuntu3, 233-8ubuntu1), libgomp1:amd64 (7.1.0-6ubuntu2, 7.1.0-7ubuntu1), xmir:amd64 (2:1.19.3-1ubuntu1, 2:1.19.3-1ubuntu2), libfontembed1:amd64 (1.14.0-1, 1.14.0-2), ubuntu-mobile-icons:amd64 (16.10+17.10.20170518-0ubuntu1, 16.10+17.10.20170619-0ubuntu1), libgutenprint2:amd64 (5.2.12-1, 5.2.12-2), libgnome-games-support-common:amd64 (1.2.1-1, 1.2.2-1), libgl1-mesa-dri:amd64 (17.1.2-1ubuntu1, 17.1.2-2ubuntu2), libgnome-games-support-1-2:amd64 (1.2.1-1, 1.2.2-1), libsmbclient:amd64 (2:4.5.8+dfsg-2ubuntu1, 2:4.5.8+dfsg-2ubuntu2), libfwupd1:amd64 (0.9.2-5, 0.9.4-1ubuntu1), libtdb1:amd64 (1.3.11-2, 1.3.13-2), gnome-session-bin:amd64 (3.24.1-0ubuntu2, 3.24.1-0ubuntu5), light-themes:amd64 (16.10+17.10.20170518-0ubuntu1, 16.10+17.10.20170619-0ubuntu1), cups-filters-core-drivers:amd64 (1.14.0-1, 1.14.0-2), libtracker-sparql-1.0-0:amd64 (1.12.0-0ubuntu1, 1.12.0-1ubuntu1), ubuntu-artwork:amd64 (1:16.10+17.10.20170518-0ubuntu1, 1:16.10+17.10.20170619-0ubuntu1), libgl1-mesa-glx:amd64 (17.1.2-1ubuntu1, 17.1.2-2ubuntu2), apport-gtk:amd64 (2.20.5-0ubuntu4, 2.20.5-0ubuntu5), fwupd:amd64 (0.9.2-5, 0.9.4-1ubuntu1), libnss-resolve:amd64 (233-6ubuntu3, 233-8ubuntu1), libedit2:amd64 (3.1-20160903-3, 3.1-20170329-1), unity-settings-daemon:amd64 (15.04.1+17.04.20170418-0ubuntu1, 15.04.1+17.04.20170619-0ubuntu1), snapd-login-service:amd64 (1.12-0ubuntu1, 1.13-0ubuntu1), modemmanager:amd64 (1.6.4-1, 1.6.8-1), gdbserver:amd64 (7.99.90.20170502-0ubuntu1, 8.0-0ubuntu1), gnome-shell:amd64 (3.24.2-0ubuntu6, 3.24.2-0ubuntu7), gir1.2-gstreamer-1.0:amd64 (1.12.0-2, 1.12.1-1), libsnapd-glib1:amd64 (1.12-0ubuntu1, 1.13-0ubuntu1), libcc1-0:amd64 (7.1.0-6ubuntu2, 7.1.0-7ubuntu1), netcat-openbsd:amd64 (1.130-3, 1.178-1), python3-lxml:amd64 (3.7.3-1build1, 3.8.0-1), libstdc++6:amd64 (7.1.0-6ubuntu2, 7.1.0-7ubuntu1), update-notifier:amd64 (3.179, 3.180), python3-chardet:amd64 (2.3.0-2, 3.0.4-1), libgstreamer1.0-0:amd64 (1.12.0-2, 1.12.1-1), python3-problem-report:amd64 (2.20.5-0ubuntu4, 2.20.5-0ubuntu5), ubuntu-mono:amd64 (16.10+17.10.20170518-0ubuntu1, 16.10+17.10.20170619-0ubuntu1), lightdm:amd64 (1.22.0-0ubuntu4, 1.22.0-0ubuntu5), printer-driver-foo2zjs-common:amd64 (20160902dfsg0-2, 20170320dfsg0-2), liblightdm-gobject-1-0:amd64 (1.22.0-0ubuntu4, 1.22.0-0ubuntu5), libinput10:amd64 (1.6.3-1ubuntu1, 1.7.3-1ubuntu1), python3-setuptools:amd64 (33.1.1-1, 36.0.1-1), cups-browsed:amd64 (1.14.0-1, 1.14.0-2), tzdata:amd64 (2017b-1, 2017b-2), libkpathsea6:amd64 (2016.20160513.41080.dfsg-2, 2017.20170613.44572-2)
End-Date: 2017-06-24  10:47:38

```
Got this error message
```
W: Download is performed unsandboxed as root as file '/var/cache/apt/archives/partial/libnss-resolve_233-8ubuntu1_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

```
Rebooted and got a black screen pressed Ctrl+Alt+F7 and Ctrl+Alt+F3 a couple of times and got the login menu. Now the login menu, if I remember correctly, included
- Ubuntu Gnome
- Ubuntu Gnome on Wayland
- Ubuntu (Default)
- Ubuntu on Wayland

Logged in to Ubuntu and the system behaved as expected.

There are obviously some problem with the last update.

---

### Post by grahammechanical on 2017-07-01
I expect a future update to remove the Gnome & Gnome on Wayland options. Ubuntu is actually Ubuntu + Gnome 3 shell. And Ubuntu on Wayland is actually Ubuntu + Gnome 3 shell on Wayland. So, there is a duplication of login options.

I am just glad the Unity option has not been removed as that is my preferred choice. Oh, whether it is called Gnome on Wayland or Ubuntu on Wayland I get a black screen on this Ubuntu 17.04 upgraded to 17.10. But on a 17.10 Ubuntu Gnome the On Wayland option works. How strange is that?

Regards.

---

### Post by lammert-nijhof on 2017-07-01
The only version working is Unity, all other options Gnome, Ubuntu with or without Wayland do not work and never worked on my PC. If I log in the screen get black and the system returns to the login screen. It is early, but I hope it will change soon.

---

### Post by jbicha on 2017-07-02
> **grahammechanical said:**
> I expect a future update to remove the Gnome & Gnome on Wayland options.

I don't think it's going to work like that. You can remove *gnome-session* now if you don't want the extra GNOME session choices.

Someone upgrading from Ubuntu 17.04 shouldn't have the GNOME options.

---

### Post by mc4man on 2017-07-02
> **jbicha said:**
> I don't think it's going to work like that. You can remove *gnome-session* now if you don't want the extra GNOME session choices.

Someone upgrading from Ubuntu 17.04 shouldn't have the GNOME options.
The current 17.10 Ubuntu images do not include gnome-session on the image so there would only be 2 choices, Ubuntu (Default), Ubuntu on Wayland

---

### Post by rrnbtter on 2017-07-02
Greetings,

> **mc4man said:**
> The current 17.10 Ubuntu images do not include gnome-session on the image so there would only be 2 choices, Ubuntu (Default), Ubuntu on Wayland

I agree. But Ubuntu (Default) now loads the Gnome desktop with X.  Ubuntu on Wayland loads a Gnome desktop with XWayland.  
Currently the Wayland option won't run gksudo on x11 apps because the x11 apps don't support Wayland security.  In this case if I want for instance to run LuckyBackup as super user I have to log out of xwayland and use Ubuntu (default) which is x11 Gnome.  I'm certain this will be fixed over time but right now I'm happy because in my opinion both versions are wonderful and not at all what I expected after using Unity for six years. Right now the advantage to running the Wayland Gnome desktop is that it is very fast. My understanding is that the gksudo problem has to be fixed on the x11 side and not by Wayland.

---

### Post by #&amp;thj^% on 2017-07-02
> **rrnbtter said:**
> Greetings,



I agree. But Ubuntu (Default) now loads the Gnome desktop with X.  Ubuntu on Wayland loads a Gnome desktop with XWayland.  
Currently the Wayland option won't run gksudo on x11 apps because the x11 apps don't support Wayland security. **_ In this case if I want for instance to run LuckyBackup as super user _**I have to log out of xwayland and use Ubuntu (default) which is x11 Gnome.  I'm certain this will be fixed over time but right now I'm happy because in my opinion both versions are wonderful and not at all what I expected after using Unity for six years. Right now the advantage to running the Wayland Gnome desktop is that it is very fast. My understanding is that the gksudo problem has to be fixed on the x11 side and not by Wayland.

In a wayland session you can run this in the terminal:
```

 xhost +si:localuser:root
```
Credit to mc4man: So run this command in a terminal, then try again. _This command will only last until you reboot, it can be scripted to autorun on login _but as I mentioned before don't know it's advisability...
(you'll now be able to also use synaptic, ect.
I made an alias in my .bashrc file for these occasions.
Hope this is helpful.;)

---

### Post by rrnbtter on 2017-07-02
Greetings,
@1fallen;  thanks, I made the bin file to load the script and it works just fine for synaptic. However, still no luck with LuckyBackup.  It won't open in it's installed super user mode, nor using gksudo from a terminal, nor sudo -H from a terminal. It works in Gnome x11 just fine. 

rrnbtter@rrnbtter-110-15ISK:~$ wysu
localuser:root being added to access control list


rrnbtter@rrnbtter-110-15ISK:~$ pkexec luckybackup
QCoreApplication::applicationDirPath: Please instantiate the QApplication object first
luckybackup: cannot connect to X server

---

### Post by #&amp;thj^% on 2017-07-02
I remember this before wayland was here.
Command-line mode can be quite useful at systems where a graphical desktop is not available (eg servers).
Note, that no graphical libraries are needed when running luckybackup in this mode.
It can safely be used at a terminal.
I assume you have a profile already...as running from the console won't let you create one from the console.
Try it from the terminal, see if it is any better?
Sorry not more helpful here.
EDIT: Sorry I meant without <su or sudo>

---

### Post by mc4man on 2017-07-04
Since 16.04+ it no longer depends or recommends the menus package so the included super user .desktop wouldn't run anyway unless a user installed the menu package (su-to-root file
Overall the project appears long dead  & lightly maintained in Debian.
So if it would become wayland protocol usable then the Debian maintainer would have to take that up (reasonably doubtful.

---

