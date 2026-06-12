---
title: "want to learn to program in Linux, need help with where to start"
date: 2014-04-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Tyler_Francis on 2014-04-29
I'm only 20 years of age, and it's been my dream since early High School to work on a Linux distro in some way shape or form, but.... I need some serious help figuring out where to start, not only do I need to figure out what programming language to start on to get my feet wet, I also need to learn what I need to do to eventually be able to build a linux OS from scratch (that one is mostly so that I can improve my skill and hopefully work on a bigger OS like Ubuntu some day) I was just hoping someone here could help point me in the right direction, and help me find some basic tutorials to get me started, thanks to anyone who can help at all!

---

### Post by ian-weisser on 2014-04-29
Well, "building a linux OS from scratch" yourself is a truly Herculean task. Only a few huge projects really do that. I would suggest a more modest goal.

1) Learn how to use the command line (bash and/or dash) shell.
2) If you have no previous programming language experience, start learning Python. Many advanced system features are written in Python.
3) If you have some previous programming experience, start learning C. Most basic system utilities are written in C.

---

### Post by Warren Hill on 2014-04-30
To build your own Linux you will need to know a lot.

For a start there is shell scripting.  Different linuxes use different shells Ubuntu's default shell is dash though bash is also installed.  I suggest you learn which commands are [POSIX]("http://en.wikipedia.org/wiki/POSIX") as then you can write scripts that run on several different shells.

Learn Python and C.  I agree with the previous post that Python is easier to learn so if you have no programming experience it's the best place to to start.

Once you are happy with that you can start learning how to make packages, and then ...

Take your time it's going to be a long journey but there is plenty of help available.

Don't expect to be releasing your own version of Linux for some time.

---

### Post by ssam on 2014-04-30
Have a look in the programming subforum. especially this sticky [http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253)

---

### Post by lykwydchykyn on 2014-04-30
Learning to program so that you can build your own Linux distro is like learning to farm so that you can cook your own food.  

You can't swing a dead ball mouse on the internet without hitting some kind of website that wants to teach you to code; codeacademy, coursera, edX, khanacademy, etc. etc.  A quick search should give you material for months.

But if you want to put together your own Linux distro, there really isn't typically a whole lot of coding involved.  It's more about selecting packages and configuring them to work together.  Knowing some scripting helps there, but it's a separate discipline from sitting down and writing an application, for example.

So which do you really want to do:  create a linux distro, or develop software?

---

### Post by tgalati4 on 2014-04-30
Why do you want to program?

---

### Post by Tyler_Francis on 2014-04-30
well I meant more so the learning to build a linux distro like to learn the basics, mostly how it works so I could eventually attempt to work on something else bigger, but that's for later on, MUCH later on, I'll look into python then if you guys think that's the best one to try and get started with. oh, and Tgalati4, the reason i wanna learn to program is that it's my dream to eventually work on linux on a regular basis, and actually have a purpose (not just tweaks or things for myself) I wanna do something with it. Thanks though, much easier to hear from people that know what to look into than to go through very vague google searches to figure out what may be best to use.

---

### Post by tgalati4 on 2014-04-30
It's your dream to do something with Linux that has a purpose.  

1. Why do you want to do something with a purpose?

2.  What purpose did you have in mind?

---

### Post by RadicaX on 2014-04-30
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

This also has books you use to get to setting up a Linux from scratch. This can give you an idea, but it takes a long time, and you need to follow instructions to a t when you do it first. 

As far as Programming, it is just to either tweak programs, or to make programs that fulfill a purpose. I one day was sick of typing in forumla for my calculator, and wanted a faster way of doing it, so I made a small program with python that let me do that on the command-line. Which made for finding the answers to problems much faster.

If you wanted a quick set of video tutorials on it. Thenewboston on youtube had a lot on there, and his videos are quick, and you can learn lots of commands. Programming as a tip from what I have done with it, is problem solving, you may learn commands, and be given tools, sometimes it does not work right, the computer does not understand, so you need to tell it a different way.

So programming is used to make features, or tweaks, or whatever, to get a job done. Some languages are better at certain things, or can do certain things. but go ahead and start with 1 language, do not try learning like 8 at a time or even 2 languages, learn one, get good at it, move on to the next one. If you learn python well enough, and decide you like programming still, move onto C or another language that is commonly used for things you like.

---

