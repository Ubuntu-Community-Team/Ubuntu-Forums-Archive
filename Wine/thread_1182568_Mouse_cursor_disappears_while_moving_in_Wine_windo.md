---
title: "Mouse cursor disappears while moving in Wine window"
date: 2009-06-09
forum: Wine
---

### Post by hathiphnath on 2009-06-09
Hi all!

Using Jaunty and Wine 1.1.23. Until today, everything worked fine for me, but from today mouse coursor disappears when  moving in Wine window. More precisely, it turns "invisible". It still works, but I can't see the cursor. I believe no systemwide changes were made to the system (the user doesn't add apps by herself nor uses terminal).

I found an old thead with similar problem: [http://bugs.winehq.org/show_bug.cgi?id=10026](http://bugs.winehq.org/show_bug.cgi?id=10026)

But when I added the line
    Option       "SWCursor" "true"
into the xorg.conf "Devices" section and rebooted for the effect to show, the cursor became invisible SYSTEMWIDE, only sometimes showing up at random, so, I changed it back.

I'm at loss here. Here's my xorg.conf if that's needed:

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

Any help appreciated. :)

---

### Post by lightstream on 2009-06-09
I know what you mean, I've had this happen on occasion, unfortunately I can't remember what - if anything - I did to correct it...

What happens in winecfg? Is the cursor not even visible there? There are a couple of options you could try changing in winecfg that relate to cursor on the Graphics tab, although it seems a long shot!

---

### Post by hathiphnath on 2009-06-10
The Wine configuration window works just fine. I'm at my wits end really.:(

---

### Post by hathiphnath on 2009-06-11
Anyone?

---

### Post by NightMKoder on 2009-06-11
What are you trying to run? Try it on an empty wine prefix, ie:

```

mkdir /tmp/my_wine
WINEPREFIX=/tmp/my_wine/.wine wine notepad

```

and see if the cursor is there. If it is, then your prefix is weird.

---

### Post by hathiphnath on 2009-06-12
Ugh, I never realised that I had notepad installed. Anyway, Notepad worked fine after I executed those two commands. Will reboot offset those two? I rebooted and notepad worked fine even without me giving those two commands.

I'm trying to run two games. Fish Tycoon and Plant Tycoon. Both worked fine until this issue came up.

---

### Post by hathiphnath on 2009-06-18
Should I turn to wine forums?

---

### Post by hathiphnath on 2009-06-22
Okay, I turned to the [_wine forums_]("http://forum.winehq.org/viewtopic.php?t=5275") and it was suggested there that the issue might originate from an automatic update of a graphic driver... where would I see whether my system has been automatically updated and how do I remove that update to see whether that caused the issue?

---

### Post by hathiphnath on 2009-06-26
I installed nVidia graphics driver v96 (as opposed to the v173 and v180 also available) and the games work now. I only hope that the change didn't affect anything else.

---

