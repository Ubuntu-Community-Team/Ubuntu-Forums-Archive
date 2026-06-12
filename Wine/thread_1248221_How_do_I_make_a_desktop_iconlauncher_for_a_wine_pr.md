---
title: "How do I make a desktop icon/launcher for a wine program with special run commands?"
date: 2009-08-23
forum: Wine
---

### Post by lockaar on 2009-08-23
**EDIT: Thanks to Marlonsm the problem has been resolved!**

**FIXED!**





I have installed Guild Wars under WINE and it runs wonderfully if I launch it using the debug command:
```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe"
```Also I can place specific "switches" to the end of that line of code to implement specific settings, for instance the following would launch the game in windowed mode and also force it to use DirectX 8 as opposed to newer DirectX versions:
```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -windowed -dx8
```I am pretty new to Ubuntu and all of the terminal commands, how do I go about creating a desktop icon or a launcher which will use the above command to launch the game? This is opposed to launching the game through the WINE menu in which none of these specific switches can be applied.

Any help would be greatly appreciated!

---

### Post by lockaar on 2009-08-25
Bump - Is there anybody who can help me with this, I'm sure this very complicated, but I tried making a "launcher" and failed.

---

### Post by Marlonsm on 2009-08-25
It's pretty easy actually.
If it's in the Wine menu, just drag it to your desktop.
If it's not, right click your desktop > Create launcher, give it a name, put that command, choose an icon and you're good to go.

BTW, if it doesn't work, there is a way, I'm not really sure about how to do it, but you need to create a file with that command in and save it as executable. I'm sure someone will explain better...

---

### Post by lockaar on 2009-08-25
> **Marlonsm said:**
> right click your desktop > Create launcher, give it a name, put that command, choose an icon and you're good to go.


I just tried this, and I placed ```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -windowed
``` in the "command" section and with its type set to "application" I get the error "Details: Failed to execute child process "WINEDEBUG=-all" (No such file or directory)"

I also cannot get it to work if I set the type to "application in terminal".

Any ideas?

**EDIT: I fixed it**! I pulled the icon to the desktop and edited the command line in there, for some reason that worked whereas creating my own launcher didn't. **Thank you for the help Marlonsm!!**

---

### Post by cnbiz850 on 2010-10-03
> **lockaar said:**
> 
**EDIT: I fixed it**! I pulled the icon to the desktop and edited the command line in there, for some reason that worked whereas creating my own launcher didn't. **Thank you for the help Marlonsm!!**

This is very strange.  Happens to me and I don't understand.  What is the difference between an icon in the menu and one created from scratch?

---

