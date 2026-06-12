---
title: "Civ 5 demo...help!"
date: 2010-09-21
forum: Wine
---

### Post by Neo40 on 2010-09-21
Hello,

I have installed Civ 5 demo via Steam and I can't launch it.
If I try from a terminal, I got theses messages:

```
eric@crunchbang:~/.wine/drive_c/Program Files/Steam/steamapps/common/sid meier's civilization v - demo$ wine CivilizationV.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
wine: Call from 0x7b83845b to unimplemented function msvcp90.dll.??0?$basic_ofstream@DU?$char_traits@D@std@@@std@@QAE@XZ, aborting
err:module:attach_process_dlls "CvGameDatabaseWin32Final Release.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Steam\\steamapps\\common\\sid meier's civilization v - demo\\CivilizationV.exe" failed, status 80000100

```

Any idea?

---

### Post by soowei on 2010-09-21
You want to run "winetricks vcrun2008" to install the VS2008 runtimes.

---

### Post by endintears on 2010-09-22
Same problem here. Have installed VS2008 runtime but still no joy. Any other suggestions?

---

### Post by endintears on 2010-09-23
Ok so I created a new wine prefix, installed Steam and copied over my SteamApps folder. I then used winetricks to install vcrun2008 and Civilization V worked.

Any ideas on how to fix my original wine prefix?

---

### Post by Neo40 on 2010-09-23
> **endintears said:**
> Ok so I created a new wine prefix, installed Steam and copied over my SteamApps folder. I then used winetricks to install vcrun2008 and Civilization V worked.

Any ideas on how to fix my original wine prefix?

Let me know if you find a fix!

---

### Post by Half-Left on 2010-09-24
Also, 1.3 runs it better without texture issues. I installed the vcrun packages and it worked fine.

---

### Post by BigScaryDragon on 2010-09-25
Make sure you are using Wine 1.2. I haven't tried it with Wine 1.3.

Here is proof the game works (the full thing, not the demo though):

[http://www.redirecttonull.com/?p=213](http://www.redirecttonull.com/?p=213)

---

### Post by Half-Left on 2010-09-25
Screenshot of Civ5 demo, 1440x900/AF x16/AA x4/High settings/Wine 1.3.3

---

### Post by jacobmh on 2010-09-25
What exactly did you do to get it working? And I've heard a lot of people are having trouble after the latest update, how did you deal with that?

---

### Post by andymcca on 2010-10-01
> **jacobmh said:**
> What exactly did you do to get it working? And I've heard a lot of people are having trouble after the latest update, how did you deal with that?
I was having this trouble and followed the link to the Steam support page. This page mentioned that some people fixed this error by moving steam to the base C drive, so I tried it out.
I copied my steam directory from ./wine/drive_c/Program\ Files/games (which is a ext4 raid0 volume) to just ./wine/drive_c (which is an ext4 raid1 volume). Now the game loads fine. Sadly it is not on the raid1 like I want, though. Perhaps it has to do with the space in "program files"? (Although I tried running it from ~/games/steam, which is a bind of the same raid0 volume, and it failed there also)

---

