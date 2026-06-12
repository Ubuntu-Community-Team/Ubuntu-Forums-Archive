---
title: "Standardizatiion"
date: 2007-12-30
forum: The Cafe
---

### Post by george3095 on 2007-12-30
Yes, I know I don't know anything about Linux, but I do know what happened when Beta and VHS (remember video cassette recordings?) competed. One survived. Of course, we now have Blu-ray and HD-DVD and there are combo players that can play both formats. Great! Eventually, there'll be ONE.

But, you ask, what does talk about video recording and optical drive players have anything to do with Linux? I have wondered why we have ".rpm", ".tar.gz", ".tar.bz2", ".run", and most likely a slew of others many of you have run across, all of which, one way or the other are for installing something. This might even be considered sacrilegious, but wouldn't it be better for the entire Linux community if EACH distribution's overlords selected its own unique installer and made how it worked consistent. As it is now, our community is fragmented into many different (and yet similar) camps. We've diluted ourselves. ME? I have to keep printouts handy to figure out how to install some new program or update that's not done by automatically by Synaptic or "Applications, Add/Remove Applications" in Ubuntu. So far, for my manual installation attempts, it's been a mixed bag of success and failure with emphasis on failures. The drawback of using the two auto-install methods above is that their available version often lags the latest version by several releases. I'd appreciate constructive comments.

---

### Post by dpar on 2007-12-30
Have you seen this yet??

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by JoshuaRL on 2007-12-30
Well I'm not sure about you, but when I was a Windows only user, I tried to install a LOT of programs.  Some were utilities, some were media related, some were games.  And it didn't matter if the official specs said I could use a program or not, I just had to try it to see if it would or not.  Several that I really wanted just didn't work despite all my efforts and the specs saying I could.

And all those were .exe files.

So I'm not sure whether the issue is about installer issues so much as a general computer thing.  But then I'm new so you're perfectly welcome to disagree.

---

### Post by Dr Small on 2007-12-30
Each package manager uses something else.

Apt uses debian's.
Yum uses RPMs.
Tar.gz are generally source files,

There is no mass confusion about this, but certain files are for certain package managers and whatnot.

Dr Small

---

### Post by jken146 on 2007-12-30
They're all just basically gzipped tarballs with bits stuck on, so not really that different from one another.  Then there's alien, and the source code itself, so there's no real package format lock-in.  Packaging and package managing is one of the big things that makes the distros stand out from one another IMO.  I like the diversity of the GNU/Linux world.

---

### Post by PeterJS on 2007-12-30
Run
The .run extension really doesn't tell you anything other than the person that built isn't a linux native, and don't really understand what they're doing. There is no standard for what a .run actually is. In most cases, it's a script that automatically extracts a compressed archive that's some how encoded in to the script itself which then kicks off a second script once the extraction stage is done. It's a neat hack, I'd be impressed with myself if I thought it up, but I would never ever use it as a distribution method.

RPM
In the beginning there was no package management, and things sucked badly, so red hat created the RPM format and it was better than a poke in the eye with a sharp stick, but just barely. From this was spawned the idea of dependency hell, dependency  hell has been solved, but it's legacy remains. RPM has vastly improved since then and is today the gold standard of commercial distro package formats.

Deb
The deb format was created back in the dark days of dependency  hell, and solved the problem long before RPM got it's act together. It has become the de-facto community package format because the debian code base is the de-facto standard to build a distribution around.

Tar.gz
Tar.gz is just an archive format, nothing more nothing less. The only reason it's associated with installing things is that most things you want to install need to be distributed in some form and downloading each individual file would be a monster pain. You wouldn't accuse a zip file of being an install format?

Tar.bz2
See above. If you want to find a mathematician to debate the merits of gzip compression versus bz2 compression go for it, but the math is well over my head.

Package Management Lag
Yes the things in the repositories lag behind the bleeding edge, but that's not a bad thing. Not being bleeding edge gives the ubuntu maintainers a stable base to manage security patches on. Another benefit of not being on the bleeding edge is that things can be tested to make a best effort attempt at finding and fixing bugs.

If you really want to have that bleeding edge stuff take a look at Debian Sid or Gentoo. But bare in mind that each of those have their draw backs, Sid likes to break often, there's very little between Sid and the upstream developers. In gentoo you compile everything yourself (that's how you know it's fresh).

---

### Post by JoshuaRL on 2007-12-30
Dude, that's the best description I've ever heard.  Thanks PeterJS.

---

### Post by Dr Small on 2007-12-30
> **JoshuaRL said:**
> Dude, that's the best description I've ever heard.  Thanks PeterJS.
Yes, that is an awesome description of things ;)

---

### Post by bodhi.zazen on 2007-12-30
Moved to the cafe.

I tend to agree that Linux would benefit from standardization. For example, IMO, the file system, tree (directory), default configuration files, etc. I think this would benefit development as it is hard to develop software that installs on all the various distros (for example the Nvidia driver).

There are also a lot of small distros and I too wonder if it would be better if there was more collaboration between developers / distros.

However, I would not like to stifle diversity or choice. If there were no diversity we would all be running Debian or Red Hat or (insert distro here) ... or worse, Vista.

I also like that I can choose between applications. Open Office is nice, but it is also nice to have light weight alternates like Abiword :)

So, while you raise a good question, there really is no simple solution. 
Over time the situation tends to resolve itself. Good projects gain users and support while the not so good ones tend to fade away.

---

### Post by maybeway36 on 2007-12-30
Someday every machine should have alien installed...

---

### Post by bruce89 on 2007-12-30
Pray for [PackageKit]("http://www.packagekit.org/").

---

### Post by Dr Small on 2007-12-30
There's also AutoPackage :p

---

