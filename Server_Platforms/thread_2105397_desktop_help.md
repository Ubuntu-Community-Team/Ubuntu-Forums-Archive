---
title: "desktop help"
date: 2013-01-15
forum: Server Platforms
---

### Post by autotron on 2013-01-15
I have a remote server with Ubuntu 11.10 installed, I did not at the time have option from the server company to install desktop but was told I could install it myself later. 
So I used "apt-get install ubuntu-desktop" to install the desktop but now the noob part, I tried accessing the server via windows remote desktop to my server IP (understanding this is how to access the desktop) and get error remote desktop can not access server.
I can access fine via ftp or putty, I googled further and found one site saying i had to start the desktop using /etc/init.d/gdm but turns out gdm is not in init.d directory lol.
can some one tell me how to install, start and login to desktop? when i installed I did not get a prompt even to set up user or password...

---

### Post by Bucky Ball on 2013-01-15
*Thread moved to **Server Platforms***

Welcome to the forums and good luck.

---

### Post by eenofonn on 2013-01-15
First things first, don't try to use Windows Remote Desktop client (mstsc.exe) to connect to a linux box ;)

this should have installed gdm for you
```

sudo apt-get install ubuntu-desktop

```

so as to why you're not seeing gdm is kind of strange, can you post the output of:
```

which gdm

```

Also now you need to figure out how you want to access the desktop

You can do some cool things with ssh -X but you might want to use VNC

---

### Post by autotron on 2013-01-16
I started again, this time using slightly lighter install
sudo aptitude install --without-recommends ubuntu-desktop

this is the output at the end of everything
```
Updating software catalog...this may take a moment.
Software catalog update was successful.
Setting up system-config-printer-gnome (1.3.6+20110831-0ubuntu9.4) ...
Setting up ubuntu-wallpapers (0.32.1) ...
Setting up adium-theme-ubuntu (0.3.1-0ubuntu1) ...
Setting up ubuntu-artwork (54) ...
Setting up ubuntu-sounds (0.13) ...
Setting up unity-greeter (0.1.1-0ubuntu1) ...
Setting up xdg-user-dirs-gtk (0.8-1ubuntu2) ...
Setting up xdiagnose (1.6.1) ...
Setting up qdbus (4:4.7.4-0ubuntu8.2) ...
Setting up libqt4-dbus (4:4.7.4-0ubuntu8.2) ...
Setting up libqt4-network (4:4.7.4-0ubuntu8.2) ...
Setting up libqt4-script (4:4.7.4-0ubuntu8.2) ...
Setting up libqt4-xmlpatterns (4:4.7.4-0ubuntu8.2) ...
Setting up libqt4-declarative (4:4.7.4-0ubuntu8.2) ...
Setting up libdconf-qt0 (0.0.0.110722-0ubuntu3) ...
Setting up libqtbamf1 (0.2.2-0ubuntu1) ...
Setting up libqtdee2 (0.2.3-0ubuntu1) ...
Setting up libqtgconf1 (0.1-0ubuntu5) ...
Setting up libqtgui4 (4:4.7.4-0ubuntu8.2) ...
Setting up libdbusmenu-qt2 (0.9.0-0ubuntu2) ...
Setting up libqt4-opengl (4:4.7.4-0ubuntu8.2) ...
Setting up libqt4-svg (4:4.7.4-0ubuntu8.2) ...
Setting up libunity-2d-private0 (4.12.0-0ubuntu1.4) ...
Setting up unity-2d-launcher (4.12.0-0ubuntu1.4) ...
Setting up unity-2d-panel (4.12.0-0ubuntu1.4) ...
Setting up unity-2d-places (4.12.0-0ubuntu1.4) ...
Setting up unity-2d-spread (4.12.0-0ubuntu1.4) ...
Setting up unity-2d (4.12.0-0ubuntu1.4) ...
Setting up ubuntu-desktop (1.245.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

root@server200183:~# /etc/init.d/gdm start
-bash: /etc/init.d/gdm: No such file or directory
root@server200183:~# which gdm
root@server200183:~# 

```it seems to have installed fine, but when I do which gdm it just goes to prompt, if i do locate gdm I get this
```
root@server200183:~# locate gdm
/usr/lib/lightdm/lightdm/gdmflexiserver
/usr/share/app-install/desktop/gdmap:gdmap.desktop
/usr/share/app-install/icons/gdmap_icon.png
/usr/share/vim/vim73/syntax/gdmo.vim

```startx gives me this output
```

X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux server200183.myserver.net 3.2.13-grsec-xxxx-grs-ipv6-64 #1 SMP Thu Mar 29 09:48:59 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/bzImage-3.2.13-xxxx-grs-ipv6-64 root=/dev/sda1 ro
Build Date: 23 May 2012  07:44:07AM
xorg-server 2:1.10.4-1ubuntu4.3 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.22.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 16 15:14:58 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) open /dev/fb0: No such file or directory
```

