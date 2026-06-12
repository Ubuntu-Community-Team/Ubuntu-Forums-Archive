---
title: "Ubuntu 10.10 Wine 1.2 and Ableton 8.2"
date: 2011-04-24
forum: Wine
---

### Post by S34R3D.astryx on 2011-04-24
Howdy All,

Hope i get the proper posting etiquette down as this is one of my first times posting here. But here is my problem:

I have installed Ableton 8.2 via Wine. I have installed quicktime via winetricks and the actual .exe along with all the Visual c runtime libraries from 2005-2010. (as far as i know)

This is what i get when i run the following command in the terminal:

$ wine Live\ 8.2.exe 

fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8 )
err:module:attach_process_dlls "MSVCR90.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Ableton\\Live 8.2\\Program\\Live 8.2.exe" failed, status c0000142

I also get a pop up windows error message that says:

Runtime Error!

Program: C:\Program Files\Ableton\Live 8.2\Program\Live 8.2.exe

R6034
An application has made an attempt to load the C++ runtime library incorrectly.
Please contact the applications support team for more information.

Anyways any help or suggestions would be great. Thanks in advance!!

---

