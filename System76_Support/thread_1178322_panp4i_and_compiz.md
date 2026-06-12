---
title: "panp4i and compiz"
date: 2009-06-04
forum: System76 Support
---

### Post by thebinaryblob on 2009-06-04
I am currently running Jaunty on my PanP4 intel and cannot get Compiz to work
I try running compiz in a terminal and it gives:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/home/aaron/.themes/After Hours/gtk-2.0/panels/panel.rc:39: error: invalid string constant "theme-dark-button", expected valid string constant
/home/aaron/.themes/After Hours/gtk-2.0/apps/gmpc.rc:85: error: invalid string constant "theme-dark", expected valid string constant
```what do I do to get compiz working?

---

### Post by thomasaaron on 2009-06-04
Compiz has blacklisted your video card. The workaround is in the first post of this thread...

[https://answers.launchpad.net/ubuntu/+question/67975](https://answers.launchpad.net/ubuntu/+question/67975)

---

### Post by thebinaryblob on 2009-06-04
disabling metacity's compositing worked!

---

