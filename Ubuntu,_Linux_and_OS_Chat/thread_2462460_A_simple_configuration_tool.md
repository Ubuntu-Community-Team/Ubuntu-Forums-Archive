---
title: "A simple configuration tool?"
date: 2021-05-21
forum: Ubuntu, Linux and OS Chat
---

### Post by him610 on 2021-05-21
My other OSs are Raspbian GNU/Linux 10 (buster) armv6l, and Raspbian GNU/Linux 10 (buster) x86. Included with each distribution is a neat character based configuration tool run from the terminal called 'raspi-config.'
```

$ apt show raspi-config
Package: raspi-config
Version: 20210212
Priority: optional
Section: utils
Maintainer: Serge Schneider <serge@raspberrypi.org>
Installed-Size: 124 kB
Depends: whiptail, parted, lua5.1, alsa-utils, psmisc, initramfs-tools
Recommends: triggerhappy, iw
Download-Size: 28.0 kB
APT-Manual-Installed: yes
APT-Sources: http://archive.raspberrypi.org/debian buster/main armhf Packages
Description: Raspberry Pi configuration tool
 A simple configuration tool for common Raspberry Pi administrative tasks

```
Do any of the *buntu distros/flavors have a comparable configuration tool?

---

### Post by scorp123 on 2021-05-21
> **him610 said:**
>  Do any of the *buntu distros/flavors have a comparable configuration tool?

Not that I am aware of. If you want something like that maybe look at e.g. **OpenSUSE**?
They have **"yast"**  which works both in graphical and in text mode ...

