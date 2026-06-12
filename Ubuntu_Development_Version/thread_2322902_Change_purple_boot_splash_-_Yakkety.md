---
title: "Change purple boot splash - Yakkety"
date: 2016-04-30
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-04-30
I'm bringing this up again!

I will post my complete recipe for a Black Ubuntu, however I'm bringing it back up because every time there's an update (and I expect Yak to have alot) to "these packages" i have to do it all over. I'm looking for an override or a way to keep the system from changing this.
The main reason why I do this is the Nvidia "boot resolution" issue. It just does not look nice with Purple and black frames...

**Grub**:
/usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.grub
Change the value to : 

if background_color 0,0,0 ; then
clear
fi

Optional: Add background to Grub "/etc/default/grub"
update-grub



**Splash:**
/usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.script
Change:
Window.SetBackgroundTopColor (0.0, 0.00, 0.0);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.0, 0.00, 0.0);  # an equally nice colour on the bottom
sudo update-initramfs -u


**Login manager:**
/usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
Change color to black #000000
Change background picture to color #000000
Recompile:
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/

---

### Post by cariboo on 2016-05-01
Moved to a new thread of it's own.

---

