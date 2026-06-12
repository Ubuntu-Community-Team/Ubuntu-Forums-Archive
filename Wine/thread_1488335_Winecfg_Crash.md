---
title: "Winecfg Crash"
date: 2010-05-19
forum: Wine
---

### Post by Mark XIII on 2010-05-19
Please Help!

Winecfg crash after run and System  freezes.

Ubuntu lucid x86

Source: wine1.2
Version: 1.1.44-0ubuntu1~lucidppa1
Depends: wine1.2 

gnome-terminal:

> ...:$ winecfg

system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg is not a valid registry file

err:process:start_wineboot failed to start wineboot, err 11



---

### Post by asdfoo on 2010-05-20
sounds like your system is broken if it freezes.

you can try in a clean wineprefix

WINEPREFIX=~/wine-temp winecfg

---

### Post by Mark XIII on 2010-05-20
> **asdfoo said:**
> sounds like your system is broken if it freezes.

you can try in a clean wineprefix

WINEPREFIX=~/wine-temp winecfg

The System still freezes.

---

### Post by Blackleker on 2011-02-22
Do  to my me pasa lo mismo with one line on the same screen I have  discovered that the cause is the openchome drivers are using openchrome  drivers? If you edit the xorg sudo gedit /etc/X11/xorg.conf change the line:

Driver "openchrome"

by

Driver "vesa"

o

Driver "via"

If you have installed the drivers via 

):P

---

### Post by Blackleker on 2011-03-07
Hello was apparently a bug I found a solution applying the patch that I found here:

[http://www.openchrome.org/trac/ticket/400](http://www.openchrome.org/trac/ticket/400)

[ATTACH]185377[/ATTACH]

---

