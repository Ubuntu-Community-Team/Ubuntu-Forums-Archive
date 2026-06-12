---
title: "Pop_os"
date: 2021-10-12
forum: Ubuntu/Debian BASED
---

### Post by sardonic2 on 2021-10-12
Hello,

I've recently installed POP_OS on my laptop.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289271&stc=1[/IMG]

I have noticed sometime this visual glitch when using the cursor to make window bigger or smaller in a fast pace.
I managed to immortalized it with this screenshot.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289270&stc=1[/IMG]

What would trigger this, any thought?
Thank you.

---

### Post by howefield on 2021-10-12
Thread moved to the "Ubuntu/Debian BASED" forum.

---

### Post by sardonic2 on 2021-10-12
@ howefield Thanks.

---

### Post by Claus7 on 2021-10-12
Hello,

I remember having such kind of "glitch" a long time ago for a short period of time. If I recall correctly this was supposed to be a graphics driver problem that vanished when properly a proprietary driver at that time was installed. This is the input I can provide. Someone else might have more information.

Regards!

---

### Post by sardonic2 on 2021-10-12
@Claus7, thank you for your input.

---

### Post by oldfred on 2021-10-12
Do not know Pop.

May have some info, arch often has better descriptions of settings which often apply across many distributions:
[https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics)

A list of all options along with short descriptions and default values can be generated with the following command:
modinfo -p i915
To check which options are currently enabled, run
systool -m i915 -av
glxinfo | grep "OpenGL version"

My 6500Intel based system:
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ glxinfo | grep "OpenGL version" [/COLOR]
[COLOR=#ff5454]**OpenGL version**[/COLOR][COLOR=#000000] string: 4.6 (Compatibility Profile) Mesa 21.0.3[/COLOR]

Have you updated UEFI to latest available?
[/FONT]

---

### Post by sardonic2 on 2021-10-13
@oldfred,
Thank you very much for your comment, sound promising, will check the BIOS and the rest...

[FONT=monospace][COLOR=#54ff54][/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ glxinfo | grep "OpenGL version"  

[/COLOR][/FONT][B]*OpenGL version string: 4.6 (Compatibility Profile) Mesa 21.2.1*
[/B]
[B]-------------------------------------------------------------

[/B]From settings: 
[I]**Mesa Intel® HD Graphics 520 (SKL GT2)**
[/I]
**------------------------------------------------------------**

[FONT=monospace][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo dmidecode -s bios-version:
***1.2.8***
[/COLOR][/FONT]

---

