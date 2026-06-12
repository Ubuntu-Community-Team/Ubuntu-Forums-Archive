---
title: "Gnome 2.12 Released!"
date: 2005-09-08
forum: The Cafe
---

### Post by benplaut on 2005-09-08
hot off the /. !  :grin: 

[www.gnome.org](www.gnome.org)

---

### Post by poofyhairguy on 2005-09-08
Using it now.

I couldn't wait a month.

---

### Post by Ride Jib on 2005-09-08
edit. nevermind

---

### Post by gorkhal on 2005-09-08
ran using the live cd off gnome's website....it is freakin amazing...

ooohhh the font rendering is soo much better, and a lot of the other stuff's good as well.

---

### Post by gord on 2005-09-08
im waiting for a apt-get version or a nice how-to before trying 2.12. some of the stuff sounds great but the compiling was getting a little over my head.. also its very very early in the morning

---

### Post by manicka on 2005-09-08
[QUOTE=poofyhairguy]Using it now.

I couldn't wait a month.[/QUOTE]
 I couldn't wait either.

It's very nice.... as is breezy :D

---

### Post by samjam on 2005-09-08
[QUOTE=manicka]I couldn't wait either.

It's very nice.... as is breezy :D[/QUOTE]

is it avilable on brezy as apt, i.e. should I do a dist-upgrade from hoary?

Sam

---

### Post by benplaut on 2005-09-08
[QUOTE=samjam]is it avilable on brezy as apt, i.e. should I do a dist-upgrade from hoary?

Sam[/QUOTE]

before i tell you anything, are you a new linux user? breezy is still unstable, and not ready for desktop use...



[SIZE=1]i have a fealing i'm required to say that...[/SIZE]

---

### Post by samjam on 2005-09-08
[QUOTE=benplaut]before i tell you anything, are you a new linux user? breezy is still unstable, and not ready for desktop use...



[SIZE=1]i have a fealing i'm required to say that...[/SIZE][/QUOTE]

Top marks for asking; I'm a long-time linux freaker having moved to ubuntu in the last 3 months finding it a much nicer experience for my family than debian testing/unstable (sarge) that I had been using.

so, having warned, feel free to speak on

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=samjam]Top marks for asking; I'm a long-time linux freaker having moved to ubuntu in the last 3 months finding it a much nicer experience for my family than debian testing/unstable (sarge) that I had been using.

so, having warned, feel free to speak on[/QUOTE]

Put in this command to terminal:

sudo gedit /etc/apt/sources.list

when that opens, copy and paste it here.

---

### Post by escuchamezz on 2005-09-08
OMG there's a menu editor, welcome to the revolution of Gnome  :razz:

---

### Post by Wolki on 2005-09-08
Since some people here don't read Planet Ubuntu:

"jrb [says](http://webwynk.net/jrb/#1126152882) :

    Of all the features in evince, the one that I'm most proud of is that we don't have a preference dialog. It's taken a lot of discipline and creativity along the way, but we managed."

Ah, the spirit of Gnome :)

Oh btw, here's th OSnews review: [http://www.osnews.com/story.php?news_id=11800](http://www.osnews.com/story.php?news_id=11800)

---

### Post by samjam on 2005-09-08
[QUOTE=poofyhairguy]Put in this command to terminal:

sudo gedit /etc/apt/sources.list

when that opens, copy and paste it here.[/QUOTE]
 well; I used cat, but here it is:

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

#debian sources
deb-src [ftp://packages.debian.org/debian](ftp://packages.debian.org/debian) unstable contrib main non-free
#deb-src [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free
#deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) testing main contrib non-free
#deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

## Backports Staging
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb-src [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb-src [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main
#deb-src [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

# for amarok
#deb-src [http://archive.kalyxo.org](http://archive.kalyxo.org) staging main

# for zonealarm
#deb-src [http://www.spic.net/zoneminder/debian](http://www.spic.net/zoneminder/debian) ./

## e17 repository from Elive
#deb [http://www.vobcopy.org/mirror/elive/](http://www.vobcopy.org/mirror/elive/) elive main efl elive

---

### Post by poofyhairguy on 2005-09-08
No offense....but that was the most messed up sources.list I've ever seen.  So many debian repos....I'm surprised your computer did not explode! I'm so glad I asked you to show me it so I could fix it!

Here is the one you need for Breezy:

> 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse


When we have a Breezy backport repo, add it to. I must warn you that putting so many Debian sources in your sources.list is the easiest way to really mess up Ubuntu, especially this one:

> deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main

Please never put that back in!

Now do this:
> 
sudo apt-get update

sudo apt-get dist-upgrade

---

