---
title: "Windows/Ubuntu Dual Boot and Drivers"
date: 2007-03-17
forum: System76 Support
---

### Post by AlphaMack on 2007-03-17
Hi all...

I'm exploring the possibility of upgrading to a System76 laptop (probably Gazelle) from a 3-year-old PowerBook G4 that is already starting to fall apart.  I would like to set up a XP/Ubuntu dual-boot system.  Although I've read the how-to in the Wiki on accomplishing this task, my question is this:

Are Windows drivers conveniently provided by System76 and if so, how can they be obtained?  Or will I need to hunt down the drivers myself (what fun)?

---

### Post by crichell on 2007-03-19
> Are Windows drivers conveniently provided by System76 and if so, how can they be obtained?

We provide all of the Windows drivers with the system.

---

### Post by aussie_in_rome on 2007-05-02
> **crichell said:**
> We provide all of the Windows drivers with the system.

I've got a Sony Vaio UX (VGN-UX17GP) - I installed Ubuntu on it last night. Ubuntu is BEAUTIFUL and FAST!

Does Ubuntu support the UX's GUNZE touch screen for example, where can I get the driver? Also does it support the two built in web cams?

I have never used Linux in my life and I'm not a tech-head so unless it's a simple execute an app to install these drivers, then I can't do it. Which will be a pitty as many other new Ubuntu users will be in the same boat.

---

### Post by thomasaaron on 2007-05-02
Here's a guy who apparently got it to work on a Vaio with some simple additions to the xorg.conf file.

[http://mozy.org/vaio/](http://mozy.org/vaio/)

---

### Post by aussie_in_rome on 2007-05-02
> **thomasaaron said:**
> Here's a guy who apparently got it to work on a Vaio with some simple additions to the xorg.conf file.

[http://mozy.org/vaio/](http://mozy.org/vaio/)

What's an Xorg.conf file?

---

### Post by thomasaaron on 2007-05-02
It's a configuration file contains parameters for your xserver.

You can view/change it by typing the following into a terminal:

sudo gedit /etc/X11/xorg.conf

CAUTION ADVISED.

---

### Post by madcow72 on 2007-05-02
As a first time Linux user, I understand your confusion on the xorg.conf file and the mention of an X server.  You can read about the X server at Wikipedia [here]("http://en.wikipedia.org/wiki/X_server"), but basically you can think of it as the user interface which sits on top of the Linux operating system.  In other words, it links all of your devices and your display to the actual Linux operating system underneath, and the xorg.conf file is a small textual configuration file that describes how each device is to be configured (mouse, screen, dual monitors, keyboard, etc.)

Ubuntu is getting to the point that an average user doesn't have to make any changes manually to this file anymore, however you may have touched upon one occasion in which it may be necessary or convenient to edit the xorg.conf file directly.  

It's very easy to edit, actually.  Take what thomasaaron just suggested, and type this into a terminal:  (You can open a terminal by going to Applications -> Accessories -> Terminal  or you can hit Alt+F2, which will open a small window where you can type gnome-terminal, and hit enter.)
```
sudo gedit /etc/X11/xorg.conf
```
You will have to enter your user password, and then this will open your xorg.conf file in a small program called Gedit, which is similar to Notepad in Windows.

Inside this file, you would want to paste the section of the xorg.conf that was on the page that thomasaaron referred you to earlier:  [http://mozy.org/vaio/]("http://mozy.org/vaio/")  You should be able to go to the bottom of the entire file and paste this in:

```
Section "InputDevice"
        Identifier      "Gunze touchscreen"
        Driver          "evdev"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event3"
        Option          "minx"                  "50"
        Option          "maxx"                  "970"
        Option          "miny"                  "90"
        Option          "maxy"                  "970"
EndSection

Section "serverlayout"
        Inputdevice     "gunze touchscreen"
EndSection
```

When you're done, save the file and exit the program (Ctrl+S then Ctrl+Q).  Finally, to actually use your new configuration, you will have to restart the X server.  The easiest way to do that is to make sure you don't have any programs open where you may lose data, and then hit Ctrl+Alt+Backspace.  This is similar to Ctrl+Alt+Del in Windows, but only restarts the X server, not the entire computer - so it's much faster.  When you log back in, if this in fact works, you should be able to use the touchscreen.

In case you run into problems, you can always get back into the xorg.conf file and delete those lines to restore it back to its original state.  Then we'll have to try something else, such as the howto found [here]("http://ubuntuforums.org/showthread.php?t=419235&highlight=touchscreen").

---

### Post by newlinux on 2007-05-02
I recommend you make a backup of the current xorg.conf first:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then modify it.

If something goes wrong that you can't fix right away you can always restore the backup.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by aussie_in_rome on 2007-05-10
I did this and my PC got corrupted... it said that there was an odd character...

I think it was this, the \ in the "Device" entry.

Option          "Device" \               "/dev/input/event3"

would that do it?

---

### Post by thomasaaron on 2007-05-10
Yeah, that might cause some problems.
Just delete the \.
Save the file.
Press Ctrl-Alt-Backspace to reset.

---

### Post by aussie_in_rome on 2007-05-11
So I copy and paste all this at the bottom of the xorg.conf file?

Section "InputDevice"
        Identifier      "Gunze touchscreen"
        Driver          "evdev"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event3"
        Option          "minx"                  "50"
        Option          "maxx"                  "970"
        Option          "miny"                  "90"
        Option          "maxy"                  "970"
EndSection

Section "serverlayout"
        Inputdevice     "gunze touchscreen"
EndSection

---

### Post by thomasaaron on 2007-05-11
Yes.

Make sure all of the whitespace (tabs) matches up.
Then save the file.
Then hit Ctrl-Alt-Backspace.

---

### Post by madcow72 on 2007-05-23
> **thomasaaron said:**
> Make sure all of the whitespace (tabs) matches up.


Do the tabs really need to line up?  I think I do that anyway to keep things neat looking, but I didn't know it was important...
By the way, aussie_in_rome, does your touchscreen actually work after doing this?  I'd be curious to find out.

---

