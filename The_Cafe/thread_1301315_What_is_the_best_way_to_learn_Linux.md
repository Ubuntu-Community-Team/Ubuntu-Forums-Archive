---
title: "What is the best way to learn Linux"
date: 2009-10-25
forum: The Cafe
---

### Post by Quick Silver on 2009-10-25
I am not sure exactly where else to post this other then here so I appologiize if I posted it in the wrong spot. Anyways, I have some basic and general knowledge of Linux (ubuntu) and I am able to get around fairly well. However, I want to learn more. I really want to learn how Linux works. I want to learn what each part of the file system and its folder do. Why they are there and how they can help me to get the most out of Linux. I have read a few suggestions like trying slax or gentoo and arch. I believe I read somewhere to start with arch then move to gentoo, then LFS. I really just want to get your opinion of where I should start and how I should progress. Also what are the advantages of learning from each of these different distros and are they going to help me learn linux overall or just their system and way of doing things.

---

### Post by mivo on 2009-10-25
For me it was installing Arch Linux on a spare machine with the Wiki for assistance.

---

### Post by ndefontenay on 2009-10-25
This is such a broad knowledge that it's hard to know everything.

I personally like cheat sheets. They tend to compile a set of useful information on one page, such as the one in my signature.

As for the different folders, it's actually pretty simple. You'll find a lot of good explanation online. I'm sure you figured out the following already:


    *  / - root directory
    * /home - where directories are contained for each user, example:
    * /usr - pronounced 'user' and contains Linux commands and utilities
          o /bin - binary executable programs
          o /lib - program libraries, similar to Windows 'dll' files
          o /sbin - more executable programs and Linux utilities for administrative purposes
          o /doc - documentation
          o /src - source code to programs
    * /tmp - temporary work files
    * /etc - configuration files
          o /rc.d - scripts used during boot and shutdown process
          o /sysconfig - default configuration files
          o /sysconfig/network-scripts - network scripts
          o /sysconfig/daemons - special programs that run in background, such as print spooling
    * /bin - binary executable programs that all users need
    * /dev - device files that control drives, terminals and any equipment attached to the server
    * /var - user specific files
          o /log - log files containing system usage and errors
          o /spool - where spooled files are stored during print spooling process
          o /mail - where Email files are stored until retrieved by client Email program
    * /proc - system files
    * /root - root's home directory
    * /opt - other options
    * /sbin - more executable programs and utilities

Enjoy : )

If you're into scripting and such, I guess you have to think of a little project you would like to do and find a way to make it work.

I've blown my wife's mind with the cal command:

cal 1979 (my birth year) returns a calendar with days and dates allowing me to find the day I'm born. Something important in Thailand.

