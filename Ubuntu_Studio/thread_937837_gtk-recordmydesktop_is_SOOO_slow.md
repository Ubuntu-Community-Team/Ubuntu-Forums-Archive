---
title: "gtk-recordmydesktop is SOOO slow"
date: 2008-10-04
forum: Ubuntu Studio
---

### Post by binbash on 2008-10-04
I am using hard and when i try to record a desktop movie.The problem is, it is SOOO slow (like 2 fps :D) i cant even record or move the mouse.Even i did not record (only gtk-recordmydesktop open), when i try to write this, there is a LOT of lag ^^ xorg jumps to %40 cpu usage(normal %2) without recording just gtk-recordmydesktop open.

I have a lot of compiz effects open btw.

I did not enabled recording audio
My video quality is %70
at performance options zero compression,quick subsampling, full shots at every frame ticked.
FPS 15

ANy solutions : 

here is my xorg.conf : 

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Synaptics Touchpad"
	Option	    "AIGLX" "on" #->Enables Xorg's AIGLX rendering technic
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "tr"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
        Option      "SHMConfig" "true"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideo" "off"
	Option	    "Textured2D" "on"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "BackingStore" "on" 
	Option	    "UseFastTLS" "1"
	Option	    "TexturedVideoSync" "True"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "RENDER" "Enable"
EndSection

```

---

### Post by binbash on 2008-10-04
I changed Option "TexturedVideo" "off" to Option "TexturedVideo" "on" and it reduces lag a lot, but still all advices are welcome

---

### Post by Meelis on 2009-02-17
Hi

[SIZE="6"][COLOR="YellowGreen"]recordMyDesktop sucks[/COLOR][/SIZE]

Disable **--full-shots** [SIZE="5"]NB![/SIZE] no 3D then.
My P43, C2D e7400 2,8GHz, HD-4670 1GB, 2GB DDR2 1066 wont handle 1fps @1440x896 pix [SIZE="5"]IF[/SIZE] **--full-shots** enabled.

Screencasting isn't for Linux. Take a look of my video about how fast recordMyDesktop is.
[-Video Link-]("http://www.youtube.com/watch?v=t3O2HoMYSjA")

---

### Post by lukeiamyourfather on 2009-02-20
I've had good luck with running x11vnc on the host and then recording the VNC session on another system. Using the -noxdamage flag for x11vnc will update the screen to include OpenGL elements on the server side. 

On the client side connect with the high speed default for the TightVNC viewer and it works great. There are multiple programs to capture the VNC sessions or screen recorders in Windows like Camtasia also work good to record the VNC session. Cheers!

---

### Post by kenglxn on 2009-06-23
use istanbul instead.  I had this problem on a Dell XPS Studio 16. 
just remove gtk-record my desktop and install istanbul.  :)

--
ehem... nevermind, it is just as slow, but only when recording...

---

### Post by hellocatfood on 2010-01-18
Has anyone found any similar software that actually works?

---

### Post by AutoStatic on 2010-01-18
Everyone should start filing bugreports for recordMyDesktop:
- Probably the encoding rate of recordmydesktop is not well configured: [https://bugzilla.redhat.com/show_bug.cgi?id=525155](https://bugzilla.redhat.com/show_bug.cgi?id=525155)
- No JACK support

But there are little bugreports and the reports that exist are unassigned because apparently nobody is affected and/or leaves feedback.

---

### Post by mrayyy on 2010-03-18
I have the same issue on a lenovo thinkpad t500 with the AMD drivers - if you compeltely uninstall them you loose compiz effects - but rmd starts to work as expected.

this is really bad imho - it breaks the application for me. but RMD is actually really great.

---

### Post by AutoStatic on 2010-03-18
I've uploaded a patched version of recordMyDesktop to my PPA, works well for me.

[http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/)

---

### Post by Claus7 on 2010-03-21
Hello,

the patched version seems to be somewhat quicker, yet with gtk you can select part of your desktop to be recorded. No matter what the process seems slow enough both with gtk and the simple version. Also the procedure of running a program you want to record to another computer does not seem to affect the slowing downs.

Nice try,
Regards!

---

### Post by hellocatfood on 2010-04-04
I've been doing a bit of researching around this bug. As mentioned above it could be due to the graphics driver being used. If you're using an ATI graphics driver and are being affected mark this bug as also affecting you

[https://bugs.launchpad.net/recordmydesktop/+bug/509111](https://bugs.launchpad.net/recordmydesktop/+bug/509111)

I've also added a bug report for the [fglrx driver](http://ati.cchtml.com/show_bug.cgi?id=1451) and one for the [parent project](https://sourceforge.net/tracker/?func=detail&aid=2981887&group_id=172357&atid=861428), recordmydesktop

Hopefully with enough people saying that they have the same problem will get it fixed

---

### Post by flatlinecoder on 2010-07-08
If anyone has an ATI Graphics card check out this tutorial on how to fix the slow down using gtk recordMyDesktop  [http://flax.ie/ubuntu-10-04-gtk-recordmydesktop-screen-casting/](http://flax.ie/ubuntu-10-04-gtk-recordmydesktop-screen-casting/)

---

