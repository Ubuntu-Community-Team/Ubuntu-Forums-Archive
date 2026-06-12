---
title: "gnomebaker 0.5.3"
date: 2006-02-19
forum: Requests
---

### Post by teolemon on 2006-02-19
I'd like version 0.5.3 to be backported
There are many fixes that benefit the user ,even though Dapper is nearer.
> 
* Test Fix copying and disk detection when the cd reader is also the writer.
 * Fix devices_mount as it only works in english locales.
 * Attempt to enable large file support (>2GB) using AC_SYS_LARGEFILE.
 * Apply patch #1329223 Escaping song names
 * Apply patch #1328125 Patch to make Desktop file more compliant
 * Fix the progress dialog so when you are viewing output it scrolls to the bottom properly.
 * Show burning progress in the main window title so when you minimise the app you can see when it’s finished.
 * Apply patch #1329438 Fix exec layer in 64bit architecures
 * Apply patch #1328641 Fix build on GNU/kFreeBSD
 * Apply patch #1329831 Updated pt_BR translation
 * Use valgrind to fix minor memory leaks.
 * Remember the last selected data and audio disk sizes.
 * Add raw96r write mode.
 * Fix up datacd sizes according to cdrfaq.org
 * Refactor the start burn dialog so that burning a data disk won’t pop up loads of dialogs.
 * Unmount devices using the device node rather than the mount point.
 * Apply patch #1385469 Change default tempdir location
 * Apply patch #1389004 fixed File Browser show/hide logic
 * Fix bug #1385461 Default tempdir location doesn´t work for a second user
 * Fix bug #1221654 Interface not usable from keyboard
 * Fix bug #1252914 ‘delete’ key should work in Disk tabs
 * Fix bug #1336559 Gnomebaker asks for an empty disk when there is one inserted
 * Apply patch #1333284 Patch for GNU Build System - Brian Pepple
 * Apply patch from Bjoern Schiessle to export m3u and pls playlists.
 * Apply patch from gamehack to use GOption for parsing startup arguments.
 * Apply patch #1395049 Ask for confirmation when burning images which are not *.iso - goedson
 * Apply patch from gamehack to enable -force option to cdrecord
 * Apply patch from gamehack for option of scrolling progress window output
 * Fix RFE #1275226 Show Space Remaining on disk
 * Apply patch from gamehack for nice summary in configure.in
 * Make toolbar button enablement and menu enablement consistent.
 * Use gamehacks animated icons to show progress when burning.
 * Splash dialog is now only shown on platforms other than linux as they use manual cdrecord device discovery.
 * Fix Bug #1270524 Won’t allow burning of 700mb files
 * Icons - you’ve been tango’d. Nice one Gamehack.
 * Added quite a few translations (and updated the rest)
 * Apply patch from mattias nissler to fix endian audio conversion problems on PPC. 
AFAIK there's no dependency ,nor compiler,interpreter problem (it's a micro release)

---

### Post by s6dalane on 2006-02-22
I would like to see that getting backported too :D.

---

### Post by ats247 on 2006-02-23
me too.

---

### Post by xrado on 2006-03-05
me too!!!

---

### Post by SpEcIeS on 2006-03-07
Where is the elusive gnomebaker 0.5.3? All I seem to find is 0.5.1, which is available for Ubuntu. :confused:

---

### Post by brian g on 2006-03-16
anyone anyone?

---

### Post by s6dalane on 2006-03-26
Any chance for a 0.5.1 backport then? Is it in Dapper?
In Breezy repositories i can only find 0.5.0 or am I missing something?

---

### Post by limaunion on 2006-04-02
+1 Pse!

---

