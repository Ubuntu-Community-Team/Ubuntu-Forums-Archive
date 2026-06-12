---
title: "a few questions about Ubuntu"
date: 2006-04-25
forum: Testimonials &amp; Experiences
---

### Post by mentallysilent on 2006-04-25
I love this distro, it is really something. However I wonder why such a cool distro misses things like C/C++ compilers, man pages, and most importantly the source code. Afterall not everyone uses their computer just for "sending emails" and "creating spreadsheets". Some people use it for writing their programming assignments and need cc/gcc. Others like myself develop device drivers and for that the kernel source is needed. Admittedly it is not much of a hassle to start Synaptics and get dev-essential, etc, but I'd rather have these things come with the system. For device drivers I have switched to Gentoo and I don't want to because it is time consuming to get a Gentoo system up and running. I know its probably easy to install the kernel myself but this makes no sense. It's a critical part of the system that must be there in the first place. I'd rather break my head against the wall trying to setup a high performance cluster of Ubuntu machines, not how to install the kernel source!! So please include things mentioned above in the future releases. Like I said, there ARE people who do more things with their machines than "reading email";)

Regards

---

### Post by dermotti on 2006-04-25
That doesnt make sense to do what your saying. Because eveyrone has certain packages they use, and arent on the base system. Ubuntu just tries to put in the what the majority of people will use. And most people won't be using hte build-essential package.

I mean i wish Ubuntu came with Lighttpd, PHP, and MySql standard, but the majority of people could care less.

Thats the beauty of the repos, you can get whatever you want after the fact.

---

### Post by cilynx on 2006-04-25
I don't quite get what you're looking for.  Everything you mentioned is easily available via a quick apt-get.  Thus, they are included "in the system".  Are you saying that you think they should be installed by default?  If so, I'm going to have to disagree.  While I'm a power user on a couple of systems, most of my Ubuntu systems are desktop machines.  Having the kernel sources, compilers, and linkers and such installed would just be wasting my space.  It all comes down to where you draw the line on things that some people are going to use and others aren't.

---

### Post by Packman5280 on 2006-04-25
well, I may be too much a noob for this conversation, but judging by what i am looking at, it would be good to have the kernal source included.  I could be dumb, but I am reading an error right now that says I need the kernal source in order to install my chipset drivers.  maybe I am just missing something.

---

### Post by mentallysilent on 2006-04-25
Then would you kindly enlighten me with a simple apt-get line that will get me kernel sources compiled and installed? I mean that 200MB mammoth of a software Oo is included which I never use, but a tiny gcc compiler is not. I'm not saying scrap Oo. I'm saying include both and the end user will decide what he does or doesn't need. From the oh-so-many people that use any flavour of Linux, I guarantee most would want to be able to compile things. Those who don't are already happy witht their swiss cheese OS that is XP and MSOffice. Again my friends I do not intend a flame war, I was just surprised to realize that I have to install the kernel sources and compiler on a UNIX based system...

---

### Post by harishg on 2006-04-25
There are people from all background who use the operating system and it is not possible to include everything in a single CD.Well the idea would be may be using multiple CDs but it becomes cumbersome for a beginner.Also those who want to have a look at te codes obviously have some sort of internet connection and hence they can apt the software.Most people need a simple system to read email use office and listen to music and watch movies and for that Ubuntu system is perfect.

---

