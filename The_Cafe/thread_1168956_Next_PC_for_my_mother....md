---
title: "Next PC for my mother..."
date: 2009-05-24
forum: The Cafe
---

### Post by bryonak on 2009-05-24
Just saw that DisplayLink has [released their source code]("http://www.desktoplinux.com/news/NS3167589970.html") under LGPL, which reminded me of a nice wish thought I had before...

Take [this here]("http://linuxdevices.com/news/NS9634061300.html"), add an USB hub + DisplayLink monitor + USB keyboard/mouse + USB printer, plug in an ethernet cable and there you go!
Who needs CDROMs these days? The rest is all there.

Just wish the SheevaPlug had PowerLine networking, but it's all already awesome as it is! Makes a very good home server/NAS (just add an external 1TB USB drive ;)).

---

### Post by logos34 on 2009-05-24
wow, interesting...to think it has nearly the specs of a entry-level Mac-mini from four years ago! (minus the dvdrom of course).

but how do you manage with only one usb port and 512 MB internal flash storage? Can you run three usb via hub on one port? (keyboard+mouse, display, extra usb stick, portable audio player)

---

### Post by bryonak on 2009-05-25
> **logos34 said:**
> Can you run three usb via hub on one port? (keyboard+mouse, display, extra usb stick, portable audio player)

Yep, I recently ran two mice, one wireless receiver for a keyboard and an external drive over one USB hub.

512 MB flash storage should be more than enough for DamnSmall or Puppy with Firefox, OpenOffice (or maybe rather AbiWord), etc... but in case you want to run Ubuntu, just plug in a bigger SD card ;)
You could also attach an external USB drive, but then you might get problems with the performance of two high-bandwidth devices (drive and monitor).

---

### Post by logos34 on 2009-05-25
neat idea...I love these green-machines...talk about a power miser...just really really neat...I wish I could build one for myself...I've been thinking about how much total overkill computers are for websurfing...hate to tell you what my 19" crt consumes...and I wish I could trade in my 62W cpu for a 35W model or better...But a computer that uses 5W is just too good to be true...i agree about NAS/server--ideal use for it.  Just leave it on, never have to reboot, just flick on the monitor.

---

### Post by kernelhaxor on 2009-05-25
Thanks for sharing, I didn't know about that sheeva plug, looks interesting!

> **bryonak said:**
> Yep, I recently ran two mice, one wireless receiver for a keyboard and an external drive over one USB hub.

512 MB flash storage should be more than enough for DamnSmall or Puppy with Firefox, OpenOffice (or maybe rather AbiWord), etc... but in case you want to run Ubuntu, just plug in a bigger SD card ;)
You could also attach an external USB drive, but then you might get problems with the performance of two high-bandwidth devices (drive and monitor).

I highly doubt if it can run Firefox, OpenOffice .. it has no GPU and I doubt if that CPU can take that much load .. have you tried installing Damnsmall or puppy ?  I doubt if it'll even install on that architecture

I am guessing it has a highly stripped down linux kernel and can only do CLI .. one can still do awesome things with that!

---

### Post by Xbehave on 2009-05-25
Not sure if it has enough power for a full destkop, mother friendly, pc. 
Also AFAIK software support on ARM isn't great as there is no official firefox, etc

