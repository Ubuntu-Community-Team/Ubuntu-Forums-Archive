---
title: "Server Platform suggestions!"
date: 2010-12-17
forum: Server Platforms
---

### Post by ductiletoaster on 2010-12-17
I have used Ubuntu and other Debian distros for many years now.... I have used server editions and Desktop editions... 

As of right now i use ubuntu 10.04 LTS desktop edition for all my programming and web development. However Im not goin to lie I think Ubuntu is getting a little to bloated and Im I am kinda looking for an alternative.

So I wanted to see what other people use for there server distros and how they implement a gui if they do at all?

O I should probably also say I am very very comfortable with linux and in fact use it on all but one of my four computers. I know termial very well so please give me your input

---

### Post by Vegan on 2010-12-17
I have used a range of junk machines for Linux fine.

Currently my Linux box is styling with the Acer T320 PC I have at present.

I was using an even older machine before I got the T320

Of course a more capable machine could used if performance matters.

---

### Post by wojox on 2010-12-17
Personally I use Debian Lenny for my server. Command line install. I ssh in from Fedora 14.

I've seen this question a lot. It's usually recommended to install a server/cli  distro and use [Webmin]("http://www.webmin.com/") instead of a GUI.

I've always just used a server/cli without Webmin. It's taught me a lot about unleashing the full power of Linux. ;)

---

### Post by ductiletoaster on 2010-12-17
I was more referring to the OS which linux distro and what software. I should have specified sorry...

I too have use a wide variety of machines though. One I have right now and in fact was my first linux server... (cant seem to let it go :)) is and old emachines with:

196 MB (Upgraded) used to be 128 of RAM
667MHZ AMD processor 
15GB hard drive

The machine has worked like a dream! though I have replaced it with my more modern 3.2GHZ AMD 2GB RAM and 1.25 TB for my server!

I Have used TEXT only even without a web based admin but Lately i have found my self needing windows on my new machine for some specific software and so For alot of my development I like to use a simple gui for programming and what not.... and thus the need for a server with a gui!

---

### Post by cariboo on 2010-12-17
I put together a server earlier this year, it's running 10.04.1 server version, and it really is overkill for what I use it for. It's main job is serving files internally, but it has enough resources to run a couple of virtual appliances I use for development/testing.  There is no gui on the system, and everything is accessed remotely. The systems uses an Intel dual core E5400 cpu and 2Gb ram along with 4Tb of storage. Currently with one VM running and serving files to a system running XBMC the cpu is bouncing between 0 and .2% and memory usage sits at 654Mb, and thats with 512Mb allocated to the VM.

I also have an old Apple G3 running Debian stable, that only plays mp3s, it runs headless with no gui, and normally uses about 20Mb ram, although the 350Mhz cpu is running at about 20% usage. It gets turned on every morning when I get to work, and is shutdown at closing time, otherwise it's so trouble free I usually forget about it.

---

### Post by ductiletoaster on 2010-12-17
Very nice! So for some one who would need a gui what would u suggest. As I said I dont really like how Ubuntu-desktop packages comes with all this stuff (some of which cant be uninstalled without removing the whole thing. I I have been looking at Linux Mints newish Fluxbox edition the problem its not 32 bit.

I prefer Debian based distros.... Though I want to use a the best distro for server applications. Ur your guys opinion what do u think that is?

---

### Post by wojox on 2010-12-18
Have a look at [Crunchbang]("http://crunchbanglinux.org/") 

It recently switched to Debian from Ubuntu and uses Openbox.

---

### Post by ductiletoaster on 2010-12-18
Hmm I like it.. I was thinking of going back to debian...I think I switched from Debian to Ubuntu back when Ubuntu was in the 4's or 5's haha so maybe its time to go back the the roots!

---

### Post by spynappels on 2010-12-19
I use both Ubuntu and CentOS, I'm relatively new to CentOS but moved to it to give me more experience with a RHEL-derived OS, but Ubuntu Server is still working well for me in both text and text/Webmin incarnations in lots of production locations.

---

