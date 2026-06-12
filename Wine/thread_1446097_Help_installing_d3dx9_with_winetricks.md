---
title: "Help installing d3dx9 with winetricks"
date: 2010-04-03
forum: Wine
---

### Post by abrake on 2010-04-03
Whenever I try installing d3dx9 with winetricks I get the following message:

```
Note: command '/usr/bin/cabextract -d /home/aaron/.wine/dosdevices/c:/winetrickstmp -L -F *d3dx9*x86* /home/aaron/.winetrickscache/directx_feb2010_redist.exe' returned status 1.  Aborting.
```

Can anyone help me decipher what is wrong and how I can install this?

---

### Post by bobwyajnr on 2011-06-14
> **abrake said:**
> Whenever I try installing d3dx9 with winetricks I get the following message:

```
Note: command '/usr/bin/cabextract -d /home/aaron/.wine/dosdevices/c:/winetrickstmp -L -F *d3dx9*x86* /home/aaron/.winetrickscache/directx_feb2010_redist.exe' returned status 1.  Aborting.
```

Can anyone help me decipher what is wrong and how I can install this?

Do you really need the full DirectX 9.0c libraries? Generally that will break games - you should initially try to use the builtin Wine DirectX->OpenGL compatibility layer. A few games need the odd addon DirectX .dll - as indicated on [WineHQ AppDB]("http://appdb.winehq.org/").

As any of the developers on WineHQ would tell you - "don't go too overboard with Wine .dll overrides"! :popcorn: It only complicates the debugging process for the indented target Windows application. 

[URL="http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107"]
As an extreme example Crysis 1 only needs a d3dx9_36.dll override (as my recent test shows).[/URL]

Bob

---

