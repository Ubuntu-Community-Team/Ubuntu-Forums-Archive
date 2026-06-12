---
title: "Wine error message"
date: 2008-12-06
forum: Wine
---

### Post by timofthec on 2008-12-06
Hi all, 

Been setting up wine and I can't seem to get it to work so I had a perusal of the community documents.  

When In try to run anything, I get the following message in a terminal :-

> xxxx@xxxx-desktop:~/FG$ wine install.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing

The game is an old win95 game called Fantasy General that I recently re-discovered when having a clear out and would like to get it running.

Any ideas?

---

### Post by Cresho on 2008-12-06
terminal........
#winecfg

applications

add application, locate exe, use windows version win95 or 98.  or just use the default settings and in windows version try the older windows.

---

### Post by timofthec on 2008-12-08
> **Cresho said:**
> terminal........
#winecfg

applications

add application, locate exe, use windows version win95 or 98.  or just use the default settings and in windows version try the older windows.

Tried that Cresho and I still get the error message when I try and run an exe.  Not sure what I'm doing wrong at the moment :confused:

---

### Post by tyle on 2008-12-08
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem) might solve your problem. It will at the very least make the preloader warnings go away.

---

