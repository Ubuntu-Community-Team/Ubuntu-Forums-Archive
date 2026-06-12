---
title: "VBox Information message on boot-up"
date: 2009-04-10
forum: Virtualisation
---

### Post by MoebusNet on 2009-04-10
The virtual machine window is optimized to work in 32 bit color mode but the color quality of the virtual display is currently set to 16 bit.
Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color quality to see if this message disappears or you can simply disable the message now if you are sure the required color quality (32 bit) is not available in the given guest OS.

I'm running VBox 2.20 on 8.04LTS. I get the same message whether I start a Hardy VM or a Jaunty VM.

What should I do about this?

---

### Post by Perryg on 2009-04-10
> **MoebusNet said:**
> The virtual machine window is optimized to work in 32 bit color mode but the color quality of the virtual display is currently set to 16 bit.
Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color quality to see if this message disappears or you can simply disable the message now if you are sure the required color quality (32 bit) is not available in the given guest OS.

I'm running VBox 2.20 on 8.04LTS. I get the same message whether I start a Hardy VM or a Jaunty VM.

What should I do about this?

Did you install the Guest Additions for VBox?

---

### Post by MoebusNet on 2009-04-10
Yes, the Guest Additions are installed.

---

### Post by Therion on 2009-04-10
Have you tried doing what the error message suggests? 

Opening the display properties dialog of the guest OS and selecting a 32 bit color mode, if it is available (etc.)?

---

### Post by MoebusNet on 2009-04-10
I have attempted to find mention of display properties in both Hardy and Jaunty, but neither mention color depth under System>Preferences>Screen Resolution or under System>Preferences>Appearance.

---

### Post by Perryg on 2009-04-10
> **MoebusNet said:**
> Yes, the Guest Additions are installed.

Actually you do not want to change the display property from within the guest if you want to be able to change the screen resolution using the resize option in VBox.   How much video memory did you allow to VBox for the guest?

---

### Post by MoebusNet on 2009-04-10
Default of 8MB.

---

### Post by Perryg on 2009-04-10
> **MoebusNet said:**
> Default of 8MB.

Try it with 16.  
Also you can look at the /var/logs/vboxadd.log and vboxinstall.log file to see if it mentions anything.

---

### Post by MoebusNet on 2009-04-10
Thanks, I'll try that.

---

### Post by MoebusNet on 2009-04-10
Message is still there...

---

### Post by Perryg on 2009-04-10
> **MoebusNet said:**
> Message is still there...

OK there a a couple of things that you can do here.  Usually you see this message when the host has only 256 colors (thus the 8 bit) If this is adaquit for you then you can just dismiss the warning and continue on your way.

If however you have more than 256 colors on the host and it is just reporting this you can make sure that the xorg.conf file has vboxvideo as the device driver in the device section.  I am including an older xorg.conf file so you can see what I am talking about.  Look at the section labeled "Device"  all you should need to add is that line (Driver   "vboxvideo")

```
# Xorg configuration created by system-config-display

Section "ServerLayout"
        Identifier     "single head configuration"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        ModelName    "Samsung SyncMaster 243T/CX240T (Digital)"
 ### Comment all HorizSync and VertSync values to use DDC:
        HorizSync    30.0 - 80.0
        VertRefresh  55.0 - 75.0
        Option      "dpms"
EndSection

Section "Device"
        Identifier  "Videocard0"
    Driver      "vboxvideo"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1750x1090" "1600x1200" "1600x1024" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Section "InputDevice"
        Identifier  "VBoxMouse"
        Driver      "vboxmouse"
        Option      "CorePointer"
EndSection

```

---

### Post by MoebusNet on 2009-04-10
Thanks, I'll look into that. By the way, I tried using up to 32MB of video memory (the limit of my card) and up to 1GB of main memory for the VM in Hardy guest and still got the message. Googling the message shows it appearing as far back as a couple of years with no definitive resolution that I have found other than yours.

---

### Post by Perryg on 2009-04-10
> **MoebusNet said:**
> Thanks, I'll look into that. By the way, I tried using up to 32MB of video memory (the limit of my card) and up to 1GB of main memory for the VM in Hardy guest and still got the message. Googling the message shows it appearing as far back as a couple of years with no definitive resolution that I have found other than yours.

A lot of people have struggled with this over the last few years.  I have this all working in about 12 different Linux distros (the xorg that I sent you was from my Debian4 that is the reason for all of the screen resolutions)and 5 different Windows versions.  I remember seeing this about a year os so ago and hopefully remember all that it will take to make this work for you.  As I said it may just be as easy as saying to not show this again but why not try to fix it right if you can.

