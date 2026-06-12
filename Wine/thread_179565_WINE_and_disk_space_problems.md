---
title: "WINE and disk space problems"
date: 2006-05-20
forum: Wine
---

### Post by johso on 2006-05-20
Hiya folks!

First of all, I tried to search Google and this forum, but without luck. But if somebody could throw a link or something, I'd be happy.

Anyhoo, I've just installed Steam and ran into the problem that I seem to forget everytime I think about installing Half-Life 2 on my machine: WINE counts free disk space on my home drive **only**.
I want to install the games on my fat32 partition, where there's loads of space, but in Steam it's not possible since it's led to believe that there's only 1.5GB free space (by WINE).
Is there any way around this?
(Except for freeing up disk space on my home drive, it's quite impossible. Only 7.5GB)

---

### Post by Nikusan on 2006-05-22
[QUOTE=johso]Hiya folks!

First of all, I tried to search Google and this forum, but without luck. But if somebody could throw a link or something, I'd be happy.

Anyhoo, I've just installed Steam and ran into the problem that I seem to forget everytime I think about installing Half-Life 2 on my machine: WINE counts free disk space on my home drive **only**.
I want to install the games on my fat32 partition, where there's loads of space, but in Steam it's not possible since it's led to believe that there's only 1.5GB free space (by WINE).
Is there any way around this?
(Except for freeing up disk space on my home drive, it's quite impossible. Only 7.5GB)[/QUOTE]


run winecfg and on the drives tab create a drive that maps to your fat32 partition.

---

### Post by johso on 2006-05-22
I've tried that, but it doesn't help me. See, the Steam install thinks that it is installed on my home drive, and thus counts the space available there. And of course, there's no option to ignore the disk space problem.

---

### Post by leotemp on 2008-05-06
I am having this exact problem, did anyone figure out a solution to this?

---

### Post by Intangir on 2009-02-20
im having the same problem

my root directory has only 2.3
my home directory is a seperate partition with a ton more

but its reporting the space available (on Z) as that of roots, even though Z:/home/intangir is my other partition with plenty, thats where steam is..


is there a way to just fool wine into just saying theres enough space?

---

### Post by Intangir on 2009-02-20
i figured out a solution for my situation

i made a new symlink inside my wine dir

/home/intangir/.wine/drive_z/home/intangir -> /home/intangir

then i changed the Z path in winecfg from / to /home/intangir/.wine/drive_z/home/intangir

now it shows the size as being my home directory

---

### Post by NightMKoder on 2009-02-20
You may have some luck by changing the WINEPREFIX env variable. See [http://forum.winehq.org/viewtopic.php?t=209](http://forum.winehq.org/viewtopic.php?t=209) (but don't use their approach). wineprefixcreate has been deprecated, so when you try to install your game - do it through console, and do something like:

env WINEPREFIX="/media/otherDriver/.wine" wine setup.exe

I'm not sure whether this will actually work. Also you may need to change your shortcuts once they are created to use this prefix.

---

### Post by johso on 2009-02-20
> **Intangir said:**
> i figured out a solution for my situation

i made a new symlink inside my wine dir

/home/intangir/.wine/drive_z/home/intangir -> /home/intangir

then i changed the Z path in winecfg from / to /home/intangir/.wine/drive_z/home/intangir

now it shows the size as being my home directory

Simple, yet powerful solution, Intangir ;-)
It's been forever since I tried this, can't recall exactly how, but I remember I solved it somehow. The game ran like crap though, because I had an ATi card. So it was a lot of trouble for pretty much nothing :-P

But thanks for sharing!

---

