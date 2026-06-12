---
title: "Where do I put my GTA Vice City save games?"
date: 2009-11-20
forum: Wine
---

### Post by Redsandro on 2009-11-20
I found my save games from a long time ago on a windows machine and I'd like to play them on Ubuntu.

I've got GTA Vice City running just fine with wine, but GTA never finds my save games and I cannot save new games either because the games are gone when I want to load. That's probably a permission issue or a non-existing folder issue.

Where am I supposed to copy my saves, or where are saves stored with wine?

In Windows it was **My Documents\GTA Vice City User Files**. Wine has My Documents configured as **~/**. But **~/GTA Vice City User Files** does not work for GTA.

I own all files and folders and have write permissions. I am missing something.

---

### Post by hikaricore on 2009-11-20
For some reason mine are stored at:

> ~/.wine/drive_c/My.Documents/GTA Vice City User Files/

No idea why but it works for me *shrugs* guess it's worth a shot.

---

### Post by Redsandro on 2009-11-20
Thanks I will try that!

Can you tell me the paths in winecfg Desktop Integration and the location where GTA VC is located?

'Cause maybe you have everything in ~/.wine/drive_c/ while I have GTA in /usr/local/games/ because it's for multiple accounts.

---

### Post by hal10000 on 2009-11-20
If they are nit in the directory **~/.wine/drive_c/My.Documents/GTA Vice City User Files/** then you may look if they are stored in a hidden directory under /home/your_name e.g. /home/your_name/.gta or a similar name (hidden directorier and files always start with a dot as first character).

---

### Post by Redsandro on 2009-11-20
I've tried it and it doesn't work. :(

Actually I just mounted the drive from my old (broken) windows machine and moved the game dir to /usr/local/games. The game runs perfectly and all options and settings are stored. But maybe because I just moved the files, some directories weren't created.

Unfortunately the console sais nothing, but is there a way to see or trace what files a wine application tries to access? It would be convenient if I know where GTA looks and I can just move the saves to that directory.

---

### Post by Redsandro on 2009-11-20
I did some debug tracing using
```
env WINEDEBUG=+file wine gta-vc.exe 2>&1 | tee /home/sander/gta.log 

```

And there when I try to save in gta.log on line 29912 and on I see
```
trace:file:RtlGetFullPathName_U (L"L:\\games\\gta-vc\\" 520 0x32f5b4 (nil))
trace:file:wine_nt_to_unix_file_name L"\\??\\L:\\games\\gta-vc\\" -> "/home/sander/.wine/dosdevices/l:/games/gta-vc/"
trace:file:RtlSetCurrentDirectory_U curdir now L"L:\\games\\gta-vc\\" 0x184
trace:file:RtlGetCurrentDirectory_U (520 0x32f6a0)
trace:file:CreateFileW L"%USERPROFILE%\\My Documents\\GTA Vice City User Files\\GTAVCsf1.b" GENERIC_READ FILE_SHARE_READ FILE_SHARE_WRITE  creation 3 attributes 0x0
trace:file:RtlDosPathNameToNtPathName_U (L"%USERPROFILE%\\My Documents\\GTA Vice City User Files\\GTAVCsf1.b",0x32f698,(nil),(nil))
trace:file:RtlGetFullPathName_U (L"%USERPROFILE%\\My Documents\\GTA Vice City User Files\\GTAVCsf1.b" 520 0x32f3dc (nil))
warn:file:wine_nt_to_unix_file_name L"%USERPROFILE%\\My Documents\\GTA Vice City User Files\\GTAVCsf1.b" not found in /home/sander/.wine/dosdevices/l:/games/gta-vc
warn:file:CreateFileW Unable to create file L"%USERPROFILE%\\My Documents\\GTA Vice City User Files\\GTAVCsf1.b" (status c000003a)
trace:file:CreateFileW returning 0xffffffff

```

So the correct path for my saves would be in :
**%USERPROFILE%/My Documents/GTA Vice City User Files/**

Now I just need to find out what **%USERPROFILE%** links to, but I cannot find it anywhere on google. I tried entering that in the save dialog from **wine notepad** to see where I end up, but it doesn't work like that. :P

-edit-

Wow I'm so glad I remember how MS DOS works :P
I started 'dos' with wine **cmd.exe** and entered **set** to see the environmental variables. And there between all the rest I see:
**USERPROFILE=C:\windows\profiles\sander**

Sooo I guess that I will move my saves to
**/home/sander/.wine/dosdevices/c:/windows/profiles/sander/My Documents/GTA Vice City User Files/**
and see what happens. :)

Dammit, **/home/sander/.wine/dosdevices/c:/windows/profiles/sander/My Documents** links to **/home/sander/** and the folder is already there. It doesn't work. Yes I have all the permissions! :((

---

### Post by dgandhi on 2009-12-19
I had the same problem, tried to move the saved games, but no luck.

Then I remembered that the GTAVC installer allowed you to install for your account instead of for the entire system, so I reinstalled for my account only. after that the saved games worked.

I used PlayOnLinux, and just uninstalled, and re-ran their installer that creates a wine prefix, and has all the config settings, I put my user name in the "user account only" section.

After resetting the virtual desktop to match my monitor, it works like a charm.

---

### Post by Redsandro on 2009-12-19
It's very probable that something like that is the issue. But I am very curious to *what is the difference* in the resulting installation. It is probably literally 1 bit in some configuration file, and I'd like to set that manually because I just literally copied the game over from my ancient Windows XP harddrive of a failing computer. The installation CD is probably at my parents' or little brothers' house. Everyone lives in different cities. :P I was there last week but I forgot to look because I had totally forgotten about this.

---

