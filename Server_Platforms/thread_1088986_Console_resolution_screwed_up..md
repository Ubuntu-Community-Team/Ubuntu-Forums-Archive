---
title: "Console resolution screwed up."
date: 2009-03-06
forum: Server Platforms
---

### Post by PinkFloyd102489 on 2009-03-06
I had Xorg installed on my server platform because I had Fluxbox window manager installed.

When I uninstalled Xorg and Fluxbox, the resolution scaled down from 1024x768 to 720x640. I googled around for a solution, such as re-adding the vga defoption to GRUB's menu.lst, but it didnt work.

Does anyone know how to fix this?

---

### Post by hictio on 2009-03-06
But, the 'vga' option doesn't help in getting a higher resolution while running a Window Manager in X Window.

If you want to have a higher resolution console (no X Window, all CLI, but with a lot more information on screen than the default 80x25 chars), take a look here: [Ubuntu high resolution console](http://oesediez.blogspot.com/2008/09/ubuntu-high-resolution-console.html)

If you want to have a higher resolution Window Manager, while running X Window, then you'll have to edit the '/etc/X11/xorg.conf' file, most likely, adding the "1024x768" resolution to the Modes line, on the Display subsection of the section Section.

Like this:
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Samsung SyncMaster 920NW"
        Device          "NV11 [GeForce2 MX/MX 400]"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"

        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
                Viewport        0 0
        EndSubSection
EndSection

```

Provided, of course, that the config file includes a vertical & horizontal refresh rate setting that can handle that resolution.

---

### Post by PinkFloyd102489 on 2009-03-07
I tried the high res console link you provided but the resolution is still 720x400.

---

### Post by hictio on 2009-03-07
That's weird, I have used that to get a high resolution console since 7.10 w/o a problem...
Are you rebooting the box after you finish editing all the files?

Once again, the configuration changes on the link I posted are only for changing the console resolution, they wouldn't have any effect on a graphical environment.

What 'vga' value are you using? Perhaps you are using one that you can't handle, here is a table of all the values and their resolutions and depths [VGA Boot modes to set screen resolution](http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/)

---

### Post by PinkFloyd102489 on 2009-03-07
The monitor I have can handle 1280x1024 @ 60Hz. Ive tried 795, 794, 792, and 791.

The only option I can think of is to reinstall, but Id have to back up all of my SQL tables which I really do not want to do.

---

### Post by hictio on 2009-03-08
That's really weird, just did a test on a plain vanilla 8.10 Server install I did on a crappy box, after the initial install followed the steps I posted [here](http://oesediez.blogspot.com/2008/09/ubuntu-high-resolution-console.html), question, if you follow the steps, and reboot, when you do a:

```

dmesg | egrep fb

```

Does it print that its in use?

Another thing, in what order are you adding the 'vag=xxx' option on  '/boot/grub/menu.lst'?
Mine looks like this:

```

# defoptions=vga=788 quiet splash

```

I can only test 788 on that box (its a crappy old Compaq Presario that only delivers 800x600)

---

### Post by PinkFloyd102489 on 2009-03-20
Nothing relevant in the dmesg.

---

### Post by blackbelt_jones on 2009-05-07
I'm not sure what's meant here by running the console while running X, but my console resolution in jaunty when not running X is completely whacked.  Reinstalling doesn't help.

---

### Post by hictio on 2009-05-07
> **blackbelt_jones said:**
> I'm not sure what's meant here by running the console while running X, but my console resolution in jaunty when not running X is completely whacked.  Reinstalling doesn't help.

What you mean "whacked"? I have tested the high resolution console setup on Jaunty, and at least on plain vanilla Ubuntu, not Server, it works perfectly.
It is the same as on Intrepid, for one step, placed the procedure I did here: [Ubuntu high resolution console (3)](http://oesediez.blogspot.com/2009/05/ubuntu-high-resolution-console-3.html)

The only thing I noticed is that I didn't have the usplash Ubuntu logo after it, but I'm not sure if that it due to the high resolution console, or a set of [installed updates](http://oesediez.blogspot.com/2009/05/updates-dujour_05.html) I did after.

But nevertheless, the high resolution console works just fine, I'm using a 791 value for the vga directive.

---

### Post by qlinux on 2009-05-20
I was having what appeared to be resolution problems as well.  The letters were all jittery and sort of appeared to be shimmering.  Also the text was starting about an inch in from the right side of the screen and then continuing from the left on the same line.  

I tried the examples above but settings like vga=771 or vga=778 would not work. The monitor would just show a message that the resolution was not supported.  

Here's what worked.  In /etc/grub/menu.lst I set ```
# defoptions=vga=0x301 quiet splash
```  Then ran sudo update-grub and rebooted.

This setting forced a vesa setting of 640x480x8. It's an older PIII system and I think the issue might have been limitations on the graphics chip, not the monitor.  Anyway I hope this helps others.

Q!

---

