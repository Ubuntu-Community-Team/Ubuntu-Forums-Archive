---
title: "Diablo 1 Crashes"
date: 2008-12-21
forum: Wine
---

### Post by CrusaderAD on 2008-12-21
Can't seem to find a solution to this. Diablo 1 crashes after the video plays in the beginning. I installed Wine and the game just fine, but it won't load past the video screens in the beginning. Any Ideas?

---

### Post by Sprut1 on 2008-12-21
Take a look here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498)

Quoting:
```

You must have DirectDrawRenderer in the registry set to "gdi" (which is the default) for Diablo to work. If you have changed it to "opengl" at any point then the game will crash after the Blizzard logos.

 for your convenience here is a reg file that will change it for you:

-------------start DDrawRender.reg-------------

REGEDIT4
[HKEY_CURRENT_USER\Software\Wine\AppDefaults\Diablo.exe\Direct3D] "DirectDrawRenderer"="gdi"

--------------end DDrawRender.reg--------------

just copy the date NOT including the dashed lines to DDrawRender.reg and then use

wine regedit DDrawRender.reg

to add it to the registry

```

I would try this first.

---

### Post by CrusaderAD on 2008-12-21
Hm... tried that... still doesn't work.

---

### Post by Sprut1 on 2008-12-21
Whats your system like? I noticed this:

```
Bug #14611 	Diablo 1.0x crashes on a read exception when entering main menu on x86_64
```

Also, you might want to try the directdraw hack found here: [http://glados.iwanek.co.uk/dokuwiki/projects:wine-hacks](http://glados.iwanek.co.uk/dokuwiki/projects:wine-hacks) (middle of site)

Copy the correct ddraw.dll from the correct wine version folder in the file and to your wine system32 folder, and run the hack.reg. This should work on Hardy.

(This is not tested by me, all info found at winehq)

---

### Post by cthulhuuk on 2008-12-23
actually my site has a second slash (/) not a colon (:)

its: [http://glados.iwanek.co.uk/dokuwiki/projects/wine-hacks]("http://glados.iwanek.co.uk/dokuwiki/projects/wine-hacks")

I havnt updated the binaries on there since wine 1.1.5 so its a bit out of date but I'm doing some new builds as we speak :-)

--
Jasmine

---

### Post by CrusaderAD on 2008-12-26
How do I run Diablo from the command line with wine so I can see the output?

---

### Post by Sprut1 on 2008-12-26
"wine program"

type man wine for help

---

