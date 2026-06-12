---
title: "Nvidia and TwinView"
date: 2012-01-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by P-I H on 2012-01-02
I suppose many users, that use proprietary graphic drivers, want to connect their laptops to the TV over HDMI.
I do not use a laptop, but have connected my desktop with a Geforce GTS250 graphic card to the TV.
It works, but it isn't exactly plug and play.
Most times when I use nvidia-settings Compiz crashes, which results in a screen without the Launcher and the top panel. and the system has to be rebooted.
However if I start nvidia-settings from the terminal with sudo nvidia-settings it is possible to activate the second sceen in TwinView. It doesn't work the first time, but after two activations it is OK.
Nvidia-settings will not save the changed xorg config, but it is possible to get a copy of the changed xorg config and copy it manually to /etc/X11/xorg.conf.

Has anybody else experienced these problems?

---

### Post by effenberg0x0 on 2012-01-04
> **P-I H said:**
> I suppose many users, that use proprietary graphic drivers, want to connect their laptops to the TV over HDMI.
I do not use a laptop, but have connected my desktop with a Geforce GTS250 graphic card to the TV.
It works, but it isn't exactly plug and play.
Most times when I use nvidia-settings Compiz crashes, which results in a screen without the Launcher and the top panel. and the system has to be rebooted.
However if I start nvidia-settings from the terminal with sudo nvidia-settings it is possible to activate the second sceen in TwinView. It doesn't work the first time, but after two activations it is OK.
Nvidia-settings will not save the changed xorg config, but it is possible to get a copy of the changed xorg config and copy it manually to /etc/X11/xorg.conf.

Has anybody else experienced these problems?

HI, I have a desktop-server that is connected to three 40"+ LCD TVs and one 19" LCD monitor using two Nvidia cards (GTS450 and 9500GT) and running three separate instances of XBMC/Lircd and separate pulseaudio outputs via hdmi. Until a couple weeks ago I was using the Ubuntu (Unity) session flawlessly. I have never experienced any of the problems you mention. Compiz never crashed as a result of using nvidia-settings. 

The TVs were setup as separate X Screens on nvidia-settings and, if running nvidia-settings as root, I could normally write to xorg.conf. At any rate, if root can't write to xorg.conf, something very wrong is going on there.

Then, about a week ago, I installed Lubuntu/Xubuntu (PP) sessions as alternate DEs that can be selected via lightdm and started running this HTPC with the Lubuntu session as the default, just to see if it would work well. Everything was setup with nvidia-settings and worked perfectly. There's no issue with compiz/xorg.conf or any crash. It's turned on 24/7 displaying 1080p content on all screens.

If I were you, I would:

[LIST]
[*]Investigate why root/sudoers can't write to /etc/X11/xorg.conf
[*]The important dirs in the system must have proper ownership/permissions. Fix it if needed.
[*]Check if your user and root have no nvidia*rc file stuck in their $HOME that overrides global settings (although it would be weird if that was the case).
[*]Make sure ati*, fglrx*, intel*, gdm* are not installed.
[*]Blacklist nouveau and remove nvidia* completely. Also sudo find / -name "*compiz*", sudo find / -name "*nvidia*", etc to do a manual remove of libs and other remains.
[*]Download latest proprietary nvidia from nvidia website (290.10) for your architecture (32/64-bit) and install it over the latest kernel (3.2.0-030200rc7).
[*]Check && fix /usr/lib/libGL* and /usr/lib32/libGL* so that soft links are valid.
[*]apt remove  --purge / reinstall critic  packages, such as unity*, lightdm*, compiz*, ccsm*, as well as their  libs. Get rid of old ccsm/compiz settings (again, sudo find / -name "*compiz*", etc, if needed) and then apt install && dpkg-reconfigure them. Only activate basic  ccsm plugins or, preferably, leave it at default, for all users including root.
[*]Run nvidia-settings for the first time from the terminal as a sudoer and set a valid config, save to xorg.conf as well as a nvidia-rc file in your $HOME. Reboot and do not run nvidia-settings as root any more unless it's needed.
[*]sudo apt-get upgrade && sudo apt-get update. Run nvidia installer -K if there's an upgrade to kernel, to make sure the kernel module is built.
[/LIST]

---

### Post by P-I H on 2012-01-04
I installed the daily build from today, January 4, and activated  Nvidia TwinView.
This time there were no problems with Compiz, but as before it is not exactly plug and play.
I haven't tried with separate X-screens. The driver is installed by use of Additional Drivers (version current).

I had to activate TwinView two times in nvidia-settings to make it work.

I couldn't save the xorg.conf file, but nvidia-settings showed a proposed xorg.conf file, that I copied and saved to /etc/X11/xorg.conf. With this xorg file both screens worked also after a reboot.

When I started nvidia-settings in the terminal it showed the error message "Faild to parse existing X config file '/etc/X11/xorg.conf'!" and this information in the terminal window

