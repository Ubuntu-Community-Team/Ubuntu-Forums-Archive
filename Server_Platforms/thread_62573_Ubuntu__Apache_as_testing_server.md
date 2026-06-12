---
title: "Ubuntu / Apache as testing server"
date: 2005-09-05
forum: Server Platforms
---

### Post by stef25 on 2005-09-05
Im a webdesigner and linux virgin, wanting to install Apache as a testing server on an Ubuntu desktop. It will be mainly used for php, perl etc. But, Id also like to give Ubuntu a shot as an XP replacement for desktop and office applications.

Im buying a new computer to accomodate this all. My question is: what are the ideal  hardware requirements for such a setup? I was thinking of an old Dell of around 600 - 1000Mhz with 250 mb Ram. 

Is this sufficient? What are people's experiences with such setups?

Id also like to hook up a wifi router through which 3-4 computers would access the net and share files. Is Ubuntu appropriate for this, esp concerning compatibility with common routers?

many thanks
stefan

---

### Post by jameswilhelm on 2005-09-05
What will probably slow you down on that machine is the desktop part or if your scripts are going to do a lot of processing.

At home I run a 200MHz Pentium MMX in a headless configuration (no monitor) with 256MB of RAM. It sits in a corner out of the way.

On it I run Apache, MySQL and proftpd. To be fair, it does not do much most of the time, but a friend and I are experimenting with a small MySQL database and he commented on how fast it was (he is in IT, I'm not) - him over the internet. Previously, I also ran Samba and NFS on it - no problems or noticable slowing.

I get 40Mbps+ up and downloads over the local network, so no slowing there either.

It seems that I can throw anything at the old machine, and it just keeps going.

So, to cut a long story short, that machine of yours should be more than fast enough for the server bits, especially if you'll be the only one using it.

Can't comment on Wi-Fi, but other people have it working, so it might not be too much of an issue.

---

### Post by LordHunter317 on 2005-09-05
You need more memory.

---

### Post by stef25 on 2005-09-05
thanks for all the replies. 

Would i be better off getting a slower processor, say a 2-300Mhz, but with 500MB ram?

obviously more of everything is better but im trying to save $$$

---

### Post by drummer on 2005-09-05
[QUOTE=LordHunter317]You need more memory.[/QUOTE]
 I had a headless server running with 128mb of ram (6 year old Gateway, Celeron 500mHz) and was fine for what I was doing: using as a test server for my Software Design & Development major work (a website to store and manage images). I used PHP, MySQL, Apache, ProFTPd, webalizer, and a bunch of other stuff, basically just toying with different server things and it ran fine with 128mb ram, so 250 should be plenty for a test server. I don't know how much memory is needed if the server has lots of traffic, but i would have thought that that's mostly dependent on the cpu. Also, I have my Ubuntu box (desktop, not the server) connected to a Netgear WGR614 (?) router via a wireless pci card (Netgear WG311v2) and this works fine with ndiswrapper, I think it works out-of-the-box if you don't use WEP.

I say go for it.

---

### Post by LordHunter317 on 2005-09-05
[QUOTE=stef25]Would i be better off getting a slower processor, say a 2-300Mhz, but with 500MB ram?[/quote]Probably.  Though I would just spring for the extra RAM.  As long as you don't get stuck buying a box requiring RDRAM, you'll be fine.

[quote=drummer] I had a headless server running with 128mb of ram [/quote]Stop right there.  You're making an apples to oranges comparsion.  He intends to use this as a regular desktop as well, which will require more memory to be used comfortably.

---

### Post by drummer on 2005-09-05
[QUOTE=LordHunter317]He intends to use this as a regular desktop as well, which will require more memory to be used comfortably.[/QUOTE]Sorry, must have missep that bit :P
I wouldn't skimp that much on the cpu though, 2-300mHz is quite slow, especially if you want to use desktop apps (OO.o, etc.)

---

### Post by stef25 on 2005-09-05
thanks again for all the answers. scouring ebay for some good old pc's now ...

- stef

---

### Post by TheDanMan on 2005-09-05
You don't really need more memory, not for a small testing environment.  More would be nice, but need you do not.

I run an old Dell 300mhz with 128mb of ram and while I'd like more memory, it is fine for testing scripts and sites.

Some here will tell you its overkill but you can use webmin, [www.webmin.com](www.webmin.com) to manage your system.  That way you'll have no need for setting it up as a desktop and that should take your system requirements down.  You can apt-get webmin, however the version in the repository is almost always out of date and does not install all the modules you typically get if you install from the tar.gz from the webmin site.  A goo reference for webmin setup is The Book of Webmin by Joe Cooper.  [http://www.swelltech.com/support/webminguide/index.html](http://www.swelltech.com/support/webminguide/index.html)

You may also consider installing virtualmin, which is a module you can get from the webmin site.  A good reference for administering that is found at [http://www.swelltech.com/support/virtual-servers/index.html](http://www.swelltech.com/support/virtual-servers/index.html).  Virtualmin will make it easier for you to set up multiple test domains on the one system.  Very painfree if you ask me :-D

A good place for webmin and virtualmin help is [www.virtualmin.com](www.virtualmin.com).  If you register and post on the forums they'll be glad to help, as will I where I can.  That is actually the site for Virtualmin Pro which would be complete overkill for you.  However they have sections in the forums for both gpl virtualmin and webmin help.  There are a few caveats to using webmin on ubuntu but if you can follow directions in the webmin book and the virtualmin page, you'll be just fine.

And have fun with your ubuntu system!

---

