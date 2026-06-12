---
title: "Is cygwin any good?"
date: 2013-01-26
forum: The Cafe
---

### Post by monkeybrain2012 on 2013-01-26
In my Windows days I have tried it to learn Linux and use some Linux applications. But it was always horrible, pulled in a whole bunch of stuffs and x window crashed on me all the time, kind of like a monstrously huge and slumbering twin of WINE from the evil parallel universe. It was much easier to go full blown Linux (have used Ubuntu Debian CentOS and Fedora since)

Now I am in the mood and want to try it again on VM (I am WIndows free except on VM :))  Wonder if anyone has tried it lately and what do you think of it.

---

### Post by kevdog on 2013-01-27
I'm not sure what this thread has to do with cygwin. cygwin basically gives you a good set of posix tools which you can run linux commands at a shell prompt -- yes they include an X windowing system but its crashes enough to drive my batty so I don't even use that.  I due however run an ssh daemon via cygwin from windows so I found that very useful

In all honesty there is no substitute for linux rather than running linux.  The hardest part about running linux in my mind is getting used to the commands to do things.  No matter how good the linux GUIs are -- and there are a ton of them, you are always going to have to get your hands dirty and do things running at a command prompt.  There really is no substitute for this. Once you get over the learning curve of basic commands, you'll be good.

---

### Post by forrestcupp on 2013-01-27
I think cygwin's uses are pretty minimal. A better choice for running Linux apps in Windows is [andLinux](http://www.andlinux.org/). I'm not sure how well it's still supported, and it looks like it only works with 32-bit Windows.

---

### Post by freetolio on 2013-04-19
I wouldn't use it to learn Linux, but Cygwin is good for what it is. If you want easy access to editors, several scripting languages, a decent terminal, ssh, and some other tools, it is pretty good compared to installing a bunch of separate Windows programs.

The X functionality has always been more stable for me than Putty + XMing on Windows (especially on server editions), and with the apt-cyg tool you don't have to fire up the windows GUI program to add features. Having used it years ago, I was surprised at how much better it is now when I started using it a few months ago on Windows boxes at work.

That said, I don't bother with it on systems where I have a choice. Running a real Linux distro is the way to learn it.

---

### Post by sudodus on 2013-04-19
I used cygwin about ten years ago and was quite happy with it. I'm glad to read that it is even better now. I have Windows but hardly run it any more (except when it is necessary for some special hardware or software). So I don't need cygwin, I use linux. It is easy to carry linux on a USB pendrive for use in other people's computers.

---

### Post by duke.tim on 2013-04-19
I use cygwin on windows on occasion, though only command tools, none of the non-sense gui stuff (because native windows apps are more stable than cygwin dependent stuff imo).
look at source forge for a windows build of whatever the application is.

The biggest problem i've ran into is tracking down which package contain what tools.

---

### Post by mr john on 2013-04-20
I use it for ssh tunnelling. I've found the free version of Bitvise tunneleir to be faster then Putty for multithreaded tunneling. I also like that it automatically reconnects unlike putty. Meaning that i can use my British ip address to watch streaming video while I'm abroad. I think cygwin is part of the backend of bitvise.

---

### Post by forrestcupp on 2013-04-20
Can you use cygwin to run Cinelerra in Windows?

---

### Post by kevdog on 2013-04-21
What's cinelerra?  I've found with most things, cygwin will actually run most linux programs, but with many you may have to compile from source.

---

### Post by forrestcupp on 2013-04-22
> **kevdog said:**
> What's cinelerra?  I've found with most things, cygwin will actually run most linux programs, but with many you may have to compile from source.

[It's a pretty decent video editor](http://cinelerra.org/) that only works in Linux.

---

