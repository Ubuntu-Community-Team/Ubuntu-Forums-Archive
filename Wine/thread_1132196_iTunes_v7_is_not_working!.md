---
title: "iTunes v7 is not working!"
date: 2009-04-21
forum: Wine
---

### Post by wolfyking2 on 2009-04-21
I downloaded iTunes v7 installer and installed it.  I try to launch it, but nothing happens.  Heres what I get in a terminal

user@ubuntu:~$ '/home/user/.wine/drive_c/Program Files/iTunes/iTunes.exe' 
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x141be0,0x141b68): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea9c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Segmentation fault
user@ubuntu:~$ 

help?

---

### Post by asdfoo on 2009-04-21
> **wolfyking2 said:**
> I downloaded iTunes v7 installer and installed it.  I try to launch it, but nothing happens.  Heres what I get in a terminal

user@ubuntu:~$ '/home/user/.wine/drive_c/Program Files/iTunes/iTunes.exe' 
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x141be0,0x141b68): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea9c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Segmentation fault
user@ubuntu:~$ 

help?

cd to the install directory first.  not everything in itunes works.  tell us which version of Wine you are using.

---

### Post by wolfyking2 on 2009-04-21
This is what I get when I cd to the iTunes directory (install directory)

user@ubuntu:~$ cd '/home/user/.wine/drive_c/Program Files/iTunes' 
[email]user@ubuntu:~/.wine[/email]/drive_c/Program Files/iTunes$ '/home/user/.wine/drive_c/Program Files/iTunes/iTunes.exe' 
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x141910,0x141898): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea9c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Segmentation fault
[email]user@ubuntu:~/.wine[/email]/drive_c/Program Files/iTunes$ 

I'm using Wine 1.1.19

---

### Post by wolfyking2 on 2009-04-22
bump

---

### Post by wolfyking2 on 2009-04-23
Bump!

---

### Post by wolfyking2 on 2009-04-24
Got it fixed!  Used this guide [http://sudosys.be/?q=itunes_7.3_on_ubuntu_8.04]("http://sudosys.be/?q=itunes_7.3_on_ubuntu_8.04")

---

