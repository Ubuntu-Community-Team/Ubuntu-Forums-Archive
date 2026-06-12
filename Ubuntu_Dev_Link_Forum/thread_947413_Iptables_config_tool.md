---
title: "Iptables config tool"
date: 2008-10-14
forum: Ubuntu Dev Link Forum
---

### Post by intel17 on 2008-10-14
For my course I have been asked to create a project.  I have decided to write a GUI iptables config tool.  Just wondering if there would be any need for it in Ubuntu.  It will be written in python and I will design it to work on Ubuntu, obviously it will work on all Linux distros because its based on iptables. 

It would be great if I could get it included in to Ubuntu once it's complete and working fine.

Thanks,
Pete

---

### Post by ciscosurfer on 2008-10-26
> **intel17 said:**
> For my course I have been asked to create a project.  I have decided to write a GUI iptables config tool.  Just wondering if there would be any need for it in Ubuntu.  It will be written in python and I will design it to work on Ubuntu, obviously it will work on all Linux distros because its based on iptables. 

It would be great if I could get it included in to Ubuntu once it's complete and working fine.

Thanks,
PeteI think new tools are always fun to check out.  A frontend for iptables may end up being no small feat though.  Additionally, there are many frontends already available.  These come to mind: kmyfirewall, knetfilter, firestarter (not in devel anymore I don't think, but still worthy of a look), gufw (frontend for ufw), fwbuilder, guarddog, guidedog, gnome-lokkit...and there are definitely others out there.  

I say, be bold!  Check out what has been created already, get some inspiration, and start coding!

Good Luck!

---

### Post by intel17 on 2008-11-03
all right then! Lets get things rolling ^_^ I'll use this thread to keep people upto date.

Pete

---

### Post by intel17 on 2009-02-08
Right, now its time to start work on the actual code. 
Wheres the best place to start, I will be writing it in Python and use wxPython for the GUI.  I've spent some time working on the GUI and now I've sorta come to a stand still.  

I'm not sure where to start from here.  I need a way to get the data from iptables to the GUI, I was thinking use XML.  I used iptables-xml to turn the rules into XML but now I'm not sure if this is the best way to go.

A little nudge in the right direction would be a great help, what would you do if you where in my place.  

Thanks, 
Pete

PS during the time I started this post and finished it I looked up Gufw and have started to explore the code inside it.  So I'll probably find an answer soon(ish) but I would still like to hear you views.

---

### Post by badrunner on 2009-02-08
Isnt xml a bit overkill, why dont you just parse the output from the iptables commands? Easy with some regular expressions

---

### Post by intel17 on 2009-02-09
yeah that's true, could I be pointed in the direction of an example of file parsing... please ^_^

---

### Post by jchiar on 2009-06-13
> **intel17 said:**
> yeah that's true, could I be pointed in the direction of an example of file parsing... please ^_^
Here are some links, but man man and man -h are the best ways to learn.
[http://firehol.sourceforge.net/invoking.html](http://firehol.sourceforge.net/invoking.html)
[http://www.weidner.ch/fwconf.html](http://www.weidner.ch/fwconf.html)
I allways liked Firewall Builder. I think it is BSD lisence. It helps to learn that stuff.
[http://www.fwbuilder.org/news.html](http://www.fwbuilder.org/news.html)
Snort is also a good frontend:
[http://trac.cipherdyne.org/trac/fwsnort/changeset/507/?format=diff&new=507](http://trac.cipherdyne.org/trac/fwsnort/changeset/507/?format=diff&new=507)
This one be very careful with, read the WARNING! and always make a backup of a stable kernel before it could become unstable with a misplaced DOT or SEMI-COLON.
[http://www.t2-project.org/handbook/html/t2.config.netconf.html](http://www.t2-project.org/handbook/html/t2.config.netconf.html)
This wiki says FireHOL also, there is also ARNO, but I never played with that,,,,yet.
[https://wiki.kubuntu.org/SoC-Firewall](https://wiki.kubuntu.org/SoC-Firewall)
[http://www.fwbuilder.org/](http://www.fwbuilder.org/)
There are many many GUI apps that work with iptables, some are overkill others are just eyecandy and serve minimal needs.
KDE uses Gaurdog. 
Debian uses alot of different stuff.
This is Ubuntu based on Debian, so that is where I would start my searches at.

---

