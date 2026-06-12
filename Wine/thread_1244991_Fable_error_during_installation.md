---
title: "Fable error during installation"
date: 2009-08-20
forum: Wine
---

### Post by Desktop_n00b on 2009-08-20
Ok 1st, I am very sorry for posting this in the wrong forum, I am new and didn't read the rules (my fault) so I did not see the thread that said there was a wine forum.


			 		   		 		 		So I have been looking around and have found a lot of stuff on how to install it on ubuntu 8.10 but little on Ubuntu 9.04, and little on errors during the installation.


When I type in the product key and press ok it says "Error loading the PID generator DLL. The DLL could not be found!" does anyone know how to fix this?

I went to wine HQ and the latest fix was for 8.10 so does that also apply for 9.04? and if it does is there possibly a new way to fix it for 9.04 that might not lose the sound?

---

### Post by Desktop_n00b on 2009-08-20
bump

---

### Post by myromance123 on 2009-10-10
I'm sorry if this is a little too late but this MIGHT help you. (I hope this isn't going against any rules? The .dlls are provided free by that site legally it seems).
 
 From what I've read, it would seem that error means you are missing an mfc42.dll file.

 Download mfc42.dll from [here]("http://www.dll-files.com/dllindex/pop.php?mfc42").
Then copy the dll and paste it in your ~/.wine/drive_c/windows/system32 folder. If you don't know where that is, click Places->Home Folder and then click View and Show Hidden Files and go down until you see a folder named .wine and from there follow the above directory to the System32 folder.
 Now try and type in your CD-Key, it should work now (at least it did for me). I hope this helps :)


More information on this problem I obtained from experiencing this with another game. It fixed the problem (although the solution is for Windows Gamers, it can be done under Wine as well as I have tried).
> The pidgen.dll has a 'dependacy' on the mfc42.dll - which both reside in C:\Windows\System32 DIR (or should) & in C:\Windows\ServicePackFiles\i386

Well, on the computer that wasn't allowing me to install (one would other wouldn't) the mfc42.dll was missing from the C:\..\System32 DIR - so a simple copy & paste from the C:\Win...\Service..\i386 and it started working.

---

### Post by beastrace91 on 2009-10-10
> **Desktop_n00b said:**
> I went to wine HQ and the latest fix was for 8.10 so does that also apply for 9.04? 

The fix for 8.10 *should* also work in 9.04

~Jeff

---

### Post by macdhuibh on 2010-03-13
Works in 9.10 also.

---

