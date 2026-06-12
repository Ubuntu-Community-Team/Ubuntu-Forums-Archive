---
title: "Kubuntu annoying and unstable"
date: 2008-02-08
forum: Testimonials &amp; Experiences
---

### Post by rcs2007 on 2008-02-08
I have been running Kubuntu 7.10 for several months and have had annoying problems with multimedia in general. Annoying because I was expecting basic things like playing music CDs to work like I was used to in Mandrake and Mandriva. I can now play music CDs and MP3s but for some reason I can't rip a music CD to MP3 with either KB3 or SoundKonverter. I have installed all kinds of codecs and it seems fixing one thing breaks another. Getting Kubuntu to play DVDs was much more difficult than with Mandrake/Mandriva.  I think Ubuntu has really dropped the ball on multimedia. 

Kubuntu is also much less stable than I am used to. I have had several freezeups where KDE refuses to respond to anything which required a hard reset. The number of these incidents in 3 months is more than twice the number I had running Mandrake/Mandriva over several years!

I also can't get comfortable with the absence of a root account but that's a philosophy issue rather than a bug. 

Just my 3 cents on running Kubuntu after having great results with Mandrake/Mandriva (which is RedHat running KDE instead of Gnome as far as I'm concerned.) If I keep getting lockups, I will go back to Mandrake/Mandriva.

---

### Post by kellemes on 2008-02-08
> **rcs2007 said:**
> If I keep getting lockups, I will go back to Mandrake/Mandriva.

bye

---

### Post by k2t0f12d on 2008-02-08
Here is a useful tip from a former user.

Stop installing Kubuntu.  Get the regular Ubuntu installation media and do the following:

[list]
Update and then upgrade all your packages
[/list]
```

sudo apt-get update && sudo apt-get dist-upgrade

```
[list]
Install the KDE desktop on top of Ubuntu
[/list]
```

sudo apt-get kubuntu-desktop kdm gtk-qt-engine

```

Then reboot, change your session to "KDE" at the login screen, and login normally.

You can also activate the root account with:
```

sudo passwd root

```
and just give the account a password.

Cheers!

---

### Post by HappyFeet on 2008-02-08
while not a fan of KDE to begin with, i also found kubuntu to be somewhat glitchy. needless to say it didnt last long on my machine. though regular ubuntu has been nothing short of awesome for me.

---

### Post by Whiffle on 2008-02-08
Yeah the kubuntu-desktop package seems to curse an otherwise good install.  I installed an ubuntu install, removed everything gnome, removed networkmanager, and then installed kde-base i think, and it works very nicely.  They should just drop kubuntu and focus on ubuntu, they mangle KDE and then wonder why people don't use it.

---

### Post by AlanR8 on 2008-02-08
Kubuntu now for more than a year, in a WORKING environment, sole operating system on this laptop.

Unstable, I don't think so.........

Always a learning curve in Linux but when I do a fresh install, or install on a new machine, it takes about 20 minutes to get all the multimedia side working.

Don't give up

---

### Post by lespaul_rentals on 2008-02-08
**Stop using 7.10**.

Install Kubuntu 7.04.  One of my favorite distros by far.  I love KDE and I know that some KDE fans think Kubuntu is not a great example of KDE, but it's great for me.  Upgrading and installing 7.10 was a disaster.  Please stick with 7.04 and I think you will find an improvement.

---

### Post by sam-c on 2008-02-08
I have both Ubuntu 7.10 and Now Kubuntu 7.10
Konqueror is good but I prefer Firefox that comes with Ubuntu
I prefer KDE for Development.
I will download Opera and Firefox on the Kubuntu.:guitar:

---

### Post by k2t0f12d on 2008-02-08
> **Whiffle said:**
> I installed an ubuntu install, removed everything gnome, removed networkmanager, and then installed kde-base i think, and it works very nicely.

Why do you need to "rip out" everything GNOME?  If you install kubuntu-desktop and gtk-qt-engine you get the best of both worlds.  Even with Debian I use both GNOME and KDE apps on a K desktop.  You aren't forced to use only one or the other.

---

### Post by Whiffle on 2008-02-08
> **k2t0f12d said:**
> Why do you need to "rip out" everything GNOME?  If you install kubuntu-desktop and gtk-qt-engine you get the best of both worlds.  Even with Debian I use both GNOME and KDE apps on a K desktop.  You aren't forced to use only one or the other.

Primarily because I pretty much never use it.  I think the only apps I use that even use gtk are gaim, xchat and occasionally firefox.  Its certainly not necessary to remove it, but I do just for housekeeping purposes.

---

### Post by AlanR8 on 2008-02-08
> Stop using 7.10.



Now there's an opinion. All entitled to one.

Not my experience. 7.10 installed perfectly and all went well.

---

### Post by MNICY on 2008-02-08
Kubuntu 7.04 and 7.10 were both glitchy for me. I liked the GNOME versions much bettter ;)
The sad thing is, i like KDE more.. :(
But, i would rather have a stable base to work of of then to have my fresh install have problems i dont get untill several days of messing with stuff ;)

---

### Post by rcs2007 on 2008-02-09
Thanks for the useful tips everyone. I will take k2t0f12d's advice and reinstall with plain Ubuntu and give it a go for a few months. Oh, and a nice simple solution to the root account as well. Thankee!

---

