---
title: "What Linux Drivers?"
date: 2005-03-01
forum: The Cafe
---

### Post by LonelyTraveler on 2005-03-01
I wanted to download a driver for my Lexmark Z35 printer, but I only have the option to choose between an Red Hat, Mandrakea nd SuSE driver. When searching for Ubuntu Linux drivers, what do I search for? I know that Ubuntu is based on Debain Linux, so do I search for Debain drivers. It it possible that the Red Hat, Mandrakea nd SuSE driver might work on Ubuntu? I can't check this at this stage because I'm still running Windows XP. I'm still waiting for my Ubuntu Linux CD. :?:

---

### Post by tim1 on 2005-03-01
Normally no driver should be distribution dependend, but the packaging format is. If the files are rpm you can try to convert them with alien.

However, if the printer has support for redhat/mdk/..., you also have very good chances that it will just work out-of-the-box without additional drivers. Try that first.

greets, tim

---

### Post by jdong on 2005-03-01
Most of the times, CUPS, foomatic, or gimp-print will support your printer out-of-the-box, with none of this driver crap.

In fact, usually "Linux" drivers coming from the manufacturer are nothing but a repackage of the already-built-in Linux drivers.


Try it out first, then look for drivers!

---

### Post by lordofkhemenu on 2005-03-01
[QUOTE=LonelyTraveler]I wanted to download a driver for my Lexmark Z35 printer, but I only have the option to choose between an Red Hat, Mandrakea nd SuSE driver. When searching for Ubuntu Linux drivers, what do I search for? I know that Ubuntu is based on Debain Linux, so do I search for Debain drivers. It it possible that the Red Hat, Mandrakea nd SuSE driver might work on Ubuntu? I can't check this at this stage because I'm still running Windows XP. I'm still waiting for my Ubuntu Linux CD. :?:[/QUOTE]
"alien" is included with debian/Ubuntu. It converts RPMs and Slack packages to deb packages.
You'll notice on the Lexmark Linux [driver pages]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:338:0:0&emeaframe=&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::") that the SuSE, Mandrake and Redhat driver all point to [the same files]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:338:0:0&os_group=SuSE&target="). I'm thinkin' it won't matter which one you download ;)

---

### Post by LonelyTraveler on 2005-03-01
Thanks. I have a program called Pryme. It's a webcam program that takes picture when movement is detected. Do you know of you get something like that for Linux. And another thing. I was told that I don't have to worry with anti virus software or anti spyware software. What is your view on this?

---

### Post by poofyhairguy on 2005-03-01
[QUOTE=LonelyTraveler]I was told that I don't have to worry with anti virus software or anti spyware software. What is your view on this?[/QUOTE]

two things.

First of all I have never experiance or heard of an experiance with a Linux virus. It will happen one day I am sure, but I don't worry about it now. 

Secondly, if there is such thing as a Linux virus it cannot do the damage that a Windows virus does. In Ubuntu, you run all the time in a restricted mode- programs can't install or change you important settings without your password. But unlike Windows' restricted mode, programs actually work! *except for cd burning programs, but there is a safe way around that.

---

### Post by LonelyTraveler on 2005-03-01
Thanks.

Like I said, I'm still waiting for my Ubuntu CD and I have never worked or even seen a Linux system upclose. What do you think of Ubuntu Linux?

---

### Post by DJ_Max on 2005-03-01
Ubuntu is great, there are tons of reviews, most on this forum, some on others websites. 

As far as viruses, there are only a few trojans, and rootkits, but aren't easy to get. 

They ship the CD's off on certain dates, they get A LOT of orders.

---

### Post by LonelyTraveler on 2005-03-05
If I want to download software and there isn't a download link for Ubuntu Linux, can I also then use another distro's link or can't I use the software?

---

### Post by kassetra on 2005-03-05
[QUOTE=LonelyTraveler]If I want to download software and there isn't a download link for Ubuntu Linux, can I also then use another distro's link or can't I use the software?[/QUOTE]

Most likely the software you're looking for will be inside of a program called Synaptic when you run Ubuntu.  Synaptic is a program that works like a software menu / installation system (think of a restaurant menu and ordering) - showing you all of the software available from specific "archives" or "repositories" of software (you can add many repositories to Synaptic).  So most likely you don't need to download any software.

Software from/for other distros simply are "packaged" forms of software that may or not be distro specific. 

One of the neat things about linux is that usually software is "distribution-ignorant" to begin with (called source code), and then is packaged for a distribution by hardworking developers/maintainers/etc.  

So almost all linux software in original form (source code) will work in any Linux distribution (that meets the software-specific requirements), but it's much easier to use a pre-packaged distribution-specific piece of software.

So to answer your question, yes, you can use the software you found for linux.  It's very possible it's already listed in Synaptic, and if it's not you can add software repositories to Synaptic to list even more software, and if it's still not there, you can still install it by using the source code (which is not hard anymore).

---

### Post by tim1 on 2005-03-05
[QUOTE=LonelyTraveler]If I want to download software and there isn't a download link for Ubuntu Linux, can I also then use another distro's link or can't I use the software?[/QUOTE]

That's always different. If there are source packages it should work with any Distro including Ubuntu. The same with compiled binaries in a tarball (.tar). Debian packages (.deb), although not specifically for Ubuntu but for Debian itself also work most of the time. If there are rpms, you can convert them with alien. So you'll hardly find any linux software with no way at all to run on Ubuntu :)

greets, tim

---

