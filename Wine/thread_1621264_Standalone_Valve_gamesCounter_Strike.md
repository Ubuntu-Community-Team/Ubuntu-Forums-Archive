---
title: "Standalone Valve games/Counter Strike?"
date: 2010-11-14
forum: Wine
---

### Post by WonderousIce on 2010-11-14
Hi.

I'm hoping I find anyone who can help me, I've dug the internet for an answer but found nothing.

I'm trying to create a shortcut to run an exe file WITH PARAMETERS.
E.g. I'm trying to make a shortcut of hl.exe to play Condition Zero (I know, old time gamer).

And keep in mind, this is standalone. Non-steam.

Is it possible to run that exe with parameters (e.g. "hl.exe" -steam -nomaster... etc) using Wine?

Any help would be appreciated. Thanks!

---

### Post by Sugi on 2010-11-14
I also had this same question a long time ago, and I thought I got it working... But I can't find any notes on it.  I'll get back to you when I find the answer...

Sugi

---

### Post by WonderousIce on 2010-11-16
Thanks..

But I really wanna know how is it possible to do this, so..


Bump.

---

### Post by mastablasta on 2010-11-16
**4.3. How should I start Windows programs from the command line?**
 
 
This will allow you to see messages from Wine that may help troubleshoot problems. 
Because Windows programs will often look for files in the location they were started from, when using the command line you should start them in a very specific way: "change directory" to the folder where the program is located and run the .exe file using **only** its filename. For example: 
 
Code:
```
 
cd '.wine/drive_c/Games/Tron'wine tron.exe

```In some cases you may wish to specify the full path to the program's .exe file. For example, if you need to install a program from multiple CDs, the previous method won't work (entering the directory in the terminal will prevent you from removing the CD). You can provide Wine with a DOS or Windows style path inside single quotes like so: 
 
Code:
```
 
wine start 'C:\Games\Tron\tron.exe'

```from: [[COLOR=#444444]http://wiki.winehq.org/FAQ#run_from_terminal[/COLOR]]("http://wiki.winehq.org/FAQ#run_from_terminal")
 
 
You need to use wine start if you specify a full path, because that allows Wine to set the working directory for the program if it needs it. You can also use double quotes, but you need two backslashes instead of one: 
 
Code:
```
 
wine start "C:\\Games\\Tron\\tron.exe"

```If you need to use a Unix style pathname, use the /Unix option to start, e.g. 
 
Code:
```
 
wine start /Unix "$HOME/installers/TronSetup.exe"

```For current Wine, once a program is installed, you can safely use any shortcuts that the installer has created.

---

### Post by WonderousIce on 2010-11-16
Interesting..

This should be able to help.

Would the command "wine start" help me add arguments/parameters to the exe I'm about to run?


Thanks for the help!

Edit: Actually I figured out from what you've said.
The **wine** command followed by a path in single quotes can be dealt with as I was using Windows (Windows-Style).
Therefore parameters can indeed be put after the path.
And it worked. Finally found my way.

Thank you. That was VERY helpful.

---

