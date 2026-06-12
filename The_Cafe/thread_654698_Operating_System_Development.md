---
title: "Operating System Development"
date: 2007-12-31
forum: The Cafe
---

### Post by Tux.Ice on 2007-12-31
Hello,

Me and a few buddies have decided to develop an operating system much like linux.

i am in need of graphic designers (i am one myself), and programmers(c, c++, python)

The operating system will be able to open .exe, .deb , .rpm, .tar.gz, as well as the other standard formats.

to ask specific questions please go to glacier.techotec.com/forum

tux.ice

---

### Post by Ozor Mox on 2007-12-31
Wow. Er, do you mean an operating system *kernel* like Linux, or a complete operating system like GNU/Linux distributions?

Have you considered contributing to one of the various open source operating system projects already out there?

---

### Post by fatality_uk on 2007-12-31
[http://mikeos.berlios.de/]("http://mikeos.berlios.de/")

This is quite cute

---

### Post by EdThaSlayer on 2007-12-31
That is quite a daunting task you have set there sir. GNU/Linux can do all the things you are proposing but that has been in development since the 1990's.

---

### Post by science4sail on 2007-12-31
well, one could combine several projects...

namely:
ReactOS
Wine

for the exe part, but that's just a kludge...

---

### Post by LaRoza on 2007-12-31
> **science4sail said:**
> well, one could combine several projects...

namely:
ReactOS
Wine


ReactOS isn't usable yet.

---

### Post by EdThaSlayer on 2007-12-31
> **LaRoza said:**
> ReactOS isn't usable yet.

It really needs a lot of work, I tried a live-cd of React OS, and it has quite a few bugs(and needs to look a bit prettier). :)

---

### Post by M$LOL on 2007-12-31
I wouldn't be too worried about it being ugly, functionality is what I would value. But yes, it's nowhere near usable yet, although the source code is fun to play with :)

---

### Post by Lster on 2007-12-31
May I say as someone who was and still is developing a kernel, you're in for a lot of work! Good luck all the same!

---

### Post by Methuselah on 2007-12-31
OS development is interesting and easier now with the greater availability of VMs.
Something more than a toy will probably be hard to achieve though.
Getting devices to work will be especially tough.

I have mixed feeling about ReactOS.
Everytime I think of helping, I wonder if my efforts wouldn't be better spent somewhere else. The end result would be liberating (ReactOS in a VM could replace windows for most uses especially if 3D acceleration through VMs becomes possible) but it seems like it would be better for it not to be necessary to emulate windows.

Ah well, I guess reality is what it is.

---

### Post by az on 2007-12-31
> **Tux.Ice said:**
> Hello,

Me and a few buddies have decided to develop an operating system much like linux.

i am in need of graphic designers (i am one myself), and programmers(c, c++, python)

The operating system will be able to open .exe, .deb , .rpm, .tar.gz, as well as the other standard formats.

to ask specific questions please go to glacier.techotec.com/forum

tux.ice

If you are starting from the point of wanting it to look a certain way and be able to open standard formats, I would tend to think you have no idea how much work is ahead of you.

You don't build any program from the ground-up by trying to make it look a certain way.  That's the last step.

It sounds to me as if your needs would be served a lot better by taking an existing OS and theming it.

---

### Post by insane_alien on 2007-12-31
> **science4sail said:**
> well, one could combine several projects...

namely:
ReactOS
Wine

for the exe part, but that's just a kludge...

those projects are pretty heavily intertwined.ReactOS is (at the moment) just standalone WINE with some bits stuck on.

---

### Post by forrestcupp on 2007-12-31
> **az said:**
> If you are starting from the point of wanting it to look a certain way and be able to open standard formats, I would tend to think you have no idea how much work is ahead of you.

You don't build any program from the ground-up by trying to make it look a certain way.  That's the last step.

It sounds to me as if your needs would be served a lot better by taking an existing OS and theming it.

That's true.  You're not going to need a graphic designer for a long, long time.

---

### Post by Nano Geek on 2007-12-31
> **az said:**
> If you are starting from the point of wanting it to look a certain way and be able to open standard formats, I would tend to think you have no idea how much work is ahead of you.

You don't build any program from the ground-up by trying to make it look a certain way.  That's the last step.

It sounds to me as if your needs would be served a lot better by taking an existing OS and theming it.

> **forrestcupp said:**
> That's true.  You're not going to need a graphic designer for a long, long time.I'd have to agree with both of these statements. 

Developing a new OS is *huge*. It will take you years of work just to make it somewhat usable. 

Make sure you're ready to do that much work before you start.

---

### Post by Tux.Ice on 2007-12-31
it will be like gnu/linux but yes we will be developing our own kernel by changing linux source code.

if anyone wants to contribute graphics or even coding please do

---

### Post by Tux.Ice on 2007-12-31
i do know that graphics and gui is last step, kernel being first , then a terminal like environment then gui

