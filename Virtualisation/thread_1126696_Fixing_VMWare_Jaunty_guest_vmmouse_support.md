---
title: "Fixing VMWare Jaunty guest vmmouse support"
date: 2009-04-15
forum: Virtualisation
---

### Post by jdong on 2009-04-15
This is just me talking to a wall, but in hopes it'd help googlers find an answer:


PROBLEM: In Jaunty, VMWare doesn't correctly grab the mouse seamlessly because the vmmouse module is not being used. Rather, HAL input hotplugging is choosing USB HID mouse support which exclusively locks the mouse into the window and is laggy.


WORKAROUND: After installing Tools, make your /etc/X11/xorg.conf look like this (emphasis to bolded parts)

```


 # VMware SVGA

Section "Module"
    Load        "dbe"  	# Double buffer extension
    SubSection  "extmod"
    EndSubSection
    Load        "type1"
    Load        "freetype"
#    Load       "glx"
EndSection

Section "Files"
    RgbPath	"/usr/X11R6/lib/X11/rgb"
#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
#    ModulePath "/usr/X11R6/lib/modules"
EndSection

Section "ServerFlags"
#    Option NoTrapSignals
EndSection

Section "InputDevice"
    Identifier	"VMware Keyboard"
    Driver	"keyboard"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"
    Option "XkbCompat"	""
EndSection

Section "InputDevice"
    Identifier	"VMware Mouse"
[b]    Driver	"vmmouse"
	Option "CorePointer"
Option "AlwaysCore"
[/b]    Option "Protocol"    "ps/2"
    Option "Device"      "/dev/input/mice"
    Option "ZAxisMapping"	"4 5"
#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"
#    Option "ChordMiddle"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "Device"
    Identifier  "VMware SVGA"
    Driver      "vmware"
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "VMware SVGA"
    Monitor     "vmware"
    # Don't specify DefaultColorDepth unless you know what you're
    # doing. It will override the driver's preferences which can
    # cause the X server not to run if the host doesn't support the
    # depth.
    Subsection "Display"
        # VGA mode: better left untouched
        Depth       4
        Modes       "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       8
        Modes       "1024x768"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       15
        Modes       "1024x768"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1024x768"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1024x768"
        ViewPort    0 0
    EndSubsection
EndSection

Section "ServerLayout"
**	Option "AllowEmptyInput" "off"**
    Identifier  "Simple Layout"
    Screen "Screen 1"
	InputDevice	"VMware Keyboard"	"CoreKeyboard"
	InputDevice "VMware Mouse"	"CorePointer"
EndSection

[b]
Section "ServerFlags"
	Option "AutoAddDevices" "False"
EndSection
[/b]

Section "Monitor"
    Identifier      "vmware"
    VendorName      "VMware, Inc"
    HorizSync       1-10000
    VertRefresh     1-10000
EndSection


```

---

### Post by jdong on 2009-04-15
UPDATE: **Installing xserver-xorg-input-vmmouse** and **mdetect** makes it work. The problem is a missing dependency on mdetect which causes vmmouse to not be probed. I am attempting to file a bug report to get this done.

---

### Post by jdong on 2009-04-15
Final update: This is a moot point. I uploaded the fix for this into Jaunty.

---

### Post by Dedoimedo on 2009-04-16
Hello,

I've installed Jaunty and VMware Tools some 4-5 days ago without any problems. The mouse worked fine seamlessly ... I guess this was before your fix.

Interesting ...

I did encounter the nautilus respawn bug and updated to latest before installing vmware tools, though, then again, this was before your post ...

Cheers,
Dedoimedo

---

### Post by jdong on 2009-04-16
> **Dedoimedo said:**
> Hello,

I've installed Jaunty and VMware Tools some 4-5 days ago without any problems. The mouse worked fine seamlessly ... I guess this was before your fix.


Interesting; perhaps either something else (i.e. the presence of laptop components such as a passed-through battery) triggered mdetect's installation, or your VMWare Tools version did correctly set those flags in xorg.conf.

The fix I uploaded has been accepted into Jaunty, so like before, the only thing you HAVE to do for full VMWare acceleration after install is install **xserver-xorg-input-vmmouse**. For those who don't need unity functionality, this is pretty convenient.

---

### Post by sabi on 2009-04-16
I just tried installing VMware Tools 7.8.5 build-156735 in the latest daily build of a newly installed Jaunty guest (14-Apr) and the mouse is "locked" inside the guest window.

This is using VMWare Workstation 6.5.2 build-156735.

I did install xserver-xorg-input-vmmouse.

I also tried the open source vmware tools, same result.



Any ideas?

Thanks,
sabi

---

### Post by jdong on 2009-04-16
> **sabi said:**
> I just tried installing VMware Tools 7.8.5 build-156735 in the latest daily build of a newly installed Jaunty guest (14-Apr) and the mouse is "locked" inside the guest window.

This is using VMWare Workstation 6.5.2 build-156735.

I also tried the open source vmware tools, same result.

Any ideas?

Thanks,
sabi

Please try installing xserver-xorg-input-vmmouse version 1:12.5.1-4ubuntu5. It may not be on the Daily CD's yet; and VMWare's own tools in fact do not install the mouse driver correctly.

