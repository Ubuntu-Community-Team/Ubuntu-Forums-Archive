---
title: "Distro for grandma..."
date: 2006-02-19
forum: The Cafe
---

### Post by nemik on 2006-02-19
Hello guys,

So my girlfriend's grandmother's birthday is coming up. I want to get her a small cheap laptop to use with wifi because she loves looking at my GF's picture gallery site.

2 problems:

1) I can't afford to get her something so super, so a maximum 200 MHz, 128MB RAM, 8 GB HD would be the specs (or close to that).

2) she speaks and reads Russian and doesn't understand a work of English. 

3) it has to be a laptop because her apartment is too small for a desktop + monitor + keyboard + mouse.

So with that info, what would you guys recommend? I SO want to put on Ubuntu because of great int'l support and ease of getting a cheap PCMCIA card working on there, but it would take too much resources given the hardware.

Thank you all!

-nemik

---

### Post by CaptainTux on 2006-02-19
The top three ideas I could think of would be Mepis Lite, Vector Linux, and Damn Small Linux.  

The other option would be to choose a Debian Sarge, Fedora Core, Mandriva, or Open SUSE and choose to install with a slimmer GUI than GNOME or KDE such as IceVM.

You could also try an older distro like an old copy of Redhat 9 or SUSE 8.2 or something in that order.

---

### Post by Wallakoala on 2006-02-19
ubuntu might not run so great on such an old laptop. There is a linux distro called Damn Small Linux (DSL) which would probably work pretty nicely on that, but it is not as easy to use as ubuntu, and I don't think that there is a russian version. If you are going to get a laptop, you might want to get a beefier laptop.

---

### Post by CaptainTux on 2006-02-19
Wallakoala brings up a very valid point on DSL.  

RedHat and Fedora Core have good international support.  My old RHL 9.0 CD's still get use on older systems from time to time.

---

### Post by nemik on 2006-02-19
yea the Russian language is an absolute necessity. Essentially though all it'd need was a GUI for Firefox (RU version) and Thunderbird for email (or some other email client with RU version) and some buttons to click to get to those 2 apps.

---

### Post by nemik on 2006-02-19
yea the Russian language is an absolute necessity. Essentially though all it'd need was a GUI for Firefox (RU version) and Thunderbird for email (or some other email client with RU version) and some buttons to click to get to those 2 apps.

---

### Post by TTT_travis on 2006-02-19
I have used Slackware 9 with Fluxbox on a p1 133mhz with 80mb of ram and even that was enough for very basic surf, like a photogallery. You *MIGHT* beable to get by with a server install of Ubuntu and then install X with Fluxbox, although I don't know if you can setup X without installing Gnome. But Damn Small Linux might be a good idea if you install a nice Fluxbox theme, That or nUbuntu, it uses Fluxbox and is a live cd version but there is a guide that explains howto install to hard drive, it also has a fancy Fluxbox theme, it a security distro not really focused at Grandmas but still ;) Oh and I think you can select russian.

---

### Post by CaptainTux on 2006-02-19
Fluxbox...good choice!

---

### Post by nemik on 2006-02-19
if fluxbox is really as light-weight and fast as people say, it would be perfect! and i think i can get russian on it too. even if not, its ok as long as i can put icons on there for firefox and thunderbird which do have russian extensions.

thanks guys!

---

### Post by teet on 2006-02-20
I've messed around with linux on my old pentium 200 mhz, 64 mb ram, 2 gb harddrive (this sounds *similar* to the sort of machine you're wanting to get).

I first tried a base install of debian with fluxbox as my window manager.  I got it working okay but to be quite honest, Firefox is way to big of a program to run a machine that old (the 128 mb of RAM might help this some though).  Don't get me wrong, Firefox worked and went places on the internet....it was just incredibly slow to do anything (even with flash and java disabled).  Dillo (the web browser) ran really great on the machine, however, it doesn't have support for a lot of things you'll find on the web (i.e. a lot of pages looked really screwed up).

