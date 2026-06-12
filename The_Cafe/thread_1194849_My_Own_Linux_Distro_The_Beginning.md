---
title: "My Own Linux Distro: The Beginning"
date: 2009-06-23
forum: The Cafe
---

### Post by safe357 on 2009-06-23
I'd like to try and build my own custom Linux distribution.the reason to do this is I want to study more detail about Linux and i am planning to follow lfs. please reply with your suggestion

---

### Post by frodon on 2009-06-23
Moved to community cafe.

---

### Post by pbpersson on 2009-06-23
Please tell us what your goals are.

How will this distro be different from the other distros currently available?

What group of users are you attempting to reach?

What is your mission statement?

---

### Post by konnorrigby on 2009-06-23
I think yhu shud give more details. it sounds lyke yhu have know idea where to start.
i think mabey yhu shud mabe come up wyth something before yhu post things lyke that. i think its a good idea though.  :)

---

### Post by Sand &amp; Mercury on 2009-06-23
> **pbpersson said:**
> Please tell us what your goals are.

How will this distro be different from the other distros currently available?

What group of users are you attempting to reach?

What is your mission statement?
OP: You should consider these questions very carefully if you plan on developing a distro that you want other people to use. If it's just for your own learning and amusement, then I dunno, just call it Foobuntu or something and see what you can change.

---

### Post by HappyFeet on 2009-06-23
> **konnorrigby said:**
> I think yhu shud give more details. it sounds lyke yhu have know idea where to start.
i think mabey yhu shud mabe come up wyth something before yhu post things lyke that. i think its a good idea though.  :)

What language is that?

---

### Post by hyperdude111 on 2009-06-23
> **konnorrigby said:**
> I think yhu shud give more details. it sounds lyke yhu have know idea where to start.
i think mabey yhu shud mabe come up wyth something before yhu post things lyke that. i think its a good idea though.  :)

En inglés por favor?

---

### Post by earthpigg on 2009-06-23
> **safe357 said:**
> I'd like to try and build my own custom Linux distribution.the reason to do this is I want to study more detail about Linux and i am planning to follow lfs. please reply with your suggestion

if your goal is to learn more about linux, i suggest first building a usable desktop from the ground up. try slackware, linux from scratch, arch, or something like that.

---

### Post by koenn on 2009-06-23
> **HappyFeet said:**
> What language is that?

illiterate leet speak ?

---

### Post by chaslinux on 2009-06-23
> **pbpersson said:**
> Please tell us what your goals are.

How will this distro be different from the other distros currently available?

What group of users are you attempting to reach?

What is your mission statement?

This is good advice. I worked on [http://wclp.sourceforge.net/](http://wclp.sourceforge.net/) many years ago. Our goal at the time was to create a distribution that:

* took few resources, but had a desktop similar to Windows 9x
* could be easily deployed on many machines at the same time (through a NFS server using 1 boot floppy)
* could be customized at each machine level (though FAI, Fully Automatic Installer)

Knowing what your end goal is will help you determine where to start. Ubuntu is an excellent place to start.

If your goal is simply knowledge about Linux you don't have to start from scratch. There is soooo much you can learn about Linux (creating a MythTV PVR for example is much different than setting up DNS servers) that if you just say "I want to start from scratch and learn everything" I think you'll struggle, there's so much to learn.

If you want to learn about how Linux boots, the various configuration files, and differences between distributions I highly, highly recommend the Linux System Administration handbook. I have the second edition and find it's a wonderful reference for many topics... Just my $0.02.

I'm not so brave as to suggest LFS (Linux From Scratch), but I do recommend Gentoo because the documentation is excellent (but then again I find Ubuntu's just as good, sometimes better).:D

---

### Post by k2t0f12d on 2009-06-23
> **safe357 said:**
> I'd like to try and build my own custom Linux distribution.the reason to do this is I want to study more detail about Linux and i am planning to follow lfs. please reply with your suggestion[list][*]Build Linux from Scratch and boot it successfully in a virtual machine or on bare metal *at least* once[*]Consult DIY Linux for more ideas[*]Look at the layouts of some of the major distributions[*]Decide on a package manager or implement your own[*]Decide on an init system or implement your own[*]Write some bootscripts or adapt others to your system[COLOR="DarkRed"][*]EDIT: Write buildscripts or adapt others to your system[/COLOR][/list]

---

### Post by DeadSuperHero on 2009-06-23
Well, I wish you the best with this endeavour, but like everyone else has said, I too will ask:

-What will your distribution do?

Of course, that's a very broad question, so let me slim it down. There are many reasons to start your own distribution, one of them because I'd imagine it's quite fun to have all that power over your own distribution of software.

When I think about it, distributions are made for the following reasons:

