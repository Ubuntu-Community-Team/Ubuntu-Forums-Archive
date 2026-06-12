---
title: "xp to linux primer?"
date: 2005-10-10
forum: The Cafe
---

### Post by lost.sync on 2005-10-10
i only installed ubuntu as an act of boredom.  now i'm completely hooked, as it's solved all of my previous gripes about linux (i'd previously only tried rpm-based distros and installing anything wound up a tangled mess of unmet dependencies).  i've actually completely switched from xp except for my audio work, which can't be done on linux, and for watching dvds because i haven't gotten my ati's s-video out to work yet (haven't tried).

thing is, i'm an xp power user.  if i need it done in xp, it gets done.  i know where everything is and what to change and blah blah.  i'm totally that guy people call when something breaks.  i am the spyware cleaner.  i am the trojan remover.  i am the 'please please please stop opening IE' guy.  

and i've done pretty well with ubuntu so far, i think, much thanks to the existance of this forum and ubuntuguide.org, but there are some things i just don't know where the windows equivalents of are, or locations of files and installed programs.  some very basic things (like what exactly a lib* package is for - i assume it's the linux equivalent of a .dll but i don't honestly know for sure) are still very foggy concepts to me.  

and it's a little frustrating.  

so i was wondering if there was an article or something somewhere that shows where linux equivalents of things are.  mostly i just mean in the filesystem.  in windows, everything is pretty much in the registry or /system32 somewhere, /program files if it's a speciffic app i'm trying to mess with, but in linux, i have no clue.  

also some info about _why_ some things are the way they are.  why is there no linux equivalent to .exe?  why can't apps just have installers?  why do i have to compile things?  why would i want to compile my own kernel?  why can't i write to my ntfs partition (problematic because in xp i can't even see my linux one)?

so many questions.  how important is a swap partition?  is this identical to pagefile.sys? where can i get more fonts?  why do so many fonts look exactly the same?

it goes on and on.  i feel pretty lost sometimes.  i basically just don't quite get the architechure of it all.  i don't know where things are coming from.  but overall it's a breath of fresh air and a very welcomed set of challenges.  it's a lot of information to suddenly not have anymore though, you know?

i really love this distro.  i've dual booted a fair amount since i got my first distro (red hat, late 90s) but i never thought i'd make a full-on switch - it'd been years since i even thought about installing linux when i did it this time - i tried a long list before i got to ubuntu and once it booted i just quit looking instantly (synaptic totally owns me).  if it weren't for my being a musician and needing Max/MSP and Reason as well as not being able to get my wifi to work under ubuntu, xp would be history.

anyway, any help would be much appreciated.  thanks in advance.  just to clarify, i'm not asking these questions, just where to find out the answers to them.  i figured some of you probably have some good resources.

---

### Post by brt on 2005-10-10
contains lots of helpful info and links:

[http://linux-newbie.sunsite.dk/]("http://linux-newbie.sunsite.dk/")

for me this was also very helpful:
[http://www.debian.org/doc/manuals/securing-debian-howto/]("http://www.debian.org/doc/manuals/securing-debian-howto/")

---

### Post by GeneralZod on 2005-10-10
> **lost.sync] 
some very basic things (like what exactly a lib* package is for - i assume it's the linux equivalent of a .dll but i don't honestly know for sure) are still very foggy concepts to me.  
[/QUOTE]

That's pretty much spot-on said:**
>  
in windows, everything is pretty much in the registry or /system32 somewhere, /program files if it's a speciffic app i'm trying to mess with, but in linux, i have no clue.  


What type of things are you looking for? There's (thankfully!) no concept of a system registry in Linux.  Typically, system-wide configurations are stored in /etc.  Give us a few details of the type of tasks you're trying to perform, and we'll see if we can give the Linux equivalents :)

As for programs, typically the executable file is placed in /usr/bin, and thus can be invoked from the command-line (or the "Run Program" prompt) by typing its name.  The rest of the stuff is scattered all over the shop :) If you're looking to be able to just move your installed programs around for some reason (and, as someone who is probably a "power user" of Linux, I've never once wanted to do this), then I'm afraid you're out of luck.  Again, give us some specific tasks you'd like to perform and we'll let you know if there is an equivalent in Linux.

As mentioned, an application's system-wide configuration, if it has one, will be placed in /etc.  It's user-specific configs will invariably be located in ~ or a subdirectory; for example, the configs for most KDE apps are placed in ~/.kde/share/config (I think).  gaim's are stored in ~/.gaim, etc.


