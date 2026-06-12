---
title: "Help me?"
date: 2007-01-31
forum: Sun Sparc Users
---

### Post by Su37amelia on 2007-01-31
I've downloaded Ubuntu for SPARC machines...I have an 888P Sun Mobile Workstation. It boots, I hit "enter" to start the installation, then the screen blacks out. There is continued CD/HD activity, but the display goes completely black (can't even read front-lit or with an external monitor) - am  I doing something wrong?:confused:

---

### Post by Moulton on 2007-02-01
What kind of display adaptor does your system have?

I found that the display drivers for the Sparc platforms only worked for some video adaptors and not others.

You might need to select a text-mode installer if the graphical installer isn't cooperating with your video hardware.

---

### Post by Su37amelia on 2007-02-03
It has the XVR-100 graphics chip.

---

### Post by Moulton on 2007-02-04
I'm not sure of the mapping between video-chip IDs and the conventional names of Sun graphic adaptors.  The Ubuntu repositories include X.Org drivers for these well-known models of Sun graphic adaptors:

SunFFB (Creator and Elite UPA-bus adaptor)
SunLeo
SunTCX

If your Sun graphic adaptor is different from the above models, then there might not be an X.Org driver available for it (at least not in the Ubuntu repositories).

You can visit the X.Org site to find out more about what drivers are available (or under development) for unusual or exotic graphic adaptors.

On Edit:  According to the [discussion in this thread]("http://ubuntuforums.org/showthread.php?t=264760"), there were no X.Org drivers for any of the XVR chips as of 6 months ago.

---

