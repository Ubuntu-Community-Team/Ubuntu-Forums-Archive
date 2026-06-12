---
title: "Microsoft.VC80.CRT"
date: 2010-01-25
forum: Wine
---

### Post by Keith Fox on 2010-01-25
Trying to run this command:
```
wine /home/chieffox/.wine/dosdevices/c:/"Program Files"/FixYa/FixYaUtility
```
[LEFT]
and I'm getting this error:
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
```

This thread:
[http://www.linuxforums.org/forum/wine/114210-microsoft-vc80-crt.html](http://www.linuxforums.org/forum/wine/114210-microsoft-vc80-crt.html)

tells me, "That you're missing the VC80.CRT is an indication that you do not have  the visual C++ libraries installed. You can download them from:"

This page:
[/LEFT]
[microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en]("http://ubuntuforums.org/microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en")


Just wondering if this is correct, anybody know anything about this error message?

---

### Post by Keith Fox on 2010-01-25
well after installing that requirement it did solve that error but now got another error.
```
X Error of failed request:  BadPixmap (invalid Pixmap parameter)
  Major opcode of failed request:  54 (X_FreePixmap)
  Resource id in failed request:  0x580002a
  Serial number of failed request:  233
  Current serial number in output stream:  248
```If I did get this software to work in wine, I would be the first to successfully install it on Linux, that I know of.

Here is what the software is I'm trying to install:
**[SIZE=2]_FixYa Expert Utility  Software_[/SIZE]**


Current Version:     1.5.1
Date Added:        June 15th, 2008
File Size:            170KB
Requirements:    Windows (2000, XP, 2003, Vista), Microsoft .NET Framework
License:         Free                     
[SIZE=1][IMG]http://www.fixya.com/images/icons/im_demo.png[/IMG][/SIZE]

---