---

### Post by smartboyathome on 2007-12-31
I would say if you are going to change the Linux kernel source code, maybe develop a better software installer into the kernel (no ./configure, make, make install, just one command). Also, it would be very hard to interwind all those install formats since they install to different places normally (for example, .exe installs to C:\ while deb/tar/rpm/etc installs to /. I would suggest looking at the gobolinux project for an idea if you want to change the filesystem to accomodate this.

---

### Post by kopinux on 2007-12-31
ahhh! the spring time of youth!

until they learn it the hard way. it will take years to have a decent OS, maybe 10 years or so, and even with the stash cash of billions of $ like microsoft, they cant even buy time.

---

### Post by the_darkside_986 on 2007-12-31
Yeah really... the linux kernel is heavily developed, and distributions are heavily polished, but half of the distros don't even recognize my soundcard. 

Why not just make higher level software that can "open" or "read" those formats? You know, you can do basic binary file input/output without having to bypass the OS or make a new OS. 

If you mean opening and using the files as they are intended, linux can already be customized to do that. I've heard of people installing the redhat package manager in Debian or Ubuntu. I'm sure it is possible to associate the "exe" file type to be opened with "wine" in the nautilus settings. (Well, I'm not sure if it can distinguish between .NET executables and Win32 programs. By the way, does anyone know of a quick and safe way I can make my mono programs have a .mono extension instead of .exe? It seems so icky having exe's in Ubuntu...)

---

### Post by macogw on 2008-01-01
> **LaRoza said:**
> ReactOS isn't usable yet.

My friend Shane says it can play a bunch of his Windows games that don't work with Wine.

---

### Post by M$LOL on 2008-01-01
Yeah, a lot of people have good experiences with it from what I've heard, but it's far from finished. Certainly in my experience it's nowhere near useable, it won't boot natively on any of my machines, and it freezes randomly in my VM. There's still a lot of work to be done on it before it can even be considered for widespread use.

---

### Post by Tux.Ice on 2008-01-01
i was thinking of using a script so that when an application prompts to install to c:\ refine the directory to \ would this work??

---

### Post by Tux.Ice on 2008-01-01
would anybody like to help??

---

### Post by Tux.Ice on 2008-01-01
**bump**

---

### Post by Namtabmai on 2008-01-01
> **Tux.Ice said:**
> would anybody like to help??

Errr... perhaps you should review the posts in this thread. Creating a new operating system is no small task. Not to mention a few of your posts in this thread show you naivety in the subject, for example
[quote=Tux.Ice]
i was thinking of using a script so that when an application prompts to install to c:\ refine the directory to \ would this work??[/quote]
Suggesting that an operating system should, perhaps blindly, install into the root of a hard disk is just asking for trouble.

If you really want to go ahead with this project, I suggest doing the most important thing your project needs first. Planning.
Plan out, what you need to do, how you're going to do it, a time line of the events you need to achieve along with which parts of the project need to be completed before moving on to the next stage.
If you're starting from the ground up, get your kernel up and running and show people the benefits over Linux. This alone will probably take you a couple of years. Once you have a stable base such as this which can be shown to have major benefits over the Linux kernel then you'll find that you have lots of people wanting to help out, especially when you've got your project plan sorted and people can start asking to be involved with the various aspects of the OS that you plan on creating.

---

### Post by Tux.Ice on 2008-01-01
ok i shall do this - ty

---

### Post by Tux.Ice on 2008-01-01
any body have an idea where i can download the kernel source

---

### Post by Ebuntor on 2008-01-01
> **Tux.Ice said:**
> any body have an idea where i can download the kernel source

Here you go: [http://www.kernel.org/](http://www.kernel.org/)

I wish you good luck with your project, as people stated in previous posts it will take many many years before you even have a basic OS. 

You'd better review everyone's replies because I doubt you've got a clear picture of what you're getting yourself into, it's **a lot** of work, seriously.

---

### Post by zipperback on 2008-01-01
> **Tux.Ice said:**
> would anybody like to help??
 

Rather than try and get people from the Ubuntu community to try and build a new operating system from the ground up, why not try and improve on the very powerful and open source operating system that we already have.

And just so you know, I do have a great deal of experience with computers and programming. I've been using computers since the mid 1970's.

- zipperback
:popcorn:

---

### Post by bruce89 on 2008-01-01
It took me about 5 hours to write a GTK+ widget, goodness knows how long it would take someone to write a kernel.

---

### Post by Linuxratty on 2008-01-01
>  why not try and improve on the very powerful and open source operating system that we already have.

- zipperback
:popcorn:

 I'm in agreement with the other folks here...
Why reinvent the wheel?
 There are plenty of Linux distros you could work with who could benefit from your services...Pick one..
Or if you want to work with React, or BSD,  go for it.
  I really think you should work on what is already out there,rather than starting from scratch.
 Just my two cents worth.

---

### Post by p_quarles on 2008-01-01
> **bruce89 said:**
> It took me about 5 hours to write a GTK+ widget, goodness knows how long it would take someone to write a kernel.
I think it took Torvalds about a year to write the original (0.1) kernel -- but A) he's not a normal person; and B) it had nothing even remotely approaching the functionality of the current kernel, which is a massive, collaborative project that's been going on for nearly two decades. 

And let's not even mention Hurd. ;)

---

### Post by samwyse on 2008-01-01
> **Tux.Ice said:**
> any body have an idea where i can download the kernel source

Sorry, but I don't think this project is going anywhere.

---

### Post by bruce89 on 2008-01-01
> **p_quarles said:**
> I think it took Torvalds about a year to write the original (0.1) kernel -- but A) he's not a normal person; and B) it had nothing even remotely approaching the functionality of the current kernel, which is a massive, collaborative project that's been going on for nearly two decades. 

