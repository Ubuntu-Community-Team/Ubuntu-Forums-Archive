---
title: "Using Alien to install .rpm"
date: 2007-05-24
forum: The Cafe
---

### Post by Lucifiel on 2007-05-24
Ugh, so it's come to this. Either I install Gimp 2.2.14 using alien or I'll have to try and install/run another distro or go back to WinXP.

So, how safe is installing a .rpm on Ubuntu?

---

### Post by starcraft.man on 2007-05-24
Ummm, whats wrong with the GIMP in the repos? Or if its installed (should be by default) the one you have...? And if that ones not working whats wrong with the 2.3 Debian that was released (its around the forums, search I guess)?

I'ved used alien on a few RPMs to make em Deb, I haven't had any stability issues... so I guess its ok. I don't see whats so vital about this version?

---

### Post by Lucifiel on 2007-05-24
Because 2.3.## doesn't work with the method I'm using. 

Because 2.2.13, the version I have keeps crashing non-stop. Even though I reinstalled countless of times. 

Because well, I booted using the Livecd and tried to create a package from Gimp 2.2.14 for myself but that didn't work(a variety of errors and problems and I'd rather not explain yet again). 

So... *shrugs* I'd rather not go into some more details. I am really tired of explaining myself over and over again.

---

### Post by TheMono on 2007-05-24
Sure, use Alien... But why not just compile from source?

---

### Post by tehkain on 2007-05-24
> **TheMono said:**
> Sure, use Alien... But why not just compile from source?Seconding this.

---

### Post by starcraft.man on 2007-05-24
Well, thats weird. 2.2.13 has never crashed on me >.>. Sorry for your bad luck with GIMP crashing, did you modify it with anything like GIMPshop?

Anyway, [heres]("http://www.psychocats.net/ubuntu/installingsoftware#source") a quick guide to installing anything in Ubuntu. It lists installing from RPM and compiling from source, I'd go the source way, its not too hard and described well. I'm sure that will get ya your new stable version of GIMP :).

Edit: Motion thirded and passed, ye shall compile from source or face stiff fines and penalties :p.

---

### Post by Lucifiel on 2007-05-24
Actually, I've just finished compiling from source and this time, I got it right!!!!! 

Wow, for the first time in 2 months, I've managed to compile from source properly!!!! 

WOW!!!!!! :D

I'm now on the livecd, guys... didn't get to read this thread until now. :p

Yeah, compiling from source is good!!!! Good practise for all newbies!!! All you newbies must compile from source using the livecd and learn about permissions and errors and warnings!!!

---

### Post by starcraft.man on 2007-05-24
YAY! Everyone happy now, have fun with your new stable version of GIMP, best of luck with your art/work :).

---

### Post by picpak on 2007-05-24
If you're a purist, you might want to compile it from Debian's unstable repository so you can have the program separated into gimp, gimp-data, and libgimp2.0, but it's up to you. Keep in mind that you'll want to install Ubuntu's Gimp before doing a dist-upgrade to avoid any problems.

---

### Post by Lucifiel on 2007-05-24
Actually, trying to "sudo make" on this installation failed. 

Blasted...

---

### Post by BLTicklemonster on 2007-05-24
> **Lucifiel said:**
> Actually, I've just finished compiling from source and this time, I got it right!!!!! 

Wow, for the first time in 2 months, I've managed to compile from source properly!!!! 

WOW!!!!!! :D


Because you rock!!!

Congrats!

---

### Post by Lucifiel on 2007-05-25
Bah, this is the 15th time today that I'm trying to compile from source.

Commands used so far:
> 
sudo rm -Rvf gimp-2.2.14

sudo tar -zxvf gimp-2.2.14

sudo chown -Rvf lucifiel:lucifel /home/lucifiel/gimp-2.2.14

sudo chmod -Rvf 755 /home/lucifiel/gimp-2.2.14

./configure --disable-print

sudo make


If sudo make still don't work...

---

### Post by Lucifiel on 2007-05-25
Wow, just hit 18th time. Sheez... >>;;

---

### Post by TheMono on 2007-05-25
Don't know if this has any effect, but you don't need sudo for make.

Just a standard 'make' and then 'sudo make install'

I would make you a package, but I am 64 bit which would be no use I'd imagine.

---

### Post by Lucifiel on 2007-05-25
> **TheMono said:**
> Don't know if this has any effect, but you don't need sudo for make.

Just a standard 'make' and then 'sudo make install'

I would make you a package, but I am 64 bit which would be no use I'd imagine.

Thank you but I tried that already.

Does anyone have Gimp-2.2.12?

