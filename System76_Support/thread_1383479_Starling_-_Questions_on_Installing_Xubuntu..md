---
title: "Starling - Questions on Installing Xubuntu."
date: 2010-01-17
forum: System76 Support
---

### Post by black_ice=cream on 2010-01-17
I was wondering if I have an external CD drive for my starling I could use that to install Xubuntu, or if I need to use a flash drive since there is no internal CD drive.

[B]I'm not positive I'm going to install Xubuntu, but I'm definitely thinking about it.

EDIT[/B] - I have successfully installed the xubuntu-desktop using the command: apt-get install xubuntu-desktop. It's great! I can choose between GNOME and Xfce at log in. But on the drop down menu there are **2** options for an Xfce session, and sometimes when I boot into Xfce, it gives me like a half UNR half xfce type thing, but then I just log out and in again and it works fine. This happens occasionally and I was wondering if this is the norm.

---

### Post by patchwork on 2010-01-17
If you don't want to start from scratch, you can follow these instructions:  [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)  This will allow you to choose between the lightweight xfce4 and gnome sessions on login.  If you want to totally remove gnome, you can try this after installing xubuntu-desktop:  [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)   Another lightweight environment that some people like is lxde, found at lxde.org  Note:  when installing the xubuntu-desktop, the splash screens will, by default, switch to the xubuntu-desktop splash screens.  This can be changed later, but it's a bit of a hassle.

---

### Post by lev-unr on 2010-01-17
You can install it from a flash drive. Using [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by black_ice=cream on 2010-01-17
[lev-unr]("http://ubuntuforums.org/member.php?u=999196"), I have a question about UNetbootin. I don't get it. Do you just download it, download the ISO, and then put the ISO in unebootin with a flash drive in and it burns it? or something else?

---

### Post by miniyak on 2010-01-17
If you just want to try out xfce, i would install it with synaptic

log out...

then log back in as a xfce session 
...no sweat

I'm not really sure what the benefit to completely reinstalling is unless your sys will not start w/latest gnome (i have a old desktop like this.), may be some of the other members chime in on the benifits of installing Xubuntu in full vs. just adding xfce

---

### Post by jdb on 2010-01-17
> **miniyak said:**
> If you just want to try out xfce, i would install it with synaptic

log out...

then log back in as a xfce session 
...no sweat

I'm not really sure what the benefit to completely reinstalling is unless your sys will not start w/latest gnome (i have a old desktop like this.), may be some of the other members chime in on the benifits of installing Xubuntu in full vs. just adding xfce

I've done it both ways (not on a Starling)  & don't see any difference other
than having a little less disk space & a few more apts available.

After installing xfce you can get
the ubuntu bootsplash back by installing ubuntu-xsplash-artwork.

jdb

---

### Post by lev-unr on 2010-01-17
> **black_ice=cream said:**
> [lev-unr]("http://ubuntuforums.org/member.php?u=999196"), I have a question about UNetbootin. I don't get it. Do you just download it, download the ISO, and then put the ISO in unebootin with a flash drive in and it burns it? or something else?

Hey sorry for the late reply, yes it is that simple. It is the easiest program that I have ever used. :)

Takes all the thought out of making a bootable flash drive. I had my 9.10 running on my netbook in 15 minutes after using unitbootin. :D

It basically "burns" the image to the flash drive as it would to a CD and then makes it bootable. Just select it when the computer is starting to boot from the USB and you are all set!

---

### Post by thomasaaron on 2010-01-18
> I was wondering if I have an external CD drive for my starling I could use that to install Xubuntu, or if I need to use a flash drive since there is no internal CD drive.

Yes, that should work fine.

Please note that a lot of the functionality of the Starling is enabled by the System76 driver. While the driver should run in Xubuntu, we don't test to make sure all of the fixes work in Xubuntu. Some of them may not.

So, installing Xubuntu from Synaptic is probably a good idea. That way, if it doesn't work well on your Starling, you can still boot into gnome/unr.

---

### Post by black_ice=cream on 2010-01-18
So... what is Synaptic?

---

### Post by jdb on 2010-01-18
> **black_ice=cream said:**
> So... what is Synaptic?