### Post by mjm115 on 2006-04-25
From [http://www.ubuntu.com/ubuntu:](http://www.ubuntu.com/ubuntu:)
> 
When you finish your Ubuntu installation your system is immediately usable. You have a full set of business productivity applications, internet applications, drawing and graphics applications, and games. That one CD gives you a very good desktop environment out of the box, with many applications for business, home and personal computer users installed by default. There are thousands of additional pieces of software that are just a few clicks away, but **we've done the hard work to get the basics in place easily and effectively.** 

Ubuntu was designed with the "average joe" user in mind.  The "average joe" user doesn't know how to compile sources or tinker with the kernel.  Therefore, compilers and sources don't come with the default install.  The "average joe" user browses the web, checks e-mail, and types documents.  That's why the software applications are included.  That's why Ubuntu is one of the most popular distros on the planet.  It doesn't install that unnecessary apps that the majority of people don't use.

---

### Post by steve0921 on 2006-04-25
I think installing build-essential by default might be a good thing. I've installed ubuntu on 3 different systems so far, and in each case there was at least one thing (wireless, video, etc.) that did not work perfectly out of the box. The solutions to these problems often involved compiling new drivers or related programs from source.

Although it isn't hard to download the package myself, I think this is adequate justification for most users needing build-essential installed by default. Also, if a new user is simply copying and pasting instructions from a driver maker's readme, this crucial beginning step is rarely mentioned, and it may be hard to figre out what's wrong.

-Steve

---

### Post by DW5 on 2006-04-27
I second that.  I'm currently setting up an old i series Thinkpad for use as a back up machine for classroom use.  It doesn't have an internal network card so I scrounged up an old D-LINK DWL-650 PCMCIA network card, but guess what, in order to get to the network at all I have to compile wlan-ng to do it.  Thus, no synaptic, etc.  I need kernel sources installed and configured before I can compile the driver.  I can follow directions and have compiled drivers, etc before, but I don't do it everyday or every month and so doing all that prep work before I can untar and compile that driver compels me to calculate how much time I have to waste on such a project.  

Edit: Now that I think about it, do I need kernel sources, or do I just need the kernel headers and build-essential (which are on the cd)?  Like I say, I don't do this very often.

I do like ubuntu.  It's what led me to convert wholly to linux after piddling off and on for a few years.  Now, there are two applications that keep my main machine a dual boot, and I hope in a year or less, that will not be true.

---

### Post by cilynx on 2006-04-27
*Disclaimer:  I'm in a bad mood this morning...take this with a grain of salt...*

I think the 'average joe' idea holds a lot of water.  Keeping the system as trim as possible while being a fully featured desktop is IMHO a good thing.  My other argument is that while I personally install build-essentials pretty much immediately, most 'end users' don't.  Keep in mind, if you're not techno-savvy enough to have 'apt-get install build-essentials' not be a problem, then you're definately not techno-savvy enough to build a kernel from source.  (I know there are exceptions to this...an old boss of mine was a UNIX master, but couldn't do package management to save his life...)

A second point on the kernel topic:  Distros aren't supposed to make rolling your own kernel easy.  It's not their job.  The point of a distro is that you can quickly and easily get a system up and running without having to know what you're doing.  If you want to roll your own kernel, go for it.  I do for a couple of my systems.  I just don't understand why you would want the hinderance of having to compile the kernel the way your distro wants you to.  It seems to me that you're pretty likely to wind up back with the distro stock kernel or at least something close to it.  Personally, I just get my source from kernel.org.

To answer the question above:  to build a package againts the stock kernel that you're running, all you need is build-essential and the kernel-headers for your running kernel.

---

### Post by mmcmonster on 2006-04-27
I think that most users will not need build essentials at all.

That is because they will not *ever* compile a kernel or kernel module.

Think of it this way:  If you are a user that needs to do a compilation, you have to know where to get the source, where to install the binary, how to do the build, how to make sure the PATH is correct, make sure all the dependencies are met, etc.

Downloading build-essentials is the least of their problems.

---

### Post by .t. on 2006-04-30
Since switching to Ubuntu, I have not needed to compile a kernel or even a kernel module. This may change when a patch is release for Ubuntu Studio that enables realtime preemption, however, I do still think that having build-essential and the kernel headers installed by default is a very good idea.

On the other hand, making users install them forces them to think about what they are doing; makes them take notice that they *can* recompile the kernel. It gives them the FOSS mentality, which I think is more important.

---

