---
title: "Icons in KDE apps missing in Gnome DE!"
date: 2007-05-30
forum: Ubuntu Christian Edition
---

### Post by Isoss on 2007-05-30
Hello all

I am using Ubuntu 7.04 CE which is really great except for a problem I've been facing with KDE apps.

I posted the problem [HERE]("http://ubuntuforums.org/showthread.php?t=456983")  in the "Desktop Environments" Section but I didn't get any help! but then I suspected this might be caused because of CE configurations or something.

I'll explain the problem here again and please reply here not there:

I am using Ubuntu CE, which has some apps that are designed for kde desktop environments like bibletime, Amarok or Kaffeine. They are working fine except that icons are missing! it's only text, no folders icons when browsing, nothing!

What's missing in my installation? does it have anything to do with QT or configuration or something?

Thanks

---

### Post by tak1150 on 2007-05-30
> **Isoss said:**
> Hello all

I am using Ubuntu CE, which has some apps that are designed for kde desktop environments like bibletime, Amarok or Kaffeine. They are working fine except that icons are missing! it's only text, no folders icons when browsing, nothing!



I have the same problem (i think) and posted the problem [here]("http://ubuntuforums.org/showthread.php?t=457502") with a screenshot.

I'd appreciate any help as well. :)

---

### Post by zozobra on 2008-02-10
I'm having the same issue. Anyone have any luck with this?

---

### Post by milesje on 2008-02-11
I am also using 7.04 CE, butI am NOT having any problems with amarok not having the Icons. I will check the other KDE apps (bibletime, Kaffeine, ...)

---

### Post by ice60 on 2008-10-27
my icons were missing in KDE apps too and i fixed it by editting a file called **kdeglobals**, here -
~/.kde/share/config/kdeglobals

i just deleted all the stuff under **[MainToolbarIcons]**
i.e. i deleted all this below, then saved the file and now it works OK.

[MainToolbarIcons]
ActiveColor=255,255,0
ActiveColor2=51,51,153
ActiveEffect=none
ActiveSemiTransparent=false
ActiveValue=1
Animated=false
DefaultColor=255,255,0
DefaultColor2=0,0,255
DefaultEffect=none
DefaultSemiTransparent=false
DefaultValue=1
DisabledColor=128,128,128
DisabledColor2=51,51,204
DisabledEffect=togray
DisabledSemiTransparent=false
DisabledValue=1
DoublePixels=false
Size=22

---