What VMWare does wrong I detailed in post #1; the proper way of autodetecting the VMWare devices is done in the Ubuntu repos by the package I just mentioned.

---

### Post by sabi on 2009-04-16
<Please try installing xserver-xorg-input-vmmouse version 1:12.5.1-4ubuntu5. It may not be on the Daily CD's yet; and VMWare's own tools in fact do not install the mouse driver correctly.>

I did that, same result

---

### Post by jdong on 2009-04-16
> **sabi said:**
> Please try installing xserver-xorg-input-vmmouse version 1:12.5.1-4ubuntu5. It may not be on the Daily CD's yet; and VMWare's own tools in fact do not install the mouse driver correctly.

I did that, same result

Can you run

```

vmmouse_detect && echo yes || echo no

```

and see if it prints yes or no?

---

### Post by sabi on 2009-04-16
> **jdong said:**
> Can you run

```

vmmouse_detect && echo yes || echo no

```

and see if it prints yes or no?

Sorry, the forum went down.

The response was no.

I will try reinstalling xserver-xorg-input-vmmouse version 1:12.5.1-4ubuntu5

Thanks,

---

### Post by sabi on 2009-04-16
> **jdong said:**
> Can you run

```

vmmouse_detect && echo yes || echo no

```

and see if it prints yes or no?

The response was "no".

I tried uninstalling/reinstalling xserver-xorg-input-vmmouse version 1:12.5.1-4ubuntu5

Again, tried the command provided, same result "no".

Other ideas?

Thanks,
sabi

---

### Post by jdong on 2009-04-16
Whoa that is crazy. The detector doesn't believe you are inside vmware. Can you attach a lshal output?

---

### Post by sabi on 2009-04-16
I should mention that when I installed vmware tools I received some errors, such as:

