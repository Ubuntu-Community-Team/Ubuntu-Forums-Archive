---
title: "Booting on ancient hardware"
date: 2005-02-06
forum: The Cafe
---

### Post by jnoreiko on 2005-02-06
I've seen a few links on this forum to distros that will work on old hardware (DSL and Beatrix both looked interesting), but how do you get round an old BIOS that can't boot off a CD?
What about ancient CD drives that don't read CD-R?

The other thing is, the ultra-light distros go back as far as pentium and fast 486, just about. What about machines even older than that? What's the linux equivalent of Windows 3?

---

### Post by miho on 2005-02-06
I booted Slackware 9.1 off a computer that used Windows 3 previously. Ubuntu could work but it'd be minimal settings.
Could you give us the specifications of the computer you want to install Linux on?

---

### Post by poofyhairguy on 2005-02-06
[QUOTE=jnoreiko]I've seen a few links on this forum to distros that will work on old hardware (DSL and Beatrix both looked interesting), but how do you get round an old BIOS that can't boot off a CD?
What about ancient CD drives that don't read CD-R?

The other thing is, the ultra-light distros go back as far as pentium and fast 486, just about. What about machines even older than that? What's the linux equivalent of Windows 3?[/QUOTE]

Debian. With the thinnest desktop manager around. So probably DSL.

---

### Post by Zundfolge on 2005-02-06
I tried to install Ubuntu on an old computer at work (Pentium 133) ... it wouldn't start the GUI because it had a Diamond Stealth 64 video card.

---

### Post by az on 2005-02-06
"tried to install Ubuntu on an old computer at work (Pentium 133) ... it wouldn't start the GUI because it had a Diamond Stealth 64 video card."

The installer assumes a lot about video hardware and defaults just about always to 24-bit video.  Try changing that to 15 bit (or less, depending on what your hardware supports)


"but how do you get round an old BIOS that can't boot off a CD?"

There is a utility floppy around that boots, detects any cdrom or usb stick and allows you to boot from them.  
Here:
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)


"What about ancient CD drives that don't read CD-R?"

Cdrom drives are cheap.



"What's the linux equivalent of Windows 3?"

Good question.  It depends on what you take into consideration.  I think the linux kernel only needs something like 4 megs of ram to run.  It may be more for the 2.6 but I m pretty sure about the 2.4 kernels.  Ubuntu uses an intrd (initial ram disk) which loads a filesystem into memory and runs things there to detect hardware and stuff.  This takes up a lot of memory, but you can compile your own kernel and not use one.
So, even the newest, latest kernel can still run as lean as windows 3.1.  You will have tons more supported hardware like usb, too.
If you mean the graphical user interface, well X windows does take up a lot of ressources.  You will need more than 32 megs of memory for it to run well.  You can install a lighter window manager like Icewm, fluxbox or fvwm.
Light file managers include Rox-filer (which includes a pinboard option to actually give you a desktop) or xfe.

With debian, you have tons of choice.  If you are interested, you could spend a month tweaking your installation (apt-getting) and discovering WindowMaker, (I won't name them all.  You have many of the debian packages available to you in the Universe repository.

Basically, you install the ubuntu base system by using the custom option after you boot the installer and then just apt-get the packages you want from the command line.

for example:
apt-get install x-window-system-core xterm icewm menu xfe abiword gdm mc mozilla-firefox
that should take up about 500 megs of disk space or so (It will tell you before it installs)

---

### Post by jnoreiko on 2005-02-07
[QUOTE=miho]Could you give us the specifications of the computer you want to install Linux on?[/QUOTE]

There's a Pentium 133MHz, 64MB ram and 220MB HD. My mother uses it, and she basically just wants to be able to play AisleRiot, the solitaire game (and maybe some of the other games that came with Ubuntu). OpenOffice would be good too, but not essential.
Then there's an AMD K6-2 500MHz, 64MB RAM, HD is something like 12 gig. My father would like to dual boot Win98 and linux on that, and run OpenOffice and that sort of thing.

Thanks for the smart boot link, azz :)

---

### Post by miho on 2005-02-07
Use Really Small Linux.

---

### Post by poofyhairguy on 2005-02-07
[QUOTE=jnoreiko]There's a Pentium 133MHz, 64MB ram and 220MB HD. My mother uses it, and she basically just wants to be able to play AisleRiot, the solitaire game (and maybe some of the other games that came with Ubuntu). OpenOffice would be good too, but not essential.
Then there's an AMD K6-2 500MHz, 64MB RAM, HD is something like 12 gig. My father would like to dual boot Win98 and linux on that, and run OpenOffice and that sort of thing.

Thanks for the smart boot link, azz :)[/QUOTE]

Here is the link you need.

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

If I was you though, I would shell out the small amount of cash it takes to add some ram to those puppies. Especially the second one- it would be able to run a full install like a dream with 256mb of ram.

---

### Post by Reb on 2005-02-09
I find twm to be a very nice window manager. Pretty light.

---

### Post by landotter on 2005-02-10
[QUOTE=poofyhairguy]- it would be able to run a full install like a dream with 256mb of ram.[/QUOTE]
 
 seconded.
 
 LInux has a high ram overhead because of X so memory is hugely important, processor speed much less so. 133mhz is pretty pokey, but I used to run Suse on a 200mhz/128mb box and it was great.
 
 BTW, do try Beatrix linux instead of Ubuntu. It's based on Ubuntu and is a Live CD that installs to the HDD. It's a lot lighter than Ubuntu, but just as "pretty". I'm on vacation and using it now.
 
 After it's installed you can use apt to grab aisle riot or whatever else you need.
 
 The download is only 200mb!!! Gnome 2.8, Openoffice. Firefox, and Gaim. Pretty much that's all you get to begin with. Elegant and runs like a champ. Ubuntu is lean--Beatrix is gaunt--but not so much as to impose something like fluxbox or xfce on a linux noob--that's harsh. :lol:
 
 [http://www.watsky.net](http://www.watsky.net)

---

### Post by Shaga on 2005-02-17
[QUOTE=landotter]seconded.
 
 LInux has a high ram overhead because of X so memory is hugely important, processor speed much less so. 133mhz is pretty pokey, but I used to run Suse on a 200mhz/128mb box and it was great.
 
 BTW, do try Beatrix linux instead of Ubuntu. It's based on Ubuntu and is a Live CD that installs to the HDD. It's a lot lighter than Ubuntu, but just as "pretty". I'm on vacation and using it now.
 
 After it's installed you can use apt to grab aisle riot or whatever else you need.
 
 The download is only 200mb!!! Gnome 2.8, Openoffice. Firefox, and Gaim. Pretty much that's all you get to begin with. Elegant and runs like a champ. Ubuntu is lean--Beatrix is gaunt--but not so much as to impose something like fluxbox or xfce on a linux noob--that's harsh. :lol:
 
 [http://www.watsky.net](http://www.watsky.net)[/QUOTE]
 I am making a debian kios browser machine with debian and fluxbox.

Specs:
Pentium 100mhz
64mb ram
1mb vga card(pci)
3com isa

Works like a charm ;) fast and furious..

---

### Post by Shaga on 2005-02-17
I am making a debian kios browser machine with debian and fluxbox.

Specs:
Pentium 100mhz
64mb ram
1mb vga card(pci)
3com isa

Works like a charm ;) fast and furious..

---