### Post by Tyler_Francis on 2014-04-30
thanks Radicax, those may help as even knowing what to look for still left me with the issues of where to look. and Tgalati4, not sure where you're going with this entirely? I've always wanted to do something with computers since I was little, when I was first introduced to Linux, I was just in awe at the number of possibilities with it. I love getting people set up on it, and the fact that it helps people who can't afford to buy the newest copy of windows or buy a bloody Mac still get to use their computers for something. So really I just wanna do anything I can to help linux as a whole grow (not just one distro but try and get more people to use it) I do know it's commonly used in server environments already, but I want it to reach out to more and more people, if I can learn to program in Linux, then I can hopefully help out more open source projects and if I'm lucky get more and more people into free computing. That's why I love the idea of working on Linux, I want it to expand so that more people can afford to get a computer, and so that we overall get more native Linux apps

---

### Post by SeijiSensei on 2014-04-30
I recommend you invest some time learning how to use the bash shell and how to write scripts.  Bash is a long way from writing kernel code in C, but it's a lot more useful in the immediate term.  I doubt you'd find writing device drivers from some poorly-supported network device the most rewarding way to spend your time.  Figuring out how to put together the right sequence of commands to accomplish a complex task may be more what you're looking for.

You might start here: [http://shop.oreilly.com/product/9780596009656.do](http://shop.oreilly.com/product/9780596009656.do)

---

### Post by Warren Hill on 2014-05-01
We still need lots of help fixing bugs.

Some of which you can do without being a programmer by reading the bug reports on launchpad and confirming the ones that are real and converting the ones that are not to questions

There is more detail here: [BugSquad]("https://wiki.ubuntu.com/BugSquad")

As your programming skills improve you will be able to submit patches and fix some of these bugs your self.

I Applaud your efforts, take your time learn one thing at a time but learn it well, stay active in the forum: you will be able to to help here before you are ready to contribute to the code.

Maybe you will build your own OS one day whether its a fork of an existing one with minor tweaks or you decide to stay with an existing one and try to make it better Linux is about community and helping each other.

You are free to say "it's just an OS" and use it but as this forum shows it can be much more.

I don't know if you have what it takes to become a developer, or if you will find it rewarding, but you will find  a level where you can contribute and I welcome you to the community.

---

### Post by Martha_Lois on 2014-05-01
Thanks for sharing some information about Linux. Actually, I only know Oracle Linux that can be downloaded, used and distributed free of charge.  This makes an ideal choice for your development, testing and production systems. Other than that, I just hope  I could easily learn Linux program also.

---

### Post by LastDino on 2014-05-01
I'm not gonna lie, programming scares me, I've long since learned that it is not my cup of tea when I was first introduced to C and C++ in collage as subjects.
Though, building Linux might more depend on your understanding of system and how things work rather than just programming. You can start by putting some light not so user friendly version of Linux in VM and try playing with it, your own experience is a great teacher and it will surely help you in long term whether you actually become good enough programer to make a difference or not. Good luck with it!

---

### Post by SeijiSensei on 2014-05-01
> **Martha_Lois said:**
> Thanks for sharing some information about Linux. Actually, I only know Oracle Linux that can be downloaded, used and distributed free of charge.  This makes an ideal choice for your development, testing and production systems. Other than that, I just hope  I could easily learn Linux program also.

Any Linux distribution can be freely distributed because most of the software is licensed under the [General Public License]("https://www.gnu.org/copyleft/gpl.html") or other [open-source licenses]("http://opensource.org/").  Oracle Linux is actually a "re-spin" of [RedHat Enterprise Linux]("http://www.redhat.com/").  RedHat was none too happy to see Oracle use RHEL to [convert RedHat's customers into all-Oracle shops]("http://www.serverwatch.com/server-trends/oracle-linux-gains-momentum.html").  But that is the way of the GPL.  Another re-spin, [CentOS]("http://www.centos.org/"), is basically RHEL without the support contracts and without RedHat's copyrighted materials like its logo.  They have [much friendlier relationship]("http://www.redhat.com/about/news/press-archive/2014/1/red-hat-and-centos-join-forces?utm_source=rss&utm_medium=rss&utm_campaign=red-hat-and-the-centos-project-join-forces-to-speed-open-source-innovation") than RedHat has with Oracle.

Ubuntu, by the way, uses [Debian]("http://www.debian.org/") as its base.

---

### Post by tgalati4 on 2014-05-01
Sorry for the [Vulcan Mind Probe]("http://en.memory-alpha.org/wiki/Vulcan_mind_meld").  Your journey into programming should align with what your desires are.  No sense learning C to write a network card driver if that doesn't help you move toward your purpose.  Joining a local Linux Users Group (lug), going to an open source conference (at least once a year), participating in forums, testing new distros, and helping others find freedom in their computing experience will keep you busy.

Is there is a particular open source project that you want to contribute your time and effort?  Find out what language or languages (many projects are built with frameworks written in multiple languages).  That will narrow down your choice.

Sometimes the questions are more important than the answers.

---

### Post by abbat.81 on 2014-05-02
Gambas.
Very easy to make any GUI apps.

---

