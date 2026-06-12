---
title: "[HELP] Lightweight Customized Ubuntu"
date: 2010-01-11
forum: Ubuntu Customization Guide
---

### Post by adudutz on 2010-01-11
I've been using Ubuntu for a while and had installed it on several PCs with no internet connection by default. I've been observing lately that these old systems (mostly Pentium III PCs with 256-384 RAM and old VGAs) work slowly, even if I installed Xubuntu in them (I often have problem with the xfce4-panel as well).

To counter these problems, I'm planning to make my own customized version of Ubuntu which is lightweight, easy to use, and has a complete out-of-the-box printer driver support.

These old systems are used in form of SOHO. Most of the people using them are used to be Windows XP users, so I want to create a GUI which resembles Windows.

After some surfing and looking through various guides, I've decided to make these modifications in the default Ubuntu installation:
[LIST]
[*]IceWM as the default window manager
[*]PCManFM as the default file manager (may be changed) <<< suggestions needed
[*]Epiphany as the default web browser
[*]SLiM/qingy as the default login manager (replaces GDM)
[*]GNOME Office (Abiword/Gnumeric) as the default office program (replaces OpenOffice.Org)
[*]VLC as the media player (replaces other media players)
[*]InfraRecorder as the disc authoring tool
[*]WINE as the Windows compability layer
[*]Java (out-of-the-box)
[*]Proprietary Microsoft fonts
[*]Customized background, boot splash-screen, login menu
[/LIST]

and the rest may be same to Ubuntu (Synaptic, Printing, etc.)

My question is:

[LIST=1]
[*]What items will be required to build such system?
[*]Do I need to manually compile and configure this system through Command-Line Ubuntu Installation (using the alt-CD) before putting it into another computer? (using VirtualBox for the simulation)
[*]How to automatically configure the system during installation (so I just need to personalize the users only, not the whole system)?
[*]How to make a Live CD from this customized Ubuntu?
[/LIST]

Sorry for the quite long reading. Any help will be highly appreciated.

Thanks :)

---

### Post by Taras.M.K on 2010-01-11
I'd recommend to check other projects firstly. Something's been done already. Try par example Vector-linux ([http://vectorlinux.com/](http://vectorlinux.com/)), Puppy linux ([http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)) or Lighthouse pup ([http://www.lhpup.org/](http://www.lhpup.org/))...

---

### Post by michaelzap on 2010-01-11
You might try the LXDE version of Debian as a base instead:
[http://lxde.org/download](http://lxde.org/download)

Reconstructor might be a good way to create your own mix if you decide to do that after all:
[http://www.webupd8.org/2010/01/web-based-ubuntu-and-debian-custom.html](http://www.webupd8.org/2010/01/web-based-ubuntu-and-debian-custom.html)

---

### Post by adudutz on 2010-01-12
I surfed around the net and found this Ubuntu-based distro:

[Spri]("http://sprilinux.com")

From the screenshots, I think this is similar to what I'm going to compile. I wanna give it a shot to learn from it.

PS: I decided to make the system from minimal Ubuntu installation (command-line only), compile the packages I need, and then packing it using remastersys.

---

### Post by adudutz on 2010-01-12
edit: double post

---

