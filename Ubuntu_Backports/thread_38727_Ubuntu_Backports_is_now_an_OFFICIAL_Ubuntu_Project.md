---
title: "Ubuntu Backports is now an OFFICIAL Ubuntu Project"
date: 2005-06-01
forum: Ubuntu Backports
---

### Post by jdong on 2005-06-01
After an almost 3-hour meeting with core Ubuntu developers, we've come to agree on the value of Backports, and a common protocol for our project to abide by. Furthermore, we're now an **official Ubuntu project**, meaning we'll use the Ubuntu build system, work closely with the Ubuntu team and MOTU, plus we'll have our repository at archive.ubuntu.com AND a unified bugtracking/QA system.

Details should start emerging at [http://www.ubuntulinux.org/wiki/UbuntuBackports](http://www.ubuntulinux.org/wiki/UbuntuBackports) , when Kassetra updates it.

---

### Post by Mez on 2005-06-01
For now though - I hope you'll carry on with your work as usual until all that get sput into place?

---

### Post by ametade on 2005-06-01
Congratulations to all Backport members!

---

### Post by jdong on 2005-06-01
Yep, I'm still gonna develop with our existing repos until they get their infrastructure ready for me. That'll include APT key signing and all other sorts of stuff.

---

### Post by kassetra on 2005-06-01
[QUOTE=jdong]
Details should start emerging at [http://www.ubuntulinux.org/wiki/UbuntuBackports]("http://www.ubuntulinux.org/wiki/UbuntuBackports") , when Kassetra updates it.[/QUOTE]

Oh sure, it's all up to me now.  ;)
give me a couple of days, ok?  :)

---

### Post by Mez on 2005-06-01
thats a long list of packages :D

Maybe cut them to s aubpage while you're doin it?
congrats ppl :D you guys deserve it

---

### Post by poofyhairguy on 2005-06-01
Congrats. The project finally gets the respect it deserves.

Long live backports.

---

### Post by Leif on 2005-06-01
Congratulations. The backports project has been very valuable and useful since it started, and it's great that it's getting official backing now. Thanks for all the hard work.

---

### Post by ow50 on 2005-06-01
I'll await with great interest to see what changes this brings. Official status could bring the backports project great resources, but on the other hand also great restrictions. At least with the popularity of backports it's good to have some official contact with ubuntu devs.

---

### Post by jdong on 2005-06-01
[QUOTE=ow50]I'll await with great interest to see what changes this brings. Official status could bring the backports project great resources, but on the other hand also great restrictions.[/QUOTE]


Well, I wouldn't have accepted the deal unless Backports would stay relatively unchanged.

Basically, the compromise we reached was already outlined in the Packages section. The only change that MAY affect how backports is done now is that I'll ONLY backport from Breezy (no more Sid-to-Hoary imports or hackjob patching).

Of course, MOTU will furnish me (hopefully) with brand-spanking-new, up-to-date packages for Breezy for me to backport :).

---

### Post by RastaMahata on 2005-06-02
congratulations :)

---

### Post by JDay on 2005-06-02
This is great news. Is there a log of today's meeting available somewhere?

---

### Post by wolovids on 2005-06-02
It's stuff like this that makes Ubuntu the best operating system.  I couldn't be more happy.  Good work to jdong and the Ubuntu developers.  Your work is definitely appreciated.

---

### Post by Spif on 2005-06-02
Wow, congratulations jdong!

---