And let's not even mention Hurd. ;)

I forgot about Hurd, now I feel better.

> **samwyse said:**
> Sorry, but I don't think this project is going anywhere.

Linux? It certainly is.

If you meant this new one, fair enough.

---

### Post by Tux.Ice on 2008-01-04
yes yes i know i have now decided to just modify the kernel slightly and basically build a linux distro on top of it - and as long as i create a credits sheet i dont even have to call it glacier linux. :) ty for your criticism

---

### Post by bobbocanfly on 2008-01-04
If you are really serious about writing operating systems you could try hacking Minix's code. It is used in university Operating Systems courses and was designed to be educational. There are some really simple but satisfying hacks that can be done by changing one string in one functions, like editing the announce() function which displays the "Minix Version x.x.x - Copyright XXXXX". Thats obviously to get started with compiling it etc. there is much more stuff you can do with it.

---

### Post by smartboyathome on 2008-01-04
If you do want to run Windows programs on it, you will HAVE to use something like gobolinux's gobohide in order to hide the symlinks for the folders.

---

### Post by mips on 2008-01-04
Maybe try the programming forum?

---

### Post by hockey97 on 2008-01-04
since we are on the topic OS development.

I want to ask you guy's what a Kernal is really??
and what is really an .iso image?

---

### Post by DUDE_2000 on 2008-01-04
the one thing that comes to mind here, is trying to merge the reactos kernel with the linux kernel, then mess around with parts of debian and fedora, throw a DE on top of that, and start testing.

---

### Post by bobbocanfly on 2008-01-04
> **hockey97 said:**
> since we are on the topic OS development.

I want to ask you guy's what a Kernal is really??
and what is really an .iso image?

The Kernel is the low-level part of an operating system that connects between the CPU, RAM and other devices and allows applications to run. [http://en.wikipedia.org/wiki/Kernel_%28computer_science%29](http://en.wikipedia.org/wiki/Kernel_%28computer_science%29) will help a lot!

An iso image is a raw copy of an ISO9660 (CD) Filesystem. Its basically just the whole of a CD copied onto a comuter.

---

### Post by forrestcupp on 2008-01-04
Maybe it would be better for you to use the Linux Kernel, and just program a new window manager or desktop environment.

Or if you really want to get compatibility with .exe's why not just help with the Wine project.

You don't really need to start from the ground level.  Why not just create a DE, then create a new distro and figure out a way to integrate Wine into it seamlessly, then really go to work helping Wine become more compatible with Windows?

This would still be a huge project, but nothing like creating a kernel *and* doing all of the stuff I mentioned.  The Linux Kernel has taken 17 years to get where it is now, with many contributors.

---

### Post by Kernel Sanders on 2008-01-04
Personally, I suggest making contributing to PC-BSD. That project would be awesome if it had more support.

---

### Post by mehaga on 2008-01-04
Reading this thread, I keep asking myself how did the OP, who:

- started developing a new OS, but decided to plan it out only after someone here suggested he should do so, 
- wanted to develop it by modifying linux kernel without knowing where to find it's source code
- ...

get so many serious answers? :confused: :)

---

### Post by Tux.Ice on 2008-01-06
actually i knew about kernel.org i was just wondering if there was another site.

---

### Post by Namtabmai on 2008-01-06
> **Tux.Ice said:**
> actually i knew about kernel.org i was just wondering if there was another site.

Ah so you want the site which has the Python implementation of the Linux kernel for easier hacking? You want, [http://www.pythonkernel.org/](http://www.pythonkernel.org/).












Now be honest please, who actually clicked the link? :)

---

### Post by science4sail on 2008-01-08
> Ah so you want the site which has the Python implementation of the Linux kernel for easier hacking? You want, [http://www.pythonkernel.org/](http://www.pythonkernel.org/).


:lolflag:

---

### Post by Tux.Ice on 2008-01-10
hahaha :lolflag:

---

