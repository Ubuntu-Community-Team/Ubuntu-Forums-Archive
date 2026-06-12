---
title: "SunBlade 100 Installation"
date: 2006-09-28
forum: Sun Sparc Users
---

### Post by shawnerz on 2006-09-28
I want to say that I am impressed.  Very impressed.  I downloaded and installed Ubuntu Dapper without any problems.
In the past, I tried, the Aurora port, Debian (from debian.org), and even Solaris 10.  Nothing installed without problems and the one that did install was not stable.

I do have a question: is a graphical mode or is this a text only release?  I tried 'startx' at the command prompt but that did not work.
Thanks in advance,
-Shawn

---

### Post by netztier on 2006-09-28
> **shawnerz said:**
> I do have a question: is a graphical mode or is this a text only release?  I tried 'startx' at the command prompt but that did not work.


For Sparc, the CD does an install of ubuntu-server, and that is without X.org or a desktop environment.
With apt-get or aptitude, you can install the packages ubuntu-desktop, xubuntu-desktop or kubuntu-desktop, depending on your preference of desktop environment. This will then install X.org and all other packages you need. 

kind regards

Marc

---

### Post by rimtech on 2006-09-28
if you are going to desktop route and installing the GUI (ie by running apt-get install ubuntu-desktop), you will have to manually edit /etc/X11/xorg.conf and add



```
Option "ReferenceClock" "29.500"

```


into the Device section. This is specific for Sun Blade 100, if you dont do it X will crash on startup.

---

### Post by shawnerz on 2006-09-28
Rimtech and Marc,
Thanks for your help.  I did a apt-get ubuntu-desktop.  I made the change to xorg.conf.
I'm not sure what video chipset is in this machine.  When prompted during the setup, I selected vga.

I did a reboot and got a message saying the video server had been shutdown 6 times in the last 90 seconds.

Once I got to a stable text screen, I typed 'startx' and the machine locked up and a steady tone came from the speaker.

I will do a dpkg-reconfigure -phigh xserver-xorg again, but do you know which chipset I should select?
Thanks,
-Shawn

---

### Post by netztier on 2006-09-29
> **shawnerz said:**
> Rimtech and Marc,
Thanks for your help.  I did a apt-get ubuntu-desktop.  I made the change to xorg.conf.
I'm not sure what video chipset is in this machine.  When prompted during the setup, I selected vga.
[...]
I will do a dpkg-reconfigure -phigh xserver-xorg again, but do you know which chipset I should select?


Try ati, as suggested in this [forum thread]("http://www.ubuntuforums.org/showthread.php?t=202443").

regards

Marc

---

### Post by shawnerz on 2006-09-29
Marc (and all),
Thanks for your help.  I read over the thread that you linked to me.
I seem to be having the same problem that the other person is having.
I selected ATI in the setup and added the ReferenceClock line to xorg.conf.
My Dell LCD monitor says it can't display the image due to the scan rate being too high.
I've tried both 800 X 600 and 640 X 480 with both scan rates of 56 and 60 Hz.  The LCD display won't display either one.
My analog 17" monitor displays the image with no problems.


My second problem is I want to install the Tulka Whitebaord server.  The installation stops because it says Java is not installed.
I typed apt-get install java and that did not work. Is there a Java port for Dapper Drake?

Thank you very much in advance.
-Shawn

---

### Post by rimtech on 2006-09-29
the problem with your monitor is undoubtedly your horizontal and vertical scan rates, what YOU are reffering to as the scan rate of 56 and 60hz is actually the REFRESH rate of the monitor.

what specific model is your dell monitor?
this may give us some information as to what the exact specs of that monitor is, if you can't get this information from dell's website you may be able to google the info.

If you can't, please provide us with the model number to the unit so we can try looking for the info.

As for Java you can go to the community java docs here...
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

which states...

Sun Java5: Install it from the Applications -> Add/Remove... menu making sure to check the unsupported and proprietary software checkboxes, or install the sun-java5-bin package. 

Blackdown Java2 1.4 packages: Install the j2re1.4 package, available in the multiverse repositories. Install it from the Applications -> Add/Remove... menu, or install the j2re1.4 package.

---

