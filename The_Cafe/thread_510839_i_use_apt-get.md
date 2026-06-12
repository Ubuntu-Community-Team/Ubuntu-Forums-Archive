---
title: "i use apt-get"
date: 2007-07-27
forum: The Cafe
---

### Post by tomcheng76 on 2007-07-27
i heard that aptitude handles dependencies better when u try to uninstall thing

but i am used to apt-get, so who are using aptitude?

---

### Post by mcduck on 2007-07-27
Aptitude *used to* handle dependencies better when removing packages. Today apt-get has autoremove function which gives same results..

I use apt-get. I've tried aptitude couple of times but it didn't seem as reliable as apt-get is.

---

### Post by mostwanted on 2007-07-27
Sometimes aptitude, sometimes apt-get, sometimes Synaptic. It depends on the task at hand.

---

### Post by AlexenderReez on 2007-07-27
i use apt-get for most of software installation and use aptitude for install kubuntu-desktop:)

---

### Post by cunawarit on 2007-07-27
apt-get almost all the time...

---

### Post by LookTJ on 2007-07-27
I use pacman in Arch. I don't use Ubuntu atm.

---

### Post by Corvo78 on 2007-07-27
Well... since most tutorials and guides use *apt-get*, that's what I ended up using.
Although I do use Synaptic a lot as well. And at the moment the usage is about 50-50.
I have tried aptitude though (on my laptop), but I usually ended up typing apt-get... it's a habit.
And habits, are hard to break ;)

---

### Post by ssam on 2007-07-27
apt-get with new autoremove seems to work. is the aptitude equivilent any better?

generally i dont bother with autoremove, because it is usually just tiny libraries that get left behind. if i want to clear disk space i add the installed size column in synaptic and sort by that. then you might find a package that you dont use that is tens or hundreds of megs.

i usually prefer synaptic, unless i know the exact spelling of a package, or am on a ssh conection.

---

### Post by FuturePilot on 2007-07-27
I use apt-get to install most things. But I do use aptitude sometimes if I'm dealing with a lot of dependencies or meta packages like one of the desktop environments.

---

### Post by AndyCooll on 2007-07-27
I use Synaptic (the front-end for apt-get) mostly. And command line apt-get occasionally.

:cool:

---

### Post by Tmi on 2007-07-27
I've always used aptitude because when I started with Ubuntu it handled dependencies better. I've never had any problems with it so that's what I still use.

---

### Post by Sayers on 2007-07-27
I can't tell the difference.

---

### Post by LaRoza on 2007-07-27
I use aptitude.

---

### Post by euler_fan on 2007-07-27
Just to be different I voted for the configure/make/make install option even though I usually use synaptic, there are several programs which I install from source (after verifying signatures and checksums . . . )

---

### Post by Nikron on 2007-07-27
pacman is what I use

---

### Post by Foxmike on 2007-07-27
I use apt-get in Ubuntu since I installed kubuntu-desktop with aptitude, and then unsinstalling it to be able to remove all those bluetooth things, now each time I want to use aptitude, it tells me that I have xxx packages no longer needed and those will be removed (all kde related packages for instance), which is bad.

I love portage from Gentoo and I dream about a mix of apt-get and portage... the best of the two extremes, I guess!:)

---

### Post by eentonig on 2007-07-27
> **ssam said:**
> ...

i usually prefer synaptic, unless i know the exact spelling of a package, or am on a ssh conection.

Probably a redundant remark, but just in case:
I had the same. Now I use

> apt-cache search <part of package name/description>
sudo apt-get install <result of previous output>

Even when I have to use apt-cache a few times before narrowing down my list of possibilities to a manageable size, it has proven to be faster for me.

---

### Post by guitarmaniac on 2007-07-28
I would use aptitude if synaptic used it, but it uses apt-get so I'd rather only use the one.

---