```
p-i@pi-GA-MA770-UD3-precise-0401:~$ sudo nvidia-settings
[sudo] password for p-i: 

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line.
```I got the same result both with and without "sudo".
The initial xorg.conf looked like this

```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```

After the error message was OK:ed, there was a new dialogue screen with the possibility to look at and copy a proposed xorg.conf file. There was also a possibility to save the xorg file and in this case the terminal window showed

```
python: can't open file '/usr/share/screen-resolution-extra/nvidia-polkit.py': [Errno 2] No such file or directory

ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.
```

---

### Post by effenberg0x0 on 2012-01-04
> **P-I H said:**
> I installed the daily build from today, January 4, and activated  Nvidia TwinView.
This time there were no problems with Compiz, but as before it is not exactly plug and play.
I haven't tried with separate X-screens. The driver is installed by use of Additional Drivers (version current).

I had to activate TwinView two times in nvidia-settings to make it work.

I couldn't save the xorg.conf file, but nvidia-settings showed a proposed xorg.conf file, that I copied and saved to /etc/X11/xorg.conf. With this xorg file both screens worked also after a reboot.

When I started nvidia-settings in the terminal it showed the error message "Faild to parse existing X config file '/etc/X11/xorg.conf'!" and this information in the terminal window

```
p-i@pi-GA-MA770-UD3-precise-0401:~$ sudo nvidia-settings
[sudo] password for p-i: 

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line.
```I got the same result both with and without "sudo".
The initial xorg.conf looked like this

```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```After the error message was OK:ed, there was a new dialogue screen with the possibility to look at and copy a proposed xorg.conf file. There was also a possibility to save the xorg file and in this case the terminal window showed

```
python: can't open file '/usr/share/screen-resolution-extra/nvidia-polkit.py': [Errno 2] No such file or directory

ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.
```

Hey, 

Post your xorg.conf. Maybe it is set in such a way that it confuses nvidia-settings?
Although I still find it weird to see a message such as the above write error if you're running it as root. Also, what are the permissions and ownership of /etc/X11/xorg.conf?
```

ls -la /etc/X11/xorg.conf
if [[ -w /etc/X11/xorg.conf ]]; then echo "Writeable"; else echo "Not writeable"; fi
sudo -s
if [[ -w /etc/X11/xorg.conf ]]; then echo "Writeable"; else echo "Not writeable"; fi

```**EDIT: **You can simply move or remove xorg.conf and re-run nividia proprietary installer if you want to.
```

ctrl+alt+f6 #Switch to VT6
(login with user and password)
sudo service lightdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_$(date +%d-%m-%y_%H:%M)
cd /wherever/your/nvidia-installer/is
sudo chmod +x NVIDIA*290.10*run && sudo ./NVIDIA*290.10*run
sudo service lightdm start

```

---

### Post by cariboo on 2012-01-04
Didn't we see this same sort of weirdness running a graphical application using sudo earlier?

To the op did can you try pressing Alt-F2 and typing:

```
gksu nvidia-settings
```

to see if you can save your xorg.conf file without an error

---

### Post by P-I H on 2012-01-05
> **cariboo907 said:**
> Didn't we see this same sort of weirdness running a graphical application using sudo earlier?

To the op did can you try pressing Alt-F2 and typing:

```
gksu nvidia-settings
```to see if you can save your xorg.conf file without an error

It didn't work.

I got the the error **Unable to open X config file '/etc/X11/xorg.conf' for writing.**
from nvidia-settings.
When  I used sudo nvidia-settings in the terminal I got this
```
p-i@pi-GA-MA770-UD3-precise-0401:~$ sudo nvidia-settings
[sudo] password for p-i: 

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
python: can't open file '/usr/share/screen-resolution-extra/nvidia-polkit.py': [Errno 2] No such file or directory

ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.

p-i@pi-GA-MA770-UD3-precise-0401:~$
```

---

### Post by Bowmore on 2012-01-05
It seems to be a bug in the package screen-resolution-extra missing those polkit files.

A workaround is to use *Show preview* after *Save to X Configuration file*, then manually copy that content into your xorg.conf.

Also install the package *gtk2-engines-pixbuf* to get rid of the pixbuf warnings. This one is a dependency bug already being reported.

---

### Post by P-I H on 2012-01-05
> **Bowmore said:**
> It seems to be a bug in the package screen-resolution-extra missing those polkit files.

A workaround is to use *Show preview* after *Save to X Configuration file*, then manually copy that content into your xorg.conf..

That's what i did, so it is working OK, but these type of settings must work as expected to make it easy for everyone to use Ubuntu.

> **Bowmore said:**
> 

Also install the package *gtk2-engines-pixbuf* to get rid of the pixbuf warnings. This one is a dependency bug already being reported.

Thanks for the tip about pixbuf.

---