### Post by Amaranth on 2005-06-02
[QUOTE=JDay]This is great news. Is there a log of today's meeting available somewhere?[/QUOTE]
 [http://people.ubuntu.com/~fabbione/irclogs/ubuntu-meeting-2005-06-01.html](http://people.ubuntu.com/~fabbione/irclogs/ubuntu-meeting-2005-06-01.html)
It starts at 09:30

---

### Post by fng on 2005-06-02
congratz

---

### Post by bored2k on 2005-06-02
[QUOTE=Amaranth][http://people.ubuntu.com/~fabbione/irclogs/ubuntu-meeting-2005-06-01.html](http://people.ubuntu.com/~fabbione/irclogs/ubuntu-meeting-2005-06-01.html)
It starts at 09:30[/QUOTE]
 Thanks for the link.

---

### Post by mc_cgp on 2005-06-02
Congratulations!

---

### Post by Technoviking on 2005-06-02
[QUOTE=Amaranth][http://people.ubuntu.com/~fabbione/irclogs/ubuntu-meeting-2005-06-01.html](http://people.ubuntu.com/~fabbione/irclogs/ubuntu-meeting-2005-06-01.html)
It starts at 09:30[/QUOTE]
It is a very interesting read.

Mike

---

### Post by XDevHald on 2005-06-02
YES!!!!!! that is very good news to hear, gratz jdong and u-g, job well done and I am using the new mirrors by the way, took me a bit to actually catch up with the forum due to personal issues, but we're good now and glad to be back active!

---

### Post by kb00heda on 2005-06-03
Does this have any (good) implications on the version update once Breezy is out? 

I recall going from Warty to Hoary required some handling (besides the usual "apt-get dist-upgrade") concerning backports if one had such installed. 

Can this be avoided in the future, i.e., going from Hoary to Breezy would really be as simple as changing the sources list and then apt-get...?

BTW --- great work, thanks!

---

### Post by Amaranth on 2005-06-03
[QUOTE=kb00heda]Does this have any (good) implications on the version update once Breezy is out? 

I recall going from Warty to Hoary required some handling (besides the usual "apt-get dist-upgrade") concerning backports if one had such installed. 

Can this be avoided in the future, i.e., going from Hoary to Breezy would really be as simple as changing the sources list and then apt-get...?

BTW --- great work, thanks![/QUOTE]
 That has already been fixed for the hoary backports. All the version numbers have ~5.04ubp on the end so when a new version is available (through breezy) the backport version gets replaced.

---

### Post by kb00heda on 2005-06-03
Sounds great! :)

---

### Post by jasplund on 2005-06-08
When will this happen?

---

### Post by Amaranth on 2005-06-08
[QUOTE=jasplund]When will this happen?[/QUOTE]
 Soon(TM)

---

### Post by jdong on 2005-06-08
I need to make contact with a local guy and get my key signed... that's the first step. I hope to do that sometime this week.

---

### Post by gregorian21 on 2005-06-10
Congratulations, it is indeed great news.

What will this mean for AMD64 backports?


[list=1]
[*]A good chance we'll see (most) popular apps backported
[*]No difference at all.
[/list]Thanks

---

### Post by Mez on 2005-06-10
If I remember correctly during the meeting, they'll be using the ubuntu autobuiild sysetm, so it'll be autobuilt on that archive (whether that'll work or get a fail is a fdifferent matteR)

---

### Post by angrykeyboarder on 2005-06-10
[QUOTE=jdong]After an almost 3-hour meeting with core Ubuntu developers, we've come to agree on the value of Backports, and a common protocol for our project to abide by. Furthermore, we're now an **official Ubuntu project**, meaning we'll use the Ubuntu build system, work closely with the Ubuntu team and MOTU, plus we'll have our repository at archive.ubuntu.com AND a unified bugtracking/QA system.

Details should start emerging at [http://www.ubuntulinux.org/wiki/UbuntuBackports]("http://www.ubuntulinux.org/wiki/UbuntuBackports") , when Kassetra updates it.[/QUOTE]

***Wonderful*** news!

---

### Post by jdong on 2005-06-11
[QUOTE=gregorian21]Congratulations, it is indeed great news.

What will this mean for AMD64 backports?


[list=1]
[*]A good chance we'll see (most) popular apps backported
[*]No difference at all.
[/list]Thanks[/QUOTE]

You'll get everything possible to backport backported.

---

### Post by angrykeyboarder on 2005-06-11
[QUOTE=jdong]Well, I wouldn't have accepted the deal unless Backports would stay relatively unchanged.

Basically, the compromise we reached was already outlined in the Packages section. The only change that MAY affect how backports is done now is that I'll ONLY backport from Breezy (no more Sid-to-Hoary imports or hackjob patching).

Of course, MOTU will furnish me (hopefully) with brand-spanking-new, up-to-date packages for Breezy for me to backport :).[/QUOTE]

Aren't there packages in Sid that aren't in Breezy though?

And thanks to you I have a nice easily-installable and compatible version of [Nvu]("http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/nvu_0.99+1.0pre-1%7E5.04ubp1_i386.deb") (which as of this writing, is nowhere to be found on an Ubuntu server....).

It seems as if someone may have to pickup where the current version of the Backports team left off..... 

I don't wanna wait months for Ubuntu developers to agree that Nvu is worthwhile...

---

### Post by jdong on 2005-06-11
[QUOTE=angrykeyboarder]Aren't there packages in Sid that aren't in Breezy though?
[/quote]
Yes, but that usually isn't the case unless it doesn't build on Breezy to begin with.
> 
And thanks to you I have a nice easily-installable and compatible version of [Nvu]("http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/nvu_0.99+1.0pre-1%7E5.04ubp1_i386.deb") (which as of this writing, is nowhere to be found on an Ubuntu server....).

I'll continue to offer these.
> 
It seems as if someone may have to pickup where the current version of the Backports team left off..... 

We are continuing hoary-extras as a repository of software that doesn't abide by the new policy. Nvu and marillat stuff, for example.

---

### Post by Xian on 2005-06-11
[QUOTE=poofyhairguy]Congrats. The project finally gets the respect it deserves.
[/QUOTE]

Very good point. I can recall when this was getting started and the attitude from "upstairs" was not too positive. I'm sure they had what they felt were good reasons, but I like to see when diligent people pursue what they know to be a good thing for the community in spite of superfluous objections.

jdong & team deserve a lot of kudos over that decision.

---

### Post by Mez on 2005-06-11
Well, I;m glad John did what he did - if it wasnt for backports, I wouldnt have stayed with ubuntu, and I wouldnt be where I am now!

---

### Post by Amaranth on 2005-06-11
[QUOTE=Xian]Very good point. I can recall when this was getting started and the attitude from "upstairs" was not too positive. I'm sure they had what they felt were good reasons, but I like to see when diligent people pursue what they know to be a good thing for the community in spite of superfluous objections.

jdong & team deserve a lot of kudos over that decision.[/QUOTE]
 They weren't superfluous, there were some problems with warty backports and there are still some with hoary backports (might actually be resolved now). That's what the new rules are for.

---

### Post by Xian on 2005-06-11
Based on some of the comments I read I was being generous. :)

---

