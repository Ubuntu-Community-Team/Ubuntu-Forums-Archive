---
title: "Karmic server: cups broken?"
date: 2010-03-04
forum: Server Platforms
---

### Post by frankvw on 2010-03-04
OK. I have now spent half the day trying to install a CUPS printer on Karmic Server, and the next step could be rampant alcoholism... so I need some advice here. :-)

I have tried to install a printer using the command line tools, *and* via the web interface. When I select the driver (the recommended foomatic driver for a HP laserjet 4L) I get an error message:

```
Unable to copy ppd file!
```

I can imagine the command line tools using a default path that doesn't match the actual install on a particular distro, but the web interface has the same problem.

Seeing as this is an out-of-the-box (but up to date) Karmic server install and all I'm trying to do is to install a laser printer in the most standard way possible, I cannot imaging that I'm the only one to experience what really appears to be a bug in the cups config that comes with Karmic server.

So. Is this a know problem (and if so, why hasn't it been fixed, because being unable to use a standard printer setup procedure would quickly attract attention) and what do I do about it?

All suggestions appreciated - please help me safe my sanity here... :-)

// FvW

---

### Post by Queue29 on 2010-03-04
> I cannot imaging that I'm the only one to experience what really appears to be a bug in the cups config that comes with Karmic server.

I like to think of successfully setting up an Ubuntu print server as a sort of right of passage for new server admins. 

Good luck!
=;

---

### Post by frankvw on 2010-03-05
> **Queue29 said:**
> I like to think of successfully setting up an Ubuntu print server as a sort of right of passage for new server admins.

Heheh. I had heard of "It's not a bug, it's a feature" but "It's not a bug, it's a test of your wits" is new to me...:D

That said, I find it strange that on the cups version that comes with an out-of-the-box install of Karmic, something as trivial as installing an HP Laserjet printer according to the instructions that come with it, only result in an error message and an abort of the operation. I am not used to that sort of thing happening on stable Linux distro's.

And it's not like I haven't used command line tools or set up printing and other services before. My first production server was Slackware 1.18 back in, if memory serves, 1993. If you wanted support for a printer port, you compiled your own kernel to include it. We dinna have dem newfangled gui thingamajigs in them days... :-)

// Frank

---

### Post by Chrisso101 on 2010-03-05
Yes Frank CUPS is broken. imho the whole thing sucks.

I too have spent half a day or so with no positive results. The CUPS manual is dreadful. I just wonder what the commercial Linux/unix offerings are like when it comes to printer and other documentation. I suspect not much better.

What is the point in offering up software that doesn't work and is not properly supported - god only knows!

---

### Post by frankvw on 2010-03-06
> **Chrisso101 said:**
> Yes Frank CUPS is broken. imho the whole thing sucks.

Now, now. It's not that bad. The fact that there seems to be a stuff-up in one version of one package (it looks like the cups package for Karmic server expects to find the ppd driver files in one directory while they actually have been installed in another one) does not mean that cups itself is trash.

> **Chrisso101 said:**
> I too have spent half a day or so with no positive results. The CUPS manual is dreadful.
While it could be better, it could also be a lot worse. Right now its main drawback is that the procedure described in it does not work due to the fact that in this package version the ppd files seem to have been moved to a non-default location of which cups is unaware. That said, cups is not an end-user toy, so the manual is not aimed at end-users, either. It doesn't come with a "troubleshooting" section that suggests you "make sure it is plugged in" as its most important advice. ;-)

> **Chrisso101 said:**
> I just wonder what the commercial Linux/unix offerings are like when it comes to printer and other documentation. I suspect not much better.
Documentation is indeed one of the most common weaknesses of many open source projects. This is simply the result of the fact that open source projects tend to be developer-driven, which means there the step between having a working program and having a market-ready product (including a proper manual icorporating the results of usability field tests) is often skipped. This is an inherent problem with software released by developers rather than by profit-driven companies, and part of the price we pay for having software that is essentially excellent but comes without an inflated price tag.

> **Chrisso101 said:**
> What is the point in offering up software that doesn't work and is not properly supported - god only knows!
Let's not fly off the handle here. A packaging bug that the cups manual does not render open source software in general and Linux in particular pointless. Let's keep some perspective, shall we? :-)

But I digress. The problem seems to be that there are various drivers (e.g. foomatic) in /usr/lib/cups/driver, and a library of ppd files in /usr/share/ppd, but cups-driverd expects them in /usr/share/cups/model. Also, immediately after installing the cups package, cups-driverd complains about

```
Bad driver information file "/usr/share/cups/drv/sample.drv"!
```

So it definitely looks like a packaging problem.

// FvW

---

### Post by frankvw on 2010-03-06
In the end it worked. Don't ask me why or how. I did a lot of fiddling (for example, running cusp-driverd manually) without learning much. Then, just for the heck of it, I ran the installation procedure via the web interface, and it worked. Just like that.

On the desktop version of Ubuntu I have never had any hiccups with CUPS. On CentOS (my previous server distro of choice) no problems either. But on Karmic server? 

Let me put it this way:

it was about as much fun as removing one of your own kidneys.

While sober.

Without an anaesthetic.

Using nothing but gardening tools.

// FvW

---

