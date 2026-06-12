---
title: "Jaunty Wine packages dont install on karmic"
date: 2009-10-02
forum: Wine
---

### Post by Meow27 on 2009-10-02
this wasn't a problem with ubuntu jaunty when installing intrepid package files..... but here is what i do

i install libaudio2, as required by all wine packages, then when i run any win deb, i get this failure output
```
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>:Bad file descriptor
```

does anyone have any Karmic Wine packages i can use?

edit----

im referring to recent wine versions, not 1.0.1

2nd edit---
the wine package from the repos give the same output
mind i also add that im on a livecd right now

---

### Post by amauk on 2009-10-02
```
sudo apt-get install wine1.2
```

---

### Post by Meow27 on 2009-10-02
> **amauk said:**
> ```
sudo apt-get install wine1.2
```

didnt work, probably cause im on a live cd right now :/

---

### Post by hikaricore on 2009-10-02
Works fine for me, I've been using Karmic since pre-alpha too..
Sounds like something is wrong with your install.

---

### Post by Meow27 on 2009-10-02
its a livecd...


do you think it will work if i get a persistance file into it?

---

### Post by Capt. Blackwood on 2009-10-03
A live cd, from my experiance, is a full feature demo of the operating system. The only primary limitation is...you can't install anything on it. You can surf the web, access your stuff...the list goes on. But you cannot install.

---

### Post by hikaricore on 2009-10-03
You can install things on a livecd just fine.
All you have to be sure if is that you have enough ram.

---

### Post by Meow27 on 2009-10-03
well, i tried it on my desktop and have the same problem, should i download the livecd all over again and try it out again?

---

### Post by gordion on 2009-10-28
> **hikaricore said:**
> Works fine for me, I've been using Karmic since pre-alpha too..
Sounds like something is wrong with your install.

hikaricore, which wine version did you install on karmic? i've installed the last one for jaunty (wine 1.1.32) but it gives an error. i guess there is no wine version for karmic so far? i have to install wine immediatly, i can't wait until they release new wine version for karmic :D

---

### Post by dino99 on 2009-10-28
last release is there:

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main

add this in your sources.list

in a console, run:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0

then update, safe-upgrade

---

### Post by gordion on 2009-10-28
with wine, is it possible to run the programmes that are already installed in windows partition?
i reinstalled wine, it just works if i setup the programmes, but even for winamp and windows messenger, they don't work properly. i can't play an song, i can't log in. i don't know what if i install hardr programmes.

---

### Post by hikaricore on 2009-10-28
Depends on the software.

Older versions of winamp before they bloated it and made a damn mess would work fine.
Hell I used to copy them from system to system on windows years ago, but now everything is a mess.
You'll need to install most software though wine BEFORE you can run it, being sure to follow any specific directions on the appdb or a howto guide in some cases.
Why are you trying to run winamp on linux when there are hundreds of native alternatives for music playback?

---

### Post by Meow27 on 2009-10-28
> **hikaricore said:**
>  winamp on linux when there are hundreds of native alternatives for music playback?

because programs like audacious suck because they are too quiet by defualt.

and winamp has its own winamp feel. (though it lacks codecs for ogg :x)

anyhow, the problem doesnt persist in the RC of karmic so im marking this thread [/solved]

---

