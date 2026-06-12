---
title: "Internet Accountability Software"
date: 2007-01-28
forum: Ubuntu Christian Edition
---

### Post by bsalt on 2007-01-28
Hey, I am looking to get a program that does not quite focus on internet filtering (especially through a proxy - like dansguardian), but rather a program similar to X3Watch.com or CovenenantEyes.com that reports internet usage to a friend's email address for accountability purposes. 

Is there such a thing? I found Accountability Partner, but I could not successfully install it.

Thanks,
Jonathan

---

### Post by danoyoto on 2007-02-02
I haven't found anything either.  I do like the fact that CE has DansGuardian preinstalled but I really want to have an accountability app.  Let me know if you find anything.

thanks.

---

### Post by djuse on 2007-03-12
I tried installing Covenant Eyes recently and was dissappointed that it is not compatible with my Anti-Virus program NOD 32.  I used to use x3 as my accountability software but was told that it is not very reliable.  Does anyone out there have a suggestion for me?

Is x3 pro a better program than the free version?  Will it be compatible with NOD 32?

What other software is out there that I could try?

Thanks,

---

### Post by Elif Tymes on 2007-03-13
Well, we're working on fixing Nod32. It's one of the few remaining applications that is incompatible with Covenant Eyes...

The problem with Nod32 is it's "intrusive" with how it interacts with the network. It sets itself up as primary gateway, and shoves everything else out of the system, which with Covenant Eyes installed causes them to fight. Windows networking code is... poor... compared to other OSes, which means that when the two of them fight, if there's no clear winner the system will behave... sporadically ;). Basically system hangs, etc.

Right now we're trying to figure out the best way to make the fight for the network control never happen....

> **djuse said:**
> I tried installing Covenant Eyes recently and was dissappointed that it is not compatible with my Anti-Virus program NOD 32.  I used to use x3 as my accountability software but was told that it is not very reliable.  Does anyone out there have a suggestion for me?

Is x3 pro a better program than the free version?  Will it be compatible with NOD 32?

What other software is out there that I could try?

Thanks,

---

### Post by internetaccountability on 2007-09-04
I am the maker of this software.

