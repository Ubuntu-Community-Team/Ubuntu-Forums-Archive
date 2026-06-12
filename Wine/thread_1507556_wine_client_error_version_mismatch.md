---
title: "wine client error: version mismatch"
date: 2010-06-11
forum: Wine
---

### Post by Metrop021 on 2010-06-11
I've seen a few solutions to this on google but my situation seems a little unique.

I have used this exact technique on my desktop comp, running ubuntu 10.04

Now i'm trying this on my laptop that runs puppy linux 5.0.

Pretty much what is happening is, you need some strange dll tweaks and registry tweaks to run this game properly, so these guys ([http://lookias.inventforum.com/viewtopic.php?p=19#19](http://lookias.inventforum.com/viewtopic.php?p=19#19)) made a modified wine that has the tweaks, and is available for download. 

On my desktop i just downloaded their modified wine, went to the path that the wine binaries are in and typed ```
./wine /root/.wine/drive_c/..../WA.exe /nointro
```
and it works perfectly.

now i'm trying to do the same on my laptop, but i'm not getting this error:

"Wine client error:0: version mismatch 0/398
your wineserver binary was not upgraded properly
or you have an older one somewhere in your path
Or maybe the wrong winserver is still running?"

It's true that i have a different version of wine installed on this computer, but i don't think that should matter. if i type winserver into console (which runs the wineserver already installed on the computer, i'm able to use the ./wine command to run the game but it gets the same bug that happens when i run using the unmodified wine. then if i run wineserver -kill and try to run their wine server using ./wineserver, i get the version mismatch error. I'm thinking about uninstalling the wine already on this computer and trying again then. But i'm not sure if that's necessary.

---

### Post by asdfoo on 2010-06-11
This means a different version of Wine is already running when you get that message.

Also, you should be running programs this way:

[http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0](http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0)

---

### Post by Metrop021 on 2010-06-11
ah yes i got that much figured out, so how do I 'turn off' that other version of wine?

---

### Post by Metrop021 on 2010-06-12
i'm having trouble fully uninstalling wine... the package remover on my os doesnt seem to remove it fully, as i can still use the wine command in terminal after 'uninstalling' it

---

### Post by hikaricore on 2010-06-13
> **Metrop021 said:**
> i'm having trouble fully uninstalling wine... the package remover on my os doesnt seem to remove it fully, as i can still use the wine command in terminal after 'uninstalling' it

This likely means you tried to install wine in more than one way. IE source, packages, alternate methods.
Also this was probably done without fully removing the previous installation.
If you installed wine from source you'll need to run a make uninstall from the source directory before installing deb packages.

---