> 
also some info about _why_ some things are the way they are.  why is there no linux equivalent to .exe?  why can't apps just have installers?  why do i have to compile things?  


Poofyhairguy made an excellent thread on this topic; I'll try and track it down and post it here.

Edit:

Here it is:

[http://ubuntuforums.org/showthread.php?t=54227&highlight=linux+exe](http://ubuntuforums.org/showthread.php?t=54227&highlight=linux+exe)

> 
why would i want to compile my own kernel?  


99.9% of home users wouldn't.  Some people want to keep a very lean, mean kernel, though, and will re-compile it after configuring out all of the stuff they don't want.  

> 
why can't i write to my ntfs partition (problematic because in xp i can't even see my linux one)?


Microsoft has never released the specs, and it is proving exceedingly hard to reverse-engineer - in my opinion, it probably won't ever happen, unfortunately.  Check out captive-ntfs for a stop-gap solution, though, although I really cannot recommend it.

> 
so many questions.  how important is a swap partition?  is this identical to pagefile.sys? 


Very important; if you run out of RAM, you will need to write to swap or you'll be in trouble :) It serves the same function (I think) as pagefile.sys, but has the disadvantage that, since it is a partition and not a file, it cannot easily be resized.

> 
where can i get more fonts?  why do so many fonts look exactly the same?


Search the forums for "mscorefonts" (I think) :)


Glad to see that you're enjoying things so far, and are willing to learn this new system instead of insisting that it copies Windows - it's really a breath of fresh air! Any more specific questions, please post here.  This should really be in Community Chat, though, so I'll ask an admin to move it there.

---

### Post by dr.drake on 2005-10-10
hello,

I've also just try to switch to linux, and a lot of the questions are the same...

the hardest part about not having installer files for programs for me is that if i want a program that is not in synaptic, I really have no clue as how to install it?
where do I put the downloaded file and how do I install it? how to install a plugin for software is my main concern now. (next to getting my ATI-radeon 7000 tv-out to work)

as for your ntsc partitions: while in windows convert them into FAT32 and there will be no problem anymore. and come next thursday, with the release of ubuntu  breezy, you don't even have to mount the partitions anymore, they will be just available.

about the fonts: you can just copy all your fonts that you have in windows into linux with a simple copy/paste of the 2 fonts folders.

and when you find a solution for the audio multitrack software: please let me know!!! I also am a musician that will be dual booting with windows for this reason: I need my cubase/protools...
I have tried to instal "audacity" which is suposed to be the linux version, but have never gotten it to work really.

anyway, I'll be looking at the two links that brt gave above.

cheers, eric.

---

### Post by brt on 2005-10-10
i will try to answer a few of them:

> **lost.sync]
and i've done pretty well with ubuntu so far, i think, much thanks to the existance of this forum and ubuntuguide.org, but there are some things i just don't know where the windows equivalents of are, or locations of files and installed programs.  some very basic things (like what exactly a lib* package is for - i assume it's the linux equivalent of a .dll but i don't honestly know for sure) are still very foggy concepts to me. 

and it's a little frustrating.  
[/QUOTE]

hmm, i am using Debian/Ubuntu for years now and never had to worry about lib* packages as all dependencies are managed by my OS (synaptic,dselect,dpkg,apt). the only time when i ran into trouble was when i had to compile software for myself and the ./configure script complained about missing header files, then i just had to install a lib*-dev package and everything worked fine...

[QUOTE=lost.sync]
so i was wondering if there was an article or something somewhere that shows where linux equivalents of things are. [/QUOTE]

well maybe some things may have equivalents some things are just different, the most important directories are:
/usr     -  (allmost) all programs, src files, libs
/var     - changing files like logs, mail etc.
/etc     - all global configuration files (services, X11, ...)
/home - where all the personal users files will be stored
/dev    - device-files (eg. /dev/hda: your first ide-hd, /dev/input/mice, ...)
/lib      - is where all your kernel drivers are (you will never have to mess around here)

all your personal application-configuration files are stored in your home-dir (/home/username). they are in hidden directories which means they have a leading dot in their name (eg. .mozilla). to list hidden files in a terminal you will need ls -a or ls -la (long format) btw. ~/ is a short for your home-dir so you can use "ls -la ~/" to have a complete list of all your files and directories in your homefolder.

[QUOTE=lost.sync]also some info about _why_ some things are the way they are.  
[/QUOTE]
maybe because its not designed by M$  said:**
> why can't apps just have installers?
because you don't need them. your OS has a program (synaptic) which does that for you in an absolut clever way...