---

### Post by eenofonn on 2013-01-16
The locate database has to refresh and I forget the command to do it manually.. What happens if you try to do 

/etc/init.d/gdm start?

---

### Post by autotron on 2013-01-16
when I do /etc/init.d/gdm start i get
```
root@server200183:~# /etc/init.d/gdm start
-bash: /etc/init.d/gdm: No such file or directory
root@server200183:~#

```

updatedb and now get

```

root@server200183:~# updatedb
root@server200183:~# locate gdm
/usr/lib/lightdm/lightdm/gdmflexiserver
/usr/share/gdm
/usr/share/app-install/desktop/gdmap:gdmap.desktop
/usr/share/app-install/icons/gdmap_icon.png
/usr/share/gdm/autostart
/usr/share/gdm/autostart/LoginWindow
/usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop
/usr/share/icons/Humanity/apps/22/gdm-setup.svg
/usr/share/icons/Humanity/apps/24/gdm-setup.svg
/usr/share/icons/Humanity/apps/48/gdm-setup.svg
/usr/share/icons/Humanity/apps/48/gdmsetup.svg
/usr/share/vim/vim73/syntax/gdmo.vim

```

---

### Post by collisionystm on 2013-01-16
FYI....


11.10+ uses lightdm as the display manager. Not GDM.

---

### Post by sandyd on 2013-01-16
just type
```

apt-get install lightdm
lightdm
```

and lightdm will start

---

### Post by eenofonn on 2013-01-16
> **collisionystm said:**
> FYI....


11.10+ uses lightdm as the display manager. Not GDM.
oh very good to know :) here's an idea that I don't know why I didn't think of before 

```

sudo init 5

```

---

### Post by autotron on 2013-01-16
tried the above suggestions...still cant access server or desktop via VNC or remote desktop...

---

### Post by collisionystm on 2013-01-17
> **autotron said:**
> tried the above suggestions...still cant access server or desktop via VNC or remote desktop...


So... You installed ubuntu-desktop. Did you actually turn on the VNC services? You cant just remote to ubuntu without actually enabling the ability to do so....


Check this out...
[http://wiki.amahi.org/index.php/Install_VNC_server_on_Ubuntu_Server_12.04](http://wiki.amahi.org/index.php/Install_VNC_server_on_Ubuntu_Server_12.04)

I'd skip past the bits about installing Gnome and go straight to installing the vnc server.

You dont need to install gnome since you already did the meta-package ubuntu-desktop, therefore giving you lightdm instead of gdm.

Hopefully this helps... good luck!

---

### Post by eenofonn on 2013-01-17
> **collisionystm said:**
> so... You installed ubuntu-desktop. Did you actually turn on the vnc services? You cant just remote to ubuntu without actually enabling the ability to do so....


Check this out...
[http://wiki.amahi.org/index.php/install_vnc_server_on_ubuntu_server_12.04](http://wiki.amahi.org/index.php/install_vnc_server_on_ubuntu_server_12.04)

i'd skip past the bits about installing gnome and go straight to installing the vnc server.

You dont need to install gnome since you already did the meta-package ubuntu-desktop, therefore giving you lightdm instead of gdm.

Hopefully this helps... Good luck!
+1

---

### Post by collisionystm on 2013-01-17
And actually..... hold up a sec. I just tried this...

I have an ubuntu server 12.04 running minecraft for me. No GUI. I wanted to see how easy remote desktop would be.

First I installed XRDP (windows remote desktop compatible)

sudo apt-get install xrdp

Hopped on windows machine, was able to remote desktop to my linux box. All I get is a terminal though, but I have a mouse cursor!

Now I need a gui

sudo apt-get install lxde  (only 28.5mb ) 

Reboot your system...

sudo reboot


Wait a few minutes and voila! You can now remote desktop into a gui. Congrats.

---

### Post by eenofonn on 2013-01-17
> **collisionystm said:**
> And actually..... hold up a sec. I just tried this...

I have an ubuntu server 12.04 running minecraft for me. No GUI. I wanted to see how easy remote desktop would be.

First I installed XRDP (windows remote desktop compatible)

sudo apt-get install xrdp

Hopped on windows machine, was able to remote desktop to my linux box. All I get is a terminal though, but I have a mouse cursor!

Now I need a gui

sudo apt-get install lxde  (only 28.5mb ) 

Reboot your system...

sudo reboot


Wait a few minutes and voila! You can now remote desktop into a gui. Congrats.
Now THAT is cool! :guitar:

---

### Post by collisionystm on 2013-01-17
> **eenofonn said:**
> now that is cool! :guitar:


):p

---