[http://www.internetaccountability.com](http://www.internetaccountability.com)

I charge a nominal fee per year.

Alex

---

### Post by xilix on 2007-09-04
> **internetaccountability said:**
> I am the maker of this software.

[http://www.internetaccountability.com](http://www.internetaccountability.com)

I charge a nominal fee per year.

Alex

Is your software easy to install under ubuntu?

---

### Post by internetaccountability on 2007-09-04
> **xilix said:**
> Is your software easy to install under ubuntu?

I have created a simple install package.

You have 1 week for FREE trial so try it out and see.

Thanks

Alex

---

### Post by xilix on 2007-09-04
... when I click on "Download Program" just a new page opens, but I can find no package.

---

### Post by internetaccountability on 2007-09-04
The download page that opens is locating the setup file. Please let it find it and then it will prompt you to Save to your computer. Depending on your connection speed, it may take longer than you expect.

Thanks

Alex

---

### Post by xilix on 2007-09-04
> **internetaccountability said:**
> The download page that opens is locating the setup file. Please let it find it and then it will prompt you to Save to your computer. Depending on your connection speed, it may take longer than you expect.

Thanks

Alex

I have a very fast connection. There seems to be a problem. I tried Firefox and Opera. JavaScript is enabled... no promt.

I would like to test it, but ...

---

### Post by internetaccountability on 2007-09-04
> **xilix said:**
> I have a very fast connection. There seems to be a problem. I tried Firefox and Opera. JavaScript is enabled... no promt.

I would like to test it, but ...

My program only works with IE. Try downloading with IE instead.

---

### Post by xilix on 2007-09-05
Sorry, but that's no alternative for me...

---

### Post by clmorg01 on 2007-09-05
> **internetaccountability said:**
> My program only works with IE. Try downloading with IE instead.

:confused:  So, how would this work on Ubuntu?  Do you download on a windows machine then copy over to a Ubuntu box?

---

### Post by Cryophallion on 2007-09-05
This will NOT work with Ubuntu.

See this thread: [http://ubuntuforums.org/showthread.php?t=356118](http://ubuntuforums.org/showthread.php?t=356118) for a discussion of it. There are a couple of links for things that may help you for now, while people are working on some solution (There was one person who was working on this a little while back, but I haven't seen any recent updates from them).

---

### Post by mhancoc7 on 2007-09-06
> **internetaccountability said:**
> My program only works with IE. Try downloading with IE instead.

Just curious, but you do know that this is an Ubuntu Linux forum right? :D

Jereme

---

### Post by internetaccountability on 2007-09-07
> **mhancoc7 said:**
> Just curious, but you do know that this is an Ubuntu Linux forum right? :D

Jereme

Not until AFTER the first post I created in this thread.

---

### Post by mhancoc7 on 2007-09-07
> **internetaccountability said:**
> Not until AFTER the first post I created in this thread.

Oh, OK.  

Jereme

---

### Post by Elif Tymes on 2007-09-10
> **bsalt said:**
> Hey, I am looking to get a program that does not quite focus on internet filtering (especially through a proxy - like dansguardian), but rather a program similar to X3Watch.com or CovenenantEyes.com that reports internet usage to a friend's email address for accountability purposes. 

Is there such a thing? I found Accountability Partner, but I could not successfully install it.

Thanks,
Jonathan

Just so you know, I'm still on the quest to get something working with the Covenant Eyes application. The problem is I am not a systems programmer, merely a web developer...

If you know of any software which generates a list of url's... But... Heh, my experience falls short :(

---

### Post by clmorg01 on 2007-09-10
> **Elif Tymes said:**
> Just so you know, I'm still on the quest to get something working with the Covenant Eyes application. The problem is I am not a systems programmer, merely a web developer...

If you know of any software which generates a list of url's... But... Heh, my experience falls short :(

I've avoided linux for several years because of this issue but I've been getting the linux itch again.  So, that's why I've only installed ubuntu on a laptop with no internet connection so far.  I've been looking for a solution as well.  I came across the dsniff package which has a program called urlsnarf.  Urlsnarf produces a log (a very detailed and verbose log) of all url access.  I was bouncing around the idea in my own head of possibly producing an interface to make use of this log.  Possibly, include features that make sure the program is running and if not then include alerts to that effect.

---

### Post by Elif Tymes on 2007-09-11
> **clmorg01 said:**
> I've avoided linux for several years because of this issue but I've been getting the linux itch again.  So, that's why I've only installed ubuntu on a laptop with no internet connection so far.  I've been looking for a solution as well.  I came across the dsniff package which has a program called urlsnarf.  Urlsnarf produces a log (a very detailed and verbose log) of all url access.  I was bouncing around the idea in my own head of possibly producing an interface to make use of this log.  Possibly, include features that make sure the program is running and if not then include alerts to that effect.


Hmm, that looks promising... Unfortunately it seems to be a bugger getting working on wireless cards...

Hmmm...

Will look into that more tonight after work.

---

### Post by mssever on 2007-09-11
> **clmorg01 said:**
> I've been looking for a solution as well.  I came across the dsniff package which has a program called urlsnarf.  Urlsnarf produces a log (a very detailed and verbose log) of all url access.  I was bouncing around the idea in my own head of possibly producing an interface to make use of this log.  Possibly, include features that make sure the program is running and if not then include alerts to that effect.

I'm considering this option, too. Perhaps we can collaborate on this...

I'm working on a basic proof of concept right now. I'll post it when it's ready.

---

### Post by mssever on 2007-09-12
OK. Here's the first part of the program. It has a few dependencies (all in the universe):
```
sudo aptitude install ruby dsniff libdaemonize-ruby
```This part is the daemon that captures and logs the URLs to a YAML file in the background.

Still to be done (in no particular order):[LIST]
[*]Write the program that reads the logs and either e-mails it directly or (perhaps better) hands off the data to a still-to-be-written web service which does the mailing.
[*]Add some configuration options
[*]Add a GUI (Note: The GUI needs to be in a process of its own, rather than tacked on to the existing program.)
[*]Make the program send out notifications if it is disabled or its files are tampered with
[*]Package it up into a .deb
[*]Daemon control scripts
[*]Anything else?[/LIST]This is an extremely early version of the program. It isn't yet usable for real accountability. What's needed now are testers. Also, if you're a programmer, feel free to contribute. (I prefer code written in either Ruby or Python.)

---

### Post by clmorg01 on 2007-09-12
I've been programming in Basic on an OpenVMS system for the past five years.  I was thinking about this project as way for me to learn python and to get my feet wet with OOP again.  My skills are starting to get rusty from college.

So, I would love to at least test and contribute code where I can.  Just don't expect any feats of programming magic from me.  :-P

---

### Post by xilix on 2007-09-13
I would like to contribute by testing the software, but I need a few instructions ...

---

### Post by mssever on 2007-09-13
I've moved this project to its own thread. Here it is: [http://ubuntuforums.org/showthread.php?t=550287](http://ubuntuforums.org/showthread.php?t=550287)

It is a major improvement over what I've posted in this thread.

@xilix: Hopefully the instructions there are sufficient. If not, then just ask (in that thread).

---

### Post by xilix on 2007-09-13
Thank you. Thats great.

---

