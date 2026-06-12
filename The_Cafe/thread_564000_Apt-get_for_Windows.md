---
title: "Apt-get for Windows?"
date: 2007-09-30
forum: The Cafe
---

### Post by corney91 on 2007-09-30
I came across this article and thought it was quite interesting:[http://www.pcworld.com/article/id,136454-c,opensource/article.html]("http://www.pcworld.com/article/id,136454-c,opensource/article.html")
It describes a program that does the same thing as apt-get, but for windows. IMO it won't take off as the majority of windows users don't like to use the command line, so anyway, opinions anyone?

Here's the link to the program:[Win-Get]("http://windows-get.sourceforge.net/")

---

### Post by Polygon on 2007-09-30
nice! i will definitely try this out

---

### Post by Crashmaxx on 2007-09-30
Sounds pretty crappy. Seems it can't even update itself, much less anything it installs. Still have to go through all the next options or just hope the defaults work.

---

### Post by n3tfury on 2007-09-30
dumb.  no sense in this at ALL.  only nerds might find it neat, most everyone else will not care.

---

### Post by corney91 on 2007-09-30
I think it's a step in the right direction. If it sorts out the update thing and adds a GUI, it would be more appealing though. I'd definately prefer it over .exe's.

---

### Post by n3tfury on 2007-09-30
> **corney91 said:**
> I think it's a step in the right direction. If it sorts out the update thing and adds a GUI, it would be more appealing though. I'd definately prefer it over .exe's.

explain to me how it's a step in the right direction for windows.

---

### Post by Frak on 2007-09-30
> **n3tfury said:**
> dumb.  no sense in this at ALL.  only nerds might find it neat, most everyone else will not care.
Hey now, this is one of my favorite programs on Windows, it makes such things as codec installation much easier.

win-get install klite /s

> **corney91 said:**
> I think it's a step in the right direction. If it sorts out the update thing and adds a GUI, it would be more appealing though. I'd definately prefer it over .exe's.
I'm thinking of taking win-get and[ Winpackman]("http://www.winpackman.org/") to merge them into a Synaptic like app.

---

### Post by n3tfury on 2007-09-30
> **Frak said:**
> Hey now, this is one of my favorite programs on Windows, it makes such things as codec installation much easier.

win-get install klite /s

again, only nerds will get anything out of this.  nothing wrong with being a nerd, but this will not become popular by any means.

---

### Post by Billy_McBong on 2007-09-30
[COLOR="Blue"]unless it is installed by default i don't think it will be used much[/COLOR]

---

### Post by Wiebelhaus on 2007-09-30
WAIT! HOLD THE PRESS!


you mean I could set up a script to install the 2452435243 billionty freaking craplets I have to install on the dozens of windows installs I have to do a week?

omg e-gasm.

---

### Post by corney91 on 2007-09-30
> **n3tfury said:**
> explain to me how it's a step in the right direction for windows.

Well, I know that when I switched to linux (from windows), I loved the fact that all the programs where in one place, easy to install. And I'm sure other people find it easier as well. Also after some improvements, I doubt there will be many things different to the package managers on linux, and we all love them;-)

---

### Post by n3tfury on 2007-09-30
> **corney91 said:**
> Well, I know that when I switched to linux (from windows), I loved the fact that all the programs where in one place, easy to install. And I'm sure other people find it easier as well. Also after some improvements, I doubt there will be many things different to the package managers on linux, and we all love them;-)

one place?  you must mean synaptic.  you need to realize most windows users aren't about to ditch their mouse and type ANYTHING in the command line to get programs.  not gonna happen.

---

### Post by FuturePilot on 2007-09-30
This is a really cool thing. :)

---

### Post by corney91 on 2007-09-30
> **n3tfury said:**
> one place?  you must mean synaptic.  you need to realize most windows users aren't about to ditch their mouse and type ANYTHING in the command line to get programs.  not gonna happen.

Nah, I meant the default repositories, not much else needed than those. And to be honest, there's not that much typing involved, especially if a GUI was developed.

> **Frak said:**
> 
I'm thinking of taking win-get and[ Winpackman]("http://www.winpackman.org/") to merge them into a Synaptic like app.

Sounds cool, I'd be interested to see your reults.

---

### Post by Polygon on 2007-09-30
> **sx66gns said:**
> WAIT! HOLD THE PRESS!


you mean I could set up a script to install the 2452435243 billionty freaking craplets I have to install on the dozens of windows installs I have to do a week?

omg e-gasm.

exactly my point.

and i can care less if its 'a step in the right direction', it looks like its going to help me deal with having to use windows

---

### Post by capink on 2007-10-01
A good package management requires a good package format to start with, something like debian packages. A good package has everything hardcoded  into it so that it does not modify files after installing them. One can try to port debian package format to windows (specially for open source programs), but will be confronted with a big obstacle called the registry. Instead of hardcoding the settings of the program in the package (it is a matter of placing a file in /etc), the package manager would have to modify the registry at install and uninstall time, which is not optimal I think.

---

### Post by fynlam on 2007-10-01
it would definately be an imporvement. but its easier to install software on windows and remove it also, althoug maybe not completely remove it. so i don't see a great advantage for it over dling an exe, except maybe to write a .bat file to install things automatically.

---

### Post by jinx099 on 2007-10-01
I tried this out a few months ago and I can say from personal experience that it is worthless.  All it does is download an exe (usually outdated even) from the vendors site and starts the installer for you.

Pointless.

---

### Post by Frak on 2007-10-01
> **capink said:**
> A good package management requires a good package format to start with, something like debian packages. A good package has everything hardcoded  into it so that it does not modify files after installing them. One can try to port debian package format to windows (specially for open source programs), but will be confronted with a big obstacle called the registry. Instead of hardcoding the settings of the program in the package (it is a matter of placing a file in /etc), the package manager would have to modify the registry at install and uninstall time, which is not optimal I think.
Its very possible to make an installer for Windows for use of .deb's and .rpm's via Cygwin and MinGW. I may take that up sometime. Sounds fun, and not that difficult.

---

### Post by phrostbyte on 2007-10-01
This is somewhat of a hack. I don't think it can uninstall or update applications, but just having the ability to unattended install a nice amount of applications is a god-send for Windows. No worries people, it still doesn't match the power of our package manager. :)

---