If so, would you mind uploading it to Rapidshare ? (I can't access Megaupload.)

[http://www.rapidshare.de](http://www.rapidshare.de)

Thank you!

Well, it looks like I have two choices: set up Virtualbox and install another Linux distro or go back to Windows XP. 

I just don't know anymore. :(

---

### Post by forrestcupp on 2007-05-25
If you're having that much problem, just use alien.  It's ok; it won't violate any code of conduct.  I've used alien with rpm's before without trouble.  While it's not the first choice, if there are no other options, it's ok.

---

### Post by starcraft.man on 2007-05-25
> **Lucifiel said:**
> Thank you but I tried that already.

Does anyone have Gimp-2.2.12?

If so, would you mind uploading it to Rapidshare ? (I can't access Megaupload.)

[http://www.rapidshare.de](http://www.rapidshare.de)

Thank you!

Well, it looks like I have two choices: set up Virtualbox and install another Linux distro or go back to Windows XP. 

I just don't know anymore. :(

Are you sure that this isn't all systemic of a larger problem? I mean, if your having this much trouble with GIMP and compiling from source, maybe theres a problem with your install of Ubuntu/linux? Just a thought. 
Has anything else been giving you problems? I just don't see how GIMP could become so unstable on its own and compiling fail so bad >.>.

Anyway, sorry to hear so much trouble... I don't have any debs of older GIMP, just 2.3 version.

Anyway, ya, just try alien. I just can't understand why your having this much trouble... it just doesn't seem right.

---

### Post by Lucifiel on 2007-05-25
> **starcraft.man said:**
> Are you sure that this isn't all systemic of a larger problem? I mean, if your having this much trouble with GIMP and compiling from source, maybe theres a problem with your install of Ubuntu/linux? Just a thought. 
Has anything else been giving you problems? I just don't see how GIMP could become so unstable on its own and compiling fail so bad >.>.

Anyway, sorry to hear so much trouble... I don't have any debs of older GIMP, just 2.3 version.

Anyway, ya, just try alien. I just can't understand why your having this much trouble... it just doesn't seem right.

Everything is okay on my system. Gimp crashing is related to a set of symptoms which i noticed way back like 2 weeks ago, on an older installation of Feisty. It seemed to be related to pressing Ctrl + Shift + S and also, it would crash after i'd saved a file or while I was saving a file. 

Sometimes, when I was not doing anything within Gimp, the cursor would turn into an animated circular cursor(which likely indicates its' trying to perform a task) and then, the cursor would keep spinning for a few seconds or about a minute or so, before crashing.

Oh well, I'll give alien a try then! :)

---

### Post by Lucifiel on 2007-05-25
> **forrestcupp said:**
> If you're having that much problem, just use alien.  It's ok; it won't violate any code of conduct.  I've used alien with rpm's before without trouble.  While it's not the first choice, if there are no other options, it's ok.

I dunno man... I thought that rpms contained code meant for other distros?

---

### Post by reacocard on 2007-05-25
> **Lucifiel said:**
> I dunno man... I thought that rpms contained code meant for other distros?

They do, but it often works anyway. It's at least good enough for a standby until you can get the source compile working for you.

Also, you could try installing gimp packages from other Ubuntu versions: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gimp&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gimp&searchon=names&subword=1&version=all&release=all)
It's not the best idea, but it's certainly no worse than alien.

---

### Post by forrestcupp on 2007-05-25
Just to make sure, did you install build-essential?
```
sudo apt-get install build-essential
```

If you don't have that installed, you can't compile anything.  Ubuntu defaults without the ability to compile for safety reasons.  People shouldn't try it until they understand what they are doing.

edit:

And by the way, that's what alien is for.  It takes an rpm and tries to make it work with your system.

---

### Post by Lucifiel on 2007-05-25
> **forrestcupp said:**
> Just to make sure, did you install build-essential?
```
sudo apt-get install build-essential
```

If you don't have that installed, you can't compile anything.  Ubuntu defaults without the ability to compile for safety reasons.  People shouldn't try it until they understand what they are doing.

edit:

And by the way, that's what alien is for.  It takes an rpm and tries to make it work with your system.

Well, I had build-essentials installed.

In fact, I did this!

sudo apt-get install  build-essential bison libglib2.0-dev libgtk2.0-dev gtk-doc-tools libart-2.0-dev python-dev python-gtk2-dev libtiff-dev

and
sudo apt-get --reinstall install libmng-dev libxpm-dev libexif-dev libwmf-dev libgnomeui-dev librsvg2-dev libgtkhtml2-dev libpoppler-dev libpoppler-glib-dev

Anyways, no matter. I reinstalled 2.3.13 again and am running it through Terminal. That way, if anything crashes, I'll likely get an output. :)

---

