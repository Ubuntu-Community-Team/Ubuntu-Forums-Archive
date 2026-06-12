---
title: "Ubuntu Server GUI?"
date: 2011-01-29
forum: Server Platforms
---

### Post by twtrout on 2011-01-29
Hello,
I am new to Ubuntu Forums but have been using Ubuntu Desktop off and on since Hardy Herron. I have just installed Ubuntu Server 10.10 on an older IBM PC Server 325 that I have and am struggling with Bash since it installed as a non-GUI installation. I was very comfortable with the command line back in MSDOS 4.0 days and later but just don't have the time to acclimate to oe learn a new command line OS and/or can't find a good Bash guide. Is there a GUI interface that I can add on top of Server 10.10 until I pick up an understanding of the Linux/Ubuntu command line?
Thanks,
TW

---

### Post by CharlesA on 2011-01-29
You can install gnome-core if you want a really basic GUI.

However, it's normally better/more secure to just leave it without a GUI unless you absolutely need it for something.

See here: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by twtrout on 2011-01-29
CharlesA,
 
Thanks! I will give X11 a whirl. I just need a minimal GUI interface I can be productive with until I can pick up an understanding of the Linux/Ubuntu command line.
 
TW

---

### Post by fela on 2011-01-29
From my experience, the only way to start being productive with the command line is to use that as your primary interface. In my opinion, GUIs have no place on servers and I advise you to learn how to use the command line :)

---

### Post by HermanAB on 2011-01-30
Howdy,

The GUI version of Ubuntu server edition is regular Ubuntu...

---

### Post by clasificados on 2011-01-30
> **twtrout said:**
> Hello,
I am new to Ubuntu Forums but have been using Ubuntu Desktop off and on since Hardy Herron. I have just installed Ubuntu Server 10.10 on an older IBM PC Server 325 that I have and am struggling with Bash since it installed as a non-GUI installation. I was very comfortable with the command line back in MSDOS 4.0 days and later but just don't have the time to acclimate to oe learn a new command line OS and/or can't find a good Bash guide. Is there a GUI interface that I can add on top of Server 10.10 until I pick up an understanding of the Linux/Ubuntu command line?
Thanks,
TW

Hey dude just install webmin, you should be able to control most of your servers settings via its web interface.
Installing X on a server is never a good idea.

---

### Post by ryannathans on 2011-01-30
> **fela said:**
> From my experience, the only way to start being productive with the command line is to use that as your primary interface. In my opinion, GUIs have no place on servers and I advise you to learn how to use the command line :)

> **clasificados said:**
> Hey dude just install webmin, you should be able to control most of your servers settings via its web interface.
Installing X on a server is never a good idea.


Agree with both of these. Webmin uses port 10000 by default and https, so it's quite secure and shouldn't interfere with anything else. Plus it has great documentation and is easy to set up, I have this on my ubuntu server 10.04 with NO GUI. It's great!

GUIs have no place on the server unless it is an absolute must, in addition to adding security problems it also tends to hog resources, something you don't want on servers, if you MUST get a GUI go for something like [xmonad]("http://en.wikipedia.org/wiki/Xmonad") (less than 1200 lines of code) or [wmii]("http://en.wikipedia.org/wiki/Wmii") even [Blackbox]("http://en.wikipedia.org/wiki/Blackbox") or [Fluxbox]("http://en.wikipedia.org/wiki/Fluxbox") should be fine. Have a look at [this]("http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments") if you REALLY MUST have a GUI.

-ryannathans

---

### Post by eentonig on 2011-01-30
My advice would be to leave your server without any GUI. Just enable ssh and work from your Ubuntu desktop. 

You can search for all the necessary commands and config options via your regular tools and copy& paste them to your server over ssh.

---

### Post by fela on 2011-01-30
> **eentonig said:**
> My advice would be to leave your server without any GUI. Just enable ssh and work from your Ubuntu desktop. 

You can search for all the necessary commands and config options via your regular tools and copy& paste them to your server over ssh.

Yes, that's what I do with my server (well, my server runs Debian and I SSH it primarily from a Windows box).

I also think, something about servers is you really should only expose it to the outside world if you're fairly knowledgeable that it's all configured correctly, and this I'm afraid involves using the CLI (at least on *nix/Linux servers). A badly configured web server is a recipe for disaster.

A big difference between Linux and Windows is that Linux is based around text configuration/CLI administration as opposed to Windows tasks that can only be accomplished using the GUI (although I've heard that's changed a bit with Powershell), and this is why I also think Windows has no place on servers.

There are plenty of tools available to simply the task of configuring (such as webmin), but when it comes down to it it's all a bunch of text files that you must get right. GUI tools have the potential to go wrong, but in a config file, what you see is what you get ;)

On the other hand, if all you want is a local, say media or file server (or even web server running on the local network maybe), then you can get a GUI if you really want. How are you thinking of running it though? I run my server headless (no display or keyboard), so you'd either have to run it with those (and a mouse, heaven forbid!), or VNC it from a desktop PC. I think either of those would be quite cumbersome don't you think?

---

