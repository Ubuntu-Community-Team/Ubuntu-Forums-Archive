---
title: "Problems with installing the Ardour program."
date: 2009-01-04
forum: Ubuntu Studio
---

### Post by khelben1979 on 2009-01-04
81-224-174-84-o1123:/home/nightrazer# apt-get -f install ardour-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ardour-gtk: Depends: libgtk-canvas1 (>= 0.1.1) but it is not going to be installed
              Depends: libgtk1.2 (>= 1.2.10-4) but it is not going to be installed
              Depends: libgtkmm1.2-0c2a but it is not going to be installed
E: Broken packages


I have spent an hour with this now (something like that) and I don't get anywhere with this. I need to know how to install this ardour program.

Any suggestions?

*The system is Debian Lenny on an 64 bit PC model.*

---

### Post by thorgal on 2009-01-04
```

sudo apt-get install ardour

```

not ardour-gtk, which is a prehistorical version (0.99)

---

### Post by babarosa on 2009-01-04
Hi Khelben,

you are using Debian Lenny or Etch.
I do not know if it is compatible, but you can download the most recent version ardour 2.7.1 from [www.getdeb.net](www.getdeb.net) (I'd suggest you choose from the menu distribution hardy not the default intrepid).

It is adventurous so you'd better save your files first [-o<

Good luck, Michael

---

