---
title: "Starcraft patch SC-116.exe doesn't work"
date: 2008-12-02
forum: Wine
---

### Post by bearing on 2008-12-02
When running SC-116.exe through wine I get errors about missing files, see attached screenshots.

How do I solve this?

---

### Post by dbos on 2008-12-06
Hey I was also having troubles, and in the process saw a potential solution to your problem. I also put the solution to my problem of being unable to validate the game version. Basically the digital download version that you can get using your CD key on the blizzard store website didn't patch properly at first (this happened regardless of what OS you run). 

As far as I understand, it tried to patch right up to 1.16 but forgot a file that was introduced during the more standard patching procedure. Blizzard decided it wasn't optimal to just let that file float around for people to fix themselves, so they made a 1.15.3 patch since then which is used during autopatch to make the files exist for the 1.16 patch. If you still cant get it to work, you'll have to start the whole procedure over and it should patch ok. If it doesn't, the official tech support forums have a few threads remaining from other people who had unfortunate timing trying to patch their digitally licensed versions before they put the fix on the patching process. Basically this issue shouldn't effect people anymore.

BUT you will soon find that battle.net will be unable to "validate the application version". What you need to do to fix this is to replace a couple of wines libraries with native ones, namely mshtml.dll and wininet.dll. I don't know why suddenly you need these to validate game version, but I was trying forever to figure this out before stumbling upon the solution so hopefully it helps someone. 

Battle.net will likely crash if you don't fix the fonts, but thats another issue and you'd be better off searching separately for that. Once it all "works" battle.net will still be pretty unusable. The text of the interface doesn't get replaced when it should so new text covers it and you end up with unreadable garbage everywhere. If you can get into a game fast enough it's ok, and creating games is ok too. 

Basically, battle.net is pretty awful for Starcraft and wine, so even though it "works" don't get your hopes up.

---

### Post by kazzmir on 2008-12-26
> 
BUT you will soon find that battle.net will be unable to "validate the application version". What you need to do to fix this is to replace a couple of wines libraries with native ones, namely mshtml.dll and wininet.dll. I don't know why suddenly you need these to validate game version, but I was trying forever to figure this out before stumbling upon the solution so hopefully it helps someone.


Can you explain how to do this? I downloaded the dll's from some site but the wine versions are native ELF files, not win32 PE/COFF files so I don't think I can just replace them.

```

jon@jon-laptop /usr/lib/wine $ file mshtml.dll.so 
mshtml.dll.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), stripped
jon@jon-laptop /usr/lib/wine $ file wininet.dll.so 
wininet.dll.so: ELF 32-bit LSB shared object, Intel 80386, version 1 
(SYSV), stripped

$ file *
mshtml.dll:  MS-DOS executable PE  for MS Windows (DLL) (GUI) Intel 80386 32-bit
wininet.dll: MS-DOS executable PE  for MS Windows (DLL) (GUI) Intel 80386 32-bit

```

---