### Post by torches on 2006-09-30
Here is my xorg.conf file. I use a SB100 with a Sun 19" LCD. Get the Horizantla and vertical refresh rates for your display and all should work. make sure to round up for the lower limit and round down for the upper limits. mine were 
# 31.5 kHz to 81.1 kHz  Horizantal
# 56.0 Hz to 76.0 Hz    Vertical
and I set them for 
        HorizSync       32-81
        VertRefresh     56-76

======cut here ==============
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage XL"
        Driver          "ati"
        BusID           "PCI:0:19:0"
        Option "ReferenceClock" "29.500MHz"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
# 31.5 kHz to 81.1 kHz  Horizantal
# 56.0 Hz to 76.0 Hz    Vertical
        HorizSync       32-81
        VertRefresh     56-76
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Rage XL"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
==========cut here ===========

---

### Post by netztier on 2006-09-30
> **rimtech said:**
> 

Sun Java5: Install it from the Applications -> Add/Remove... menu making sure to check the unsupported and proprietary software checkboxes, or install the sun-java5-bin package. 


sun-java5-bin is not available for the sparc architecture at this time (just tried on my U5). Which is odd, especially for a Server, where Java Servlets with tomcat and the like are (should be?) quite common

kind regards

Marc

---

### Post by netztier on 2006-10-02
> **shawnerz said:**
> Marc (and all),
My analog 17" monitor displays the image with no problems.


Does this monitor have some kind of on-screen-information menu where it shows the picture parameters (scan rate, refresh rate and the like)? That'd give some info what kind of signal is output by the card itself. 

Seeing if it matches the flat panels capabilities will then become a matter of browsing through the FP's data sheet.

kind regards

Marc

---

### Post by shawnerz on 2006-10-02
Marc,
I installed Java by installing OpenOffice.  I did a search of j2re1.4.  Blackdown Java was listed as an option, but was unavailible.  OpenOffice was the only other choice.
I successfully installed Tulka Whiteboard, but I have some configuration issues.  I guess I will have to read the manual.

---

### Post by shawnerz on 2006-10-03
Hello Marc.
I was busy yesterday and unable to give the monitor information.
I made the change to the horizontal and verticle rates in xorg.conf.  I now have the same values that you do in your file.  Again, the LCD monitor doesn't work but, the CRT monitor does work.

The LCD monitor is a Dell 1704FPTt.
The CRT monitor is a Dell P1130.  I suspect it is really a Sony model since "Trinitron" is printed on the top left of the display.

Thank you very much for your help.
-Shawn

---

### Post by netztier on 2006-10-03
> **shawnerz said:**
> Hello Marc.
I was busy yesterday and unable to give the monitor information.
I made the change to the horizontal and verticle rates in xorg.conf.  I now have the same values that you do in your file. 


Not my file. It was torches' posting that contained an xorg.conf

> **shawnerz said:**
> 
The LCD monitor is a Dell 1704FPTt.
The CRT monitor is a Dell P1130.  I suspect it is really a Sony model since "Trinitron" is printed on the top left of the display.


the P1130's [data sheet]("http://support.euro.dell.com/support/edocs/monitors/p1130/en/g_ug/specs.htm")

Thats a fine 21" block of glass you have there. Will do 1600x1200 pixels at 85Hz vertical refresh rate. Impressive. From the data sheet you'll see that it has a horizontal scan range of 30-130kHz, a vertical scan range of 48 to 170Hz. This is typically a lot more than flat panels can cope with.

See here: the [1704FPTs data sheet]("http://support.euro.dell.com/support/edocs/monitors/1704fpt/EN/index.htm"). It does "only" 30-81kHz horizontal and 56 to 76Hz vertical. 

These values should match what you enter into the Monitor's Device Section of your xorg.conf:

```
Section "Monitor"
  ...
  HorizSync    30-81
  VertRefresh  56-76
  ...
EndSection
```

Typically, FPs work best at 60Hz vertical. The table in the data sheet shows that you need 64kHz horizontal scan range (thats 64k horizontal lines per second) to have 60Hz vertical refresh rate at the flat panel's native 1280x1024 resolution. Any other than the native resolution should not be used with flat panels - they have to do pixel interpolation to match a 1024x768 sized picture to a 1280x1024 sized screen. The results are always blurred and ugly.

