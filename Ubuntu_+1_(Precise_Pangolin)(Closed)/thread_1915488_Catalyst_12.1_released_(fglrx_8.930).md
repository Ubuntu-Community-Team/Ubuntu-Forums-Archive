---
title: "Catalyst 12.1 released (fglrx 8.930)"
date: 2012-01-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2012-01-26
OK people, another month another Catalyst.

Download is here: [http://www2.ati.com/drivers/linux/amd-driver-installer-12-1-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-1-x86.x86_64.run)

Tip! For a simple ramdisk, use /dev/shm !

As normal, I run:

$ chmod +x amd-driver-installer-12-1-x86.x86_64.run
$ ./amd-driver-installer-12-1-x86.x86_64.run --buildpkg Ubuntu/precise
$ sudo dpkg -i *.deb

then copy the .debs somewhere for safekeeping. :)

Installation proceeds as expected (no errors). Will reboot and see how it goes. According to a Phoronix thread linked from the Arch catalyst AUR page this release fixes rendering in gnome-shell. We'll see about that. :D

---

### Post by jfernyhough on 2012-01-26
Well, there are no graphical glitches in gnome-shell, which is nice. Window dragging is still laggy as anything, though, but this is a problem with VSYNC (surprise!). I'm looking into how to disable vsync by default; there has to be a better way than running

$ CLUTTER_VBLANK=none gnome-shell --replace

---

### Post by lucazade on 2012-01-26
> **jfernyhough said:**
> Well, there are no graphical glitches in gnome-shell, which is nice. Window dragging is still laggy as anything, though, but this is a problem with VSYNC (surprise!). I'm looking into how to disable vsync by default; there has to be a better way than running

$ CLUTTER_VBLANK=none gnome-shell --replace

great to hear catalyst now supports gnomeshell without glitches.. I see many in the past especially in the menu with distorted textures.

usually I put that clutter_vblank export in /etc/environment to use apply it at boot time.

---

### Post by Superlinkx on 2012-01-28
Thanks so much! Using the CLUTTER_VBLANK=none fixed my only video problems in 12.1. Gnome-shell is buttery smooth with no graphical glitches. Plus, all my graphics intensive programs (eg Minecraft) are working better than ever!

Thanks again @jfernyhough!

---

### Post by jfernyhough on 2012-01-28
Nice... just found an addition to the Arch ATI [wiki page]("https://wiki.archlinux.org/index.php/ATI_Catalyst#Laggs.2Fslow_windows_movement_in_GNOME3")...

[quote=Arch wiki]
Add this line: 
 export CLUTTER_VBLANK=none
into ~/.profile or into /etc/profile file. Restart X server or reboot system.[/quote]

I didn't fancy messing with /etc/environment . :) (plus I'm sure I tried that and it didn't work for me... anyway, .profile works well)

---

### Post by nardusg on 2012-02-15
Issues playing video with latest catalyst drivers:

[http://ati.cchtml.com/show_bug.cgi?id=337#c7](http://ati.cchtml.com/show_bug.cgi?id=337#c7)

Not a solution but a workaround; add the following snippet to your
/etc/X11/xorg.conf, that way the crashy code won't be executed:

Section "Extensions"
       Option "XVideo" "Disable"
EndSection

---

