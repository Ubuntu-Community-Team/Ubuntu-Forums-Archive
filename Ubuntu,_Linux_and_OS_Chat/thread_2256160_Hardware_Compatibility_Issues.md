---
title: "Hardware Compatibility Issues"
date: 2014-12-10
forum: Ubuntu, Linux and OS Chat
---

### Post by trivialpackets on 2014-12-10
It has been so long since I have had issues with hardware compatibility, that I had completely forgotten how absolutely frustrating it can be.  I vaguely remember it way back in the day, but it's seriously been a while.

I've been running a Dell laptop for quite some time, and it has run well.  Due to a need for a webcam for programming communication, I have endeavored to make the switch to an HP that I had previously had Windows 7 on for my wife.  Backed up and wiped both machines, put Windows on my machine for my wife and restored all of her data.  That worked ok.  This HP has been a bugger.  I've tried 32 bit, 64 bit, KDE, Gnome, Unity and in both 14.04 and 14.10 in multiple flavors and all have only marginal levels of success.  All of them have some difficulty until I get the legacy NVIDIA drivers installed (KDE more than others), but then they get up and running.  Once they are up and running, it's a hot mess.  Apps freezing, the entire desktop freezing.  Problems that I have never had with the same apps on the other laptop.  I actually got so frustrated by it, that I almost put Windows on it, but needed it for dev work.

Currently, had to move over to OpenSUSE 13.2 Gnome, which is working much better thus far.  I like my Ubuntu ways, so if I can ever afford a new machine, I'm sure I'll be back over, but for now, this thing has already cost me more time than I can afford to spend on it.  As someone who uses linux almost exclusively while not at work, I can definitely see how hardware incompatibility could drive away a new user.  With that said, OpenSUSE has thus far been a pretty good experience, just different and worth a look for anyone.

---

### Post by TheFu on 2014-12-10
Using virtualization removes almost all compatibility issues for me and almost any machine can support that these days well enough for work stuff - office productivity applications.  It is just the high-end graphics that is still an issue for virtual machines.

Virtualbox on the host (assuming Windows), then give a guestOS 15G of disk and be happy.

I've avoided HP/Compaq systems since they sold some crap in the late 1990s that wasn't stable running the pre-installed OS more than a few hours while doing nothing before crashing. For about 18 months there were weekly firmware updates - none helped with stability.  Since that time, I've built my own systems do ensure I'm not screwed again ... except for laptops - but I still avoid HP.  "Fool me once ...."

---

### Post by trivialpackets on 2014-12-10
Thanks.  The windows route with virtualbox may be where I end up, unless this experiment on OpenSUSE works out well.  It's mostly ruby on rails web app development and side projects that I'm working on, and maybe I could try developing on Windows, but last time I tried that, it went horribly.

From what I've gathered, the development can be done better on Windows now than it used to be, but it may add complexity to deployment, which isn't really something I want to add.  :)

We'll see how it goes.

---

### Post by TheFu on 2014-12-10
RoR development needs to be on Linux. Doing it on Windows sucks, to say it nicely.  File systems that are not case-sensitive are the main issue - NTFS is the problem.  Plus the cmd/powershell shells suck compared to bash/zsh on UNIXen.

---

### Post by trivialpackets on 2014-12-10
I'm not disagreeing with you.  Just because you can do it, doesn't mean you should.

---

### Post by TheFu on 2014-12-10
> **trivialpackets said:**
> I'm not disagreeing with you.  Just because you can do it, doesn't mean you should.

It isn't just the ruby dev stuff, but all the supporting tools just don't "feel-right" on Windows.  git, cucumber, rspec, plus you'll need a real DBMS - pg on Windows? How good is that?  Plus vim doesn't feel right on Windows either. ;)  Ok, that's my real reason. ;)

I'd also like to clarify - HP servers for HP-UX are completely fantastic. They run forever and work.  Sometimes these servers last longer than makes financial sense for companies.  I've swapped out 32-way servers for newer, faster, 8-way servers and the savings in Oracle license costs paid for the new servers.  Not to mention smaller rack use, less power, and lower license costs for all the other sw an enterprise puts on their servers .... 

I work with beginners learning Ruby. The people working on Windows tend to drop out, but that probably has more to do with their general programming skill than anything else.  Beginners on Windows tend to have been taught programming using IDEs.  In the beginner classes, they have everyone use a free online RoR development environment with a nice web GUI. That removes any of the initial setup issues.  That gets me thinking ... could you setup a Linux box anywhere, get the RoR development stuff setup there and use remote tools to perform development?  Putty copy/paste isn't bad and with a few windows open, it is workable.  

Here's a guy [using an iPad and linode VM]("http://yieldthought.com/post/31857050698/ipad-linode-1-year-later") for his job.  BTW - I also have my main desktop used for webapp devel (perl and ror) in a private cloud accessible from anywhere in the world.  For everything except video, it works nice.  For most corporate jobs, this won't work, but for freelancers and small companies, it can.

---

### Post by trivialpackets on 2014-12-11
That is definitely a consideration and something that I have been thinking about.  It would allow for me to have remote access to it from wherever and on whatever machine, depending on how I set it up.  Definitely an option.  I worked on a project like that years ago, but it was internally on a LAN, rather than with potential access from the internet, so I'm not positive on how performance would be for that.  

If primarily going ssh only and using vim as my editor, I'm sure it would be plenty, at least for the editing, then if I opened up a port for wherever I run the dev server on, I could view remotely as well while doing dev.  I wouldn't say I'm necessarily sold, but I might be.

At that point, my next notebook could be Windows, Mac, Linux or even a Chromebook.  Wouldn't necessarily matter all that much.

---

### Post by TheFu on 2014-12-11
x2go works over the ssh port - no other ports need be opened.
It also supports ssh-key based authentication.
If you run fail2ban or denyhosts on the remote system, that makes for a fairly secure connection, with excellent performance. 

I would NOT open ports for any development servers - just too dangerous.

---

### Post by trivialpackets on 2014-12-11
It's a risk based decision, like most.  Any internet connected ubuntu machine I set up is running a default firewall config to deny all incoming on all ports.  

If I were to open a port for remote development, it would be opened 'while developing' and testing the rails app, and closed afterwards and not on the default port.

As often as I get to develop currently due to time and family restrictions, I don't see it as a very high risk option.  With that said, I  haven't used x2go, so I may give it a shot either way.  Thanks!

---

