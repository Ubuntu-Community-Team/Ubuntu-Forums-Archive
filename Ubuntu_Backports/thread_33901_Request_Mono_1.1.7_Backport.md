---
title: "Request: Mono 1.1.7 Backport?"
date: 2005-05-12
forum: Ubuntu Backports
---

### Post by sebgate20 on 2005-05-12
Hi All

I'm using Mono 1.1.6 from backports (which I am glad is now in the main from staging  :) ) but I was wondering, can you (or is it being done) port Mono 1.1.7 back to Hoary?

I use Beagle, Tomboy, F-Spot and Mono a lot so the speed improvements in 1.1.7 wouldn't go a miss!

Keep up the good work.

Seb

---

### Post by rwabel on 2005-05-14
would really be nice to have 1.1.7 in backport

---

### Post by jdong on 2005-05-14
working on it.

---

### Post by rwabel on 2005-05-15
[QUOTE=jdong]working on it.[/QUOTE]
 thanks again for the backporting. I really appreciate your work and all the others doing backports.

---

### Post by Gandalf on 2005-05-15
sorry for this stupid question, but what mono is for????

---

### Post by jdong on 2005-05-15
Uploaded last night.


Mono is like .NET, only free & open source & cross platform. There are some cool new stuff, like Beagle, that uses Mono.

---

### Post by mangar on 2005-05-15
after ugrading mono to 1.1.7, 
blam got broken (can't update the rss feeds)
there's no output at all when running the program from the command-line.
so i can't provide any other useful information.
thanks in advance!

(beagle still works ok, btw)

---

### Post by rwabel on 2005-05-15
[QUOTE=mangar]after ugrading mono to 1.1.7, 
blam got broken (can't update the rss feeds)
there's no output at all when running the program from the command-line.
so i can't provide any other useful information.
thanks in advance!

(beagle still works ok, btw)[/QUOTE]
 what version of blam are you using? Version 1.80 works fine for me with mono 1.1.7

---

### Post by Gandalf on 2005-05-15
[QUOTE=jdong]Uploaded last night.


Mono is like .NET, only free & open source & cross platform. There are some cool new stuff, like Beagle, that uses Mono.[/QUOTE]
 hmmmmm i don't know anything about those apps hmmmmmmmm... *-)
will try beagle to see what it is good for and blam too

---

### Post by mangar on 2005-05-15
blam 1.6
(the version in the repo's)
is there an alternative deb?

---

### Post by rwabel on 2005-05-15
[QUOTE=Gandalf]hmmmmm i don't know anything about those apps hmmmmmmmm... *-)
will try beagle to see what it is good for and blam too[/QUOTE]
 give also muine (music player) and f-spot (photo management)

---

### Post by rwabel on 2005-05-15
[QUOTE=mangar]blam 1.6
(the version in the repo's)
is there an alternative deb?[/QUOTE]
 no, I compiled it from source. Give it the new version a try to see if it works with mono 1.1.7

---

### Post by mangar on 2005-05-15
configure fails, as it doesn't find mozilla. 
i don't have it installed, and version 1.6 worked fine without it.
the relevant compile error:

checking which mozilla to use... configure: error: no mozilla installation found

is there any way around this?
(btw, firefox is installed)

thanks in advance!

---

### Post by rwabel on 2005-05-15
[QUOTE=mangar]configure fails, as it doesn't find mozilla. 
i don't have it installed, and version 1.6 worked fine without it.
the relevant compile error:

checking which mozilla to use... configure: error: no mozilla installation found

is there any way around this?
(btw, firefox is installed)

thanks in advance![/QUOTE]
 you need mozilla to successfully compile it. I've it installed too,  even if I don't need it, because several applications require mozilla for compiling.

you can install the missing packages, compile it and afterwards remove the one you don't want to have on your system.

---