-Usability, such as Ubuntu's attempt to make Linux an easier experience for everybody.
-Stability, such as Debian's release cycle being quite long.
-Corporate environments, such as RHEL or SuSE, powerful rock-solid workstations that are dedicated to GETTING WORK DONE, and nothing else.
-Philisophical-based distros, such as gNewSense or BLAG, which aim to remove proprietary software from their catalogues.
-Bleeding edge distributions, such as Fedora's Rawhide releases. Used to flaunt the latest and greatest technologies.

There are probably a lot more reasons, but those are the basics that I can think off the top of my head.

When you've considered what the main effort will be of the distro, then it must be asked: how will you do present it exactly? I don't mean by theme or visuals, but let's say, for example, that you're making a Linux distribution based on Ubuntu that focuses even MORE on useability, and used the latest KDE desktop. Going about with usability on it would require a different sort of approach than doing it with a Gnome desktop, with a different build system, different way of building the desktop interface, etc. So there's that.

Then, how will you maintain it? True, getting servers for packages and everything is doable, but it all requires upkeep of a group of enthusiasts. To get more enthusiasts, you'll either have to:

A) Make a solid proof-of-concept release that gains interest
AND/OR
B) Release on a niche platform with ideas that haven't been fully implemented in other distros.


After all is said and done, you and your team will have to build, patch, modify, upload, and distribute packages on a fairly consistent basis. On top of that, you'll need to regularly fix bugs through a bug tracker. It's a big job when you think of all the little things that goes into developing a distribution.

---

### Post by Chilli Bob on 2009-06-23
My advice would be NOT to start with Linux from scratch or similar unless you are already quite experienced with Linux.  I would start with an established distro and start learning to set up a distro on top of that, there will be pleanty of learning in there.

Why not start with an Unbuntu minimal installation (A command line install with the Kernal, GNU utils and very little else), and add your choice of Desctop Environment or Window manager, and your own choice of appliocations and utilities, based on your vision of the perfect OS.  It could be aimed at high or low spec computers, beginner or advanced user, free or propietory software, light or full featured apps, minimalist environment or all the bling you can squeese in, whatever works for you.

Getting this running smoothly will teach you PLENTY!  Then if you wish to do a from-scratch Linux distro, you will have a much easier time of things.

As usual Psychocats tutorials will help.  Here is how to set up a minimal install....

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by k2t0f12d on 2009-06-24
> **Chilli Bob said:**
> My advice would be NOT to start with Linux from scratch or similar unless you are already quite experienced with Linux.  I would start with an established distro and start learning to set up a distro on top of that, there will be pleanty of learning in there.I started out as using Debian and then went directly to Linux from Scratch to learn how it all works, which seemed to me to be about which the OP was inquiring. I have a handmade, bootable from-source system now because of that choice, do you? If a person's goal is merely to create *yet another ubuntu remix* then your advice would be equal to the task, but it doesn't seem to me to be the question that was asked here.

I would not wager on a person becoming a competent distribution designer/maintainer who had not gone through the process of rolling one independently at least once. I'm not saying its impossible to become competent without doing that, just less likely and more burdensome. Building GNU+Linux from scratch makes many subtle aspects of distribution design obvious in a way that vicarious remixing cannot provide.

---

### Post by SunnyRabbiera on 2009-06-24
My issue is that its not like I dont have any goals if I made my own linux distro, I do but I just dont have the actual drive to start pushing myself to make it.
I know what I want:

To create a debain based system that is:
Easy to use and install
Easy to maintain and update
Have a predictable but also steady release cycle
And be something that I can have fun with myself.

But I just dont have the drive to do much these days, I am way over worked.

---

### Post by ahndoruuu on 2009-06-24
> **SunnyRabbiera said:**
> My issue is that its not like I dont have any goals if I made my own linux distro, I do but I just dont have the actual drive to start pushing myself to make it.
I know what I want:

To create a debain based system that is:
Easy to use and install
Easy to maintain and update
Have a predictable but also steady release cycle
And be something that I can have fun with myself.

But I just dont have the drive to do much these days, I am way over worked.


That, sir, sounds almost exactly like what Ubuntu provides.

---

### Post by SunnyRabbiera on 2009-06-24
> **ahndoruuu said:**
> That, sir, sounds almost exactly like what Ubuntu provides.

Thats mam by the way.
And yes I know it sounds like what Ubuntu does but I would include these things to make it stand apart from Ubuntu:

Have a more rolling release cycle, software will be kept up to date but without having to go from version A to B to use the latest version of software.

Have a centralized system control center

Be stable but also flexible to get more recent software

And have a update manager that is selective of what is updated, the user gets the choice of what is updated and not.

---

### Post by wojox on 2009-06-24
Check out this site, [http://www.dmoz.org/](http://www.dmoz.org/) great starting point.

---