[https://en.wikipedia.org/wiki/YaST]("https://en.wikipedia.org/wiki/YaST")

[IMG]https://upload.wikimedia.org/wikipedia/commons/a/a6/YaST_ncurses_openSUSE_15.1.png[/IMG]

---

### Post by &amp;KyT$0P# on 2021-05-21
If you like raspi-config, can you build it from source on/for your Ubuntu?

---

### Post by grahammechanical on 2021-05-21
What does raspi-config actually configure? I notice that one of the depends is whiptail. Ubuntu has Whiptail installed by default. When we select Advance Options for Ubuntu at the Grub menu and select a kernel with recovery mode it is Whiptail that paints the recovery menu on the screen and launches the menu options which in turn are scripts that run certain Linux commands. It is possible to modify those scripts to produce a different menu list to do different things to what the recovery menu does. Whiptail will do the work for you. I know this to be the case because I have tried it.

Check out /lib/recovery-mode/

You will see two scripts and a folder called Options.  In the Options folder are the scripts that run when we select a recovery menu option. Study those scripts and modify to suit your own purposes. Consider the "clean" script. It runs two commands apt-get clean & apt-get autoremove. It also puts some messages on the screen. 

[https://en.wikibooks.org/wiki/Bash_Shell_Scripting/Whiptail](https://en.wikibooks.org/wiki/Bash_Shell_Scripting/Whiptail)

Remember, whiptail is already installed in Ubuntu and any new script that you create to show up in a menu will have to be made executable. Two other things to study are /lib/systemd/system/friendly-recovery-service and /lib/systemd/system/friendly-recovery.target

A most important script is l10n.sh If that is not present in the new folders that you will create your new menu will not work. The l10n.sh script is referenced in all the recovery menu scripts

Regards

---

### Post by him610 on 2021-05-21
> What does raspi-config actually configure?
I will try document the top level menus and the lower level menus over the next day or two. If I have time I will try to complete it tonight.

Heading: Raspberry Pi Software Configuration Tool (raspi-config)
```

1 System options
2 Display options
3 interface options
4 Performance options
5 Localization options
6 Advanced options
8 Update
9 About raspi-config

     <Select>     <Finish>

```
Note: There is no 7.

Sub-menu levels will be added later.

---

### Post by oldfred on 2021-05-21
Explanation:

[https://www.raspberrypi.org/documentation/configuration/raspi-config.md](https://www.raspberrypi.org/documentation/configuration/raspi-config.md)

It looks a lot of the settings & that default or auto discovered in an Ubuntu install. 
Or available in System Settings.

I have created my own script to do multiple unique configuration settings, but they only apply to my system as UUID & labels or specific settings are used. And my own default list of additional applications to install.

---

### Post by him610 on 2021-05-21
As promised, the lower level menus, 

```

1 System options
  S1 Wireless Lan
  s2 Audio
  s3 Password
  s4 hostname
  s5 Boot / Auto Login
  s6 Network at Boot
  s7 Splash Screen
  s8 Power LED
2 Display options
  D1 Resolution
  D2 Underscan
  D3 Pixel Doubling
  D4 Screen Blanking
3 Interface options
  P1 Cameras
  P2 SSH
  P3 VNC
  P4 SPI
  P5 I2C
  P6 Serial Port
  P7 1-wire
  P8 Remote GPIO
4 Performance options
  P1 Overclock
  P2 GPU Memory
  P3 Overlay File System
  P4 Fan
5 Localization options
  L1 Locale
  L2 Timezone
  L3 Keyboard
  L4 WLAN Country
6 Advanced options
  A1 Expand Filesystem
  A2 GL Driveer
  A3 Compositor
  A4 Network Interface names
  A5 Network Proxy Settings
8 Update (If selected, it will update itself)
9 About raspi-config (If selected, it displays a short description of the tool)

```

Note: There is a short descriptive term explaining each selection.
The menus shown are from the arm64 version. I assume there is some difference between the arm64 and the x86 versions of the tool. I will post it in a subsequent reply.

---

### Post by him610 on 2021-05-21
@oldfred
Thanks, I had not discovered that page:)

---

### Post by him610 on 2021-05-21
Menus for X86 raspi-config. Entries beginning with X are not in X86 version
```

1 System options
  S1 Wireless Lan
X  s2 Audio
  s3 Password
  s4 hostname
  s5 Boot / Auto Login
  s6 Network at Boot
  s7 Splash Screen
X  s8 Power LED
2 Display options
X  D1 Resolution
X  D2 Underscan
  D3 Pixel Doubling
  D4 Screen Blanking
3 Interface options
X  P1 Cameras
  P2 SSH
X  P3 VNC
X  P4 SPI
X  P5 I2C
X  P6 Serial Port
X  P7 1-wire
X  P8 Remote GPIO
X 4 Performance options
X  P1 Overclock
X  P2 GPU Memory
X  P3 Overlay File System
X  P4 Fan
5 Localization options
  L1 Locale
  L2 Timezone
  L3 Keyboard
  L4 WLAN Country
6 Advanced options
X  A1 Expand Filesystem
X  A2 GL Driveer
X  A3 Compositor
  A4 Network Interface names
  A5 Network Proxy Settings
8 Update (If selected, it will update itself)
9 About raspi-config (If selected, it displays a short description of the tool)
```

---

### Post by TheFu on 2021-05-21
Cockpit?
  [https://www.unixmen.com/cockpit-a-beginner-friendly-server-administration-tool/](https://www.unixmen.com/cockpit-a-beginner-friendly-server-administration-tool/)
Canonical has been pushing it the last few releases. I'm not a fan, but that's mainly because webapps seem anti-secure to me.

---

### Post by him610 on 2021-05-21
@TheFu
One can ssh into a system then use the raspi-config tool to (re)configure the system which is why I thought some of the forum dwellers would be attracted to it.

---

### Post by TheFu on 2021-05-21
> **him610 said:**
> @TheFu
One can ssh into a system then use the raspi-config tool to (re)configure the system which is why I thought some of the forum dwellers would be attracted to it.

I'd be concerned about using a tool designed specifically for Raspberry Pi systems like raspi-config. Using it on an AMD64 Ubuntu could run into issues.  My r-pi uses conman for connection management.  That's very different from the netplan.yaml config file I use on all my Ubuntu servers.

Another concern is that if Canonical doesn't maintain it, then some of the capabilities will break, or worse, break a working system.

My concerns could be meaningless.  More tools and tool options are always good for all of us.
I've been looking for a great centralized LDAP management solution to replace what NIS/yp did in the 1990s.  Appears Cockpit might be the tool I seek with a few plugins like cockpit-389-ds and 389-ds.  Quite the personal problem, so perhaps others aren't so interested.

---

