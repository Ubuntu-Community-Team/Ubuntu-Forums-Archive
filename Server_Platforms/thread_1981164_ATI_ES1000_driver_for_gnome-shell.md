---
title: "ATI ES1000 driver for gnome-shell"
date: 2012-05-16
forum: Server Platforms
---

### Post by snotplop on 2012-05-16
Hey all,

Building up an Ubuntu 12.04 LTS server for my job;
our needs require that we have a gui, so I decided to go with gnome-shell since it's just so darn pretty. :) Problem is that support for ATI cards seems to be moving more towards a wasteland with each successive release of ubuntu... :(
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) - is really not helpful in any way, although it at least attempts to document the situation...

Our server is an HP Proliant DL380 G7, and lspci reports:
```
$ lspci -vv | grep -E "VGA.*controller"
01:03.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI ES1000 (rev 02) (prog-if 00 [VGA controller])
```Using the "preferred" method of self, automagic configuration, I'm just getting dropped into the proverbial "There is a problem with your display" message with several not-very-helpful options, just after lightdm comes up, but all before I'm granted a greeter.


Here's what I've done so far to metamorphosize ubuntu server-minimal into one with a gui:
```
$ sudo apt-get install ubuntu-desktop gnome-shell
$ sudo update-rc.d lightdm defaults
$ sudo apt-get remove ubuntu-desktop network-manager
$ sudo telinit 6
    <broked>
$ grep -E "\(EE\)" < /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.328] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.433] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.947] (EE) AIGLX error: Calling driver entry point failed
[    17.947] (EE) AIGLX: reverting to software rendering

```Funny that... By reading the Ubuntu documentation above I thought that 12.04 prefers the open source radeon driver and *not* fglrx..?
Let's force it to use "radeon" by crafting a quick n' dirty /etc/X11/xorg.conf:
```
$ cat xorg.conf
Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
       Option    "XkbLayout" "us"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "radeon"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth    24
    EndSubSection
EndSection
$ sudo telinit 6
$ grep -E "\(EE\)" < /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.292] (EE) AIGLX error: Calling driver entry point failed
[    15.292] (EE) AIGLX: reverting to software rendering
```No beans.
Hmm... maybe fglrx is actually the way to go...?

```
$ sudo apt-get install fglrx
$ cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
       Option    "XkbLayout" "us"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "fglrx"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth    24
    EndSubSection
EndSection
$ grep -E "\(EE\)" < /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   217.205] (EE) No supported AMD display adapters were found
[   217.205] (EE) No devices detected.
[   217.211] (EE) No supported AMD display adapters were found
[   217.380] (EE) GLX error: Can not get required symbols.
```Mreow... :( Anybody have any ideas?

---

### Post by evammg on 2012-05-18
I have same problem! Any light on this please?

I found this thread where he says he solves the problem moving a file calle ~/.config/autostart of gnome3.. but where is it? I can't find it in my Ubuntu 12.04

[https://bbs.archlinux.org/viewtopic.php?id=120235](https://bbs.archlinux.org/viewtopic.php?id=120235)

---

### Post by evammg on 2012-05-18
I've got something!!

I have installed "fglrx"

as it says here: [http://www.linuxgator.org/gnome/forum/viewtopic.php?p=22929](http://www.linuxgator.org/gnome/forum/viewtopic.php?p=22929)

And now X has normal performance, it works fine, but.. the resolution seems to be not the right one.. I see icons too big.. I have tried other available resolutions but they don't work.

Well, at least the problem of performance is fixed..

---

### Post by evammg on 2012-05-18
And I still have this error on my Xorg log file:

[FONT="Courier New"]GLX error: Can not get required symbols[/FONT]

---

### Post by evammg on 2012-05-18
..in fact, this is not working properly at all.. but I can't understand all that the Xorg log file says..

I attach my log files anyway.

And when I switch to load Xen, X doesn't start, it takes all the memory even swap.. ?? so I had to kill Xorg with kill -9 (pid xorg) because it didn't stop with "service lightdm stop"..

I don't know what's going on..

---

### Post by evammg on 2012-05-18
and I've just found this regarding to Xen..

[http://wiki.xen.org/wiki/Linux_3.0_bugs_impacting_Xen#32-bit_graphic_cards_.28AGP.2C_or_server_ones:_ATI_ES1000.29_can.27t_do_Xorg](http://wiki.xen.org/wiki/Linux_3.0_bugs_impacting_Xen#32-bit_graphic_cards_.28AGP.2C_or_server_ones:_ATI_ES1000.29_can.27t_do_Xorg)

---

