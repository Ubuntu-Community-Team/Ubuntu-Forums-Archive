---
title: "Deathray's Home Server"
date: 2009-03-22
forum: Server Platforms
---

### Post by Deathray on 2009-03-22
I know a fair amount about Windows based servers but am willing to learn linux. I'm waiting for the [Nvidia Ion]("http://www.bit-tech.net/hardware/pcs/2009/03/20/nvidia-ion-platform-performance/1") to come out and then I'll be using that as a low-power ( 19 watts :O ) ftp, ssh and torrentflux server and just a place to learn linux.

Is it okay if I keep this thread open for any small questions I have regarding Linux, I have so many things I am wondering about but don't feel like reading hundreds of hours to learn every aspect there is to know about.

My first question is what the equivalent to Windows services is in Linux.
In windows, a service is something that is loaded before login. So if I had apache installed as a service in Windows, the web-server would be available before logging in to the server. In that way the server doesn't have to use resources handling an entire desktop environment 

What is the Linux equivalent to a Windows service?

---

### Post by Hobgoblin on 2009-03-22
> **Deathray said:**
> 
What is the Linux equivalent to a Windows service?

A [daemon](http://en.wikipedia.org/wiki/Daemon_(computer_software)).

But if you install Apache via the package manager there will be no setting up to do unless you want to change the defaults.

---

### Post by Deathray on 2009-03-22
Thanks now I have something to look up and learn about! :)

---

### Post by FakeOutdoorsman on 2009-03-22
Why buy a new computer as a multi-use server when an old klunker will do just fine?  I have an old PII 400 Mhz that I use for web development, automated database backups, and some torrenting and it works just fine (and isn't in the landfill).  It also only uses about 35 watts.  It's a headless, command-line only machine with a minimal base install, but that's an excellent way to learn Linux.

---

### Post by Deathray on 2009-03-24
> **FakeOutdoorsman said:**
> Why buy a new computer as a multi-use server when an old klunker will do just fine?  I have an old PII 400 Mhz that I use for web development, automated database backups, and some torrenting and it works just fine (and isn't in the landfill).  It also only uses about 35 watts.  It's a headless, command-line only machine with a minimal base install, but that's an excellent way to learn Linux.

Considering it uses such a small amount of electricity, it is tempting - but I've simply fell in love with the Nvidia Ion because of it's size :D. (also, its going to be cheap fairly cheap $400-600 I hear!)

By the way, last night when I was laying in bed - I just realized something. My computer running linux - the HD led didn't go on not a SINGLE time! Linux is so unbelievably awesome, haha :D When ever I ran either XP/Vista/Server 2008 (deactivated all unnecessary services such as indexing, the HD still managed to make noise pretty often. Wow, I'm really impressed.

Well I got a question regarding my FTP. I successfully created an FTP server (I'm doing all of this on my desktop-pc until I get my ION :P). Currently the directory /user/ftp is available for anonymous login. Now my question is, is there any trick to for example put /videos into the /user/ftp/ directory without actually physically moving it there? I am using vsFTPd :)

---

### Post by Deathray on 2009-03-25
1 day ago bump :)

---

### Post by kidux on 2009-03-25
You can do a symlink. If you google for it you should be able to come up with the proper command. Can't remember right now and I'm not on my machine.

---

### Post by BkkBonanza on 2009-03-26
Yes, symlink like this,

ln -s /videos /user/ftp/videos

Anything you have in /videos will also show up in /user/ftp/videos

And I have to ask. $400-600 for a small Ion machine? That sounds pretty expensive nowadays. I don't know what an Ion is but for a small home server on low power why not just use one of the new Atom miniITX boards around. I mean the Intel one sells for about $50 or so. Heck for the price of an Ion I could by a new notebook. 

Also another way to go on a low power home server is to buy one of the more capable routers with USB support, like the Linksys WRTSL54GS. Lots of people use these as mini home servers and hang usb drives off them for file serving. They install something like dd-wrt (running linux) and can install all sorts of nifty things. I mean this is for home - not an office where you may have lots of users.

edit: just checked the Ion. It just seems kind of silly to install a fancy graphics machine as a headless server. Must be they are marketing these for home theatre use, I'd guess. Why pay for high end video and then use ssh?

You can run torrentflux and learn Linux on a $60 router. With USB it can also serve files with Samba and printers with Cups.

---

### Post by Deathray on 2009-03-26
> **BkkBonaza said:**
> Yes, symlink like this,

ln -s /videos /user/ftp/videos

Anything you have in /videos will also show up in /user/ftp/videos

And I have to ask. $400-600 for a small Ion machine? That sounds pretty expensive nowadays. I don't know what an Ion is but for a small home server on low power why not just use one of the new Atom miniITX boards around. I mean the Intel one sells for about $50 or so. Heck for the price of an Ion I could by a new notebook. 

Also another way to go on a low power home server is to buy one of the more capable routers with USB support, like the Linksys WRTSL54GS. Lots of people use these as mini home servers and hang usb drives off them for file serving. They install something like dd-wrt (running linux) and can install all sorts of nifty things. I mean this is for home - not an office where you may have lots of users.

edit: just checked the Ion. It just seems kind of silly to install a fancy graphics machine as a headless server. Must be they are marketing these for home theatre use, I'd guess. Why pay for high end video and then use ssh?

You can run torrentflux and learn Linux on a $60 router. With USB it can also serve files with Samba and printers with Cups.

I have a large full HD 42" LCD which I will want to occasionally watch a movie on. So therefore it would be a nice solution to own one of those :). But thank you so much for the tip regarding dd-wrt. My router is the WRT54G which is supported! :D, I know what I'm going to do once I get home :).
And thanks for enlightening me about symbian links.

---

### Post by BkkBonanza on 2009-03-26
Check your version of the WRT54G carefully. Some don't have support or good support.
I understand if you want to combine server with HT use. Makes more sense.

---

### Post by MrWES on 2009-03-26
I run tomato firmware on my WRT54G -- makes for a nice router with a quality QoS (Quality of Service) manager.

[http://www.polarcloud.com/tomato]("http://www.polarcloud.com/tomato")

Bill

---

### Post by Deathray on 2009-03-26
> **BkkBonaza said:**
> Check your version of the WRT54G carefully. Some don't have support or good support.
I understand if you want to combine server with HT use. Makes more sense.

I have the WRT54g**V5** which unfortunately can only run the micro version of DD-WRT with limited functions. Not even SSH :(

Nevertheless, I tried it out and through the web interface there are a lot more options for configuring the network but nothing special.

---

