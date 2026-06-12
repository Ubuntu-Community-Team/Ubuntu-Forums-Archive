---
title: "WINE 1.0 Released"
date: 2008-06-18
forum: The Cafe
---

### Post by sharks on 2008-06-18
I knew today would be a special day, because Mozilla decided to launch the final version of Firefox 3.0, but I was not expecting this... Ladies and gentlemen, we are proud to announce Wine 1.0, the final and stable release, after 15 years of development!
While the compatibility with many Windows applications is not yet perfect, thousands of programs have been reported to work very well, thanks to all the loyal Wine users and testers. Wine 1.0 fixes:

• a Counter-Strike 1.6 performance issue;
• an X11 error: BadDrawable (X_PolyFillRectangle) when you had to switch to the virtual desktop;
• the two Punisher demo bugs, where a crash occurred after the introduction movies and when it failed to start after the installation;
Starlancer draws ships as white when direct3d is enabled
• the Warcraft 3x regression when someone wanted to leave the fullscreen mode;
• the Oni issue, when it failed to start after the installation;
• the Skype 3.1 login problem on Kubuntu 7.10
• the Stata 10 bug, which caused Wine to crash when help was clicked;
• the Call of Duty scratchy/static sound problem with OSS
• the black icons showing in WinRAR with NXServer;
• the QIP issue, where the window z-order was wrong;
• the Robot Wars: Arena of Destruction bug, where it crashed when quitting the game, which caused the resolution to stay at 640 x 480 pixels;
• an Eve-online bug;
• the Dragon Naturally Speaking 9 issue;
• the Call of Duty 1.0 problem, which made the game not to start after the installation;
• the Dance Praise 2 issue, which failed to respond to input;
• the Moto Racer 2 issue with Wine 0.9.61;
• the winebrowser unicode problem (gets wrong URL).

Wine is an open source project that takes the Windows API and allows you to run seamlessly Windows applications on your Linux machine. It's like having a small version of Windows packed up in your Linux system. Wine's API is 100% non-Microsoft code, but it uses Windows DLL in case you have them.

Download From [http://linux.softpedia.com/get/System/Emulators/Wine-148.shtml](http://linux.softpedia.com/get/System/Emulators/Wine-148.shtml)

---

### Post by sharks on 2008-06-18
ine is an Open Source implementation of the Windows API on top of X and Unix.

Think of Wine as a compatibility layer for running Windows programs. Wine does not require Microsoft Windows, as it is a completely free alternative implementation of the Windows API consisting of 100% non-Microsoft code, however Wine can optionally use native Windows DLLs if they are available. Wine provides both a development toolkit for porting Windows source code to Unix as well as a program loader, allowing many unmodified Windows programs to run on x86-based Unixes, including Linux, FreeBSD, and Solaris.

Here are some key features of "Wine":

Binary Compatibility

· Loads Windows 9x/NT/2000/XP, Windows 3.x and DOS programs and libraries
· Win32 compatible memory layout, exception handling, threads and processes
· Designed for POSIX compatible operatings systems (eg. Linux and FreeBSD)
· ``bug-for-bug'' compatibility with Windows

Graphics

· X11-based graphics allows remote display to any X terminal
· X11, TrueType (.ttf/.ttc) and Windows Bitmap (.fon) Fonts
· DirectX support for games (limited Direct3D support)
· Printing via PostScript driver or legacy native Win16 printer drivers
· Enhanced Metafile (EMF) and Windows Metafile (WMF) driver
· Desktop-in-a-box or mixable windows
· Windows MultiMedia (WinMM) layer support with builtin codecs

Allows Windows program to interface with:

· Sound devices via ALSA, OSS, ARTS, JACK, and libaudio etc
· Multi-lingual keyboards and CJK input method support via XIM
· Modems, serial devices
· Networks (TCP/IP and IPX)
· ASPI Scanners
· Windows Tablets via XInput (eg. Wacom)

Wine API

· Designed for source and binary compatibility with Win32 code
· Win32 API test suite to ensure compatibility
· Compilable on a wide range of C compilers
· Permits mixing of Win32 and POSIX code
· Permits mixing of ELF (.so) and PE (.dll/.exe) binaries in one address space
· Win32 compatible header files
· Automatically generated API documentation
· Resource compiler
· Message compiler
· IDL compiler
· extensive Unicode support
· Internationalization -- Wine supports 16 languages
· Built-in debugger and configurable trace messages
· External memory checker support using Valgrind
· Sample programs

---

### Post by Bungo Pony on 2008-06-18
I'm really hoping that the multiple file select bug was fixed. Regardless, I'll be installing Wine 1.0!

Congrats to all the developers for reaching this milestone!

---

### Post by tdrusk on 2008-06-18
This is bigger than FF3 imo.

---

### Post by bufsabre666 on 2008-06-18
> **tdrusk said:**
> This is bigger than FF3 imo.

+1, ive been telling tons of people, no one seemed to think so, this is ***_[SIZE="7"]HUGE!![/SIZE]_*** this has been in development for 15 years now and its finally 1.0, granted its not perfect but still, firefox 3 doesnt campare, i use swiftweasel anyways

---

### Post by tdrusk on 2008-06-18
> **bufsabre666 said:**
> i use swiftweasel anyways
Aren't they the same? Wasn't Swiftweasel made because of Firefox's license and Debian's release schedule conflicted?

---

### Post by voteforpedro36 on 2008-06-18
> **tdrusk said:**
> Aren't they the same? Wasn't Swiftweasel made because of Firefox's license and Debian's release schedule conflicted?


Wasn't that Iceweasel?

---

### Post by bufsabre666 on 2008-06-18
> **tdrusk said:**
> Aren't they the same? Wasn't Swiftweasel made because of Firefox's license and Debian's release schedule conflicted?

iceweasel was debians creation to get rid of the non-free stuff in firefox, now its called icecat, swiftweasel works on the same principle all the non-free things are gone and then it goes a step further with architecture and cpu optimization, plus it fits ubuntus theme better

edit: nonfree meaning artwork and other mozilla copyrighted things, flash and java work

---

### Post by quanumphaze on 2008-06-18
I don't know the specifics but they made one called Icecat for Debian license issues.

I think Swiftweasel is similar but optimised for specific architectures.

Check the site for the details/truth. [http://swiftweasel.wiki.sourceforge.net/](http://swiftweasel.wiki.sourceforge.net/)

EDIT: Back on topic, I predict Wine will hijack the Win32 API from Microsoft and Windows will have to be Wine compatible. One can dream.

---

### Post by RiceMonster on 2008-06-18
I upgraded yesterday. Great news.

---

### Post by Daggo on 2008-06-18
*Immediatley downloads Wine 1.0*

---