Also for a bit of fun try:
totally useless but funny (my wife thinks I'm crazy)
 ```
apt-get moo
```

---

### Post by pluviosity on 2009-10-25
Use it.

---

### Post by renkinjutsu on 2009-10-25
yup, i would say any sort of minimum install, be it Arch or Ubuntu minimal install, would help you to understand that any linux distro is just a software stack


and from there, you can move on to becoming Master of the universe.

---

### Post by RichardLinx on 2009-10-25
There's a saying that goes something like this: 
> If you use Ubuntu, you learn Ubuntu. If you use Red Hat, you learn Red Hat. If you use Slackware, you learn Linux.
If you've got a spare computer you should download slackware and follow the wiki to get it up and running how you like. You could also install slackware through a VM on your Ubuntu installation.

---

### Post by FuturePilot on 2009-10-25
> **pluviosity said:**
> Use it.

This ^

---

### Post by chris200x9 on 2009-10-25
freebsd :P

---

### Post by fancypiper on 2009-10-25
Install, use, break it, fix it.

[LINUX: Rute User's Tutorial and Exposition]("http://rute.2038bug.com/index.html.gz")

---

### Post by Dharmachakra on 2009-10-25
Installing Arch will get you comfortable with the command-line and might help you learn configuration files but thats about it. In fact, Arch does a couple of things that aren't standard to Linux distributions. One example is 'rc.conf', where a few common settings are stored in a single file. In most distributions, the same settings would be found elsewhere. 

Here's the [Wikipedia]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") page regarding the file system structure. I'd suggest looking it over and then doing some link-surfing. You'll probably stumble upon other things that you're interested in.

---

### Post by Frak on 2009-10-25
Use it, break it fix it.

All of which you will eventually do, whether you like it or not.

---

### Post by Xbehave on 2009-10-25
play with it, a lot of people are suggesting you switch distros but you can learn about most things in the comfort of a ubuntu although you should probably switch to fedora if you want to learn selinux or opensuse/fedora for rpm/yum.

You can learn quite a bit when installing and configuring distro that doesn't do anything for you slackware/arch/gentoo*, but once you've set it up there is little advantage to keeping it. 

*you will learn patiences if you choose gentoo as compiling takes time!

---

### Post by jpmelos on 2009-10-25
Best way to learn it is use it. You'll eventually break it and when you fix it, congratulations, you learned something new. There's no book "Linux, all inside". There's always something new to be learned. I think that installing some distro that do nothing for you will teach you a lot in a small timeframe. Go for Arch Linux, Gentoo, Slackware... But never stop using and breaking whatever distro you are using. :P

---

### Post by Xbehave on 2009-10-25
> **jpmelos said:**
> Go for Arch Linux, Gentoo, Slackware... But never stop using and breaking whatever distro you are using. :P
Note, if you do need to actually use your computer it may be worth keeping a working distro around on a seperate partition

---

### Post by fancypiper on 2009-10-25
I chose Ubuntu after running Fedora/Mandrivia/Gentoo for a few years. Then I tried Debian and saw the popularity of Ubuntu skyrocketing and installed 8.04.

I loved apt-get/Synaptic for it's excellent conflict resolution.  Next, I did a network upgrade and was amazed at the ease. I had previously re-installed to upgrade, but nearly all the software as well as the OS was upgraded. Now I am hooked (I think) and believe it's a keeper.

Both of my converts (one is nearly computer illiterate) are now running Ubuntu and are Windows free.

Ubuntu is a great Linux learning distro, as well as the best homeschooling distro (Edubuntu) that I have used so far.

The freedom and many choices of software is one of the best (and possibly the most confusing to most newbies used to the one way of Microsoft/Apple), but is easier to use than my other choice of distros.

---

### Post by Exodist on 2009-10-26
> **Quick Silver said:**
> What is the best way to learn Linux

Install any version of Linux as you main OS, I prefer debian based Ubuntu. I also suggest buying a Linux for Dummies and when you feel you need alot more information purchase Linux in a Nutshell for a complete list of console CLIs and how to use them.
Also try to help folks, if you dont know the answer on the forums. Read the post and read how it was fixed. It will seem all garbage for a while, but it will click one day and youll feel more at home with Linux then windows.

IMHO,

Exo

---

### Post by Quick Silver on 2009-10-26
Thanks for all your quick responses. One thing I did not hear much about was gentoo or LFS does anyone have any opinions about those?

---

### Post by abhilashm86 on 2009-10-26
> **fancypiper said:**
> Install, use, break it, fix it.

[LINUX: Rute User's Tutorial and Exposition]("http://rute.2038bug.com/index.html.gz")

+1 
i learnt it same way!! crashed hardy heron to death on custom kernel compilation, now beating up jaunty n next waiting 4r karmic!!

---

### Post by Xbehave on 2009-10-26
> **Quick Silver said:**
> Thanks for all your quick responses. One thing I did not hear much about was gentoo or LFS does anyone have any opinions about those?
Compiling is sloooow, I learnt a lot when i installed gentoo but most of it was actually just because its a ground up distro, installing arch will probably teach most of that (if you pay attention to compiler flags when installing programs in gentoo you will more about how certain programs interact (infact just picking you compilierflags can teach you a fair bit))

reading the guides can be useful even if you choose not to install either:
[gentoo install howto]("http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?full=1") (covers compiling pretty well, probably worth a read)
[arch beginners guide]("http://wiki.archlinux.org/index.php/Beginners%27_Guide") (less compiling, so shorter/quicker)

Notes: [pulseaudio]("http://wiki.archlinux.org/index.php/Pulseaudio") is not covered by either (despite what critics say PA is the future of mainstream linux audio, so even if you don't like  it (AKA not understanding it) you should learn about it)
[Hal]("http://wiki.archlinux.org/index.php/HAL") is also worth digging into if your looking to learn the future of linux (both use hal but don't go in depth in the installation).

Can't comment on LFS as i've not read it.

---

### Post by Grifulkin on 2009-10-26
Install Crux there is a learning curve there.

---

### Post by Pasdar on 2009-10-26
> **Quick Silver said:**
> I am not sure exactly where else to post this other then here so I appologiize if I posted it in the wrong spot. Anyways, I have some basic and general knowledge of Linux (ubuntu) and I am able to get around fairly well. However, I want to learn more. I really want to learn how Linux works. I want to learn what each part of the file system and its folder do. Why they are there and how they can help me to get the most out of Linux. I have read a few suggestions like trying slax or gentoo and arch. I believe I read somewhere to start with arch then move to gentoo, then LFS. I really just want to get your opinion of where I should start and how I should progress. Also what are the advantages of learning from each of these different distros and are they going to help me learn linux overall or just their system and way of doing things.
By helping others find a solution to their problem in the problem section... you'll eventually be very experienced..

---

### Post by jpmelos on 2009-10-26
> **Pasdar said:**
> By helping others find a solution to their problem in the problem section... you'll eventually be very experienced..

I agree. Teaching is learning twice. You can see what the problem looks like through someone else experience, that's very good.

---

### Post by Quick Silver on 2009-10-27
Thanks again for all your replies. I think I'm going to mess around with Slackware

---

### Post by oobuntoo on 2009-10-28
The distros that make you pull out more hair are the ones that are best for learning Linux. All those pores left on your head will accelerate the process of learning through osmimosis.:lol:

---

### Post by Quick Silver on 2009-10-28
makes sense . . .

---

