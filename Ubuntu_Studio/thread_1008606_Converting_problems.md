---
title: "Converting problems"
date: 2008-12-11
forum: Ubuntu Studio
---

### Post by Shiv4m on 2008-12-11
Hey guys can you suggest any programs that will let me convert my .ogg to .avi?

---

### Post by FakeOutdoorsman on 2008-12-11
You can do this with ffmpeg:
```
ffmpeg -i input.ogg -sameq output.avi
```
The sameq tells ffmpeg to use the same video quality as the source video.

---

### Post by howefield on 2008-12-11
If you want a prog with a gui, iriverter is in the repository download with synaptic.

---

### Post by Shiv4m on 2008-12-11
> **howefield said:**
> If you want a prog with a gui, iriverter is in the repository download with synaptic.

Thanks for the program but hte program will not start up for me, here is what I get when I try to start it up through terminal:

> shivam@shivam-laptop:~$ iriverter
!!! An unhandled exception occured: class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
--- 
--- Settings:
--- 
--- 
!!! no swt-pi-gtk-3236 in java.library.path
!!! 
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1698)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:840)
!!! java.lang.System.loadLibrary(System.java:1047)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
!!! org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:28)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!! 
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class org.eclipse.swt.widgets.Display
	at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:675)
shivam@shivam-laptop:~$ 



What should I do?

---

### Post by howefield on 2008-12-11
I don't get errors after install. :(

What does the iriverter text file look like ?

You'll find it in usr/bin/iriverter

---

### Post by FakeOutdoorsman on 2008-12-11
You could try [WinFF](http://code.google.com/p/winff/wiki/UbuntuInstallation), a GUI for ffmpeg.

---

### Post by Shiv4m on 2008-12-12
I downloaded OGGConvert which works great, thanks for the help!

---

