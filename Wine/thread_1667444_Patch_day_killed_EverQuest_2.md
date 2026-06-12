---
title: "Patch day killed EverQuest 2"
date: 2011-01-14
forum: Wine
---

### Post by cmwatford on 2011-01-14
I recently installed EverQuest 2 on a friends computer on which I also installed the latest Ubuntu. It was copied from windows. All was working well with the game right out of the box. I didn't have to configure anything. That was until The most recent update. 
Here's terminal output.
```

fixme:win:EnumDisplayDevicesW ((null),0,0x32f0e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32eb1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec0c,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a760-90c8-11d0-bd43-00a0c911ce86} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a761-90c8-11d0-bd43-00a0c911ce86} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32f924,0x00000000), stub!
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x5907a3

```
Any advice would be appreciated.

---

### Post by Louis Cypher on 2011-01-17
The last line is the same error I get.

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x5907a3

No idea what the problem is :(

---

### Post by cmwatford on 2011-01-17
After working a day and a half on it, doing everything I could think of I fixed it. The solution makes me feel rather silly. All I had to do was change the windows version to 2008. :?

---

### Post by Louis Cypher on 2011-01-17
> **cmwatford said:**
> After working a day and a half on it, doing everything I could think of I fixed it. The solution makes me feel rather silly. All I had to do was change the windows version to 2008. :?

Nice work.  It worked for me too.  Although I do use the station launcher and when I changed it to 2008 the Station Launcher would not work.  To get around this I just added StationLauncher.exe to the APPLICATION SETTINGS screen in Wine config and used Windows XP version for it.  Works fine so far.

If you just run Everquest2.exe driectly then it works fine when just changing to version 2008.

---

### Post by Louis Cypher on 2011-01-17
> **cmwatford said:**
> After working a day and a half on it, doing everything I could think of I fixed it. The solution makes me feel rather silly. All I had to do was change the windows version to 2008. :?

Nice work.  It worked for me too.  Although I do use the station launcher and when I changed it to 2008 the Station Launcher would not work.  To get around this I just added StationLauncher.exe to the APPLICATION SETTINGS screen in Wine config and used Windows XP version for it.  Works fine so far.

If you just run Everquest2.exe driectly then it works fine when just changing to version 2008.

---

### Post by Hideaki on 2011-01-21
I can confirm that work-around works. I tried it using Windows 7 and the game runs fine, using Windows XP keeps the game from launching.

---