On the menu bar in the upper left corner of your screen:
System > Administration > Synaptic Package Manager > xubuntu-desktop

Or to do it from the command line:

```
apt-get install xubuntu-desktop
```

jdb

---

### Post by black_ice=cream on 2010-01-18
and so that pretty much dual-boots the computer?

---

### Post by patchwork on 2010-01-18
No.  The internal guts remain the same, but the xubuntu desktop, which is lighter and less resource intensive, provides the interface.  You would still have the gnome desktop, if you wanted.  You would choose between gnome (regular ubuntu) and xfce4 (xubuntu) sessions at login.

---

### Post by jdb on 2010-01-18
> **patchwork said:**
> No.  The internal guts remain the same, but the xubuntu desktop, which is lighter and less resource intensive, provides the interface.  You would still have the gnome desktop, if you wanted.  You would choose between gnome (regular ubuntu) and xfce4 (xubuntu) sessions at login.

Also you can logout & login to change desktops without rebooting or
even switch between users without logging out.

Right now I'm logged in with an Ubuntu desktop & root is logged in with a fluxbox desktop.

I switch back and forth with ctr-alt-F7 & ctr-alt-F8.

jdb

---

### Post by thomasaaron on 2010-01-19
> Right now I'm logged in with an Ubuntu desktop & root is logged in with a fluxbox desktop.

I switch back and forth with ctr-alt-F7 & ctr-alt-F8.

Ya learn a new trick every day around here! :popcorn:

---

### Post by black_ice=cream on 2010-01-19
okay. This all sounds good but what happens if I want to completely delete Xubuntu from my computer. How do you do that?

---

### Post by jdb on 2010-01-19
> **black_ice=cream said:**
> okay. This all sounds good but what happens if I want to completely delete Xubuntu from my computer. How do you do that?

That's not real easy.
xubuntu-desktop is a dummy package that installs a whole lot of other things that the Xubuntu desktop needs.
They only take up space on the disk & really don't hurt anything being there.
Some are kind of useful like the thunar file browser.
You can remove them individually with
```
apt-get remove package-name
```
then to get rid of all the extra files loaded as dependencies
```
apt-get autoremove
```
The command below will tell were a file came from, the full path works best.
```
dpkg -S filename
```

To find the full path of an executable use
```
which 
```

for example
```
23:00:41 ~ which ls
/bin/ls
23:00:49 ~ dpkg -S /bin/ls
coreutils: /bin/ls
```
 or
```
23:01:01 ~ dpkg -S `which ls`
coreutils: /bin/ls
```

Edit:

The quote ` used above is the one on the key next to the numeral 1.

jdb

---

### Post by patchwork on 2010-01-20
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)   These instructions will remove xubuntu and return you to ubuntu.

---

### Post by jdb on 2010-01-20
> **patchwork said:**
> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)   These instructions will remove xubuntu and return you to ubuntu.

That's cool, 137 removes!!

```
a2ps
abiword
abiword-common
abiword-help
abiword-plugin-grammar
abiword-plugin-mathview
abiword-plugins
app-install-data-commercial
catfish
exaile
exo-utils
feh
fortune-mod
fortunes-min
giblib1
gigolo
gnome-app-install
gnumeric
gnumeric-common
gnumeric-doc
gtk2-engines-xfce
imagemagick
libaiksaurus-1.2-0c2a
libaiksaurus-1.2-data
libaiksaurusgtk-1.2-0c2a
libexo-0.3-0
libgdome2-0
libgdome2-cpp-smart0c2a
libgnomecups1.0-1
libgnomeprint2.2-0
libgnomeprint2.2-data
libgnomeprintui2.2-0
libgnomeprintui2.2-common
libgoffice-0-8
libgoffice-0-8-common
libgtkmathview0c2a
libid3tag0
libimlib2
liblink-grammar4
libotr2
libots0
libpolkit-dbus2
libpolkit-gnome0
libpolkit-grant2
libpolkit2
librecode0
libscim8c2a
libt1-5
libtagc0
libthunar-vfs-1-2
libwv-1.2-3
libxcb-keysyms1
libxfce4menu-0.1-0
libxfce4util4
libxfcegui4-4
libxfconf-0-2
libxmlrpc-core-c3
link-grammar-dictionaries-en
mousepad
orage
pidgin
pidgin-data
pidgin-libnotify
pidgin-otr
policykit
policykit-gnome
psutils
python-cddb
python-mmkeys
python-mutagen
ristretto
scim
scim-bridge-agent
scim-bridge-client-gtk
scim-gtk2-immodule
scim-modules-socket
scim-modules-table
scim-tables-additional
tango-icon-theme
tango-icon-theme-common
tcl
thunar
thunar-archive-plugin
thunar-data
thunar-media-tags-plugin
thunar-thumbnailers
thunar-volman
thunderbird
ttf-arphic-uming
ttf-liberation
usb-creator
usplash-theme-xubuntu
vim-runtime
wdiff
xchat
xchat-common
xfce4-appfinder
xfce4-battery-plugin
xfce4-clipman-plugin
xfce4-cpugraph-plugin
xfce4-dict
xfce4-fsguard-plugin
xfce4-mailwatch-plugin
xfce4-mixer
xfce4-mount-plugin
xfce4-netload-plugin
xfce4-notes-plugin
xfce4-panel
xfce4-places-plugin
xfce4-power-manager
xfce4-power-manager-data
xfce4-quicklauncher-plugin
xfce4-screenshooter
xfce4-session
xfce4-settings
xfce4-smartbookmark-plugin
xfce4-systemload-plugin
xfce4-terminal
xfce4-utils
xfce4-verve-plugin
xfce4-volumed
xfce4-weather-plugin
xfce4-xkb-plugin
xfconf
xfdesktop4
xfdesktop4-data
xfprint4
xfswitch-plugin
xfwm4
xfwm4-themes
xubuntu-artwork
xubuntu-artwork-usplash
xubuntu-default-settings
xubuntu-desktop
xubuntu-docs
xubuntu-gdm-theme
xubuntu-wallpapers

```

jdb

---

### Post by black_ice=cream on 2010-01-20
hey guys! I installed using Syaptic successfuly, but on the log in screen it has 2 options for an Xfce session and sometimes when I pick that it keeps netbook remix so it's almost like "Xubuntu Netbook Remix" this only happens some times. It's fine I just wonder if this is the norm.

---

### Post by miniyak on 2010-01-21
are you sure it does what your explaining with only one of the presented options and not the other(as in choosing the other by accident or something)?

still, seems odd to me... but i have yet to use UNR, may be it has something to do with the way the unr environment is set-up.

---

### Post by jdb on 2010-01-21
> **black_ice=cream said:**
> hey guys! I installed using Syaptic successfuly, but on the log in screen it has 2 options for an Xfce session and sometimes when I pick that it keeps netbook remix so it's almost like "Xubuntu Netbook Remix" this only happens some times. It's fine I just wonder if this is the norm.

I've never used Remix so I don't know about that.
I get two entries for xfce also & don't know why,
but they both seem to do the same thing.
For Fluxbox, xterm & Gnome I only get one entry.

jdb

---

### Post by patchwork on 2010-01-21
I get two options each for xfce and gnome, though one of the gnome options is labeled failsafe.  Perhaps one of the xfce listings is also a failsafe option?

---

### Post by macabrem on 2010-02-07
> **black_ice=cream said:**
> hey guys! I installed using Syaptic successfuly, but on the log in screen it has 2 options for an Xfce session and sometimes when I pick that it keeps netbook remix so it's almost like "Xubuntu Netbook Remix" this only happens some times. It's fine I just wonder if this is the norm.

I just ran into this problem also.  It appears the the Netbook remix is competing with the default display in Xubuntu for some reason.  

To fix this:
1) click on Settings
2) click on Xfce 4 Settings Manager
3)click on Session and Startup
4) click on the Application Autostart tab
5) uncheck "Netbook Launcher"
6) logout or reboot

You can also kill the process while it is running and it gets rid of the netbook remix look immediately.  The above steps should prevent it from ever happening again.

---

