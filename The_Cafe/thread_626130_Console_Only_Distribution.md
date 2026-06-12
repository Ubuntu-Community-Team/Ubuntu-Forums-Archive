---
title: "Console Only Distribution"
date: 2007-11-28
forum: The Cafe
---

### Post by euchrid on 2007-11-28
Does anybody know of a really good, impressive console only distribution of Linux?

I found one: [http://www.puppylinux.org/user/news.php?readmore=23]("http://www.puppylinux.org/user/news.php?readmore=23")
It doesn't look like a lot of fun, though.

I know Damn Small Linux and Puppy Linux are small and brilliant - but that's not what I'm after. I want console ONLY - no, or very little GUI. Also, I don't mean just going to tty1-6 or running the recovery version of Ubuntu; I mean an actual distribution that comes with nearly every command line/console application you could want, and access to decent repositories built in. Can it be done?

Now, I know what you're thinking: why would anyone want such a thing? Well, I think it would help people new to Linux to realise just what can be accomplished from the command line, what goes on underneath all the GUI, how fast the command line can be, a great way to learn the command line (by having to), etc. 

But also, there are weird people like me. I started using Linux a year ago, and during that time, I have found that I am starting to prefer running certain things only in the console. Music, file management, batch processing of images, reading e-mails, writing... I don't need a GUI for any of that; in fact, it only gets in the way and slows things down (I now realise).

Here are the applications I have found that give the best idea of what I would like packaged and ready in a console only distribution:
cmus - brilliant music player, easy to use and get used to
mcdp - cd player that just plays cds
Midnight Commander (mc) - useful and quick file browser without all the confusing emblems and clutter and crashing problems
raggle - RSS reader that is simple and easy to read
lynx - text browser useful for those with disabilities, but also for viewing sites like WIkipedia when you just want to read the text
w3m - as far as I can tell, like the above, but with pictures
dict - (with dictd) a dictionary from the command line
gtypist - learn to touch type!
mutt - send and receive e-mails
talk - talk to users on the network (great for annoying my girlfriend)
aview - ascii art - can turn pretty much any image into ascii art; view images in the console!
nano - text editor
vi and emacs - complicated but obviously brilliant text editor and... well, whatever emacs is (a hell of a lot of things)
csound - make extremely complicated music in an extremely complicated way

and on and on... you get the idea. I know not all of these would be suitable for novices, but with the right documentation and perhaps a bit of tweaking - could (we or) someone make a console only distribution? Maybe even 'Clibuntu'?

Perhaps, given the difficulties involved in setting up networks and wireless routers and such, there should be a graphical display just to get things running - or perhaps this distribution could sit inside another one (like the excellent dyne:bolic does). The point of it all, as suggested above, is both to get someone used to command line and its possibilities and to provide a fast, convenient set-up that just gets on with things... any suggestions? Any takers?

---

### Post by bruce89 on 2007-11-28
Debian with no optional packages is probably a good thing to use.

---

### Post by euchrid on 2007-11-28
I'd like to point out, I've not turned into a complete nerd; I still use Ubuntu, and will continue to, because it's fantastic (and I can't run GIMP entirely in the command line - or can I?). This would be a supliment, not a replacement!

---

### Post by scorp123 on 2007-11-28
> **euchrid said:**
> Does anybody know of a really good, impressive console only distribution of Linux? ...  could (we or) someone make a console only distribution? Maybe even 'Clibuntu'?  Ubuntu Server :lolflag:

