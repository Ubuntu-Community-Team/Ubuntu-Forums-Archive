---
title: "Can't Open Sims 3"
date: 2011-01-12
forum: Wine
---

### Post by KaciLynn on 2011-01-12
So I downloaded The Sims 3 and installed it fine, and when I first tried to run it I ran into a problem with the screen going black after the video intro, so I read the forums and found a suggestion that had worked for someone else. I went into winetricks and disabled glsl, then I went into the terminal to try to run the game and I get this output:

kaci@kaci-Aspire-5532:~/Desktop$ ./TS3.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32e52c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d280,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cb04,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cbb4,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:thread:SetThreadIdealProcessor (0xe8): stub

A window also pops up that says it failed to initialize the game. Can anyone help me out here? I really want to play this game.

---

### Post by ronnielsen1 on 2011-01-12
> Does need winetricks d3dx9.  This is on an HP dv6227cl with a GeForce 6150.


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664)

This page might help

---

### Post by Mama_Bear on 2011-01-24
I have the same problem wiht not being able to open the game. I have winetricks d3dx9 and it still isn't working.

---