---

### Post by MoebusNet on 2009-04-10
Perrg, thanks for your help but I guess this is going to be a little more involved than that; it may involve a whole new /etc/X11/xorg.conf file. Here's what I've got after inserting Driver "vboxvideo"

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
    Driver      "vboxmouse"
    Option      "CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"vboxvideo"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

I still get the message...

---

### Post by Perryg on 2009-04-10
Do one more thing for me if you would.
Send me the information from (in terminal)the guest

X -version
uname -r

---

### Post by MoebusNet on 2009-04-10
Terminal is acting up; it doesn't seem to want to copy & paste. Please bear with me...

me@my-laptop:~$ X -version

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux glenn-laptop 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:38:53 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
me@my-laptop:~$ uname -r
2.6.28-11-generic

I got a crash error message for Xorg during all this; sorry for the delay. This is from Jaunty with all updates.

---

### Post by Perryg on 2009-04-10
Hummmmm.
Crash error from Xorg.  Not a good thing.  Your information suggests that it should work, but the crash error concerns me.  If you see that everything is working then I would ignore this error for now.  If I can pull a rabbit out of my hat I will reply back later.

---

### Post by MoebusNet on 2009-04-10
Thank you for your time, Perryg. I just submitted a crash report to launchpad about Xorg; it was the 4th time it happened, so it wasn't just a fluke. I don't think (hope) it affects anything but I haven't updated to the latest Hardy kernel on the host yet. I've become a bit conservative on kernel changes anymore, I guess.

---

### Post by MoebusNet on 2009-04-18
UPDATE - I applied all of the most recent updates (including the kernel) to my Hardy host and applied all of the most recent updates to my Jaunty VM. Still get the error message. Xorg crashed after the VM reboot the first time, but not the next. Launchpad attributed this to a previously known bug; maybe it'll get fixed later...

---

### Post by maxideci on 2009-11-08
> **MoebusNet said:**
>  Still get the error message. Xorg crashed after the VM reboot the first time, but not the next....

Why is it marked as Solved ????

I'm having same kind of problem.


[I]The virtual machine window is optimized to work in 32 bit color mode but the color quality of the virtual display is currently set to 16 bit.
Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color quality to see if this message disappears or you can simply disable the message now if you are sure the required color quality (32 bit) is not available in the given guest OS.[/I]

cheers!!

---

### Post by MoebusNet on 2009-11-17
Sorry I didn't give the details, but the updates to VirtualBox (it's up to version 3.0.10 now) and to Hardy eliminated the problem for me. If you're still running an earlier version of VBox you may want to consider a newer version.

---

### Post by Endolith on 2010-04-09
> **MoebusNet said:**
> Sorry I didn't give the details, but the updates to VirtualBox (it's up to version 3.0.10 now) and to Hardy eliminated the problem for me. If you're still running an earlier version of VBox you may want to consider a newer version.

That's pretty weird, because now I'm seeing this message in VirtualBox 3.1.6 and Karmic as the guest.  It doesn't seem solved to me.

---

### Post by vikas.sood on 2010-07-23
Weird indeed. I have this same problem and need a fix. 

I had been using Hardy ever since and just updated to Lucid lynx. but i still do my development work on 8.04. So i installed VBOX 3.2.6 to have 8.04 as guest. But it just doesnt go to full screen mode and splashes me the same error.

Has anyone solved it????

adding display section in xorg.conf doesnt solve it either? what to do??

please respond..or else i will have to roll back to hardy [-o<

---

### Post by whitefort on 2010-08-19
I'm also curious about why this thread was marked as solved.  I'm using Lucid Lynx, and getting the same problem.

---

### Post by majickmann on 2011-01-31
It's marked as solved because it was solved for the OP.  If the solution does not work for you, then start a new thread.

Hope this helps...
--majickmann

---

### Post by hippiehacker on 2012-01-02
It looks like much of the problem is related to people not wanting to see the message. It interferes with automation and makes people think there is an underlying problem to be solved.

I suggest just running a command to automatically never show such messages because it doesn't seem to affect performance for me at all.

From this post ->[https://forums.virtualbox.org/viewtopic.php?f=2&t=24273](https://forums.virtualbox.org/viewtopic.php?f=2&t=24273) it looks like you can make the warnings go away by settings some extra data params on the command line.

```
VBoxManage setextradata global GUI/SuppressMessages remindAboutAutoCapture,\
confirmInputCapture,remindAboutMouseIntegrationOn,remindAboutWrongColorDepth,\
confirmGoingFullscreen,remindAboutMouseIntegrationOff
```

---

