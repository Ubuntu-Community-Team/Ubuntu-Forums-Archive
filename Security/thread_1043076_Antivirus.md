---
title: "Antivirus"
date: 2009-01-18
forum: Security
---

### Post by shazimalik on 2009-01-18
I have heard and now i am sure that linux is resistent to viruses but how do we scan a USB???

---

### Post by Shippou on 2009-01-18
Use ClamAv. Or the following (personal) guide.

NOTE: Before doing this, you should make Nautilus (or whatever file manager you are using) show hidden files.

1. If you see a Recycler folder, open it. If it has a bunch of files you don't know, delete it.
2. Usually, a virus has an autorun.inf file (or something similar) which is basically a configuration file that Windows uses to launch suitable programs (or programs specified on the autorun.inf file). Open this in a text editor like Gedit (don't run esp if you have Wine). If you see some gibberish stuff there (especially the strings 
open=someprogram.exe
cmd=someprogram.exe
shell=someprogram.exe
}
then delete the file. In general, autorun.inf files are pretty useless unless you use Windows' autoplay frequently. (I don't depend on this Windows' feature; when in Windows, I use "Run As" to open flash drives and launch programs if I know their exe names).
3. Some odd files you can delete:
exe files with weird names (such as asdghs.exe)
com files with weird names (like adsfhas.com)
bat files with weird names (like asdjewr.bat)
4. Some folders you can delete:
RECYCLER
5. Also, delete executables you don't know what they do (and crack files and keygens... just for the fun of it.)
6. Of course, delete crap files. They are not really malware, but then since you are somewhat doing a maintenance, do everything on one run.

Following my personal guide, I am able to keep my Linux and Windows boxes pretty much safe against malware coming from removable media. Of course, other guides follow for other vectors of infection, such as the Internet and LAN.

Hope this post is helpful.

---

### Post by cariboo on 2009-01-18
If you are plugging your usb device into a Linux computer, you don't need to scan for windows viruses as they won't work in linux. If you plug it into a windows computer, it should be able to detect viruses, if it is set up properly.

Jim

---

