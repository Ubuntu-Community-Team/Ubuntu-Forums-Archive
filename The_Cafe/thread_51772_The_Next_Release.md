---
title: "The Next Release"
date: 2005-07-25
forum: The Cafe
---

### Post by zirus1701 on 2005-07-25
Will the next release of Ubuntu have all the sound problems this release has?  Is that something the development team is working on?

---

### Post by Lowe on 2005-07-25
Yes, you can almost guarantee those will be fixed in the next version.

---

### Post by somuchfortheafter on 2005-07-25
yea i think esd was more trouble than it was worth... i kept having to run killall esd at every startup, finally moved it to be automatically run at login.

---

### Post by Burgundavia on 2005-07-25
Breezy has already fixed these issues. Basically they introduced ALSA dmix. This allows non-esd programs to continue to use the sound card. The esd server is left for those apps that use it. It works quite well.

The reason it was not implemented earlier was due to certain sound cards having sound degradation with dmix enabled.

Corey

---

### Post by ubuntu_demon on 2005-07-25
[QUOTE=Burgundavia]Breezy has already fixed these issues. Basically they introduced ALSA dmix. This allows non-esd programs to continue to use the sound card. The esd server is left for those apps that use it. It works quite well.

The reason it was not implemented earlier was due to certain sound cards having sound degradation with dmix enabled.

Corey[/QUOTE]
 do you have any idea of ET + teamspeak running at the same time works if you have onboard audio ?

see : 
[http://www.ubuntuforums.org/showthread.php?p=254384](http://www.ubuntuforums.org/showthread.php?p=254384)

---

### Post by az on 2005-07-25
[QUOTE=Burgundavia]Breezy has already fixed these issues. Basically they introduced ALSA dmix. This allows non-esd programs to continue to use the sound card. The esd server is left for those apps that use it. It works quite well.

The reason it was not implemented earlier was due to certain sound cards having sound degradation with dmix enabled.

Corey[/QUOTE]

Thank you Corey, I did not know that.  Is this in kernel space or userspace?  Basically, what can I backport to enable dmix in Hoary?

---

