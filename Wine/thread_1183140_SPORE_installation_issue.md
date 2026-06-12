---
title: "SPORE installation issue"
date: 2009-06-09
forum: Wine
---

### Post by ninja_numbnuts on 2009-06-09
Whenever I try to install it, I get as far as in the picture and then it just stays on the blue screen!

Any ideas?

---

### Post by NightMKoder on 2009-06-09
[http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111) the "Things to include when asking for help" section.

---

### Post by ninja_numbnuts on 2009-06-09
> **NightMKoder said:**
> [http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111) the "Things to include when asking for help" section.

Ok thanks!

I'm using WINE 1.1.23 on Ubuntu 9.04 32Bit. 

My PC is;
AMD Athlon x2
2GB RAM
GeForce 8800GTS using driver 185.18.14 (the newest driver).

I don't know how to get a Terminal output for something I have to run off a DVD, maybe the command please?

---

### Post by NightMKoder on 2009-06-09
The terminal output is basically what you see when you type the command. To start something in wine, cd to it (change directory), and type 'wine filename.exe'. I'm guessing in your case it's going to be something like:

cd /media/cdrom
wine Setup.exe

If you want to get fancy (so you don't have to copy paste from the terminal):

wine Setup.exe 2>&1 | tee terminal.log

which stores your output in terminal.log and shows it to you.

---

### Post by ninja_numbnuts on 2009-06-09
> **NightMKoder said:**
> The terminal output is basically what you see when you type the command. To start something in wine, cd to it (change directory), and type 'wine filename.exe'. I'm guessing in your case it's going to be something like:

cd /media/cdrom
wine Setup.exe

If you want to get fancy (so you don't have to copy paste from the terminal):

wine Setup.exe 2>&1 | tee terminal.log

which stores your output in terminal.log and shows it to you.

Thanks, this is the readout;

crash2k@crash2k-desktop:~$ cd /media/cdrom
crash2k@crash2k-desktop:/media/cdrom$ wine SPOREsetup.exe
crash2k@crash2k-desktop:/media/cdrom$ fixme:storage:StgCreateDocfile Storage share mode not implemented.
fixme:reg:GetNativeSystemInfo (0x3328ac) using GetSystemInfo()
err:seh:setup_exception_record stack overflow 816 bytes in thread 0019 eip 7bc43f98 esp 00241000 stack 0x240000-0x241000-0x340000

---

### Post by NightMKoder on 2009-06-09
Did you by any chance install something else (winetricks/other programs) into this prefix? That stack overflow isn't pretty.

Try it with a clean wine prefix (ie delete .wine in your home folder, which erases all your apps), or start wine on a different prefix, like:

WINEPREFIX="$HOME/.wine_spore" wine Setup.exe

---

### Post by ninja_numbnuts on 2009-06-09
It worked ok in WINE 1.1.22, and WarCraft III installed flawlessly!

Should I perhaps retry installing 1.1.23, and if that fails, fall back to 1.1.22?

---

### Post by regor210 on 2009-06-09
You could try installing it with PlayOnLinux.
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by NightMKoder on 2009-06-09
> **ninja_numbnuts said:**
> It worked ok in WINE 1.1.22, and WarCraft III installed flawlessly!

Should I perhaps retry installing 1.1.23, and if that fails, fall back to 1.1.22?

Your _installation_ failed under 1.1.23? That. Is. New. 

Could you report it under bugs.winehq.org? People will tell you what to put down after you report it.

---

### Post by ninja_numbnuts on 2009-06-09
> **NightMKoder said:**
> Your _installation_ failed under 1.1.23? That. Is. New. 

Could you report it under bugs.winehq.org? People will tell you what to put down after you report it.

Lol!
I just re installed 1.1.22 and it installed perfectly! 
Guess it's a WINE bug. How do I post bug reports to WineHQ?

---

### Post by NightMKoder on 2009-06-09
[http://bugs.winehq.org/](http://bugs.winehq.org/) click new.

---

### Post by Wiebelhaus on 2009-06-09
> **regor210 said:**
> You could try installing it with PlayOnLinux.
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

Yes! or [Codeweavers]("http://www.codeweavers.com/").

---

### Post by ninja_numbnuts on 2009-06-09
> **NightMKoder said:**
> [http://bugs.winehq.org/](http://bugs.winehq.org/) click new.

Thanks, posting now.

---

### Post by ninja_numbnuts on 2009-06-09
Ummmmmm?

Can someone please explain all of this?

---

### Post by NightMKoder on 2009-06-09
> **ninja_numbnuts said:**
> Ummmmmm?

Can someone please explain all of this?

for version pick 1.1.23, your component is most likely msi, alias leave empty, url is if you have a link to the bug (you can leave it as it is). Summary is like a title, and a description is well, a description. Just write what you did and what happened and that it doesn't happen in 1.1.22.

---

### Post by ninja_numbnuts on 2009-06-09
> **NightMKoder said:**
> for version pick 1.1.23, your component is most likely msi, alias leave empty, url is if you have a link to the bug (you can leave it as it is). Summary is like a title, and a description is well, a description. Just write what you did and what happened and that it doesn't happen in 1.1.22.

Thanks again :)

I posted it as best as I can for now!

Here it is;

[http://bugs.winehq.org/show_bug.cgi?id=18878](http://bugs.winehq.org/show_bug.cgi?id=18878)

---

