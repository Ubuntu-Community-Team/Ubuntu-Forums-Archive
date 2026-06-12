---
title: "No Mountable File Systems"
date: 2013-08-12
forum: Virtualisation
---

### Post by raf3 on 2013-08-12
I am trying to open the Ubuntu 12.04 iso.dmg, and this disk image error appears: ubuntu-12.04.2-desktop-amd64.iso (no mountable file systems).

VirtualBox Manager says:Runtime error opening '/Users/username/VirtualBox VMs/Ubuntu 12.04/Ubuntu 12.04.vbox' for reading: -102 (File not found.)./Users/vbox/tinderbox/4.2-mac-rel/src/VBox/Main/src-server/MachineImpl.cpp[725] (nsresult Machine::registeredInit()).
[TABLE]
[TR]
[TD]Result Code: 
[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)
[/TD]
[/TR]
[TR]
[TD]Component: 
[/TD]
[TD]Machine
[/TD]
[/TR]
[TR]
[TD]Interface: 
[/TD]
[TD]IMachine {22781af3-1c96-4126-9edf-67a020e0e858}
[/TD]
[/TR]
[/TABLE]

Here's my Computer Information: Model Name:	Mac mini  Model Identifier:	Macmini6,2
  Processor Name:	Intel Core i7
  Processor Speed:	2.3 GHz
  Number of Processors:	1
  Total Number of Cores:	4
  L2 Cache (per Core):	256 KB
  L3 Cache:	6 MB
  Memory:	16 GB
  Boot ROM Version:	MM61.0106.B03
  SMC Version (system):	2.8f0
  Serial Number (system):	
  Hardware UUID:	070222B8-FE73-5875-8471-E2121E8119E7

Any help with this matter would be appreciated, and thanks for your time and consideration.

---

### Post by Boab1993 on 2013-08-12
First things first, your running an intel system and are trying to mount an amd image.

---

### Post by raf3 on 2013-08-12
Thanks for your reply there Boab1993. Too bad the iso file doesn't recognize what computer one has and install accordingly, eh? Well, I'm going to try this on my own, as you didn't provide a download link for the appropriate image needed for an intel systems. Thanks anyway though...

---

### Post by Boab1993 on 2013-08-12
Apologies i was in a rush earlier and was just making a daily browse.

I don't know if you need a specfic image type for your software but your Intel image for CD install(12.04) is available here: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Sorry if i sounded callous, was just running out the door.

---

### Post by raf3 on 2013-08-12
No worries Boab1993, and thanks for your prompt reply.

---

### Post by raf3 on 2013-08-12
Man Boab1993. I went to the site that you provided, burned a copy to CD, and still get, "no mountable file systems". I downloaded PC (intel x86)
 
[COLOR=#000000][FONT=Ubuntu]For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.

Not sure whats going on here, so please enlighten me. Thanks...[/FONT][/COLOR]

---

### Post by Boab1993 on 2013-08-12
It appears to be a corrupt .dmg file.

Im not a Mac wiz so ill redirect you to a few help pages on the probelm: 

[http://data-recovery-software-articles.blogspot.com/2010/11/how-to-solve-no-mountable-file-systems.html](http://data-recovery-software-articles.blogspot.com/2010/11/how-to-solve-no-mountable-file-systems.html)

[https://discussions.apple.com/thread/3801444?start=0&tstart=0](https://discussions.apple.com/thread/3801444?start=0&tstart=0)

I hope this helps you, stay vigilant.

---

### Post by raf3 on 2013-08-12
Once again Boab1993 I thank you for your prompt reply, and it looks like I got some work to do based on the links that you provided. And yes, vigilance is key...

---

