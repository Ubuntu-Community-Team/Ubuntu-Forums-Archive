---
title: "Wine doesn't work as before after reinstall: Biggest Problem: Warcraft 3"
date: 2009-02-12
forum: Wine
---

### Post by Manu311 on 2009-02-12
Hi,

I formated my PC and reinstalled Debian (Lenny) so I got a totally clean installation.
Before that my wine worked well with Warcraft 3 and much other programs (even without winetricks).
I got a few errors now, trying to start Wc3 with Wine, but the error about msvcr80 and I fixed it with installing a few vcrun packages in winetricks.
So this error is fixed, but I got an other problem now:
```
$ wine war3.exe 
err:module:attach_process_dlls "Storm.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"E:\\Warcraft III\\war3.exe" failed, status c0000005

```
that error got 3 results within google, and they are all fixed with msvcr80.
The funny thing is, 1 of these 3 results is this:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)
If you search for my error message, u will find a User, called Manu with this error (but no solution). IT ISN'T ME!!
Depending on that I think it could be caused by my username but I don't understand why.
Anyways, I got and other problem starting other programs with wine (only a few programs, not all).
Problems are:
Ventrilo:
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
wine: Unhandled page fault on execute access to 0x004b7464 at address 0x4b7464 (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x004b7464 in 32-bit code (0x004b7464).
Register dump:
[...]
Backtrace:
=>0 0x004b7464 EntryPoint() in ventrilo (0x0033ffe8)
  1 0xb7eb1b07 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

I tryd it multiple ways now:
I used 1.1.13 and 1.1.14 and 1.1.3 (because it was my first wine version last time)
I installed all winetricks packages, and all winelibs, and wineutils.
I tryd opengl (no effekt)
I installed with: dpkg, apt-get, make install, tools/wineinstall
I copied most files from my old wine directorys (I can't copy all, because I crashed my fs and only was able to repair a few Inodes - so the structure is very broken).
I also copied a few dlls from my original Windows XP version and set them to native - no effekt.
Btw: Frozen\ Throne.exe and Warcraft3.exe got similar results like Ventrilo.exe

---

### Post by Manu311 on 2009-02-14
I've got an old Cedega Version from a friend but it didn't worked either.
I'm getting crossover from an other friend now, but I don't think this will work ....

---

