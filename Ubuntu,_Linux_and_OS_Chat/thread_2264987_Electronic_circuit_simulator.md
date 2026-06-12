---
title: "Electronic circuit simulator"
date: 2015-02-11
forum: Ubuntu, Linux and OS Chat
---

### Post by thealchemist886 on 2015-02-11
Hi there, I am an student, and I'm needing an electronical circuit simulator, when using an old wine version I could emulate "Electronics Workbench" but with the latest beta build it seems I can't, (program loads but buttons don't work properly) so I'm searching for a good linux native aplication to simulate electronical circuits, I recently tried oregano, but it just don't have much components, and I'm needing a lil more complete program, so I'm asking here for help. The thing would be a Multisim alternative for Linux, I also used to use Ktechlab, a program I really liked it, very simple useful and complete, but it isn't aviable for this Ubuntu build, and since I'm very "noob" I couldn't compilate it correctly.

Thanks alot.

---

### Post by v3.xx on 2015-02-11
> I also used to use Ktechlab, a program I really liked it, very simple useful and complete, but it isn't aviable for this Ubuntu
There's a .deb package here.  Hasn't been updated though.
[http://sourceforge.net/projects/ktechlab/](http://sourceforge.net/projects/ktechlab/)

There are a few simulators here.
[https://help.ubuntu.com/community/UbuntuEngineering#Electronics](https://help.ubuntu.com/community/UbuntuEngineering#Electronics)
[http://en.wikipedia.org/wiki/List_of_free_electronics_circuit_simulators](http://en.wikipedia.org/wiki/List_of_free_electronics_circuit_simulators)

I do not use them, so thats all the help I can be. Good luck

---

### Post by thealchemist886 on 2015-02-13
Yeah, I know that there's a package but it does simply not work I get the error, "Can't satisfy dependence: kdelibs4c2a (>=4:3.5.5-1)"

---

### Post by tgalati4 on 2015-02-13
Looks like you need to install version 4 of the KDE libraries.

> tgalati4@Mint17 ~ $ apt-cache policy kdelibs4c2a
kdelibs4c2a:
  Installed: (none)
  Candidate: (none)
  Version table:
tgalati4@Mint17 ~ $ apt-cache search kdelibs
kdelibs-bin - core executables for KDE Applications
kdelibs5-data - core shared data for all KDE Applications
kdelibs5-dbg - debugging symbols for the KDE Development Platform libraries
kdelibs5-dev - development files for the KDE Development Platform libraries
kdelibs5-plugins - core plugins for KDE Applications
krosspython - Python module for Kross


---

### Post by Mike_Walsh on 2015-02-13
Hallo, there.

I don't know whether these would be of any use to you at all, but there are two similar apps available in the Software Centre.

They are:-

1) Cirkuit, and
2) QElectroTech.

Just enter the names in the searchbox, at the top right corner of the Software Centre.

Hope that helps.


Regards,

Mike. ;)

---

### Post by thealchemist886 on 2015-02-16
I won't do anything with that, they are only circuit drawers, I need one to simulate electronical circuits. As k tech lab, and I was not able to install the old KDE libraryes because, after that the it needs even more discontinued libraryes.

---

### Post by steeldriver on 2015-02-16
Well there's ngspice in the repositories - there are various graphical front ends, although tbh I tried easyspice a while back and found it annoying and ended up just writing the netlist(s) manually, which was sufficient for the simple examples I needed at the time

---

### Post by Warren Hill on 2015-02-18
Not native Linux software but LTspice runs well under wine on Ubuntu and probably most other Linux platforms too.

---

### Post by Mike_Walsh on 2015-02-19
> **Warren Hill said:**
> Not native Linux software but LTspice runs well under wine on Ubuntu and probably most other Linux platforms too.

Yep; Warren's quite right. Works very well. I've just downloaded and tried it out. I use Wine, ver. 1.7.23 myself, mainly for one Windows graphics application that I just cannot find an equivalent for in terms of functionality (not without using 3 or 4 other programs.....which seems a bit silly).

Runs without ANY problems that I can find. I think it'll fit the bill. Definitely worth a look.....it's got the coveted 'Platinum' rating.


Regards,

Mike. :)

---

### Post by hamnstar on 2015-02-19
I havn't found a simulator nearly as featured as the software my university lab used.  I typically use [http://easyeda.com](http://easyeda.com) for quick, "proof of concept" type simulations

---

### Post by Mike_Walsh on 2015-02-21
> **hamnstar said:**
> I havn't found a simulator nearly as featured as the software my university lab used.  I typically use [http://easyeda.com](http://easyeda.com) for quick, "proof of concept" type simulations

Just given this a try, too. VERY easy to use.....and it's web-based, which means you can access your diagrams anywhere, as long as you create an account. I would recommend this one.

You can even order your PCBs ready made up, to YOUR design....once you've checked that it works as you want it to. Excellent idea.

Give it a look.

Regards,

Mike. :)

---

