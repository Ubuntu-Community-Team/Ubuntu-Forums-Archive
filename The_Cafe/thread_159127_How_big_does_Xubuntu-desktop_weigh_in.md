---
title: "How big does Xubuntu-desktop weigh in?"
date: 2006-04-12
forum: The Cafe
---

### Post by K.Mandla on 2006-04-12
A very quick question: Can I squish a server install plus xubuntu-desktop onto a 1GB hard drive? 

Thanks if you can tell me the answer: you're saving me the 90 minutes it would take me to reinstall and find out.

---

### Post by bonzodog on 2006-04-12
No, it doesn't look like it - I have Xubuntu installed like this, and it's using just under 2GB.

---

### Post by K.Mandla on 2006-04-12
[QUOTE=bonzodog]No, it doesn't look like it - I have Xubuntu installed like this, and it's using just under 2GB.[/QUOTE]
Crap. I was hoping I could slip in under the wire. I found a mostly complete Dell Optiplex (1Ghz P3) at the recycling center and my techie at work is offering me an ancient 1GB WD Caviar drive to get it going (he already gave me 256Mb of PC100). I was hoping I could squeeze Xubuntu onto that, but it looks like I'll have to knuckle under and buy a real drive. 

Thanks a bunch!

---

### Post by Randomskk on 2006-04-12
How about installing DSL?
[www.damnsmalllinux.org](www.damnsmalllinux.org)

---

### Post by K.Mandla on 2006-04-12
Thanks for the suggestion. I've messed with DSL, but I just have a preference for Ubuntu and the way it feels. And besides, it's not the processor or the memory that's holding me back this time, it's my own innate, incurable and rampant stinginess -- I really don't want to spend money on a hard drive when the machine cost me nothing at the recycling center. 

There's some bullheadedness involved, too: My brother wants to spend about USD1,300 on a new desktop and I want to prove to him I can get the same job done for USDZERO. So my pride is involved.

I'll get over it. Thanks again for the idea, though.

---

### Post by Randomskk on 2006-04-12
You could also try using Fluxbox, it's the desktop/window manager DSL uses, but you can get it on Ubuntu. Server install, install X, install fluxbox.

---

### Post by aysiu on 2006-04-12
According to [the Ubuntu website](http://www.ubuntu.com/download/releasenotes/510), a server install is 500 MB of hard drive space.

Maybe you could do this after a server install (as recommended by Azz): ```
sudo apt-get update
sudo apt-get install x-window-system-core xterm gdm icewm menu firefox synaptic
```

---

### Post by Derek Djons on 2006-04-12
Couldn't you just mess around with your packetmanager and throw overboard what you don't need or want?

I don't know if Ubuntu core system is below 1Gb and if you would make it after stripping the system and adding you desired applications.

---

### Post by KingBahamut on 2006-04-12
Hmmmmm,  you could try it. 

Bonzo, you did a server install with an apt-get install xbuntu-desktop and it took 2 gig?

---

### Post by vayu on 2006-04-12
It might work.   My sons PIII computer has Gnome and a whole lot of other stuff fitting in 2 GB.  I would try it before giving up.

---

### Post by aysiu on 2006-04-15
For the record, on my junky old computer (which I use for various Ubuntu testing), I just did a fresh server install of Dapper and installed Xubuntu on top of it--it uses 1.5 GB of hard drive space.

---

### Post by fuscia on 2006-04-15
here's a tabbed, ssl dillo that's very, very small - [http://teki.jpn.ph/pc/software/index-e.shtml](http://teki.jpn.ph/pc/software/index-e.shtml)

you could also do sylpheed-claws for mail.

---

### Post by noalternative on 2006-04-16
[QUOTE=K.Mandla]Thanks for the suggestion. I've messed with DSL, but I just have a preference for Ubuntu and the way it feels. And besides, it's not the processor or the memory that's holding me back this time, it's my own innate, incurable and rampant stinginess -- I really don't want to spend money on a hard drive when the machine cost me nothing at the recycling center. 

There's some bullheadedness involved, too: My brother wants to spend about USD1,300 on a new desktop and I want to prove to him I can get the same job done for USDZERO. So my pride is involved.

I'll get over it. Thanks again for the idea, though.[/QUOTE]


I like [feather]("http://featherlinux.berlios.de") better than dsl.  If it is an issue of liking xfce you should try luit.  I don't remember the url for luit.  Google it if you are interested.  There is also ubuntu lite, and the Vedran packages.

---

### Post by moopere on 2006-04-17
[QUOTE=aysiu]For the record, on my junky old computer (which I use for various Ubuntu testing), I just did a fresh server install of Dapper and installed Xubuntu on top of it--it uses 1.5 GB of hard drive space.[/QUOTE]

Hmm, interesting.  I do "server" installs which tend to weigh in at <400MB, then install the desktop of choice.

On a machine I installed today, using Dapper Xubuntu it came in a 936MB all up (inc swap).

Mind you, I install using aptitude and turn off the option to auto install all recommended software.  I only install the stuff thats actually dependent.

I've a few machines here with 1GB-2GB drives and have never really had a problem.

Cheers,
Craig

---

### Post by Miguel on 2006-04-17
If Dapper+Xubuntu needs 1.5 Gigs (which seem like a lot), why not go for server install + IceWM (or just a barebones XFce)? Just my two cents.

---

### Post by aysiu on 2006-04-17
[QUOTE=moopere]Hmm, interesting.  I do "server" installs which tend to weigh in at <400MB, then install the desktop of choice.

On a machine I installed today, using Dapper Xubuntu it came in a 936MB all up (inc swap).

Mind you, I install using aptitude and turn off the option to auto install all recommended software.  I only install the stuff thats actually dependent.[/QUOTE] Yeah, that's not what I did. I did just a server install and an apt-get install of xubuntu-desktop.

---