That said i ram kde3 on a celeron (1.6GHZ with 512MB ram), storage may be a problem but you could always stick in a USB pen
512 is more than enough for /(500m) (my / + /var use add up to 406MB) and a small fast swap (12mb?)
add an external 8Gb usb-pen for /usr(3.5G), /home, /tmp(256?) (this is where flash videos are kept i found 100mb wasn't enough), swap(512) (optionally dont bother with a sperate /tmp just mount it to ram and make swap bigger)

I read that poweline networking was a royal PITA, as it messes up radio signals in the house and isn't too great for network speeds either!

---

### Post by Xbehave on 2009-05-25
> **kernelhaxor said:**
> I highly doubt if it can run Firefox, OpenOffice .. it has no GPU and I doubt if that CPU can take that much load Whats the deal with arm and graphics ? does it have absolutely nothing or will it have something akin to inbuilt intel graphics (which is enough for firefox but not compiz)

---

### Post by bryonak on 2009-05-25
> **kernelhaxor said:**
> 
I highly doubt if it can run Firefox, OpenOffice .. it has no GPU and I doubt if that CPU can take that much load .. have you tried installing Damnsmall or puppy ?  I doubt if it'll even install on that architecture

I am guessing it has a highly stripped down linux kernel and can only do CLI .. one can still do awesome things with that!

Marvell, the manufacturer of that neat device, says they've been running Ubuntu and Fedora (among others) on it, though presumably the alternate install.
But you're right about DSL/Puppy, I always forget about their being quite limited in terms of supported architectures.

On the other hand, a 400 MHz Pentium2 on a very old mainboard with integrated graphics is capable of running Firefox on Debian... scrolling is laggy, but it's usable.
I think a lightweight Ubuntu install (Crunchbang?) could work on the plug... but I have no reason to buy a DisplayLink montior at the moment (except for curiosity that is), so I won't be able to tell for sure in the near future.
And there are lighter browsers of course... as soon as Dillo gets full CSS support (hopefully this summer), it'll be an awesome ultralightweight Firefox replacement.


> **Xbehave said:**
> Whats the deal with arm and graphics ? does it have absolutely nothing or will it have something akin to inbuilt intel graphics (which is enough for firefox but not compiz)

I don't think they had DisplayLink (or anything similar) in mind when they designed the plug. So you'll probably have to rely solely on the CPU... which is quite a beastie nevertheless.

---

### Post by andrewabc on 2009-05-25
If you are looking for something small, just get an [ASUS EeeBox](http://event.asus.com/eeepc/microsites/eeebox/en/index.html)

Good if you are looking for something small and cheap. Mostly good for web browsing and other small tasks. Faster than what is shown in original post.

---

### Post by kernelhaxor on 2009-05-25
> **bryonak said:**
> Marvell, the manufacturer of that neat device, says they've been running Ubuntu and Fedora (among others) on it, though presumably the alternate install.


thats great!  I wanna see what all it can run.  
Have you bought one?
I'd buy but I really don't know what I'd do with it now.  Its great for network based software services like NAS but I don't have a need now.

It has good CPU and RAM but that one single USB would become a bottleneck if you connect a display, keyboard and mouse (not even sure if that's possible)

---

### Post by logos34 on 2009-05-25
no graphics processor? Looking at the diagram again it seems the cpu handles everything  except network (separate gigabit ethernet controller)

if it would limit you to sth like puppy linux, not sure it's that great after all...

---

### Post by pushbx on 2009-06-03
You can most certainly run openoffice on the sheeva plug.  I have freeNX server running on it and I could run firefox, pan and openoffice without any problems.  The sheeva also runs my website, mythtv backend and nfs.  Its a lot more powerful than you think it is.

btw, the sheeva plug comes with ubuntu 9.04 pre-installed.  The way I got openoffice and firefox to work is

> apt-get install openoffice.org firefox

yeah, that's really it.

Take a look here for all that it can do:

[http://computingplugs.com/index.php/Main_Page](http://computingplugs.com/index.php/Main_Page)

---

### Post by gn2 on 2009-06-03
An Acer Revo (Hornet in the US) is a vastly better choice than a Sheeva plug.

---

### Post by logos34 on 2009-06-03
> **gn2 said:**
> An Acer Revo (Hornet in the US) is a vastly better choice than a Sheeva plug.

makes me want to build a micro SFF-based desktop box

---

### Post by gn2 on 2009-06-03
> **logos34 said:**
> makes me want to build a micro SFF-based desktop box

You'll struggle to do it cheaper than an Acer Revo, but there are definitely some interesting options available.

---

### Post by logos34 on 2009-06-03
yeah, it seems almost impossible to find a case small enough (micro-atx is smallest)...The acer is nice, but I'd prefer to build my own if possible

---

### Post by gn2 on 2009-06-03
Plenty options [here]("http://www.mini-itx.com/store/?c=3#8k01").

---

### Post by logos34 on 2009-06-03
hey, neat, I was looking at newegg

---

### Post by anantkamath on 2009-06-23
> **pushbx said:**
> Yo btw, the sheeva plug comes with ubuntu 9.04 pre-installed. 


Did you buy 'the development kit' or any other version ?
and how did you connect a monitor?

---

