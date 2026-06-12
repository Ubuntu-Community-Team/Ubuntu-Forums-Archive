---
title: "slackware"
date: 2008-03-18
forum: Slackware and derivatives
---

### Post by stunningman on 2008-03-18
why is slackware considered as linux for hackers...........?

---

### Post by aeiah on 2008-03-18
it demands (or enables you to learn) a knowledge of linux that distros like ubuntu dont

---

### Post by stunningman on 2008-03-18
but what is the thing that makes slackware unique?

---

### Post by p_quarles on 2008-03-18
Moved to the Slackware sub-forum.

---

### Post by aeiah on 2008-03-18
it has very stable (and often not that new) software in its repositories that has been thoroughly tested. thats probably what makes it unique. its also a distro that requires a lot of command line usage and the editing of configuration files, which can make it rather intimidating for people new to linux or not that computer-savvy in general

---

### Post by Junglizer on 2008-03-18
> **aeiah said:**
> it has very stable (and often not that new) software in its repositories that has been thoroughly tested. thats probably what makes it unique. its also a distro that requires a lot of command line usage and the editing of configuration files, which can make it rather intimidating for people new to linux or not that computer-savvy in general

You might want to look in the following thread: [http://ubuntuforums.org/showthread.php?t=656807]("http://ubuntuforums.org/showthread.php?t=656807")

But going along with what aeiah said, I would say its simplicity is what makes it difficult. You *need* to understand a lot more about how the system works in order to use it successfully, or at least to get what you want out of it. You install what you want by compiling programs from source, this is really handy if you need to pass specific options to the compiler to get things to work on your system. Something doesn't work? Recompile the kernel. Editing the config files from the command line is nothing new, in all reality, most versions of linux can be viewed as similar, *if you understand linux as a whole.* By that I mean, if you've used Slackware heavily, and know where all the files to change things are, you should be able to use Ubuntu, but  you wouldn't need to navigate through the GUI, you could just edit things manually like you are used to, though some of the files will be in slightly different locations. Surely you've noticed that many people have problems with things like wireless cards not working after the updates or the newest release. This is b/c newer software is less tested and therefore less stable. Slackware (and Debian) chose the stability route, so you don't always see new updates and releases. Usually if you need to update something specific you will do it yourself. That being said, you don't need to worry about your system failing when you update it, b/c it doesn't update.

---

### Post by Junglizer on 2008-03-18
And for a side point of reference on stability (or the userbase on these forums) aside from your post being moved here, its been aproximately one full buisness week without a single post into the Slackware section.

---

### Post by deepclutch on 2008-03-18
well,I have a doubt,I heard that slackware doesnot strictly resolve dependencies.how do u ppl manage ? :confused:

---

### Post by Junglizer on 2008-03-18
> **deepclutch said:**
> well,I have a doubt,I heard that slackware doesnot strictly resolve dependencies.how do u ppl manage ? :confused:

You're quite right, but even more so, it does not even have a package manager at all. You best know how to google for what you want. Not to say that it doesn't come with loads of packages if you do the default install. I always recommend the DVD install b/c its simpler and you can just install everything if you aren't sure. (So that's around 4.5gigs of programs, plus it comes with about 6 different window managers [gui's] so you can choose the one you like.)

---

### Post by Lord Illidan on 2008-03-18
[http://www.slackbook.org/html/package-management.html](http://www.slackbook.org/html/package-management.html)

[http://www.slacksite.com/slackware/packages.html](http://www.slacksite.com/slackware/packages.html)

Personally, I'd prefer Debian stable. Or Arch Linux :D

---

### Post by Junglizer on 2008-03-18
Deepclutch: 
As far as managing it, well it just kind of comes back to who's using Slackware as a distribiton in general. Most people using Slackware have pretty decent linux experience and knowledge, so most of us already know what programs we need based on the systems use as well as where to look for new programs. If you're looking for new apps I highly recommend both [http://freshmeat.net]("http://freshmeat.net") and [http://sourceforge.net]("http://sourceforge.net").

---

### Post by Lord Illidan on 2008-03-18
I can also recommend Zenwalk as a nice slackware based distro.

---

### Post by deepclutch on 2008-03-18
well.I have tried everything in the past 6.5 yrs except slackware.
I do want to try either [**DFS**]("http://www.linux.com/articles/41627") or slackware+gnome(dropline may be!).

---

### Post by justin whitaker on 2008-03-18
I love Slackware, and I recommend it to anyone wanting to actually learn  Linux (as opposed to just using it)...but I don't use it, so that makes me a bit of a hypocrite, I guess. :)

Slackware is one of the earliest distributions of Linux, and it aims to be dead simple: download a tarball, unzip and install it via command line, and edit a few config files. 

Once you get used to it, it is quick to administer, and easy to use. 
The learning curve is fairly steep, though.

---

### Post by Junglizer on 2008-03-18
> **justin whitaker said:**
> I love Slackware, and I recommend it to anyone wanting to actually learn  Linux (as opposed to just using it)...but I don't use it, so that makes me a bit of a hypocrite, I guess. :)

Slackware is one of the earliest distributions of Linux, and it aims to be dead simple: download a tarball, unzip and install it via command line, and edit a few config files. 

Once you get used to it, it is quick to administer, and easy to use. 
The learning curve is fairly steep, though.

I agree totally, I used to recommend Gentoo mostly b/c it was so hard to install it forced you into learning all sorts of sweet stuff. So even before you had a gui installed you were like "I just spent like 4 hours installing this and now I kind of know some commands! Sweet!" However, I've had nothing but problems with their newer versions since they moved to their graphical installer. You can still do it the way I prefer with the minimal CD or just a copy of Knoppix. But you have to want to spend a full day working on it, or really have experience doing it before.

---

### Post by justin whitaker on 2008-03-18
> **Junglizer said:**
> I agree totally, I used to recommend Gentoo mostly b/c it was so hard to install it forced you into learning all sorts of sweet stuff. So even before you had a gui installed you were like "I just spent like 4 hours installing this and now I kind of know some commands! Sweet!" However, I've had nothing but problems with their newer versions since they moved to their graphical installer. You can still do it the way I prefer with the minimal CD or just a copy of Knoppix. But you have to want to spend a full day working on it, or really have experience doing it before.

Ah, Gentoo. I never really got the point of it. I mean, I understand the drive to have a system that I totally control, but the flip side of that is that if I wanted a BSD like packaging system, I'd run FreeBSD. 

But I agree with the sentiment. 

The really great part about Slackware/Gentoo/Arch is that you get a system exactly the way you want it, and you know how it got that way. That's an important skillset if you want to do something with open source.

Crap, I am talking myself into another Slackware install.....

---

### Post by Junglizer on 2008-03-18
Well consider that another Slackware install is easy. Several of my friends and I would get really hammered and try to install Gentoo from scratch, no docs. Who ever had the least problems or successful boot/working system won. Ahh good times. 4 gig disk and 2 gig swap = halarity.

---

### Post by Junglizer on 2008-03-18
I'd really love to make a good image from LFS but I'm waiting on a new laptop first. Can't really spend the time to make it a good install image and have my current system out of commision for the time being.

---

### Post by Taino on 2008-03-18
> **justin whitaker said:**
> The really great part about Slackware/Gentoo/Arch is that you get a system exactly the way you want it,

Crap, I am talking myself into another Slackware install.....

Or into a possible [Slax]("http://www.slax.org/") install.... :biggrin:

---

### Post by Lord Illidan on 2008-03-18
> **justin whitaker said:**
> Ah, Gentoo. I never really got the point of it. I mean, I understand the drive to have a system that I totally control, but the flip side of that is that if I wanted a BSD like packaging system, I'd run FreeBSD. 

But I agree with the sentiment. 

The really great part about Slackware/Gentoo/Arch is that you get a system exactly the way you want it, and you know how it got that way. That's an important skillset if you want to do something with open source.

Crap, I am talking myself into another Slackware install.....

Arch RULES!:lolflag:

---

### Post by justin whitaker on 2008-03-18
> **Taino said:**
> Or into a possible [Slax]("http://www.slax.org/") install.... :biggrin:

Slax is awesome...but rumor has it that the 6.0 series be a bit buggy. Think I will wait it out a bit. I could always roll my own: slackware 12 + live scripts & kernel.....

---

### Post by justin whitaker on 2008-03-18
> **Lord Illidan said:**
> Arch RULES!:lolflag:

Even the forum staff can't keep this thread on track! 

All right, all right, I'll try Arch.

---

### Post by factotum218 on 2008-06-10
> **deepclutch said:**
> well,I have a doubt,I heard that slackware doesnot strictly resolve dependencies.how do u ppl manage ? :confused:

<sarcasm>
It's the funniest thing really. There are these little error messages that pop up telling you that package-x is needed and you go get it and compile it. It's a new concept they are trying out.
</sarcasm>

---

### Post by cardinals_fan on 2008-06-11
> **factotum218 said:**
> <sarcasm>
It's the funniest thing really. There are these little error messages that pop up telling you that package-x is needed and you go get it and compile it. It's a new concept they are trying out.
</sarcasm>
It really isn't that bad.  I just make my own packages :)

---

### Post by Antman on 2008-06-11
> **cardinals_fan said:**
> It really isn't that bad.  I just make my own packages :)
I **really** need to start getting into creating packages... I just have to make the time and do it.:rolleyes:

---

### Post by cardinals_fan on 2008-06-11
> **Antman said:**
> I **really** need to start getting into creating packages... I just have to make the time and do it.:rolleyes:
It's easy on Slack :)

---

### Post by e.honda on 2008-06-18
@cardinals_fan:
I'm just curious, what tools do you use to make your package. Do you use src2pkg or checkinstall?...

I've attempted to use src2pkg to make packages but failed on every attempt except for one. To me it's not full proof yet and it doesn't detect missing dependencies which is a major problem. The good thing about it is, it works with pkgtools.

If you do a blind ./configure, make, make install...sometimes you'll get errors saying that you need "package-x, x, x, x" and you'll have to go out and manually download and install all the required software then restart from scratch. And plus pkgtools won't be able to upgrade the package which sucks. You'll have to update it manually. If you use a lot of software, this is gonna be a biotch. As for system updates and pre-installed applications, slapt-get will update/patch everything with ease. You can also do this manually with pkgtools which is very simple btw.

The only problem I find with slackware is that it lacks official software packages that most people want to use. Most of the popular programs are either not ported yet or not at the official slackware website. They are hosted by other site servers and most of them are unofficial packages that are known to be altered and compromised. The good thing is that if you don't trust their packages, then you can of course build your own from source or grab the official package from slackware site.

---

### Post by cardinals_fan on 2008-06-19
> **e.honda said:**
> @cardinals_fan:
I'm just curious, what tools do you use to make your package. Do you use src2pkg or checkinstall?...

I've attempted to use src2pkg to make packages but failed on every attempt except for one. To me it's not full proof yet and it doesn't detect missing dependencies which is a major problem. The good thing about it is, it works with pkgtools.

If you do a blind ./configure, make, make install...sometimes you'll get errors saying that you need "package-x, x, x, x" and you'll have to go out and manually download and install all the required software then restart from scratch. And plus pkgtools won't be able to upgrade the package which sucks. You'll have to update it manually. If you use a lot of software, this is gonna be a biotch. As for system updates and pre-installed applications, slapt-get will update/patch everything with ease. You can also do this manually with pkgtools which is very simple btw.

The only problem I find with slackware is that it lacks official software packages that most people want to use. Most of the popular programs are either not ported yet or not at the official slackware website. They are hosted by other site servers and most of them are unofficial packages that are known to be altered and compromised. The good thing is that if you don't trust their packages, then you can of course build your own from source or grab the official package from slackware site.
Checkinstall.

---

### Post by saulgoode on 2008-06-20
You should see if there is a [SlackBuild](http://slackbuilds.org) script for the program/library you are compiling. These scripts will build your Slackware package; and the ones provided by slackbuilds.org are very reliable. The process of using a SlackBuild is fairly straightforward and can be quite educational. 

As an example, today I built DOSBOX using a SlackBuild. [list][*] I found the [program on SlackBuilds.org](http://slackbuilds.org/repository/12.1/system/dosbox/) (making sure it was for my SW 12.1 system).

[*] I checked the README file to see if there were any special instructions or dependencies that needed to be met (there were none).

[*] I downloaded the file to my *~/Source* directory, entered that directory, and extracted the tarball's contents using '*tar zxf dosbox.tar.gz*'.

[*] I downloaded the source tarball using the link provided by SB.o; placing it in *~/Source/dosbox/* (the directory created in the previous step).

[*] I entered the directory, logged in a root, and executed '*./dosbox.SlackBuild*'.

[*] After a few minutes of compiling, the Slackware package was created in */tmp*.

[*] I then installed the package using '*installpkg /tmp/dosbox-0.70-i486-1_SBo.tgz*'

[*] I then logged out of the root account. :)[/list]This is all pretty straightforward but things can become more complicated when dependencies are involved. If the README for a SlackBuild lists a dependency, that dependency must be installed before you can build your package. Most projects only have a couple of dependencies but occasionally  there are more. 

For example, when I built [AbiWord](http://slackbuilds.org/repository/12.1/office/abiword/) the README specifies seven dependencies (gail, wv, libgnomecanvas, libgnomeprintui, libgnomeprint, libgnomecups, and enchant). This high number of dependencies is because AbiWord is a GNOME project and Slackware does not include GNOME. 

In this case, you should download all the SlackBuilds for the required dependencies and start building and installing them one-by-one (start with the libraries that don't list any dependencies in their README file). 

If there is no SlackBuild available for the program you are compiling, it is not too difficult to create your own, but I would recommend *using* a few SlackBuilds first until you understand the process.

---

