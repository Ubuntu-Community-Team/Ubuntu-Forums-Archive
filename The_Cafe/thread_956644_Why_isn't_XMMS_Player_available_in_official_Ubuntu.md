---
title: "Why isn't XMMS Player available in official Ubuntu repositories?"
date: 2008-10-23
forum: The Cafe
---

### Post by Kosimo on 2008-10-23
Why not?

---

### Post by Perfect Storm on 2008-10-23
1) It's ancient and havn't been maintained for a very long time (including security).
2) It depends on GTK1.2 which AFAIK is obsolite.

Solution;

Use Audacious

---

### Post by Kosimo on 2008-10-23
> **Artificial Intelligence said:**
> 1) It's ancient and havn't been maintained for a very long time (including security).
2) It depends on GTK1.2 which AFAIK is obsolite.

Solution;

Use Audacious

Thanks for the answer.
Yes, I've been using Audacious since Feisty. But I'm not really satisfy with it, and I wanted to give it a try to XMMS as I heard it is rock solid.
Audacious doesn't even have a working wepage for now, latest version has a very annoying bug witch it haven't been solved yet (I made a bug of course)...
So... There are really few Winamp-like alternatives to Audacious 1.5.1

---

### Post by Perfect Storm on 2008-10-23
You could give Xmms2 a try, just remember to get the gui as well.

Though Audacious 2 is on the drawing board (looking forward to it).

---

### Post by Kosimo on 2008-10-23
> **Artificial Intelligence said:**
> You could give Xmms2 a try, just remember to get the gui as well.

Though Audacious 2 is on the drawing board (looking forward to it).

I've never get to install XMMS2 with GUI :(  (I have to admit I'm a repository addict) sudo apt-get install xxxx  that damn easy :p

I didn't even know that Audacious 2 is on the way. I've heard that on google summer code 2008 audacious had something to say but after that, the webpage disappear.  
Where do you get that information?

---

### Post by Perfect Storm on 2008-10-23
From their homepage, wiki and forum.

---

### Post by init1 on 2008-10-23
> **Artificial Intelligence said:**
> 1) It's ancient and havn't been maintained for a very long time (including security).
2) It depends on GTK1.2 which AFAIK is obsolite.

Solution;

Use Audacious
And? Why would it need to be updated? It's already perfect.

---

### Post by FranMichaels on 2008-10-23
> **Kosimo said:**
> 
I didn't even know that Audacious 2 is on the way. I've heard that on google summer code 2008 audacious had something to say but after that, the webpage disappear.  
Where do you get that information?

