---
title: "Save me from Fedora"
date: 2005-09-07
forum: The Cafe
---

### Post by supanova on 2005-09-07
Hi All

Strange title to the thread  :grin: , but....

I love Ubuntu to a point...

My problem is that there seems to be very little going on i.t.o the backports. I know I'll be told to post there but there seems to be very little going on in that forum

I need certain very current packages such as subversion trac etc (amongst others) and with Fedora there always seems to be someone contributing and you can find RPMS for the latest of just about everything. I know that more people need to contribute to Ubuntu (including myself ... although I'm more of a java hacker than C... but I don't have time).

What I actually hate about linux is dependency hell. I though that I'd start a subversion (1.2.3) install from scratch (literally). I download the apr and apr-util source and installed in a separate location with --prefix, then moved onto to neon.
I can't remember which one complained about not finding Berkley DB... that I installed from synaptic (was getting irritated). Then onto neon which started complaining about some or the other xml parsers. At this point I was so pissed I gave up. The thing is that Fedora is that there are so many people creating packages out there even though the package management isn't that great with yum etc... at least they exist and I usually don't install all sorts of desktop gadgets as I still use windows for that as you have virtually no problems (aaargh windows.... I know, but it's a fact).

Now it's not like I'm a total newbie... actually a Solaris Certified Admin and have compiled stuff from scratch before and when a tool is complicated it can take days getting it right... but I'm tired of all of this.... I don't want to understand the dependencies when starting with something new... I want to get right into using it and with time will understand all of it's intricacies if I ever want to compile/install from scratch...

Sorry Guys I'm blowing some steam here.

Really there are 2 things

1. Ubuntu must try and put more weight around backports and start interacting with the greater world more so that eventually we can install the latest of just about everything without the problems of dependency hell

2. The opensource community at large needs to wrap their minds around this problem as we'll. I.E. if your software relies on 10 other opensource projects you must remember that people don't care why you are using what you are using nor how you are using it. People simply want to install and start playing... if they like what they see they might go on to become power users and maybe eventually contributors... but if their first brush with your software leaves a bad dependency hell taste on their mouths, they might ignore what could actually be brilliant software. I don't have the answers for how we solve this, but one thing that might be possible is allowing a user to download all code including that of the other open source code that you might be using and the compilation installs everything to one place... yes you might land up with another instance of BDB, apache or whatever, but at least it can be used... then in six months when the user has become a power user he/she might be willing to figure out how to integrate into everything else (if ever needed)....

Anyway that's enough from me...

I'd like opinions and/or experiences on this.... and If you think I'm nuts... you can tell me so... I have broad shoulders  :wink:

Ciao for know

---

### Post by N'Jal on 2005-09-07
It's Ubuntu policy to not really add anything to the distro unless it's a security risk. New features are introduced in the next release.

---

### Post by Burgundavia on 2005-09-07
Ubuntu backports are now hosted on official servers. There is not much more they can do.

Corey

---

### Post by parktownprawn on 2005-09-07
if you really want to [break your ubuntu](https://wiki.ubuntu.com/BreakMyUbuntu?highlight=%28break%29)  you can always see if they have what you want on [http://www.apt-get.org/](http://www.apt-get.org/) which are unofficial apt repositories for debian (and some ubuntu stuff too).

no guarantees that they will work and not to serious damage to your system but then there are no guarantees with random unofficial rpms you download for fedora.

---

### Post by Stormy Eyes on 2005-09-07
Be patient for a couple of months and then Breezy will be out and ready to apt-get.

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=supanova] The thing is that Fedora is that there are so many people creating packages out there even though the package management isn't that great with yum etc... at least they exist and I usually don't install all sorts of desktop gadgets as I still use windows for that as you have virtually no problems (aaargh windows.... I know, but it's a fact).
[/QUOTE]

Backports only gets stuff  already packaged for Sid and the development branch. If neither have a new package, backports can do nothing. This is nothing like the Fedora world, where 3rd parties MAKE all the RPMs from scratch. If that fits you better, Ubuntu cannot save you.

---

### Post by bored2k on 2005-09-07
"Save me from Fedora"
There is nothing to save you from. Fedora Core is a great power house distribution that should be respected just as much as Ubuntu.

---

### Post by lgoss007 on 2005-09-07
Yeah, I have similar feelings on this. Sometimes when a new release comes out for a product, the new version has features that are either needed, badly wanted, or would help tremendously. This is especially true if the product is still young so features are added at a very fast pace (which is very common in the Linux circle).

When I first came to Ubuntu, Warty was out at the time. However I didn't like the fact that it didn't have firefox, so instead I used one of the early Hoary test releases and it was working fine. So now I'm using Breezy so that I get all of the newest packages.

I do remember a few months back someone mentioning that there might be an Ubuntu developer release in the future that would be an ongoing distribution (all of the latest packages). I still hope that will happen.

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=lgoss007]
I do remember a few months back someone mentioning that there might be an Ubuntu developer release in the future that would be an ongoing distribution (all of the latest packages). I still hope that will happen.[/QUOTE]

That exists now. Thats is what Breezy is. What you heard is a plan to give the development branch a name (Grumpy) until it is released.

---

### Post by lgoss007 on 2005-09-07
Ah yes, [GrumpyGroundhog](https://wiki.ubuntu.com/GrumpyGroundhog) is the name. However when I look at that page it doesn't appear to be implemented yet  :-?

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=lgoss007]Ah yes, [GrumpyGroundhog](https://wiki.ubuntu.com/GrumpyGroundhog) is the name. However when I look at that page it doesn't appear to be implemented yet  :-?[/QUOTE]

I think thats for the next release.

---