So. You might want to try nailing down VertRefresh to 60, that might fix things.


The reason why I asked if the CRT Monitor had some OnScreenDisplay menu or config dialogs was to find out what signal the card actually delivers (I checked in the manual, the CRT has an OnScreen Menu where you can read the current picture's values, see [here]("http://support.euro.dell.com/support/edocs/monitors/p1130/en/g_ug/controls.htm").

So. Hook up the CRT to the card, tell us what it says about resolution and refresh rate, and we'll see how we can force the graphics card to deliver a signal that the flat panel can also cope with.

regards

Marc

---

### Post by shawnerz on 2006-10-05
Hello again, Marc.
I got a little busy on another project.  Then I had to fix my sudoer problem, so I am a little late in resolving this problem.
I made the changes and it still doesn't work.
Here is my entire "Monitor" section from xorg.conf:
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       32-81
        VertRefresh     56-76
EndSection

In System | Preferences | Screen Resolution, I'm set to 800 X 600 and a 60 Hz referesh rate.

Again, this setting is working on my CRT monitor but not the FP LDC.

And thanks for the comment on the monitor. :)
-Shawn

---

### Post by torches on 2006-10-05
I recommend taking my xorg.conf file and using it as is. Save a copy of the original one you have. I noticed that the V and H scan rates of your LCD are similar to my display. I only set one resolution which 1280X1024 which your display supports.

---

### Post by netztier on 2006-10-06
> **shawnerz said:**
> In System | Preferences | Screen Resolution, I'm set to 800 X 600 and a 60 Hz referesh rate.

Again, this setting is working on my CRT monitor but not the FP LDC.


Again, i'll ask this question a **third time**:

What does the CRT's OnScreenDisplay/Menu say about the picture signal it gets? It has a menu (see the links I provided or the user's manual) that gives information about the current resolution and refresh rate.

Do these values match the settings you have in "System Preferences" or in /etc/X11/xorg.conf? 

Then - leaving your CRT connected - try to achieve a 1280x1024 resolution with 60Hz vertical refresh rate. This is a mode your CRT can also handle - although the 60Hz flickering on a CRT will be painful for the eyes. 

Once you've got it, you should definitely be able to hook up your LCD and get a nice, stable picture on it.


kind regards

Marc

---

### Post by shawnerz on 2006-10-10
Marc,
Sorry for the delay in posting.  I had some other things to attend to.

I misunderstood your previous posts.  I thought you wanted to know what the LCD monitor said about the display.

I copied your xorg.conf and booted with those settings.
And I think I found what you've been trying to tell me: the monitor won't support a scan rate above 60 Hz!  DOH!

I am keeping your xorg.conf file because it gives me better resolution than the 640 X 480, and 800 x 600 I got with the default file.

Thanks for your help and sorry for the delays.
-Shawn

---

### Post by stripeycat on 2006-12-17
Hi there, i'm afraid this may be a bit off the central topic, but you're the only folks who seem to have encountered a similar problem to mine with the darn dell P1130 CRT monitor... i'll keep this as brief as possible!

i'm trying to set up a new dell optiplex GX620 box with one of the companies old P1130 monitors for one of our contractors; everything seemed almost ok, but the monitor, when you view the onscreen built-in display options, keeps registering a 60Hz refresh rate. Surely this isn't right? Windows is pushing all the way up to 160Hz, but the actual display tells a different story; it's almost certainly working at the 60Hz that the monitor itself is claiming to be running.

I've forced a reinstall of the P1130 driver, and tried every combination of res and refresh rate i can think of, it's still murder on the eyes though.

Could anyone suggest anything to get around this? Or is it time for a new monitor...?

Any help or advice appreciated... :(

---

### Post by stripeycat on 2006-12-17
Sorry, i finally answered my own question. Unfortunately ATI install a host of nasty little controls with their 'Catalyst Control Center' suite, one of which was hidden away in the Monitor controls panel inside the Advanced Display settings. This little swine was defaulted to 60Hz (Lord knows why; do ATI think someone would buy 256 megabytes worth of video card to use with a monitor that only made the entry level grade?!) so naturally the monitor was only interested in displaying 60Hz. ](*,)

---