I also tried DSL (which uses the old 2.4 kernel and doesn't have x-windows I believe) and it ran a little faster overall, but still quite slow.  Again, even with DSL firefox was too slow for me to use (maybe I'm just too impatient).  

Finally, I ended up just installing Windows 98 SE with IE6.  To be honest, I haven't found a suitable linux distro for really old machines.  You may want to consider getting a laptop that comes with a copy of win98.  IE6 is much faster than firefox and displays pages "properly" (unlike dillo).  I don't run any antivirus on the machine (that would slow it down too much), but I don't really care if I lose everything on it either.  Anyway, it's something to think about :)

-teet

---

### Post by Ahriman on 2006-02-20
There is also Slax, which is Slackware-based. Their site isn't 100% clear on Int Language support, though, and apparently the newest version doesn't have an installer to the HDD (it's designed to run from a credit-card sized CD or a USB stick).

But I used it at work for a crappy old system and it worked fine, you can also pick and choose different programs to include with it.
[www.slax.org](www.slax.org)

---

### Post by nemik on 2006-02-20
Thank you everyone for the help.

Right now the laptops I'm looking at seem a little beefier than I thought they would be, so perhaps I can get something stronger and run default Ubuntu on there anyway. 
Won't be super-fast, but the babulya is a patient lady. :) Or I'll just do a server/base install and add fluxbox on top of it with the 2 icons I need for thunderbird email and firefox browser. It is all she would need really.

Thanks again and I'll keep everyone posted on what I'm doing with it.

If it works good, perhaps I'll package it all into a Babuntu* distro! :p

*for those that don't get it, babulya is Russian for 'grandma', so babulya + Ubuntu =  Babuntu.

---

### Post by TrailerTrash on 2006-02-20
STX Linux is the best that ive seen on older systems.

---

### Post by Squalor on 2006-02-20
I'd say Arch+Openbox, or even Zenwalk.

---

### Post by towsonu2003 on 2006-02-20
or, you could do a server install, connect to the net, and apt-get install xubuntu-desktop (do you need to enable extra repos? don't know...). that will give you xfce4. looks like it has russian translation [https://launchpad.net/distros/ubuntu/breezy/+lang/ru](https://launchpad.net/distros/ubuntu/breezy/+lang/ru) mostly complete for xfce stuff? 

halfway there for overall distro though [https://launchpad.net/distros/ubuntu/breezy/+translations](https://launchpad.net/distros/ubuntu/breezy/+translations) .

Did you check distrowatch for russian distros? (only 3 distros) ( :( ) [http://distrowatch.com/search.php?category=All&origin=Russia&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=All&origin=Russia&basedon=All&desktop=All&architecture=All&status=Active)

---

### Post by Leo_01 on 2006-02-20
[QUOTE=teet]I've messed around with linux on my old pentium 200 mhz, 64 mb ram, 2 gb harddrive (this sounds *similar* to the sort of machine you're wanting to get).

I first tried a base install of debian with fluxbox as my window manager.  I got it working okay but to be quite honest, Firefox is way to big of a program to run a machine that old (the 128 mb of RAM might help this some though).  Don't get me wrong, Firefox worked and went places on the internet....it was just incredibly slow to do anything (even with flash and java disabled).  Dillo (the web browser) ran really great on the machine, however, it doesn't have support for a lot of things you'll find on the web (i.e. a lot of pages looked really screwed up).

I also tried DSL (which uses the old 2.4 kernel and doesn't have x-windows I believe) and it ran a little faster overall, but still quite slow.  Again, even with DSL firefox was too slow for me to use (maybe I'm just too impatient).  

Finally, I ended up just installing Windows 98 SE with IE6.  To be honest, I haven't found a suitable linux distro for really old machines.  You may want to consider getting a laptop that comes with a copy of win98.  IE6 is much faster than firefox and displays pages "properly" (unlike dillo).  I don't run any antivirus on the machine (that would slow it down too much), but I don't really care if I lose everything on it either.  Anyway, it's something to think about :)

-teet[/QUOTE]

Your specs on your system is really low...(2gb?!)
The swap space and the main files itself is using pretty little space...
change the HD and increase the swap if you want better speed.

---

