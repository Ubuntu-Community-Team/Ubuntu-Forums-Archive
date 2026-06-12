---
title: "Daru2 kubuntu: Xorg.conf (800x600 default res)"
date: 2008-01-25
forum: System76 Support
---

### Post by ackey on 2008-01-25
I've spent many hours fighting with my xorg.conf file after destroying it in an attempt to add another monitor.  Before everything was working fine in kubuntu.

I have used the System76 driver to restore it to a clean default.  Now my biggest problem is that the default resolution is always 800x600.  Using krandrtray I can switch to larger resolutions once it boots, but when X starts it always returns to 800x600.  This is true for the screen and when I connect to an external monitor (though there are different resolutions available then).  If I plug an external monitor in on startup, it uses the external monitor and I can't get it to use the laptop screen without restarting X - I don't remember this being the case before.

I've tried reconfiguring X and using interactive menus, and everything I have tried has made it worse.

I have a daru2 and I'm running Gutsy/KDE.  Can someone please post what my xorg.conf file should look like, or instructions on how I can fix my default resolution?  If I need to reconfig X or something similar, can someone post what values I should actually tell it?

I feel like this must be a simple problem, but every "simple" solution I have tried made it worse.

I've included below the portion of xorg.conf that seems to have anything to do with the display.
```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection
```

---

### Post by thomasaaron on 2008-01-28
Running the System 76 Driver (with the Restore Tab and Restore Button) will drop back in the correct xorg.conf file for your computer. The press Ctrl+Alt+Backspace to restart x.
You should then be able to go to Sytem > Preferences > Screen Resolution (or whatever the KDE equivalent is) and set your default resolution.

Did you use the "restore" tab and button (as opposed to the "install" tab and button)?

---

### Post by ackey on 2008-01-28
I used the restore button and it did change my xorg.conf file - was what I posted right?  I notice that there aren't any modes/modelines in it.  Any of my attempts to "fix" it resulted in there being modelines that KDE read appropriately (though I don't think they were actually right for the screen).

When I go to the KDE monitor/display menu there are only 640x480 and 600x800 listed as options.  The "hardware" tab of the menu lists Vesa driver twice with "unknown" monitor under each one.  However, krandrtray seems to know enough about the screen to list the appropriate resolutions, but doesn't seem to change the default resolution.

---

### Post by thomasaaron on 2008-01-28
OK, I don't know much about krantray, but you need to be using the intel driver, not the vesa driver.

You might want to try to run:
sudo dpkg-reconfigure xserver-xorg

*choose the intel driver
*choose ALL available resolutions
*choose "Advanced" when presented with that option
*choose default values for everything else

Then reboot the computer.

---

### Post by ackey on 2008-02-01
That did it, once I selected the new resolution and restarted.  Thanks!

---

