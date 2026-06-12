---
title: "Oblivion doesn't work."
date: 2009-01-16
forum: Wine
---

### Post by renatozink on 2009-01-16
Hi guys. I have read through the forum and also google, and I am still not able to install Oblivion on my computer. I am completely new to Ubuntu, so I really don't have much experience in using it. I am trying to install GOTY version in Oblivion. I also read through [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux) and some parts were easy to understand, but I got stuck in many parts of it. Which I do not know if I don't have the correct commands for the terminal or not. Like I said, I am new to this and I am not a programmer either.

I got stuck in:

"export WINEPREFIX=/path/to/your/OblivionWine"
it  doesn't say anything after that one.

Setup Wine for running Oblivion
I typed "winecfg" and says
"wine client error:0: version mismatch 0/378.
your wineserver binary was not upgraded correctly, or you have an older one somewhere in your PATH. Or maybe the wrong wineserver is still running?"

of course I also got stucked in some more, but those are the first ones, if anyone could please answer me and explain me how to do it. I will be thankful. 

Renato

---

### Post by beastrace91 on 2009-01-16
It sounds like your wine install is messed up. How did you go about installing it/ have you tried any other programs with it?

~Jeff

---

### Post by renatozink on 2009-01-16
No I have not tried any other programs. I will try another program and see what happens

---

### Post by renatozink on 2009-01-16
I tried different games and I still can't install them. it says I don't have the applications to read .exe .cab .isn .inx .dll and some others. 

Can someone help me?

---

### Post by beastrace91 on 2009-01-17
Yea your Wine install is messed up, how did you try to install it? I would remove it and reinstall it at any rate, hopefully that should help.

~Jeff

---

### Post by renatozink on 2009-01-17
I installed the ubuntu version 8.10 and also the packages. It let me go all the way till the end of the page [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux), but at the end when I type wine setup.exe in the terminal, it outputs this:

renato@Ares:/media/cdrom$ wine setup.exe
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xeda520,0x00000004,0xeda51c) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xed940c): Stub!
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  442
  Current serial number in output stream:  442

Do you know what it means? I learned the commands for Linux, but I still don't understand what seems to be the problem.

---

### Post by hikaricore on 2009-01-17
This isn't WINE related:

> X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 442
Current serial number in output stream: 442

You need to install/configure your video drivers.  :p

What video hardware do you have?

---

