---
title: "Your Perfect Distro?"
date: 2012-08-31
forum: The Cafe
---

### Post by mamamia88 on 2012-08-31
If you had to create a distro what would it be?   Me personally I would create a distro with no gui by default.    On booting the cd it would ask you to pick a DE to install and then it would install basically an unmodified version of the DE.   Then you would reboot and get to your desktop and it would give you a list of about 100 of the most popular applications and you would check the box next to the ones you want and hit install.     Personally I like ubuntu but i hate how they install apps that i don't want/need by default like a cd burner when i'm using it on a pc without a cd drive.  Could a distro like this work?   Or am I crazy?

---

### Post by vexorian on 2012-08-31
DE:
Unity. So that the launcher is set to hide automatically. Trash and desktop switcher icons removed.
A unity-taskbar compiz plugin running, it is a bottom side bar the size of the top panel. That acts like a proper taskbar and also enables desktop switching by a single click.

Default apps:
- LibreOffice, latest firefox. GIMP, Inkscape, Gnome-desktop-utils (Search, disk space analyzer). Ubuntu's configuration stuff. Nautilus (but not the most recent one). Rythmbox.

Latest stable WINE and winetricks by default.

All media codecs. ALL of them.

The only presence of MONO is in the wine-mono package.

And I think that's all.




No ubuntu one.

---

### Post by wheeze on 2012-08-31
> **mamamia88 said:**
> Personally I like ubuntu but i hate how they install apps that i don't want/need by default like a cd burner when i'm using it on a pc without a cd drive.  Could a distro like this work?   Or am I crazy?

This is why I build all my installs using the mini.iso. You get a bare command line installation and add only what you want from there.

One of my favorite installs ATM is 12.04/MATE with only hand-picked apps installed.

---

### Post by Lucradia on 2012-08-31
My configuration is as follows for a dream Distro:

```
## Remember to use alsamixer then, after quitting it with desired settings, use alsactl store.
## In pcmanfm, make sure it's the desktop manager.
## .config/openbox/autostart.sh
## ## Add pcmanfm -d
## ## Add conky
## /etc/apt/sources.list
## ## Add deb http://www.debian-multimedia.org squeeze main non-free
## ## Add contrib to all the debian repos.
## After installing flash, replace it with 10.1, as it's much faster.
apt-get install openbox obmenu menu obconf openbox-themes gtk-themes-murrine gtk-chtheme alsa-utils iceweasel xorg pcmanfm gnome-icon-theme stalonetray conky flashplugin-nonfree hplip xsane gimp pidgin pidgin-libnotify gstreamer0.10-x gstreamer0.10-ffmpeg ffmpeg faad faac totem freepats x264 libdvdcss2 sakura htop scrot unclutter xdg-utils usbmount --no-install-recommends
```

Some builds of pcmanfm won't take the desktop sadly (and there are no desktop options in said builds.) I get frustrated when that happens. Conky:

```
    # Conky, a system monitor, based on torsmo
    #
    # Any original torsmo code is licensed under the BSD license
    #
    # All code written since the fork of torsmo is licensed under the GPL
    #
    # Please see COPYING for details
    #
    # Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
    # Copyright (c) 2005-2009 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
    # All rights reserved.
    #
    # This program is free software: you can redistribute it and/or modify
    # it under the terms of the GNU General Public License as published by
    # the Free Software Foundation, either version 3 of the License, or
    # (at your option) any later version.
    #
    # This program is distributed in the hope that it will be useful,
    # but WITHOUT ANY WARRANTY; without even the implied warranty of
    # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    # GNU General Public License for more details.
    # You should have received a copy of the GNU General Public License
    # along with this program.  If not, see <http://www.gnu.org/licenses/>.
    #

    # Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_hints sticky,undecorated,below,skip_taskbar,skip_pager
    background no
    # Use double buffering (reduces flicker, may not work for everyone)
    double_buffer yes
    # fiddle with window
    use_spacer yes
    use_xft yes
    # Update interval in seconds
    update_interval 0.5
    # Minimum size of text area
    #minimum_size 5 5
    # Draw shades?
    draw_shades yes
    # Text stuff
    draw_outline no # amplifies text if yes
    draw_borders no
    uppercase no # set to yes if you want all text to be in uppercase
    # Stippled borders?
    stippled_borders 8

    # border margins
    border_margin 4
    # border width
    border_width 1
    # Default colors and also border colors, grey90 == #e5e5e5
    default_color white
    default_shade_color black
    default_outline_color white
    own_window_colour brown
    own_window_transparent yes
    # Text alignment, other possible values are commented
    #alignment top_left
    #alignment top_right
    alignment bottom_left
    #alignment bottom_right
    # Gap between borders of screen and text
    gap_x 10
    gap_y 10
    # stuff after 'TEXT' will be formatted on screen
    override_utf8_locale no
    xftfont Terminus:size=8
    xftalpha 0.8

    TEXT
    ${offset 0}${color lightgrey}Kern:${color }$kernel ][ ${offset 0}${color lightgrey}${time %a, } ${color }${time %e %B %G} ][ ${offset 0}${color lightgrey}${time %Z,    }${color }${time %H:%M:%S} ][ ${offset 0}${color lightgrey}CPU:${color } $cpu% ${acpitemp}C ${offset 0}${cpubar 3,100} ][ ${offset 0}${color lightgrey}MEM:  ${color } $memperc% $mem/$memmax ${offset 0}${membar 3,100} ][ ${offset 0}${color lightgrey}SWAP: ${color }$swapperc% $swap/$swapmax ${offset 0}${swapbar 3,100} ][ ${offset 0}${color lightgrey}NET: ${offset 0}${color}Up: ${color }${upspeed eth0} ${offset 0}${color}Down: ${color }${downspeed eth0}${color}
```

