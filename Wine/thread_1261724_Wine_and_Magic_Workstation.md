---
title: "Wine and Magic Workstation"
date: 2009-09-09
forum: Wine
---

### Post by Bigtime_Scrub on 2009-09-09
I have Wine 1.1.29 installed on Ubuntu 9.04.

I downloaded Magic Workstation. The install went fine and everything works well until I try to play a game in solo mode or I try to connect to another player and play that way. 

I get this error:

```
Access violation at address 70D09697 in module "gdiplus.dll'. Read of address 00000048.
```

It gives me an unending chain of pop ups and I am forced to kill the apllication. I did some research. I installed the "gdiplus.dll" using Winetricks as shown here ---> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5661&iTestingId=39875](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5661&iTestingId=39875)

I also used the Corefonts with Winetricks too but no dice. I have the same issue.

The WineHQ website tells me the .dll I am complaining about works fine. It obviously does not. I tried deleting it but I get a fatal error and the application just crashes. I also tried Wine in XP and Vista Mode. I dont know what to do. Should I just chop this up as not workable in Wine?

---

