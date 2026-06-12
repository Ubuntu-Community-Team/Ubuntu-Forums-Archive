---
title: "Breezy on a Compaq Proliant 6000 - LVM not recognized?"
date: 2005-12-10
forum: Server Platforms
---

### Post by hostile on 2005-12-10
I was wondering if anyone knows if the Compaq Smart Arrays are supported by Debian/Ubuntu.

I'm trying to get Breezy onto a ProLiant 6000 with a Smart-2DH controller.

I was under the impression that the 2.2.x kernels and above supported the Compaq controllers.

Everything goes fine during the install, but upon reboot, I get:

```

ALERT! /dev/ida/c0d0p1 does not exist! Dropping to a shell!

```

CentOS installs and runs just fine, as does FreeBSD 6.0 (I thought I'd try it), so I'm wondering if Debian/Ubuntu has something wierd going on in terms of it's kernel drivers?

Any insight would be helpful.

---

### Post by Carzzzer on 2005-12-10
Hi

I have exact same problem om Proliant 1850R with SmartArray 221... it installs and everything, but upon first boot it stops as you describe.

I dropped the SmartArray 221 for now and installed the harddrive on the on-board SCSI controller instead... that works

EDIT: Woohooo!  :D

Look what I found: 

[http://sourceforge.net/projects/cciss](http://sourceforge.net/projects/cciss)
[http://sourceforge.net/projects/cpqarray](http://sourceforge.net/projects/cpqarray) 

Also check out [http://opensource.compaq.com](http://opensource.compaq.com)

---

### Post by hostile on 2005-12-11
Well, as sad as this is to say, for some reason, Ubuntu does not build in the driver for the Smart Array.

I plopped in my Debian (Sarge) CD, and everything worked beautifully.

Pretty weak if you ask me, considering I was using my Ubuntu "Server" install CD...

---

### Post by Thearnold on 2005-12-27
[QUOTE=hostile]Well, as sad as this is to say, for some reason, Ubuntu does not build in the driver for the Smart Array.

I plopped in my Debian (Sarge) CD, and everything worked beautifully.

Pretty weak if you ask me, considering I was using my Ubuntu "Server" install CD...[/QUOTE]

I am doing an upgrade to breezy from horay and it bombed on my Compaq Proliant 6000,but I have the ES 3100 controller. I used the the Breezy 5.10 live cd to start recovery and it did not load the compaq array driver by default, but I was able to do sudo modprobe cpqarray and get the array driver to load.  I am currently recovering my files on the os partition and going to install a fresh copy of breezy over my failed horay breezy upgrade on my server and see what happens!

-TheArnold

---

### Post by mavman on 2006-03-22
[QUOTE=Carzzzer]Hi

I have exact same problem om Proliant 1850R with SmartArray 221... it installs and everything, but upon first boot it stops as you describe.

I dropped the SmartArray 221 for now and installed the harddrive on the on-board SCSI controller instead... that works

EDIT: Woohooo!  :D

Look what I found: 

[http://sourceforge.net/projects/cciss](http://sourceforge.net/projects/cciss)
[http://sourceforge.net/projects/cpqarray](http://sourceforge.net/projects/cpqarray) 

Also check out [http://opensource.compaq.com](http://opensource.compaq.com)[/QUOTE]


Hi There!

Any chanche you could give me a walk-through on installing these drivers?

I'm a Windows admin so I feel kinda stupid now, but it would be nice if I could get this old piece of junk (A dual CPU Proliant 6000 with a DH array controller) working again for a website or whatever.

I'm currently in the busybox, I just dropped to the shell.

all help is appriciated..

Mav.

---