make[2]: *** [/tmp/vmware-config0/vmhgfs-only/page.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmhgfs-only'
Unable to build the vmhgfs module.

No drivers for X.org version: 7.5.0.

but then at the end of the install I got:

The configuration of VMware Tools 7.8.5 build-156735 for Linux for this running
kernel completed successfully.

Does any of this have any bearing on the issue?

Thanks,
sabi

---

### Post by sabi on 2009-04-16
> **jdong said:**
> Whoa that is crazy. The detector doesn't believe you are inside vmware. Can you attach a lshal output?

Jadong,

When I try to embed the output I get a database error message.

Earlier, each time I submitted a reply I also received a database error message. I believe the web server is experiencing problems.

Will try again in a few minutes.

Thanks,
sabi

---

### Post by sabi on 2009-04-16
Jdong,

I just uninstalled vmware tools. Then, using Synaptic, I installed the open source vmware tools. The result, the mouse problem is fixed ! Also, the copy/paste from the guest to host works. However, when I attempt to drag a file from the guest workspace to a host workspace I get an error.

This is all very confusing to me. Are the open source vmware tools equivalent in function to the commercial vmware tools? And why does the open source vmware tools work correctly "out-of-the-box" ?

Thanks for your support,
sabi

---

### Post by jdong on 2009-04-16
> **sabi said:**
> Jdong,

I just uninstalled vmware tools. Then, using Synaptic, I installed the open source vmware tools. The result, the mouse problem is fixed ! Also, the copy/paste from the guest to host works. However, when I attempt to drag a file from the guest workspace to a host workspace I get an error.

I bet it's because our version of the VMWare tools do not support the new DnD abilities. Try installing official VMWare tools, then removing /etc/X11/xorg.conf. VMWare's modifications to the X config may be messing up autodetection for some reason.

> 

This is all very confusing to me. Are the open source vmware tools equivalent in function to the commercial vmware tools? And why does the open source vmware tools work correctly "out-of-the-box" ?



the FOSS tools may lag slightly out of date compared to the official ones, for various reasons.

---

### Post by Dedoimedo on 2009-04-16
Sabi, did you install build-essential package before compiling?
You need gcc, make, headers, etc before you can compile.
Dedoimedo

---

### Post by jdong on 2009-04-16
vmhgfs is not compatible with the 2.6.28 kernel's API; this is known. Its failure isn't fatal though -- the rest of Tools works fine without it.

---

### Post by sabi on 2009-04-17
Jdong,

Well, too many bizarre things happening. I started over. Just to close this saga, these are the steps I followed from your suggestions.

1. Created new vmware guest using RC1
2. Ran update manager
3. Installed build-essential
4. Installed VMWare tools 7.8.5 build-156735 (from VMWare workstation 6.5.2)
5. Installed xserver-xorg-input-vmmouse version 1:12.5.1-4ubuntu5 and mdetect
6. Ran /usr/bin/vmware-user
7. Added /usr/bin/vmware-user to startup applications
8. Restart

This resulted in normal (vmware fashion) mouse operation. Copy/Paste to/from guest/host works as expected. The file drag and drop is still problematic with the following error:

Unable to open: File "/proc/fs/vmblock/mountPoint/0ba02566/Payment_schedule.ods" line 1: Syntax error.

Since my primary concern was mouse and copy/paste operations, I am satisfied at this point.

Maybe the other issues will resolve in the future.

Thanks for your efforts.
sabi

PS: Spoke too soon, bizarre is back. When I right-click in a terminal window, a new terminal window opens. May or may not be related to this, but still bizarre.

---

### Post by jdong on 2009-04-17
> **sabi said:**
> 
PS: Spoke too soon, bizarre is back. When I right-click in a terminal window, a new terminal window opens. May or may not be related to this, but still bizarre.

That is due to some WEIRD mouse click bug where right click context menus, mainly in Unity mode, cause the first item to be magically selected (which is New Terminal in this case)

---

### Post by BryanPearson on 2009-04-24
> **sabi said:**
> Jdong,

Well, too many bizarre things happening. I started over. Just to close this saga, these are the steps I followed from your suggestions.

1. Created new vmware guest using RC1
2. Ran update manager
3. Installed build-essential
4. Installed VMWare tools 7.8.5 build-156735 (from VMWare workstation 6.5.2)
5. Installed xserver-xorg-input-vmmouse version 1:12.5.1-4ubuntu5 and mdetect
6. Ran /usr/bin/vmware-user
7. Added /usr/bin/vmware-user to startup applications
8. Restart


The above worked for me as well on the 9.04 official version.  Thank you for this post!  I have cut and paste, drag and drop, and proper mouse transition from host/guest on VMware WS 6.5.2 running on WinXP x64 SP2.

---

### Post by wasabinz on 2009-04-24
> **sabi said:**
> Jdong,

Well, too many bizarre things happening. I started over. Just to close this saga, these are the steps I followed from your suggestions.

1. Created new vmware guest using RC1
2. Ran update manager
3. Installed build-essential
4. Installed VMWare tools 7.8.5 build-156735 (from VMWare workstation 6.5.2)
5. Installed xserver-xorg-input-vmmouse version 1:12.5.1-4ubuntu5 and mdetect
6. Ran /usr/bin/vmware-user
7. Added /usr/bin/vmware-user to startup applications
8. Restart

This resulted in normal (vmware fashion) mouse operation. Copy/Paste to/from guest/host works as expected. The file drag and drop is still problematic with the following error:

Unable to open: File "/proc/fs/vmblock/mountPoint/0ba02566/Payment_schedule.ods" line 1: Syntax error.

Since my primary concern was mouse and copy/paste operations, I am satisfied at this point.

Maybe the other issues will resolve in the future.

Thanks for your efforts.
sabi

PS: Spoke too soon, bizarre is back. When I right-click in a terminal window, a new terminal window opens. May or may not be related to this, but still bizarre.

Thanks mate, I followed your steps and it works like a charm. Drag&Drop, mouse movement and copy&paste all works. Running Ubuntu 9.04 x86 guest on Windows Vista SP1 x86 host with VMware Workstation 6.5.2

---

### Post by jdong on 2009-04-24
I've traced down the right-click-terminal-opens bug:

When VMWare handles a click, xev shows:

(1) MouseDown event. That's expected.

(2) MotionNotify event. That's unexpected. It tells the guest that the mouse has moved for either 0 pixels or 1 or 2 pixels.

(3) MouseUp event. That's expected.


So, from what I see every time you press down the mouse the GUI toolkit interprets it as a "drag", not just a click. So, if you click in a terminal with the left mouse button it might select one character (particularly if you click a blank area), and with the right mouse button it'll select the first menu entry.


There's a bit of quibbling it seems between the VMWare people and the GTK/QT people, one blaming another. The VMWare camp says they are just passing mouse events as they happen and the GUI toolkits should exclude minor movements of the mouse as noise. The GUI toolkit folks say that MotionNotify is for notifying *LOGICAL* motion of the mouse and the mouse driver shouldn't be reporting negligible changes in mouse position to the client.

You be the judge.

---

### Post by jdong on 2009-04-24
Ok, for those nerds with too much time on their hands. In **src/vmmouse.c** line 495:


```

if (dx || dy)

```

change to

```

if ((dx || dy) && (truebuttons == pMse->lastButtons))

```

This disallows posting both a button change and a movement update. Fixes the unintentional mouse drag issue for me.

---

### Post by mattalexx on 2009-04-28
> **sabi said:**
> 
1. Created new vmware guest using RC1


This could potentially be a stupid question but when you say "RC1" are you referring to a VMWare Workstation release? VMWare Server 2.0 RC1? Or an Jaunty release of some kind?

The fact that you said "using" instead of "of" leads me to believe that you are talking about the VMWare and not the OS but I want to be completely sure.

Thanks.

---

### Post by littlebluepixle on 2009-05-12
I've had the same issue on my VMware guest when I upgraded from 8.04 to 9.04. I have since created a new guest and installed from fresh and I don't have the issue. seems to be a bit of a pain not to be able to upgrade and have a mouse. :(

---

### Post by jdong on 2009-05-12
The click bug is acknowledged by VMWare upstream now and they informed me that they are working on a proper fix for it.

---

### Post by Malik on 2009-07-14
man how do i fix the mouse? this sounds like alien talk in the Thread starters post.

---

