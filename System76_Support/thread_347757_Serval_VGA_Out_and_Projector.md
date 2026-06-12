---
title: "Serval VGA Out and Projector"
date: 2007-01-27
forum: System76 Support
---

### Post by sgtron on 2007-01-27
Sorry if I'm just being stupid here, but I can't get my Serval to play DVD's through the VGA out with my projector.

I read this post regarding the Pangolin  
[http://ubuntuforums.org/showthread.php?t=244590&highlight=vga](http://ubuntuforums.org/showthread.php?t=244590&highlight=vga)

Editing xorg.conf with this code got me the ability to reboot with a projector attached and get a display.  

```
Option		"MonitorLayout" "NONE,CRT+LFP"
Option		"Clone" "true"
```

But no DVD playing allowed.  The rest of the post dealt with the Intel graphics chip so was no use to me.

Anyone dealt with DVD playing over a VGA connected projector on a Serval Performance?  

It seems to me I should just be able to press "Fn+F3" and toggle between displays: screen, external monitor, s-video, what-have-you... not sure why we can't do that.

---

### Post by crichell on 2007-01-29
nVidia uses Twinview for piping images out of two devices (LCD & VGA).  YANC does an OK job of managing two monitors but it can sometimes hose things up.

This how to may help in setting it up:

[http://www.ubuntuforums.org/showthread.php?p=1773584](http://www.ubuntuforums.org/showthread.php?p=1773584)

---

