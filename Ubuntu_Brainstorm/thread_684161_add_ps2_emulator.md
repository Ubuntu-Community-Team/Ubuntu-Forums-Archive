---
title: "add ps2 emulator"
date: 2008-01-31
forum: Ubuntu Brainstorm
---

### Post by Mr.mouse on 2008-01-31
as some of you know it's possible to run ps2 games in linux (like [http://www.pcsx2.net/](http://www.pcsx2.net/) )

make it work so:
1 the user put in ps2 disk in the computer 
2 if the game is supported -  ubuntu pop up ui about keyboard shortcuts and buttons to run and to cancel
if it's not supported -  ubuntu pop up ui, and ask the user if he want to report about it, if the user select yes he will get mail at the time it will be support

---

### Post by smartboyathome on 2008-02-01
I wouldn't say add it by default (space, space, space), but if it is not in the repos, put it in there.

---

### Post by 23meg on 2008-02-01
[https://bugs.launchpad.net/ubuntu/+bug/103791](https://bugs.launchpad.net/ubuntu/+bug/103791)

---

### Post by graabein on 2008-02-01
Wow running old PS2 discs on Ubuntu would be fabulous!! I was not aware of this emulator. Thanks!!

---

### Post by Mr.mouse on 2008-02-01
the problem is with the BIOS, 
is it possible to add the BIOS to the sources ?
or create a new one with reverse engineering (i think it's a small file) ?

---

### Post by 23meg on 2008-02-01
Read the comments in the bug I linked to.

---

### Post by barius on 2008-02-01
> **Mr.mouse said:**
> the problem is with the BIOS, 
is it possible to add the BIOS to the sources ?
or create a new one with reverse engineering (i think it's a small file) ?

No.  There is no open-source BIOS, you must dump one from a PS2.  Since the PS2 BIOS is copyright of Sony, it is only legal for you to use the BIOS dumped from a PS2 that *you own*.  Further, each BIOS contains a unique identifier that is used when you log onto the Sony online services.  So, for example, if you use the same BIOS as someone else Sony will know immediately that your BIOS has been pirated and can ban you.

There has been some recent work on creating an open-source BIOS, but it is not even capable of booting yet.

BTW, for installation of PCSX2 see this thread:
[http://ubuntuforums.org/showthread.php?t=631979&highlight=pcsx2](http://ubuntuforums.org/showthread.php?t=631979&highlight=pcsx2)

There is also a .deb package that was created recently, though I haven't tried it myself:
[http://ubuntuforums.org/showthread.php?t=671260&highlight=pcsx2](http://ubuntuforums.org/showthread.php?t=671260&highlight=pcsx2)

---

