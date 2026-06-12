---
title: "P2-350/ 256megs ram ready for inpute."
date: 2005-10-25
forum: The Cafe
---

### Post by Omnios on 2005-10-25
Well after about a month got all the cables I need to get my old P2 running and im going to try running Gnome and KDE on it. I have one failed install so far as it just froze there with no hard drive activity during set up. Almost done the second attept but am afraid that its 6.4gigs of hard drive space is not anouph for a full install so I figued id post this now. This may be a common accurance for small hard drives.

 Anyways already thinking of doing a server install and am wondering what I have to do to get Xserver and possibly Kubuntu-desktop loaded. This is my back up e-machine so as long as I can access the net its not a problem or what is on it.

 Also had a config problem on install as it would not detect the network wich is a cable modem through a router to the two machines. I think I may manualy configure this but no idea how yet.

 I realy look forward to getting this old box running with Ubuntu as now I will be able to say I have a machine that stricly rund Linux. Well back to installing.

---

### Post by poofyhairguy on 2005-10-25
[QUOTE=Omnios]Well after about a month got all the cables I need to get my old P2 running and im going to try running Gnome and KDE on it. I have one failed install so far as it just froze there with no hard drive activity during set up. Almost done the second attept but am afraid that its 6.4gigs of hard drive space is not anouph for a full install so I figued id post this now. This may be a common accurance for small hard drives.

 Anyways already thinking of doing a server install and am wondering what I have to do to get Xserver and possibly Kubuntu-desktop loaded. This is my back up e-machine so as long as I can access the net its not a problem or what is on it.

 Also had a config problem on install as it would not detect the network wich is a cable modem through a router to the two machines. I think I may manualy configure this but no idea how yet.

 I realy look forward to getting this old box running with Ubuntu as now I will be able to say I have a machine that stricly rund Linux. Well back to installing.[/QUOTE]


Don't use KDE. In my experiance it loves CPU more than the rest. XFCE is what I use on a computer of that age with similiar specs.

---

### Post by az on 2005-10-25
You need a little more than two gigs of disk space, so you are way fine.

If you install using the server option, once you are set up, login and run
sudo apt-get install x-window-system-core xterm synaptic mozilla-firefox icewm menu gdm

Change the icewm to xfce4, if you like, or install both.

---

### Post by Omnios on 2005-10-25
I think I have a bad CD bacause its hanging at the same spot which is wierd becauise I managed to use that cd on this computer. I just got a bunch of unformated 700meg CD RW that I need to format and my old nero 5 has no format options and wond detect them as cd rw's. Is there any realy good GUI cd burner or rahter what is the best ones to use. After this im going to be a lot more carefull with my cds lol.

---

### Post by Omnios on 2005-10-26
Still strugling with my bad CD, I bought 10 700meg cd-rw but there not formated and show as nothing in XP and linux so I can not burn anythin on them and can not seem to find a CD-RW formater. 

 Anyways I managed to install Ubuntu 5.04 live CD and it looks rather promissing though I do not have any Mouse support and the screen is wierd in that the left 80% is ok nice and brown and the right looks green and lickery, then again im seeing scroll nines on my new 19' moniot which is strange. From what I have seen so far I think Gnome will run good on the p2 with its ram as from what I have played with so far seems realy quick even quicker than win98. Im contiplating installing 5.04 but still want to see if I can get this cdrw issue solved. 

 From what I have seen so far Gnome will run on a slower machine with a lot of ram.

---

### Post by xequence on 2005-10-26
On a server install, woulent you need to enable extra repositories to download gnome, x, and such?

---

### Post by Omnios on 2005-10-27
Well got a cdr and it burnt ok now the problem I am having is on base install it is stating that a kernal is pointing to an image failure. Not shure if there is a way around this. Th live cd worked with a badly configured monitor but it will run. Thing that gets me is the bad cd whent all the way past finishing extras till it crashed. A%.04 install gave me the same error maybe an advanced install may help with a p2 with sis vid

---

### Post by Takis on 2005-10-27
[QUOTE=xequence]On a server install, woulent you need to enable extra repositories to download gnome, x, and such?[/QUOTE]
No, they're all in the same repositories. They're just not installed by default on a 'server' install. To turn a server into a desktop, all you need to do is install $FLAVOUR-desktop, such as ubuntu-desktop.

---

### Post by Omnios on 2005-10-27
BORK BORK BORKEDY BORK BORK.

 Got the folling error so started an actual need help post.

                       [!!] Install the base system
          No installable Kernal found in the defined APT sources

            The current default Kernal package is 'kernal-image'.

  You may try to continue though this rather strange error is probably fatal.

[http://ubuntuforums.org/showthread.php?p=448539#post448539]("http://ubuntuforums.org/showthread.php?p=448539#post448539")

---

### Post by Omnios on 2005-10-27
Well I think the load Linux onto a P2 with an american megatrends biosy is dead as I can not seem to load a Kernal onto it, I dought if its the sound card and as I dont have a copy of win98 to put on it its getting donated somewhere though not shure where yet.

---

### Post by Omnios on 2005-11-08
Well sort of got Free BSD loaded on the old p2 and its kind of B,S,Dimented. I had difficutlies setting up the network in the install so got KDE working which isnt all that bad on a old p2 without the router network setup or a way to config it. Bootings fun so far log in as root run KDM and log into KDE, maybe ill find the right help file sometime this week to get it to boot properly.

 Anyways if someone states that Ubuntu is to hard to install point them in the driection BSD they will have loads of fun. Havent figued out how to get super user working yet either. I just might slap win98 back on it and ship it back to my sister so she can use it as for slide show presentions lol.

 If I can manage to get it to work properly it might be a good set up but couldn't bother dishing out another two bucks for blank CD's for another distro. Now I have to find a Linux compatible older system as a back up computer. I learnt a new apreciation for Ubuntu thats for shure.

---

### Post by Omnios on 2005-11-14
Downloaded Debian net install and it managed to install the base system installed but the Linksys LNE100TX 2.0 ethernet card is unsupported so could not continue with the net install. Anyways I cchecked the Linksys web site and it seems that version of 2.0 of that series changed and is not supported. I had the same problem with win 98 but managed to find an old win 98 driver for it but no luck on a linux driver yet. 

 It seems that debian installs ok and im going to wait till I get a supported ethernet card before installing it. The only other issues will be modding the monitor frequencies and setting up the mouse which is on com1. It would be eisier to just reinstall PC-BSD but I realy want linux on it.

---

### Post by majikstreet on 2005-11-14
good luck- I'd go with fluxbox, btw.

---