They also have their mercurial repositories which you can pull from.
[http://hg.atheme-project.org/](http://hg.atheme-project.org/)

I can confirm audacious 2 will rock. I'm using "1.90" from the hg repositories... They finally offer a nice gtk gui, but still support the old winamp 2 style (run with audacious -i skinned). It supports several more formats (which matters to me as I love [chiptunes]("http://en.wikipedia.org/wiki/Chiptunes"))

Either way, if xmms has an advantage over audacious, I'd like to know what it is. You can even opt to have a file loader look like xmms. Gentoo has dropped xmms as well if I'm not mistaken...

---

### Post by steveneddy on 2008-10-23
I just use audacious, use the xmms skins and listen away.

No probs here.

---

### Post by Polygon on 2008-10-23
> **init1 said:**
> And? Why would it need to be updated? It's already perfect.

gtk 1.2 is not included in hardy/intrepid by default, and they are trying to phase it out.

if there are any security holes that are present in xmms, they will never be updated as upstream is dead.

gtk 1.2 is ugly.

---

### Post by I-75 on 2008-10-23
And why isn't Real Player available in the Ubuntu Repos?

---

### Post by FranMichaels on 2008-10-23
> **I-75 said:**
> And why isn't Real Player available in the Ubuntu Repos?

Because Canonical doesn't have the right to distribute it?

Anyway, try helix-player (which is in the repos)

---

### Post by I-75 on 2008-10-23
> **FranMichaels said:**
> Because Canonical doesn't have the right to distribute it?

Anyway, try helix-player (which is in the repos)

I know it was available in Freespire.

---

### Post by -grubby on 2008-10-23
> **I-75 said:**
> I know it was available in Freespire.

They probably bought the right to that with all the money they earn on Linspire licenses.

---

### Post by Perfect Storm on 2008-10-23
> **init1 said:**
> And? Why would it need to be updated? It's already perfect.

It's far from perfect and have some annoying bugs as well.


> 
And why isn't Real Player available in the Ubuntu Repos? 

It's back in medibuntu repo on 8.10

---

### Post by Kosimo on 2008-11-08
> **FranMichaels said:**
> They also have their mercurial repositories which you can pull from.
[http://hg.atheme-project.org/](http://hg.atheme-project.org/)

I can confirm audacious 2 will rock. I'm using "1.90" from the hg repositories... They finally offer a nice gtk gui, but still support the old winamp 2 style (run with audacious -i skinned). It supports several more formats (which matters to me as I love [chiptunes]("http://en.wikipedia.org/wiki/Chiptunes"))

Either way, if xmms has an advantage over audacious, I'd like to know what it is. You can even opt to have a file loader look like xmms. Gentoo has dropped xmms as well if I'm not mistaken...

Anyone knows how to use hg Repos? I can't find out on their wepage. I would like to give it a try to audacious 1.90

Thank you

---

### Post by guayusa on 2008-11-15
> **Kosimo said:**
> Why not?

Good question!

Have a look here: 
[http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/](http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/)

and install XMMS in Intrepid:

First go to KnutA’s site:
[http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)

…where he kindly hosts an XMMS repository that allows you to add it to your apt-get system and it will pull the dependencies. Set up for Lenny, Hardy and Intrepid (which is just a copy of the Hardy repo, but it works). If you don’t know how to add a third-party software source (or repository) then look here.

That should be your first step. Install XMMS that way:

sudo apt-get install xmms (or search in Synaptic).

Then you have to add various encoding and decoding tools if you need them.

Pulseaudio, the new system: [http://0pointer.de/lennart/projects/xmms-pulse/](http://0pointer.de/lennart/projects/xmms-pulse/)

I do not use that. Choosing ALSA as output in XMMS works better for me. With Pulseaudio there were funny issues with other channels, losing sound for a half a second every now and then.

There is still an mp4 .deb here, which also works in Intrepid:
[https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1](https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1)

To get FLAC follow the second part of this how-to (you don’t need to compile XMMS as outlined in the first part of the how-to, since you can get the .deb with apt-get from KnutA):
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

More relevant compile info here:
[http://blog.xanda.org/?p=436](http://blog.xanda.org/?p=436)

You might also want .wma (but much better is to convert your files), but if you need it, then you have to compile it (or google for an .rpm and use alien to convert it):
[http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)

More relevant information here: [http://ubuntuforums.org/archive/index.php/t-21414.html](http://ubuntuforums.org/archive/index.php/t-21414.html)

However, if you trust me you can also just download this file, Plugins.tar.gz and unzip to your:

/home/user/.xmms/Plugins folder (shut down XMMS, of course, for good measure):

That file contains the Flac and .wma plugins that should work in Intrepid and possibly Hardy, but why not go ahead and do it yourself, you might just learn something in the process?! :)

Maybe you also need: [http://www.etree.org/shnutils/xmms-shn/](http://www.etree.org/shnutils/xmms-shn/)

Anything else that anyone’s uses or maintains?

If you have a virtual machine or an extra box to play around with it might be a good idea to compile your things somewhere else then your production system, but a similar environment, since it most likely will send you in dependency hell, chasing packages discerned from compiler output and with the aid of the higher spirits of telepathy. I just couldn’t be bothered to keep track of them. I know, I should have extracted it from the Apt logs and and and …

Anyway, in the end you have a system with a load of stuff that you don’t need and I ended up doing a fresh install, but I mostly do that when a new distro comes out, - first install it to check it out, stress it and try different things, before settling for a plan for the final, hopefully, install. NOTE: If you do it this way do remember to use checkinstall, which generates .debs that you can use the second time around. That is also how you should do it in a virtual or other machine, so that you can transfer it to your favourite stable machine where you just want to play music while you work on something else.

[RIGHT]:guitar:[/RIGHT]

---

### Post by init1 on 2008-11-15
> **Artificial Intelligence said:**
> It's far from perfect and have some annoying bugs as well.
Yeah, well Audacity has one MASSIVE bug, where it won't load anything from the command line. For example, doing a 
```

audacity random.mp3 

```
will load the previous playlist instead of loading the file.

---

### Post by K.Mandla on 2008-11-15
> **Polygon said:**
> gtk 1.2 is ugly.
Not necessarily. 

[[img]http://xs433.xs.to/xs433/08466/icewm-arch-617.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs433&d=08466&f=icewm-arch-617.jpg)

That's GTK1.2.

And as I think has been mentioned, there's [an XMMS deb on Launchpad]("https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2") for Hardy you can install manually. :)

---

### Post by init1 on 2008-11-15
> **K.Mandla said:**
> Not necessarily. 

[[img]http://xs433.xs.to/xs433/08466/icewm-arch-617.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs433&d=08466&f=icewm-arch-617.jpg)

That's GTK1.2.

And as I think has been mentioned, there's [an XMMS deb on Launchpad]("https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2") for Hardy you can install manually. :)
Most people would consider that ugly.

---

### Post by Polygon on 2008-11-15
thats about the best gtk 1.2 can do, besides change the colors of the widgets and all that.

---

### Post by Perfect Storm on 2008-11-16
> **init1 said:**
> Yeah, well Audacity has one MASSIVE bug, where it won't load anything from the command line. For example, doing a 
```

audacity random.mp3 

```
will load the previous playlist instead of loading the file.


Audacity? We're talking about Audacious.

---

### Post by Kosimo on 2008-11-17
> **init1 said:**
> Yeah, well Audacity has one MASSIVE bug, where it won't load anything from the command line. For example, doing a 
```

audacity random.mp3 

```
will load the previous playlist instead of loading the file.

you may mean audacious
Anyway you're right about that bug.. But, has been fixed.
If you're using Intrepid, install it from official repos and you'll see that now works perfectly.

---

### Post by Kosimo on 2008-11-17
> **K.Mandla said:**
> Not necessarily. 

[[img]http://xs433.xs.to/xs433/08466/icewm-arch-617.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs433&d=08466&f=icewm-arch-617.jpg)

That's GTK1.2.

And as I think has been mentioned, there's [an XMMS deb on Launchpad]("https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2") for Hardy you can install manually. :)

That .deb worked perfectly on intrepid! I'm using it right now. Thanks!

---

### Post by K.Mandla on 2008-11-17
No problem. I use that deb in the Ubuntu GTK1.2 Remix, which is why I knew about it at all. Luckily some distros still include XMMS (ahem - Arch - ahem!), so if you're willing to switch allegiances, I suppose that's as good a reason as any.

---

### Post by rugbert on 2008-11-24
ugh! Why is xmms.org down! I installed audacious but it has no streaming support, I installed xmm2 and it has not gui, I have amarok but its kidna bloated for what I want. Is there a mirror I can get xmms from?

---

### Post by K.Mandla on 2008-11-24
If you want the source code, you can get it from the Ubuntu package site.

[http://packages.ubuntu.com/gutsy/xmms](http://packages.ubuntu.com/gutsy/xmms)

The link is on the right. It's not the newest version, but as far as I know, Debian never picked up the dot-11 release, so Ubuntu never picked it up either. 

The md5sum on that file should match the one from the xmms.org repository, if that's necessary.

---

### Post by BLTicklemonster on 2008-11-24
> **Artificial Intelligence said:**
> 1) It's ancient and havn't been maintained for a very long time (including security).
2) It depends on GTK1.2 which AFAIK is obsolite.

Solution;

Use Audacious

Bah, who would use obsolite in the first place? Go for the gusto, get the full obso package, and let the wimps use the lite version.

No wait, it's obsolete now. My bad.

Yeah, audacious or maybe songbird....

Slap, me, AI, you know you want to!

:lolflag:

---

### Post by Perfect Storm on 2008-11-24
Your wish is my command.

*SLAP*

---

### Post by BLTicklemonster on 2008-11-24
[IMG]http://climbatizeut.users.btopenworld.com/f-smilies/f-lol_hitting.gif[/IMG]

---

