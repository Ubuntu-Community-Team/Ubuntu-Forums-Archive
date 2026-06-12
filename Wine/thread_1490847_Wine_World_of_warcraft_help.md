---
title: "Wine World of warcraft help"
date: 2010-05-22
forum: Wine
---

### Post by Jharder on 2010-05-22
So I used the install file from when i was using the windows version. I installed it and everything was ok. I tried to boot it up with wine and I got a black screen. I am an Ubuntu Noob and some people said some things about the graphic card drivers. I check mine and it was a "Intel Corporation Mobile 4 series Chipset Integrated Graphics Controller (rev 07)". I have no Idea if I need to update it or where to begin doing so. Please help me!

PS. And please make it Noob Friendly :)

---

### Post by Ozymandias_117 on 2010-05-22
You can type the command ```
glxgears
``` into a terminal to make sure your 3D OpenGL drivers are there and working.

---

### Post by emanuel.b on 2010-05-22
> **Jharder said:**
> So I used the install file from when i was using the windows version. I installed it and everything was ok. I tried to boot it up with wine and I got a black screen. I am an Ubuntu Noob and some people said some things about the graphic card drivers. I check mine and it was a "Intel Corporation Mobile 4 series Chipset Integrated Graphics Controller (rev 07)". I have no Idea if I need to update it or where to begin doing so. Please help me!

If I were you, I'd check out the Wine HQ apps database.

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

Also, it could be that you're running 64 bit. WOW is a 32 bit application. Only Windows 64 bit has the libraries in place to run 32 bit software. If you want to play WOW, you need to downgrade to 32 bit Ubuntu/Kubuntu/Xubuntu. Sorry :(

---

### Post by Jharder on 2010-05-23
Ill try the code below as well just in case. Still clinging to hope.
glxgears

PS. The Code Worked. Thank you  Ozymandias 117! You are my hero! I owe you.[URL="http://ubuntuforums.org/member.php?u=805682"]
[/URL]

---

### Post by Jharder on 2010-05-23
New Problem.... It work but needed to download updates. After they finished it tried to boot up the loader and froze. I forced the aplication closed and tried to reopen WoW using terminal. I was prompted with the screen below. Any more advice :P ?

wine "C:\Program Files\World of Warcraft\WoW.exe"
err:module:attach_process_dlls "comctl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000005

---

### Post by Elfy on 2010-05-23
moved to Wine

---

### Post by hikaricore on 2010-05-23
For future reference, being able to run glxgears proves almost nothing.
A better test would have been a native title that utilizes opengl heavily after first checking the output of glxinfo to be sure direct rendering is enabled...

---

### Post by Ozymandias_117 on 2010-05-23
> **hikaricore said:**
> For future reference, being able to run glxgears proves almost nothing.
A better test would have been a native title that utilizes opengl heavily after first checking the output of glxinfo to be sure direct rendering is enabled...

It's helped me realize there was a problem with a gfx kernel module that had been compiled and loaded, but apparently was broken somehow.

---

### Post by Jharder on 2010-05-23
Since I am a complete Noob :) what would be the next step? Thanks for the time and help by the way. I really apreciate it everyone.

---

### Post by emanuel.b on 2010-05-23
> **emanuel.b said:**
> If I were you, I'd check out the Wine HQ apps database.

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

Also, it could be that you're running 64 bit. WOW is a 32 bit application. Only Windows 64 bit has the libraries in place to run 32 bit software. If you want to play WOW, you need to downgrade to 32 bit Ubuntu/Kubuntu/Xubuntu. Sorry :(
It seems that what I said just flew over everyone's head...

---

### Post by dardack on 2010-05-23
> **emanuel.b said:**
> If I were you, I'd check out the Wine HQ apps database.

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

Also, it could be that you're running 64 bit. WOW is a 32 bit application. Only Windows 64 bit has the libraries in place to run 32 bit software. If you want to play WOW, you need to downgrade to 32 bit Ubuntu/Kubuntu/Xubuntu. Sorry :(

Not completely true.  Wine is 32 bit (unless you run the 64bit wine but that's not recommended as it's development isn't that far along) that runs in 64bit Ubuntu/linux/etc.  I know I'm doing it right now.

For reference:

[http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit")

and

[http://wiki.winehq.org/Wine64]("http://wiki.winehq.org/Wine64")

From that page:

This page is for notes on the 64-bit port of Wine for AMD64 (a.k.a. x64 or x86-64). This port is just beginning to work, but is not yet fully functional. Only people who are planning to fix the code will want to compile Wine like this.

---

### Post by Jharder on 2010-05-24
So I suffered through screens that i could barely see anything at all and was able to do all the patches. Now it starts up (takes a little bit though) and works. Then I just turned the graphics quality down because it was lagging. Now it works fine. No downgrading needed (sweet!). Thanks for the help everyone and the time you put into helping me!

---

