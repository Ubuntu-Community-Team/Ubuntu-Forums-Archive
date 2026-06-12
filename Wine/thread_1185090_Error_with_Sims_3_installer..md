---
title: "Error with Sims 3 installer."
date: 2009-06-11
forum: Wine
---

### Post by MetroidJunkie2008 on 2009-06-11
"Error Number: 0x80040708 Unable to create required engine components, check whether you have appropriate privileges to create COM components. (0x80004005)"

I hear it has to do with administration privileges and I made sure the Wine folder was writable, no luck.

---

### Post by NightMKoder on 2009-06-11
Wine version? Log? Read sticky on before posting.

---

### Post by MetroidJunkie2008 on 2009-06-11
My bad. 

Ubuntu 9.04 on Windows XP mode, I have DX9 installed with Winetricks, shows to be Windows native.


Windows version: 1.1.23
Log:

fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 300, std (d/m/y): 25/10/2009, dlt (d/m/y): 8/03/2009
fixme:reg:GetNativeSystemInfo (0x33f10c) using GetSystemInfo()
fixme:storage:StgCreateDocfile Storage share mode not implemented.
err: ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000000

---

### Post by NightMKoder on 2009-06-11
Not cool. Don't install directx, it comes built into wine. I suggest deleting your wine prefix (rm -Rf .wine - it'll also remove your other programs), and trying installing again.

---

### Post by MetroidJunkie2008 on 2009-06-11
It's kind of doing the same thing as before, I don't think that really did anything. Same log, same error. :?

---

### Post by BoilerPL on 2009-06-12
Hi, you must install Sims3 in wine 1.1.22 then u can update to 1.1.23

---

### Post by MetroidJunkie2008 on 2009-06-12
> **BoilerPL said:**
> Hi, you must install Sims3 in wine 1.1.22 then u can update to 1.1.23


You are awesome. It installed, but now it's giving a "serious problem" message when I try to run it.

---

### Post by BoilerPL on 2009-06-12
Try run it from TS3.exe

---

### Post by MetroidJunkie2008 on 2009-06-12
> **BoilerPL said:**
> Try run it from TS3.exe


Nevermind, it's working now. It must've been an error with the net framework. I think I have a new problem, though. I patched the exe file with the no cd patch and the launcher still says no disc found. The actual exe file replaced gives an error, saying the application attempted to load the c runtime library incorrectly. =\

---

### Post by BoilerPL on 2009-06-12
Try to get another TS3.exe file. I have 28,4MB file and it's working without cd

---

### Post by MetroidJunkie2008 on 2009-06-12
> **BoilerPL said:**
> Try to get another TS3.exe file. I have 28,4MB file and it's working without cd

This time, I used PlayonLinux's installer. It got past the cd requirement, but now it crashes while loading Sun Valley.

Terminal contents:

Assertion at ..\..\mono\mono\metadata\icall.c:5454, condition `err' not met


Yes, it's the official game.

---

### Post by MetroidJunkie2008 on 2009-06-13
Any suggestions to get beyond the crash?

---

### Post by BoilerPL on 2009-06-14
Sorry i can't help you, dont have that error.

1. install game with wine 1.1.22
2. upgrade to wine 1.1.23
3. replace oryginal TS3.exe with 28,4MB TS3.exe
4. strart game from TS3.exe and play.

Try to install vcrun2005sp1, .net2.0 and directx from winetricks.

---

### Post by MetroidJunkie2008 on 2009-06-14
> **BoilerPL said:**
> Sorry i can't help you, dont have that error.

1. install game with wine 1.1.22
2. upgrade to wine 1.1.23
3. replace oryginal TS3.exe with 28,4MB TS3.exe
4. strart game from TS3.exe and play.

Try to install vcrun2005sp1, .net2.0 and directx from winetricks.


I don't think using Wine will stop the game from crashing. You sure I should get Directx from winetricks? I hear the built in one in Wine is superior, anyway.

---

### Post by orlox on 2009-07-20
MetroidJunkie2008, I found a hack that allows you to play the game and skip the error you have when the town is loading. You can read more about it here:

[http://bugs.winehq.org/show_bug.cgi?id=18991](http://bugs.winehq.org/show_bug.cgi?id=18991)

However, the workaround I found is an ugly hack, so lets expect that the wine developers get aware of this issue and found a clean way of implementing this. Still, if you want to play the game, you can use my hack ant it will work flawleslly.

---

### Post by directhex on 2009-07-21
> **MetroidJunkie2008 said:**
> This time, I used PlayonLinux's installer. It got past the cd requirement, but now it crashes while loading Sun Valley.

Terminal contents:

Assertion at ..\..\mono\mono\metadata\icall.c:5454, condition `err' not met


Yes, it's the official game.

Bug 18991

---

