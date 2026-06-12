---
title: "How to run .Exe files and play games"
date: 2009-04-30
forum: Ubuntu Gamers Arena
---

### Post by ravensfx on 2009-04-30
I have copied a folder of Need for speed underground 2 to the desktop of ubuntu, but cant it to run the .exe file, it just tries to run it in its own type on WinZip.

Do i need to install or change anything before i can play or run games on the system? if so what?

any help appreciated

Raven

---

### Post by yota on 2009-04-30
Hi ravensfx,

.exe files are windows binaries; they can natively run only on windows.

So like you run OSX software on macs you should run Linux software on Ubuntu.

This said there are a number of ways to run windows software on ubuntu though emulation or virtualization, but keep in mind that this can have limits on compatibility/performance/ease of use and requires some degree of experience to be succesfully accomplished.

The most game-geared solution for this purpose is the commercial [http://www.transgaming.com/](http://www.transgaming.com/)

The best free software solution is wine, which is available in the official ubuntu repositories.

As a personal suggestion, which you can feel free to ignore and without the intention to be harsh, I wouldn't recommend an unexperienced user to go through the added complexity of running windows games on ubuntu.
IMHO is best to use windows and linux side by side running software on the native platform, while eventually searching alternatives on the other side.

Hope this helps!

---

### Post by Kareeser on 2009-04-30
Unfortunately, according to the Application Database for WINE, Need for Speed Underground 2 does not run well on Linux.

---

### Post by Sliiice on 2009-05-03
I know I am new but is it possible to extract the script from an .exe and just use a linux compiler. From my knowledge alot of things are the children of C/C++. a .exe is a compiled C++ script...

---

### Post by DuneSoldier on 2009-05-03
> **Sliiice said:**
> I know I am new but is it possible to extract the script from an .exe and just use a linux compiler. From my knowledge alot of things are the children of C/C++. a .exe is a compiled C++ script...

Sorry, you can't do that. It doesn't have a script that you can extract. You can decompile the binary, but that's just about useless. There isn't anything wrong with the game itself, Wine's libraries just don't support it well.

---

### Post by Sliiice on 2009-05-03
Well the idea is that if you decompile a .exe you get something in Assembly. I know not many people know assembly but disregarding the game is it possible to use the code if some one knows Assembly to produce a different form of code? Like decompiling a C# and using that code (with changes) and making it C++?

---

