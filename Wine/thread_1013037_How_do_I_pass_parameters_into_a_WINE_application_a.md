---
title: "How do I pass parameters into a WINE application at runtime? (Winrar)"
date: 2008-12-16
forum: Wine
---

### Post by mholland on 2008-12-16
I am currently running winrar using WINE. I know there are other choices, but for all practical purposes I would like to know how to achieve the following:

I can launch winrar one of the two ways:

wine "/home/synterprise/.wine/drive_c/Program Files/WinRAR/WinRAR.exe" 

or

wine "c:\program files\winrar\winrar.exe"

When assigning the default application to open a specific file type you can select to use a custom command. I can get winrar to open when I select a specific rar file but I can not get winrar to open along with the chosen rar file. Does anyone know how to accomplish this? I can see myself doing the same steps for many applications. Not just winrar.

---

### Post by asdfoo on 2008-12-16
> **mholland said:**
> I am currently running winrar using WINE. I know there are other choices, but for all practical purposes I would like to know how to achieve the following:

I can launch winrar one of the two ways:

wine "/home/synterprise/.wine/drive_c/Program Files/WinRAR/WinRAR.exe" 

or

wine "c:\program files\winrar\winrar.exe"

When assigning the default application to open a specific file type you can select to use a custom command. I can get winrar to open when I select a specific rar file but I can not get winrar to open along with the chosen rar file. Does anyone know how to accomplish this? I can see myself doing the same steps for many applications. Not just winrar.

/usr/bin/file-roller works well for rar files.

but as for your question, maybe first you should read how to start programs using Wine:

[http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0](http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0)

Then using that information, write a shell script such as:

#!/bin/sh
cd ~/.wine/drive_c/blah/blah
wine foo.exe $*


ymmv...

---

