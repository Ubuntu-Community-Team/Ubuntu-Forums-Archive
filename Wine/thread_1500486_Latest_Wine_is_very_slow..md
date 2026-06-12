---
title: "Latest Wine is very slow."
date: 2010-06-03
forum: Wine
---

### Post by Steam. on 2010-06-03
The latest version of Wine, is very slow.Whenever i launch a program, i don't see it anywhere in the processes, but it runs 5 mins later.I find this very annoying when i'm about to install something.Anyone else experiencing the same thing?

---

### Post by asdfoo on 2010-06-03
> **Steam. said:**
> The latest version of Wine, is very slow.Whenever i launch a program, i don't see it anywhere in the processes, but it runs 5 mins later.I find this very annoying when i'm about to install something.Anyone else experiencing the same thing?

you could have some sort of program running at startup delaying things

you could try using a fresh wineprefix or maybe you can post the terminal output here to show us what's happening

---

### Post by gjtoth on 2010-06-03
I have the same thing going on.

---

### Post by howefield on 2010-06-03
> **Steam. said:**
> The latest version of Wine, is very slow.

Only use wine (Wine 1.2-rc2) for 2 applications, and both seem to be fine.

---

### Post by Giant Enemy Cat on 2010-06-03
Takes 45 seconds to load Steam for me on the latest version of WINE. Quicker if I launch straight into a game via shortcut.

Pretty slow went compared to Windows but obviously that's to be expected when running through WINE.

EDIT: just remembered that I installed Steam through PlayOnLinux, not sure if that makes a difference.

---

### Post by asdfoo on 2010-06-03
> **Giant Enemy Cat said:**
> Takes 45 seconds to load Steam for me on the latest version of Wine. Quicker if I launch straight into a game via shortcut.

Pretty slow went compared to Windows but obviously that's to be expected when running through Wine.

EDIT: just remembered that I installed Steam through PlayOnLinux, not sure if that makes a difference.

I started steam on my vista laptop this morning and it took about 30 seconds to load.  Some days it loads fast, some days it loads slow.

---

### Post by hikaricore on 2010-06-04
I suggest trying to launch a simple program that doesn't need installation minesweeper or notepad and use a wineprefix to avoid any clutter you've setup on your main install.

> env WINEPREFIX="/home/hikaricore/.wine-test" wine notepad

note any errors or debug output if any from this first run and how long it takes.. then launch it normally:

> wine notepad

watch again for errors, debug output, etc and see how long it takes to start.

I'm almost willing to bet the second will load more slowly because of something you've installed.

---

### Post by asdfoo on 2010-06-04
again for comparison: launched steam on windows and it took about 20 seconds to load

---

### Post by mini-snapper on 2010-06-21
I get the same thing too. Loaded Memory Map into wine on 10.04 (UNE) and it takes 2 minutes to load up. CPU and Memory indicate it's essentially sleeping in this time. I had this loaded under 9.04 (UNR) & previous releases - all loaded like normal apps and I never felt the need to time em!
Following hikaricores advice i tried both mechanisms to fire off the application. Both take 2 minutes & both report the same things:-
_wine_kernel_init boot event wait timed out
and
import_dll Library RAPI.dll (which is needed by L"C:\\<my path...>\\mobdevif.dll") not found.
 
Any thoughts?

---

### Post by asdfoo on 2010-06-22
> **mini-snapper said:**
> 
_wine_kernel_init boot event wait timed out
and
import_dll Library RAPI.dll (which is needed by L"C:\\<my path...>\\mobdevif.dll") not found.
 
Any thoughts?


you've removed the crucial piece of information, whatever that program is it's probably causing the delays

---

### Post by Milos_SD on 2010-06-22
I get this too: 
```
_wine_kernel_init boot event wait timed out
```

But if I do wineboot --update, or start winecfg (first time it needs 2 minutes to start), but after that there is wineserver, wineboot and services.exe processes started, so everything work as it should (instant start, and no "_wine_kernel_init boot event wait timed out" error).

---

### Post by mini-snapper on 2010-06-26
Asdfoo, I didn't think the path was that relevant, more the message and the file - sorry about that. 
Anyway after much messing about it seems my wine install must have got seriously messed up. I tried to uninstall & reinstall wine and no change - even the wine config screen took 2 mins to load. Then uninstalled, physically deleted .wine and then reinstalled, still no joy. Recovered to a pre wine backup, loaded wine & app and everything is fine now!

---

