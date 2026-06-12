---
title: "How DO I run Google sketchup 7 on ubuntu 8.10"
date: 2009-03-16
forum: Wine
---

### Post by Firidan on 2009-03-16
How to run GoogleSkechup on ubuntu intrepid x64 with wine?
Wine complains that MSVCR80.dll and MSVCP80.dll are missing. From what I gather those are DrirectX dlls. How to I add them to wine and make GoogleSketchup run?

---

### Post by cogadh on 2009-03-16
Those aren't DX dlls, those are part of Visual Studio and .NET. To get them in Wine, just get [winetricks]("http://wiki.winehq.org/winetricks") and use that to install them.

---

### Post by Firidan on 2009-03-21
It does not complain about missing ddls any more but now it complains that opengl couldnt be initialized. I have the latest nvidia drivers installed.:(
Sorry if the text looks a little odd (I wrote it on my mobile)

---

### Post by Fenris_rising on 2009-03-21
Hi there

Google sketchup is one program I would love to run under linux or wine.
Sadly so far as I am aware it still wont play ball and as far as I know still doesn't :(

When I have previously tried it I managed to get the window frames up with the starter icon set but the work area was rendered in solid black so was unusable.

Of course if anyone has solved this let us know or if you indeed manage to solve this let us know. Good luck!

regards

Fenris

---

### Post by Potters Son on 2009-03-21
I, too, would love to run Sketchup. But when I try to run it, two things seem to happen: 1) OpenGL doesn't run (I have Intel GM965 integrated. OpenArena runs great, Frets on Fire not so much. Is Wine OpenGL broken or something???). 2) It outright crashes and shows me that bug tracker thing.

GOOGLE, IF YOU'RE READING THIS, P L E A S E  PORT SKETCHUP TO LINUX!!!

---

### Post by NightMKoder on 2009-03-22
It doesn't seem like google will port sketchup to linux, especially since their picasa port isn't much of a port at all (it uses winelib).

Firidan:
[http://bugs.winehq.org/show_bug.cgi?id=14045](http://bugs.winehq.org/show_bug.cgi?id=14045)
The "fix" is to:
> 
Put
HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display\HW_OK=1 
in the registry. 

However, this doesn't work for me. (GMA950)

---

### Post by Firidan on 2009-03-22
Still doesn't work. I have Nvidia 9500 GS 512 MB video ram.

---

### Post by Firidan on 2009-03-27
K 3d is a native Linux application and it is capable of replacing google sketchup. Video tutorials aren't as good though.
:P

---

### Post by Firidan on 2009-03-31
Come on guys, any ideas?

---

### Post by BroadArrow on 2009-04-14
> **cogadh said:**
> Those aren't DX dlls, those are part of Visual Studio and .NET. To get them in Wine, just get [winetricks]("http://wiki.winehq.org/winetricks") and use that to install them.

Do you know which option in winetricks will install MSVCR80.dll and MSVCP80.dll?

===

Ignore that. I found the option. The list of options on the winetricks site didn't name the DLLs but the script itself does when run.

In case anyone else needs it, it is vcrun2005.

---

### Post by EoRaptor013 on 2010-06-14
> **BroadArrow said:**
> Do you know which option in winetricks will install MSVCR80.dll and MSVCP80.dll?

===

Ignore that. I found the option. The list of options on the winetricks site didn't name the DLLs but the script itself does when run.

In case anyone else needs it, it is vcrun2005.
The problem is that I can't run winetricks because Lynx transferred ownership of all my home directory (and subdirectories, and individual files) to root, with plugdev as the group. Unfortunately, plugdev, of which I am a member, also can't write to the .wine directory! 

This phreaking sucks!

By the by, does anyone have a good conspiracy theory as to why Google won't port SketchUp to linux? 

Randy

---

### Post by Gemnoc on 2010-06-15
I don't understand your problems guys. Since v7 I've had almost no trouble installing and running SketchUp (but I'll confess I don't use it much). I've installed it on the following configs:

desktop PC w/ Nvidia GF6600GT running Ubuntu 9.04 32-bit
desktop PC w/ Nvidia GF8600GTS (replaced later by 9800GT) running 9.10 64-bit
laptop w/ Intel GMA4500MHD running UNR 9.10

I don't even believe I've needed winetricks. I solved the few troubles I had with the [SketchUp Wine wiki]("http://wiki.winehq.org/GoogleSketchup"). You can also have a look at Wine's AppDB [here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1815"). I believe the trick is to have a Wine version no older than v1.1.38.

Of all my setups, the Intel one has the smoothest graphics, the less artifacts. Go figure!

---