And autostart:
```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs that will run after Openbox has started
(sleep 2 && pcmanfm -d) &
(sleep 2 && conky -d) &
(sleep 2 && stalonetray --dockapp-mode --sticky true -t true --grow-gravity W) &
```

With this setup you WILL have to use CUPS webpage to add printers/scanners. It is located at **localhost:631** (If you do not have an HP Printer, you will have to forego using hplip, and just install cups, etc.)

---

### Post by mips on 2012-08-31
It would be Arch based so it would probably just be default post install script instead of a actual distro.

---

### Post by KiwiNZ on 2012-08-31
Ubuntu, but with greater continuity of branding and style and with device type spins as opposed to DE spins.

---

### Post by Mikeb85 on 2012-08-31
openSUSE with Gnome 3 and a Software Centre
- or - 
Ubuntu that runs quicker (ie. improve or remove Compiz), with less bugs, better compatibility.

Ubuntu is pretty good when it's running well, but it seems quite buggy, even the LTS, and it's the slowest Linux distro I've used - still move responsive than Windows 7, but not by alot.  

openSUSE runs much better, is more stable, much quicker, compatible with more hardware out of the box, but lacks a few of the user-friendly touches that Ubuntu has - namely a software centre, and easy installation of non-free drivers...

---

### Post by lykwydchykyn on 2012-08-31
> **mamamia88 said:**
>  Could a distro like this work?   Or am I crazy?

This is more or less how all distros worked before around 2004 or so.  Honestly, it was a nightmare for anyone learning Linux.  Then came Knoppix and MEPIS with the whole liveCD install-a-complete-desktop-with-minimal-questions thing, and it turned out to be pretty successful.  Many distros still do it "þe olde way", though.

---

### Post by mips on 2012-08-31
> **Mikeb85 said:**
> ... and it's the slowest Linux distro I've used - still move responsive than Windows 7, but not by alot.  


Have to agree. It does not have to be that way though. Compare a base/cli install + the DE of you choice to the official release and you will see a big difference in speed. When I say this I'm not talking about old hardware but a modern quad core setup with 4GB or ram and decent GPU.

---

### Post by Majorix on 2012-08-31
My dream distro would be fast-booting (like Haiku), rolling release (like Sid or Arch), would install from source (like FreeBSD or Gentoo), would have a very large community (like Ubuntu) and would look beautiful without me doing too much (like OSX). Best-of-all-worlds :D

EDIT: Oh, maybe some kind of underlying Windows code too, so I don't have to reboot into that mess :D

---

### Post by Jakin on 2012-08-31
I mentioned elsewhere-

I would like a "Distro" a group might put together as an alternative dvd installer- (LIVE-CD is not important to me, as i install in virtualbox and mess with something for a few days before ultimately installing) -that installed the base of Ubuntu first- then asked as Easy Install what DE you wanted, so it wouldn't, have anything you didn't want.
OR Custom Install, which loaded as many DEs you wanted, as well as ultimately having control over the programs installed as extras.

Major DEs i would like KDE GNOME UNITY Enlightenment XFCE LXDE.

The extras would be things like Codecs, WINE, GiMP, FireFox and Chrome, Blender, VLC, Virtualbox, Amarok/JuK/banshee, Transmission Client, Skype, flash and java latest stables, hardware video drivers, network drivers.

(All features of which the latest releases at the time of the build)

I believe this would all fit on 1 DVDiso, without extra languages. There ought be a seperate iso, that just includes languages anyway.

This is stretching it, but let me dream :P

---

### Post by dodo3773 on 2012-08-31
Somewhere between Arch and Funtoo. With additional options to edit source code during build time and complete sets of cpu specific binary packages. Oh, and more noobie friendly long use flag explanations per application with dependency information (like without use flag x these dependencies are not needed etc (maybe a live color coded output man that would be sweet)). Oh, and no overlays or aur needed, everything is in one central repository (source and binaries). Also, all programs would have included gnu long options, man pages, and lots of examples. A huge extensive wiki for almost every scenario that can be thought of online and offline. rc.conf style all in one configuration file + openrc / systemd style paralleled loading of services / daemons. The default shell would of course be zsh with all completions already setup in place. A default sane fallback kernel. It would be a netinstall with a well working wireless setup for install (similar to bsd? maybe). That's all I can think of right now.

---

### Post by afixane on 2012-09-01
Simple, Fast, Beautiful, Semi-rolling (Update the software every 1-6 Month but not the entire OS), and Easy :D

---

### Post by mamamia88 on 2012-10-09
Sorry to revive this thread but i thought of my perfect distro.    a base install of arch with yaourt and utilities for unzipping installed by default.  it would come with a script on the desktop that when run would ask you what video driver to install and what browser to install and wireless if available. really with package managers i don't really see the point in installing anything more than a browser and desktop environment by default. also none of this editing text files for basic stuff like changing timezone. of course the option would be available but no reason not to be able to chose it from a drop down list or something and just have the text inserted into the file after selecting it from a list

---

