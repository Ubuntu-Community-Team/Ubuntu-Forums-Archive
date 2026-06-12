---
title: "Windows Application Compatability?"
date: 2007-11-19
forum: Windows
---

### Post by TheLastApparatus on 2007-11-19
Alright... I'm under the impression that linux can't run Windows Applications because they would need M$ Code, and that there are obvious problems with rewriting or distributing M$ code, namely legal issues. I'm curious, however, if it would be legal, and possible, to write a linux distro that can run windows applications when, and only when, a windows installation is on the same computer -- by utilizing Windows' files, therefore not needing to rewrite nor distribute M$ code, as it would already (obviously) be on any computer that has Windows installed. I know I have a very limited understanding of programming, especially OS-wise, so if this makes no sense and is absolutely no help, or something that others have already considered, or heard about several times, I am very sorry for any time I've wasted. ^.^

On another note, if anyone has any news about recent jumps with Linux/Windows Compatibility (other than not-always-functional "Emulators" like WINE -- And Yes, I know Wine Is Not an Emulator) I'd be more than glad to hear.

---

### Post by arvevans on 2007-11-19
Suggestion:  Before posting something like this you could do a "search" on the subject or topic and probably find that it has already been discussed a great many times.

Now, to your particular question:  There are many programs available on Linux and the other ..IX systems that support execution of MS-Windows programs.  Some, like Wine, have their own support library of .dll helper programs (written as work-alike code that does not violate any Microsoft issues), or like Wine they can use the helper files of a co-installed copy of MS-Windows.  Others are pure multi-OS hosts like VM-Ware that can selectively execute code from any installed OS, including MS-Windows.  There is also the possibility of an application in Linux (or other ..ix OS) that would fully emulate the xx-86 computing platform hardware and thus could install and run a Microsoft OS installation as if it were not running on an emulated abstraction layer.

As you might expect, the emulators that rely on purpose-written .dll files to help execution of MS-Windows applications sometimes find that the application requires a special .dll or other helper file that the manufacturer did not install, or one that has very recently been provided by Microsoft.  Other MS-Windows programs that have been written by 3rd patry developers might violate even Microsoft's rules by bypassing parts of the OS abstraction layer, and thus would probably not execute correctly on Linux.

Linux capability to execute MS-Windows and MS-DOS applications is pretty good, but not yet 100%.  It has improved dramatically over the past couple of years, and will probably continue to be improved.

Arv
_._

---

### Post by TheLastApparatus on 2007-11-19
I'm sorry about not having found any similar topics -- I'm a member of many fora, and as such know the proper forum etiquette. Luck seems to have not been on my side this time, however, because after searching, and even with the "we found these similar topics" feature that alerts would-be thread starters of similar topics, I failed to find anything dealing with the specific thought I had -- Linux using an existing windows installation to improve compatability. On the subject of your quick reply, however, I am thankful. :) I will however, have to look more into WINE and VM-Ware. I'm a rather big fan of Linux, and have OSx86, Ubuntu, and WinXP all installed on my computer and switch between them for various tasks. (although, honestly, I'm finding the need for three OS' to be nonexistent at the moment) I await the day when one operating system will be enough to do everything I want -- from graphic modification, to word processing, and (perhaps windows' only use) gaming. My money is on Linux being that OS. ^.^

---

### Post by aysiu on 2007-11-19
It's not a legal issue. It's a technological issue.

Because Microsoft does not open its code, everything has to be reverse-engineered in order to create a Windows compatibility layer. That's why Wine and ReactOS will always be works in progress and not have 100% compatibility with Windows programs.

---

### Post by LaRoza on 2007-11-19
Wine runs every app that I wanted it too, DosBox runs the DOS apps I want in either OS. ReactOS is too unstable to use.

If you have an app that requires Windows, and you need it, use it in Windows. Virtual Machines are good too.

---