> **lost.sync]why do i have to compile things?[/QUOTE]
usually you don't need to compile anything, as all you need is availiable as binary packages, but you are free to compile anything you want...

[QUOTE=lost.sync]why would i want to compile my own kernel?[/QUOTE]
if you want a specialised kernel with just the few drivers/options you need to compile your own, but the standard kernels coming with ubuntu are compiled by very experienced people so i assume the will work much better then any selfcompiled by an unexperienced user...
[QUOTE=lost.sync]why can't i write to my ntfs partition (problematic because in xp i can't even see my linux one)?[/QUOTE]
because write support for ntfs in Linux is VERY limited. its because ntfs is proprietary and M$ folks are not willing publish the source code.
but there are drivers for Linux's ext-filesystem so you can read and write ext-fs under xP:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
[http://sourceforge.net/projects/ext2fsd]("http://sourceforge.net/projects/ext2fsd")

[QUOTE=lost.sync]how important is a swap partition?  is this identical to pagefile.sys?[/QUOTE]
the Linux kernel has a really smart memory-management, and will only put something into swap when its really needed. i never tried running a system without swap-partition, why should i? i am sure nothing is faster or better without a swap-partition. from a users-point of view a swap partition maybe for the same purpose like the pagefile.sys but i am sure its not identical  said:**
> where can i get more fonts?
try searching your packages (name and description) in synaptic for fonts, you may find some interesting things...
another interesting resource, also about fonts and may other...:
[http://www.mozilla.org/docs/end-user/dark-mozilla-fonts.html]("http://www.mozilla.org/docs/end-user/dark-mozilla-fonts.html")

---

### Post by brt on 2005-10-10
[QUOTE=dr.drake]the hardest part about not having installer files for programs for me is that if i want a program that is not in synaptic, I really have no clue as how to install it?
[/QUOTE]
usually i put it to /usr/src after unpacking i look for a file called README or INSTALL, this usually contains information howto compile and setup your software
in most cases, just enter the directory and execute "./configure" if there are problems it will tell you e.g. some missing header files, in this case you will have to install according headers, usually you will find them with synaptic they are called lib-*whatever*-dev. if "./configure" runs without problems, run "make" and then "sudo make install" this should compile and install the software. thats the standard way, may fit 90% of software but always look if there is any information in the package (doc, README, INSTALL) as sometimes the process maybe different or there is a install.sh shell script, whatever... there is always some information somewhere, you will see...


[QUOTE=dr.drake]how to install a plugin for software is my main concern now. (next to getting my ATI-radeon 7000 tv-out to work)[/QUOTE]
try looking for howto's here in  the forum, [ubuntuguide]("http://www.ubuntuguide.org/") or via google, i am sure you will find a solution wich will fit exactly to your problem :D

[QUOTE=dr.drake]and when you find a solution for the audio multitrack software: please let me know!!![/QUOTE]
did you know that there is a Linux distribution designed specially for multimedia-artists? its dyne:bolic, have look at: [http://www.dynebolic.org/]("http://www.dynebolic.org/")
it features a well working live cd with the ability to save things on your hardrive or install on your harddrive too... it comes with lots of audio/video tools

[ardour]("http://ardour.org/") is a very good multi-track hardiskrecording software works also together with [Jack]("http://jackit.sourceforge.net/") and [Jamin]("http://jamin.sourceforge.net/en/about.html")

---

### Post by SilentCacophony on 2005-10-10
Here are some more links that you may or may not have seen:

[New to Linux? Need a program?]("http://www.ubuntuforums.org/showthread.php?t=33183") - a sticky thread in Absolute Beginner Talk here

[The table of equivalents / replacements / analogs of Windows software in Linux]("http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml") - a link from the above thread

[http://www.ubuntuforums.org/links/]("http://www.ubuntuforums.org/links/") - The 'Link Directory' tab from the forums here has a lot of good links

I also found this quite helpful:

[LinuxCommand.org: Learning the shell]("http://www.linuxcommand.org/learning_the_shell.php") - A good starter for shell usage, with description of the filesystem organisation.

I find the learning and experimenting with linux to be the most rewarding feeling I've gotten from computer use in years. I am also 'the go-to guy' for Windows problems in my circle, but the way MS attempts to abstract the inner workings of the OS always irritated me. Being proficient at using hidden registry settings or rooting out nefarious spyware from it is nothing compared to complete command of your OS that you can achieve in linux.

Have fun!

---

### Post by lost.sync on 2005-10-10
very, very helpful stuff guys, as always.  thank you very much!

---

