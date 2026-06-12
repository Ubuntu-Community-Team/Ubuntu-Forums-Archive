---
title: "Tearing apart .exe files"
date: 2009-06-01
forum: Wine
---

### Post by crusaderbond on 2009-06-01
In windows, when I wanted to pull apart an exe, I just typed this into the command prompt

filename.exe /A /P C:\<path>

this overrides the command to run the executable, and just dumps all of its bits into a folder.

I've found that this doesn't work in wine. I have several .exes that run in wine, but that I cannot pull apart with cabextract or 7zip or winrar, or anything I find suggested.

I am either looking for the place wine dumps its temp when running .exes, or a command like the one above. I don't have windows anymore.

Thanks in advance

---

### Post by asdfoo on 2009-06-01
> **crusaderbond said:**
> In windows, when I wanted to pull apart an exe, I just typed this into the command prompt

filename.exe /A /P C:\<path>

this overrides the command to run the executable, and just dumps all of its bits into a folder.

I've found that this doesn't work in wine. I have several .exes that run in wine, but that I cannot pull apart with cabextract or 7zip or winrar, or anything I find suggested.

I am either looking for the place wine dumps its temp when running .exes, or a command like the one above. I don't have windows anymore.

Thanks in advance

wtf?  I think you mean you have a specific program, whose name you want to keep secret, which accepts commandline parameters /A /P C:\<path>

Otherwise you are confused.

---

### Post by whoop on 2009-06-01
Why don't you just use a hex editor or a disassembler?

---

### Post by norgeek on 2009-06-01
use winrar it works in wine ;)

---

### Post by YokoZar on 2009-06-01
Command line switches are a bit different in Wine because of the way the Linux terminal handles escaped characters.  There's an entry on this somewhere in the Wine FAQ I think.

---

### Post by crusaderbond on 2009-06-09
Thank you all for your input!

I hadn't heard of disassemblers before, but I'm playing with one now. 

The switches after your executable name are triggers in the program that executes executables, that tell it to dump the contents to a folder rather than run the code within. It always works.

Thankyou, and sorry I took so long to get back.

---

### Post by lisati on 2009-06-09
> **crusaderbond said:**
> 

The switches after your executable name are triggers in the program that executes executables, that tell it to dump the contents to a folder rather than run the code within. It always works.



wtf? :confused: The switches given don't do that with the MS-DOS and Windows programs I've written...:confused:

---

### Post by Rufe0 on 2009-06-09
yeah doesn't work for me never heard of it

---

