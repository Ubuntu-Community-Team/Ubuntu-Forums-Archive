---
title: "Firefox and Flash have not worked together since Breezy"
date: 2007-03-17
forum: The Cafe
---

### Post by SZF2001 on 2007-03-17
(I'm not sure where to put the thread, sorry guys.)

I'm not sure exactly what it is, really. Back in '05, I remember getting this "Ubuntu thing" and things seemed to just work (like Cannon. works toward, right?).

Then Dapper came. Awesome, hooray, time to upgrade everything...

Suddenly the flash plugin doesn't seem to want to work. I'd go to a flash page like Youtube, watch a movie, then the browser froze after the movie.

It's 2007. Since then, we've been given official packages from Adobe themselves for better Flash support (it's Flash 9, now, right?), but Firefox still seems like it wants to freeze.

I've tried almost every damn trick on these forums. Adding lines to Flash related text config files, changing browsers (Opera is NOT cutting it for me, sorry), changing the xorg file for 32/24/16 bit screen resolution...

It's been TWO YEARS without Firefox and Flash working together. Did I miss a vital step here? I've downloaded and installed the nonfree package... isn't that all your supposed to do? Any other packages to keep Firefox from freezing?

It's not just this computer, either. I installed Fiesty on my laptop - it's the EXACT same on it. Flash will work for a while, then Firefox will start crashing EVERY TIME there is something Flash related.

Double you tee eff.

---

### Post by karellen on 2007-03-17
I don't know what to say, for me flash works well with firefox. I installed it via easyubuntu and that was it. I can view youtube videos without any glitches

---

### Post by Guus on 2007-03-17
maybe you should reinstall the flash-nonfree package via synaptic 

just search for "flash" :)


Flash also works fine for me

---

### Post by SZF2001 on 2007-03-17
I have. I have done it through Synaptic countless times, I have done it on the command line with both apt-get and aptitude, I have tried my own build of Firefox (Not Ubuntu's version) and do it that way... This is through the course of years, mind you.

I've also done it on Kubuntu and Xubuntu, even Fluxbuntu, through all those different ways to go it with different tweaks... I can never get a working flash plugin ever ever.

---

### Post by bruce89 on 2007-03-17
I'm reasonably happy with Epiphany and gnash here, I seem to remember firefox crashing an awful lot.

---

### Post by SZF2001 on 2007-03-17
Every time I try Epiphany, it lists itself under the Games section with the Applications menu... And then when I try it in a terminal, it won't open.

Maybe if I got Epiphany to work with Gnash I would be set free?

---

### Post by bruce89 on 2007-03-17
> **SZF2001 said:**
> Every time I try Epiphany, it lists itself under the Games section with the Applications menu... And then when I try it in a terminal, it won't open.

You are installing the Epiphany game, install the packages epiphany-browser and epiphany-extensions to get the browser.

---

### Post by forcesofhabit on 2007-03-17
You might have Gnash installed. When I had Gnash installed my Firefox would crash quite frequently.

---

### Post by Somenoob on 2007-03-17
The flash plugin is completely flawless here.

---

### Post by corbeau on 2007-03-17
Hi everyone
I did some reading and it appears that Adobe Flash 9.0 does not support 64 bit. I have the latest version of Firefox for Linux and I understand it is meant for 64 bit.

I have AMD 64 live (dual core) in my machine and it appears that only GNASH can do the thing on the latest version of Mozilla Firefox. 
Could someone help me, I am newbee and when I get to the repository, I have like five packages there, some dev, some plugin, some finish in tar.gz some in deb. 
I download these things, extract them, follow installation instructions and get error messages. 
I sort of understand I need to package something but I have no clue how.

Compute freely as you breathe while supplies last.

Cheers,

---

### Post by SZF2001 on 2007-03-18
Tonight I thought of doing something - and OH MY FREAKING GOD, IT WORKED!!!!!!111

I went and checked through Synaptic for any Flash library packages, any Gnash packages, anything NOT relating to the nonfree package.

I left one package I always thought I had to use (since aptitude told me so) called libflash0c2. I left it installed, and tried Flash again with Firefox. Erch, boozle, crash.

I removed the package... And there hasn't been a single crash since. Holy crap on a stick. Aptitude lied to me.

---

### Post by corbeau on 2007-03-18
So, you have installed flash 9.0, is that it ?

ZFS2001 You said:
[PHP]I left one package I always thought I had to use (since aptitude told me so) called libflash0c2. I left it installed, and tried Flash again with Firefox. Erch, boozle, crash.

I removed the package... And there hasn't been a single crash since.[/PHP]

My question is the following: I do what you did on UBUNTU 6.10 64bit and then download the ADOBE package and it will work ?

Sorry if this not clear, I am green at this....

---

