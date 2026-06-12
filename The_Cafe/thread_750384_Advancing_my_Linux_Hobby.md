---
title: "Advancing my Linux Hobby"
date: 2008-04-09
forum: The Cafe
---

### Post by natibo on 2008-04-09
I have spent the last few months playing around with Linux and really enjoy it as a Hobby.  I would like to get more advanced.  Become a "power user" and maybe even get into some programming.

I have a mechanical engineering degree but am a patent attorney by trade.  I did some programming a looong time ago with what is now ancient languages (Pascal anyone?).

I would like some advice on how to get started.  First, I would like to become more familiar with the command prompt so that I better understand what it is I am typing.  Would like to know more about the Linux/GNOME architecture  so I can edit files to manipulate my machine better.  After all of that, I would like to get my feet wet with some programming.  What language is best to start off with, etc.

I don't relish going back to school, so book and website recommendations would be best.  Maybe a weekend, or weeklong starter course might be OK.

Thanks.

---

### Post by reyfer on 2008-04-09
Here, these have been great for me to learn about the CLI

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

---

### Post by notwen on 2008-04-09
[http://linux.die.net/man/](http://linux.die.net/man/)  <--- man every command you find to see it's full ability.(fyi- hit 'q' to exit man pages)

For starters work on making simple bash shell scripts using simple terminal commands.  From there you may want to consider python or mono.  LaRoza has a excellent page giving a brief explanation of each language and which may be more inclined to you.  Have a look [here]("http://laroza.pbwiki.com/HowToChoose").  Best of luck.  =]

---

### Post by MrFSL on 2008-04-09
Well I have a few suggestions:

1) O'Rielly Press: [http://www.oreilly.com/pub/topic/linux](http://www.oreilly.com/pub/topic/linux)
There are some great books out there. I have pointed people to "Running Linux" in the past and have gotten positive feedback.

2) Linux From Scratch: [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
As a hobby once I built a LFS computer and learned ALOT about how Linux is put together - the location of files - the boot sequence - service management - etc.

3) Of course tinkering is the best learning on Linux I think.

---

### Post by jonabyte on 2008-04-09
try installing the server version on a spare computer, if you have one.

it does not install a gui desktop by default and try to avoid the urge to do so, you will quickly learn commands and their meaning.

---

### Post by billgoldberg on 2008-04-09
> **jonabyte said:**
> try installing the server version on a spare computer, if you have one.

it does not install a gui desktop by default and try to avoid the urge to do so, you will quickly learn commands and their meaning.

You don't need to install the server version, the desktop version can be run without starting the xserver.

I planning to do the same. (running ubuntu without a gui, just to get to know the cli better) 

But I have a few questions:

If you only have a cli enviroment, will you be able to use programs like firefox, exaile, ... ? I think not, but want to be sure.

I know you can play music using the cli, but can be play videos? I don't think so, but again, not 100% sure.

Can you chat with people on msn using the cli?

---

### Post by days_of_ruin on 2008-04-09
LaRoza's wiki [http://ubuntuprogramming.wikidot.com/one]("http://ubuntuprogramming.wikidot.com/one")

As for what language I would highly recommend python.

---

### Post by TeraDyne on 2008-04-09
> **billgoldberg said:**
> You don't need to install the server version, the desktop version can be run without starting the xserver.

I planning to do the same. (running ubuntu without a gui, just to get to know the cli better) 

But I have a few questions:

If you only have a cli enviroment, will you be able to use programs like firefox, exaile, ... ? I think not, but want to be sure.

I know you can play music using the cli, but can be play videos? I don't think so, but again, not 100% sure.

Can you chat with people on msn using the cli?

Web: elinks and lynx are good CLI web browsers. Personally, I like lynx.

Email: mutt or pine

Music: MPD (music player daemon) and MPC (music player client)

Video: Doubt it.

chat: I don't know about msn, but there's "irssi" for IRC chat.

Wait, a quick "apt-cache search" turns up a multi-protocol IM client called "centerim". It looks like it has MSN support.

---

### Post by Barrucadu on 2008-04-09
If you want to learn how to use the CLI, just read these forums. That's taught me how to use every command I have ever needed, and I'm just as confortable in a CLI as a GUI. In fact, I often use my computer as CLI-only, and have a CLI-only option in GRUB.

---

### Post by fela on 2008-04-09
> **billgoldberg said:**
> I know you can play music using the cli, but can be play videos? I don't think so, but again, not 100% sure.

I don't see how you would go about playing a video using a framebuffer (tty)...

edit: I've had an idea - if the video wasn't too large, could there be a program that converts each frame to ascii art while it's playing? crazy idea, but sounds feasible ;)

---

### Post by billgoldberg on 2008-04-10
> **TeraDyne said:**
> Web: elinks and lynx are good CLI web browsers. Personally, I like lynx.

Email: mutt or pine

Music: MPD (music player daemon) and MPC (music player client)

Video: Doubt it.

chat: I don't know about msn, but there's "irssi" for IRC chat.

Wait, a quick "apt-cache search" turns up a multi-protocol IM client called "centerim". It looks like it has MSN support.

Thanks, I'll give those programs a try this weekend.

---

### Post by simonalpha on 2008-04-10
Apparently both VLC and MPlayer can play through the framebuffer, not exactly sure how though. In MPlayer, I think it's an option like "-vo fbdev". TWIN is also worth a look, a terminal window manager.

---

### Post by D.N.Angel_1993 on 2008-04-10
Vlc works you just have to install it and it plays both music and movies on gui and cli ,just type this in the terminal:  sudo apt-get install vlc

---