32-bit PC (Intel x86):
[http://releases.ubuntu.com/7.10/ubuntu-7.10-server-i386.iso](http://releases.ubuntu.com/7.10/ubuntu-7.10-server-i386.iso)

64-bit PC (e.g. AMD-64):
[http://releases.ubuntu.com/7.10/ubuntu-7.10-server-amd64.iso](http://releases.ubuntu.com/7.10/ubuntu-7.10-server-amd64.iso)

---

### Post by euchrid on 2007-11-28
> **bruce89 said:**
> Debian with no optional packages is probably a good thing to use.

Whoa! OK. Is it that easy? Can't believe I couldn't find that out before!

But does Debian and Ubuntu Server come with everything ready to go, as mentioned above? (i.e. music players, text browsers, etc?)

---

### Post by init1 on 2007-11-28
> **euchrid said:**
> Does anybody know of a really good, impressive console only distribution of Linux?

I found one: [http://www.puppylinux.org/user/news.php?readmore=23]("http://www.puppylinux.org/user/news.php?readmore=23")
It doesn't look like a lot of fun, though.

I know Damn Small Linux and Puppy Linux are small and brilliant - but that's not what I'm after. I want console ONLY - no, or very little GUI. Also, I don't mean just going to tty1-6 or running the recovery version of Ubuntu; I mean an actual distribution that comes with nearly every command line/console application you could want, and access to decent repositories built in. Can it be done?

Now, I know what you're thinking: why would anyone want such a thing? Well, I think it would help people new to Linux to realise just what can be accomplished from the command line, what goes on underneath all the GUI, how fast the command line can be, a great way to learn the command line (by having to), etc. 

But also, there are weird people like me. I started using Linux a year ago, and during that time, I have found that I am starting to prefer running certain things only in the console. Music, file management, batch processing of images, reading e-mails, writing... I don't need a GUI for any of that; in fact, it only gets in the way and slows things down (I now realise).

Here are the applications I have found that give the best idea of what I would like packaged and ready in a console only distribution:
cmus - brilliant music player, easy to use and get used to
mcdp - cd player that just plays cds
Midnight Commander (mc) - useful and quick file browser without all the confusing emblems and clutter and crashing problems
raggle - RSS reader that is simple and easy to read
lynx - text browser useful for those with disabilities, but also for viewing sites like WIkipedia when you just want to read the text
w3m - as far as I can tell, like the above, but with pictures
dict - (with dictd) a dictionary from the command line
gtypist - learn to touch type!
mutt - send and receive e-mails
talk - talk to users on the network (great for annoying my girlfriend)
aview - ascii art - can turn pretty much any image into ascii art; view images in the console!
nano - text editor
vi and emacs - complicated but obviously brilliant text editor and... well, whatever emacs is (a hell of a lot of things)
csound - make extremely complicated music in an extremely complicated way

and on and on... you get the idea. I know not all of these would be suitable for novices, but with the right documentation and perhaps a bit of tweaking - could (we or) someone make a console only distribution? Maybe even 'Clibuntu'?

Perhaps, given the difficulties involved in setting up networks and wireless routers and such, there should be a graphical display just to get things running - or perhaps this distribution could sit inside another one (like the excellent dyne:bolic does). The point of it all, as suggested above, is both to get someone used to command line and its possibilities and to provide a fast, convenient set-up that just gets on with things... any suggestions? Any takers?
TTY Linux is a good option, but by default it won't have many of the packages you would like. Also, it's only 5MB. 
[http://www.minimalinux.org/ttylinux/showpage.php?pid=1](http://www.minimalinux.org/ttylinux/showpage.php?pid=1)

---

### Post by ynnhoj on 2007-11-28
you'd be better off starting with a very plain base system (whether it be debian, ubuntu server, arch linux, gentoo, etc, etc) and installing all the apps that you want with yer package manager.  it's pretty simple.

---

### Post by scorp123 on 2007-11-28
> **euchrid said:**
>  Whoa! OK. Is it that easy?  "Ubuntu Server" is Ubuntu without anything GUI (no GNOME!); instead lots of server stuff (e.g. Apache web server, and so on) is shipped on the CD's. But during the text mode installation you get asked if you want to install this stuff or not ... And if you say "no" you end up with a CLI-only system without any GUI whatsoever. Ideal for servers (hence the name). But of course nobody is forced to run this stuff on dedicated server hardware. I for example installed on a very old laptop which I use now for MP3 streaming in my house -- for stuff like that it's ideal.

 > **euchrid said:**
>  Can't believe I couldn't find that out before!  Don't worry. Most people associate "Ubuntu" with the Live CD version ... But yes, there is also the "Server" edition which is pretty much stripped down. More details on the differences here:
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

Just found the "Server Guide" which explains how to do things here:
[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

---

### Post by K.Mandla on 2007-11-28
There was a cubuntu that was being touted as a console-only version for a while. I think it may have dwindled away though. ...

[https://wiki.ubuntu.com/Cubuntu](https://wiki.ubuntu.com/Cubuntu)

---

### Post by euchrid on 2007-11-28
Thanks to everyone for your responses.

init1, I like ttylinux. Hadn't come across that before. I think it would be good to build from as ynnhoj suggests, and adding stuff on top - if that's possible, as it so stripped down... still, provides a good model.

scorp 123, thanks for explaining - saves me having to try it out to see if could do what I want!

So far, it doesn't look like any particular distribution fills this particular niche, though; Ubuntu Server and Debian will certainly do what I'm after, but both require a set-up and reconfiguring. Which is fine for me; but I'm thinking, say, of taking this round to people along with and Ubuntu Live CD and Damn Small Linux and Knoppix or whatever, and basically just showing off what Linux can do. Maybe even helping out at a local adult education class...

This 'Clibuntu' would *ideally* run on pretty old machines, load nearly instantaneously, and start playing music and whatever - but all without the GUI. Something that would make people go "Oooh" and "Holy s***!" because they're so used to seeing stuff in shiny windows... But then it would also be a tool where someone new to Linux could simply shove a disk in and start using and learning about command line tools and applications without being put off or scared...

[update]: thanks, K.Mandla - that's damn near it! I can see why they want a new name. My eyes missed the 'u' and the 'b' at a quick glance, and it looks quite offensive. Don't think the project's dead yet, though; some of the pages were edited yesterday!

Can anyone else see why such a distribution would be useful and desirable for certain sectors? Shouldn't schools be teaching command line before they teach GUI? Does anyone else know where I can buy a propeller hat?

---

### Post by -grubby on 2007-11-28
> **euchrid said:**
>  propeller hat?

[http://search.ebay.com/search/search.dll?from=R40&_trksid=m37&satitle=propeller+hat&category0=](http://search.ebay.com/search/search.dll?from=R40&_trksid=m37&satitle=propeller+hat&category0=)

---

### Post by euchrid on 2007-11-28
> **nathangrubb said:**
> [http://search.ebay.com/search/search.dll?from=R40&_trksid=m37&satitle=propeller+hat&category0=](http://search.ebay.com/search/search.dll?from=R40&_trksid=m37&satitle=propeller+hat&category0=)

Wow. I might set up a large IT business and FORCE everyone to wear those to work. Maybe at home, too. The bigger the propeller, the more important the person.

---

### Post by -grubby on 2007-11-28
> **euchrid said:**
> Wow. I might set up a large IT business and FORCE everyone to wear those to work. Maybe at home, too. The bigger the propeller, the more important the person.

nice. :lolflag:

---

### Post by blithen on 2007-11-28
No one mentioned GRML? :/
[http://grml.org/download/#small](http://grml.org/download/#small)
GREAT command line only distro.

---

### Post by Whiffle on 2007-11-28
Or theres always slackware, just don't install X.

---

### Post by nixx on 2007-11-29
i'd second slackware, very nice and fast distro which will work on most of even the lowest spec hardware with no GUI installed. No official package management system though. You could always [roll your own linux]("http://www.linuxfromscratch.org/")

---

### Post by euchrid on 2007-11-29
Thanks again. I'll have a look at GRML and slackware, but it's looking increasingly like I might just do my own distribution, mainly because I'm fussy and want COMPLETE CONTROL (bwahaha, etc.) But all these suggestions at least show me what to do (and not to do). 

It seems for user-friendliness, only the GUIs are suitable for beginners and novices, while the console ones are complicated and required prior knowledge - and it doesn't look like any of them make the console look 'fun' - which it can be, even for a beginner!

If I get this baby off the ground, maybe I'll try a Spectrum Emulator Linux that turns your expensive computer into 48k Spectrum, but with all the power of the Linux command line and tty terminals and such... Or am I the only person that thought when the Spectrum died, so did most of the charm and personality of home computing? (Desktop backgrounds and the internet cannot replace the thrill of typing 200 lines of POKEs just to get infinite lives, not even sure if it will work... Maybe I could even get someone to make a console work in the Spectrum Basic language. Maybe I should lay off the coffee.)

---

### Post by jr.gotti on 2007-11-29
Hit Ctrl+Alt+F1 from your Ubuntu install...there you go! A fully functional, fun, command line only distro!

---

### Post by euchrid on 2007-11-29
> **jr.gotti said:**
> Hit Ctrl+Alt+F1 from your Ubuntu install...there you go! A fully functional, fun, command line only distro!

Err... yeah. Not quite what I was asking for in the initial post, or in any of the posts since, but hey, thanks. Although, you have a point; hit the Power Off button followed by picking up a pen and paper, and you have a simple, user-friendly version of notepad or gedit. Now, if only I could make it available for download...

---

### Post by justin whitaker on 2007-11-29
> **euchrid said:**
> Thanks again. I'll have a look at GRML and slackware, but it's looking increasingly like I might just do my own distribution, mainly because I'm fussy and want COMPLETE CONTROL (bwahaha, etc.) But all these suggestions at least show me what to do (and not to do). 

It seems for user-friendliness, only the GUIs are suitable for beginners and novices, while the console ones are complicated and required prior knowledge - and it doesn't look like any of them make the console look 'fun' - which it can be, even for a beginner!

If I get this baby off the ground, maybe I'll try a Spectrum Emulator Linux that turns your expensive computer into 48k Spectrum, but with all the power of the Linux command line and tty terminals and such... Or am I the only person that thought when the Spectrum died, so did most of the charm and personality of home computing? (Desktop backgrounds and the internet cannot replace the thrill of typing 200 lines of POKEs just to get infinite lives, not even sure if it will work... Maybe I could even get someone to make a console work in the Spectrum Basic language. Maybe I should lay off the coffee.)

Seriously, Euchrid, take a look at GRML. It is console centric, has lots of command line tools, has an easy installer, and can be remastered. 

I often thought of making GRMLbuntu, but who would use it? :)

---

### Post by bonzodog on 2007-11-29
I would also suggest trying out Arch Linux base install. You start out with a CLI only distro, and then just add the apps you want with what I also think is the most powerful package manager out there, Pacman.

alternatively, you could do what I did,and install Zenwalk Linux Core, which only installs the base system, and again, you just add the apps you want using the netpkg package manager.

Arch Linux though is amazingly powerful.

---

### Post by euchrid on 2007-11-29
> **justin whitaker said:**
> I often thought of making GRMLbuntu, but who would use it? :)

Me! 

I will look at GRML in the next couple of days. Will report back with my experiences, just in case there are other freaks that are interested. Thanks again for this suggestion, Blithen and Justin.

---

### Post by Erik Trybom on 2007-12-01
GRLM looks like a nice distribution, but it's mainly targeted at sysadmins as far as I can see. I think what the thread starter wants is a fully-featured distro for the home desktop using only the command line.

Why not just pick a random Debian version, thow in the packages you want with the installation and call it a distro? Couldn't be that much work, could it? 

By the way, I suggest offering the Fish shell as an option. Really nice, especially for beginners.

---

### Post by euchrid on 2007-12-01
> **Erik Trybom said:**
> I think what the thread starter wants is a fully-featured distro for the home desktop using only the command line.

Yes! Thank you! That is exactly it.

> **Erik Trybom said:**
> 
Why not just pick a random Debian version, thow in the packages you want with the installation and call it a distro? Couldn't be that much work, could it? 

By the way, I suggest offering the Fish shell as an option. Really nice, especially for beginners.

Thank you for these suggestions. I am going to try putting my own distribution together, as it looks like the best option, but I think I've got a bit to learn yet. I'm guessing it's not too difficult once you've done it a couple of times - but I'll need those first couple of times yet!

I hadn't heard of the Fish shell before - it looks perfect for a command line distribution. I will try it out, along with all the other options, and report back - eventually. Problems with my stupid website will delay this for a few days...

Thanks again for the helpful feedback!

---

### Post by Dr Small on 2007-12-01
Check this out for a console based live cd distro:
[http://kmandla.wordpress.com/2007/11/29/miniubuntu-710-at-last-a-command-line-ubuntu-live-cd/](http://kmandla.wordpress.com/2007/11/29/miniubuntu-710-at-last-a-command-line-ubuntu-live-cd/)

---

