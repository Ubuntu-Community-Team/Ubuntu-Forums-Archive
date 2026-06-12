---
title: "GNU/Hurd when it's finally ready think it'll be as widly used as GNU/Linux"
date: 2008-08-26
forum: The Cafe
---

### Post by jerome1232 on 2008-08-26
I just saw a page about Debian GNU/Hurd in development, just curious what's everybodies opinion on Hurd vs Linux. Have any of you tried Hurd (even though it's in development still)?

I was thinking about giving it a go once my new power supply gets here.

---

### Post by Yes on 2008-08-26
Hasn't it been in development for like... 20 years or something?

---

### Post by LaRoza on 2008-08-26
> **jerome1232 said:**
> I just saw a page about Debian GNU/Hurd in development, just curious what's everybodies opinion on Hurd vs Linux. Have any of you tried Hurd (even though it's in development still)?

I was thinking about giving it a go once my new power supply gets here.

I don't think it will overtake Linux, but I think it will be used in some environments.

And you don't need a new powersupply to use it (unless your old one needs replacing anyway)

---

### Post by jerome1232 on 2008-08-26
Yeah something like that, I didn't realize debian was part of it though

---

### Post by Dremora on 2008-08-26
HURD is 24 years old and it still doesn't work.

Something tells me that it probably never will work, it's been all but abandoned.

Even if it did work, the FSF makes it, so you wouldn't want to use it if you wanted any of your hardware to work, they'd probably put blocks in it to keep binary drivers from working.

---

### Post by howlingmadhowie on 2008-08-26
> **Dremora said:**
> Even if it did work, the FSF makes it, so you wouldn't want to use it if you wanted any of your hardware to work, they'd probably put blocks in it to keep binary drivers from working.

the binary blobs would have to be written for it first. 

even if the HURD does turn out to be remarkably good, the linux kernel has enormous momentum. the desire to complete the HURD is also lacking seeing as there already is a number of free software operating system kernels.

---

### Post by jerome1232 on 2008-08-26
> **LaRoza said:**
> I don't think it will overtake Linux, but I think it will be used in some environments.

And you don't need a new powersupply to use it (unless your old one needs replacing anyway)

And yes my non-production machine is having power woes, (at least random devices randomly fail, and in bios some voltages were almost a full volt off, I've had HDD's ruined by PSU's going out so that machine stays off 'till I can replace it)

So I take from this so far that **if** Hurd ever is ready for production machines, don't hold your breath it might be awhile lol.

---

### Post by Dremora on 2008-08-26
> **howlingmadhowie said:**
> the binary blobs would have to be written for it first. 

even if the HURD does turn out to be remarkably good, the linux kernel has enormous momentum. the desire to complete the HURD is also lacking seeing as there already is a number of free software operating system kernels.

Well, the FSF endorses Gnewsense Linux, the kernel has no binary drivers, and they even stripped out some things they disliked that were 100% free, so look how nothing works on THAT.

I think the HURD is dead and the FSF just doesn't want to admit it.

---

### Post by Bachstelze on 2008-08-26
> **Dremora said:**
> Well, the FSF endorses Gnewsense Linux, the kernel has no binary drivers

But it certainly doesn't stop you from installing them yourself if you want them.

I don't like the FSF more than you do, but no misinformation please.

---

### Post by days_of_ruin on 2008-08-26
> **jerome1232 said:**
> I just saw a page about Debian GNU/Hurd in development, just curious what's everybodies opinion on Hurd vs Linux. Have any of you tried Hurd (even though it's in development still)?

I was thinking about giving it a go once my new power supply gets here.

Gnu/hurd is a joke.

---

### Post by Bachstelze on 2008-08-26
> **days_of_ruin said:**
> Gnu/hurd is a joke.

No. It just started with a big mistake, that RMS himself admitted. The joke, however, is that they continue working on it while knowing it was designed the wrong way right from the start instead of just saying "Okay, this is going nowhere, let's just dump it and take a fresh start".

---

### Post by Dremora on 2008-08-26
> **HymnToLife said:**
> But it certainly doesn't stop you from installing them yourself if you want them.

I don't like the FSF more than you do, but no misinformation please.

Right, there's nothing stopping you cause it's Linux, HURD probably would.

And there's no reason to use Gnewsense cause it's just old Ubuntu with no drivers for anything.

---

### Post by Dremora on 2008-08-26
> **HymnToLife said:**
> No. It just started with a big mistake, that RMS himself admitted. The joke, however, is that they continue working on it while knowing it was designed the wrong way right from the start instead of just saying "Okay, this is going nowhere, let's just dump it and take a fresh start".

Look at the commit log, it's not really under development, more like someone gets bored a few times a year and comes up with a patch.

---

### Post by Bachstelze on 2008-08-26
> **Dremora said:**
> 
And there's no reason to use Gnewsense cause it's just old Ubuntu with no drivers for anything.

Just because *you* see no reason to use it doesn't mean no one does. It just wouldn't exist if that was the case.

Also, "no drivers for anything", huh? It's a wonder the thing works at all, then. Seriously, you should educate yourself a bit before talking about things.

---

### Post by Dremora on 2008-08-26
> **HymnToLife said:**
> Just because *you* see no reason to use it doesn't mean no one does. It just wouldn't exist if that was the case.

So if I take the engine out of my car, that doesn't make it useless. :lolflag:

OK, bad analogy, more like the radio, ABS system, air conditioning, heater, window controls, and windshield wipers. ;)

---

### Post by Bachstelze on 2008-08-26
> **Dremora said:**
> So if I take the engine out of my car, that doesn't make it useless. :lolflag:

Who talked about the engine? Removing the leather seats, embeded DVD player and GPS system doesn't, though.

---

### Post by Dremora on 2008-08-26
> **HymnToLife said:**
> Who talked about the engine? Removing the leather seats, embeded DVD player and GPS system doesn't, though.

Removing hardware enabling drivers, and codecs for multimedia for no reason whatsoever is just lunacy.

RMS has zero credibility, especially after his attack on the XO Laptop and sending people to annoy Apple salespeople.

---

### Post by howlingmadhowie on 2008-08-26
> **Dremora said:**
> Removing hardware enabling drivers, and codecs for multimedia for no reason whatsoever is just lunacy.

RMS has zero credibility, especially after his attack on the XO Laptop and sending people to annoy Apple salespeople.

they have been removed for very good reason. the aim of the free software movement was to create a complete fully-free operating system. when linus torvalds contributed his kernel to the project there was very little desire to complete the hurd. however, the linux kernel is still under gpl2, and the binary blobs in the kernel code are of dubious legality. 

a distribution such as gnewsense fulfills a number of purposes. To start with, it represents the current culmination of stallman's ideals. it is a totally free product. you can theoretically know everything the computer is doing. you can read the sourcecode for every piece of software on the computer. you can help yourself and also be helped by others. you can share everything with your friends without any risk of legal action being taken against you. 

you may not value these things. some people do value them very much. without these people there would be no ubuntu, there would be no open internet protocols, there would be no wikipedia or similar. these people are pushing for highest possible amount of freedom. their work is far from pointless.

---

### Post by Dremora on 2008-08-26
Meh, if I share a piece of software with a few friends, the assholes that are sue happy would never know it anyway.

So that whole "legal action for sharing with friends" deal is bull.

Come to think of it, Broadcom and Nvidia drivers have redistribution rights anyway, and are never "built in" to the kernel itself, Broadcom driver is even GPL, it's just the firmware you have to cut out of the Windows redistributable.

---

### Post by SunnyRabbiera on 2008-08-26
Well if people got their act together HURD could be the successor to linux, its concept is supposed to pick up where traditional unix has left off but with linux and BSD being a focus of open source developers there isnt much interest.

---

### Post by zmjjmz on 2008-08-26
Actually Dremora, I believe Mr. Psychopath got it working on his laptop once.

---

### Post by tom66 on 2008-08-26
If they want everything open source, then does that mean all the firmware on the computer must be open source? The CD player firmware? Also, I think a processor contains a small amount of code programmed (correct me if I'm wrong) into it so does it mean all processor designs must be open sourced?

While I appreciate free software very much - and I use it - I think that complete freedom is not really possible.

---

### Post by Vivaldi Gloria on 2008-08-26
> **Dremora said:**
> And there's no reason to use Gnewsense cause

There are some reasons:
1) It's a very good OS.
2) Some people care about freedom: [[COLOR="Blue"]shouldbefree[/COLOR]]("http://www.gnu.org/philosophy/shouldbefree.html")
3) bbrazil created a tool called 'Builder' to create your own variants of Ubuntu.
4) Contrary to gobuntu it has a nice community behind it.

>  with no drivers for anything.
I think you are confusing gnewsense with a brick.

> Well, the FSF endorses Gnewsense Linux, the kernel has no binary drivers, and they even stripped out some things they disliked that were 100% free, so look how nothing works on THAT.

Actually pretty much everything in a desktop system works in gnewsense. Depending on your graphics card you may not get 3D support. I have intel 3100 and the FOSS drivers work great. Just research a bit before you buy a new component and you can also enjoy a system with only FOSS on it.

> Removing hardware enabling drivers, and codecs for multimedia for no reason whatsoever is just lunacy.
Most codecs are removed because of legal reasons. Even ubuntu cannot ship them. Only proprietry drivers are removed. Again, some people care about software freedeom and there are a lot of advantages of using free software.

> RMS has zero credibility, 
You are funny.

> especially after his attack on the XO Laptop and sending people to annoy Apple salespeople.
I cannot see the relevance of these to case at hand. But I'll answer anyway. Actually almost everyone stated negative opinions about xo laptop. See for example

[http://radian.org/notebook/sic-transit-gloria-laptopi](http://radian.org/notebook/sic-transit-gloria-laptopi)
[http://government.zdnet.com/?p=3824](http://government.zdnet.com/?p=3824)

And the apple campaign raised valid points:

[http://www.fsf.org/blogs/community/5-reasons-to-avoid-iphone-3g](http://www.fsf.org/blogs/community/5-reasons-to-avoid-iphone-3g)
[http://www.fsf.org/blogs/community/why-free-software-and-apples-iphone-dont-mix](http://www.fsf.org/blogs/community/why-free-software-and-apples-iphone-dont-mix)

Again, they are no way alone in their opinions of apple:

[http://arstechnica.com/news.ars/post/20080725-tim-oreilly-internet-innovation-requires-an-open-web.html](http://arstechnica.com/news.ars/post/20080725-tim-oreilly-internet-innovation-requires-an-open-web.html)
[http://www.wired.com/politics/security/commentary/securitymatters/2008/02/securitymatters_0207](http://www.wired.com/politics/security/commentary/securitymatters/2008/02/securitymatters_0207)
[http://attrition.org/security/rant/z/iphone.html](http://attrition.org/security/rant/z/iphone.html)
[http://www.who-sucks.com/tech/15-reasons-why-apples-iphone-sucks](http://www.who-sucks.com/tech/15-reasons-why-apples-iphone-sucks)


About hurd:

Diversity has always been the strong point of linux. I don't see that hurd gets wide deployement. But there are a lot of lessons to be learned from hurd:

[http://video.google.com/videoplay?docid=-7449462856350014702](http://video.google.com/videoplay?docid=-7449462856350014702)



[QUOTE=tom66]I think that complete freedom is not really possible.[/QUOTE]

Well, software is almost there. On the hardware front, there are also good developments like the free ati drivers. More hardware vendors are understanding the importance of free drivers. I think an important castle to conquer is the free bios:

[http://www.fsf.org/campaigns/free-bios.html](http://www.fsf.org/campaigns/free-bios.html)
[http://www.coreboot.org/Welcome_to_coreboot](http://www.coreboot.org/Welcome_to_coreboot)

---

### Post by DeadSuperHero on 2008-08-26
> **zmjjmz said:**
> Actually Dremora, I believe Mr. Psychopath got it working on his laptop once.

That I did. It took a hell of a lot of work, though. 

That was CLI only, however.

---

### Post by andamaru on 2008-08-26
the ideas behind hurd are good, but that project is dead. The new Ubuntu distro they made is perfect, for their ideas anyways.

What I hate, and I'm sure a lot of people share this, is anyone who try to force or feels that they are better than someone because they are using 100% open software. I find that RMS and his "followers" tend to follow in one of those two groups.

---

### Post by jerome1232 on 2008-08-26
And I was hoping that maybe a in another few or so years, I'd have yet another OS to choose from. 

Being Debian and GNU I wouldn't even have to adjust much to use it.

---

### Post by Dremora on 2008-08-27
Regarding HURD's future, RMS said it best himself, something like "If Linux had existed then (mid 1980's) we never would have started working on HURD".

HURD teaches me a few things, yes:

GNU chose a piss poor kernel design that was practically unworkable.

Linux saved the GNU project.

RMS is an arrogant *** that won't make Linux the official GNU kernel, even though almost all work on HURD is stopped, and has been for a few years, and Linux is still the only reliable or credible kernel that works with it.

Being religious and political about "Free Software" scares all businesses away, and immediately loses you 75% +/- of your potential developers instantly.

GPLv2 has worked well for Linux, it instantly made all of the stuff from GNU that does work legally compatible and saved the Linux developers a few years of work, having to reimplement it all themselves, it has forced developers to license their kernel work in such a way that makes proprietary forks almost unthinkable, this is why Linus licensed Linux under GPL, not because he's religious about software.

---

### Post by teddks on 2008-11-02
HURD will start seeing a lot more development once the cancer of proprietary binary blobs spreads farther than it already has into Linux.

Yes, you know those "100% free" things that gNewSense took out? They were **binary blobs**. They had no source code and most of them had no redistribution. They just had a lot of hex gunk with "Hey guyz gpl" at the top.

At the time, microkernels were the "big thing". That's where the whole "Linux is obsolete" thing came from. RMS won't make Linux anything near "official" because Linus is a mercenary who would force his own mother to use non-free software to work on his kernel because "come on guys its better".

This thread is full of reactionary anti-freedom garbage, and is one of the reasons I will be jumping ship to gNewSense as soon as they get cdimage working.

---

### Post by DeadSuperHero on 2008-11-02
> **teddks said:**
> HURD will start seeing a lot more development once the cancer of proprietary binary blobs spreads farther than it already has into Linux.

Yes, you know those "100% free" things that gNewSense took out? They were **binary blobs**. They had no source code and most of them had no redistribution. They just had a lot of hex gunk with "Hey guyz gpl" at the top.

At the time, microkernels were the "big thing". That's where the whole "Linux is obsolete" thing came from. RMS won't make Linux anything near "official" because Linus is a mercenary who would force his own mother to use non-free software to work on his kernel because "come on guys its better".

This thread is full of reactionary anti-freedom garbage, and is one of the reasons I will be jumping ship to gNewSense as soon as they get cdimage working.

+1.

I, for one, see quite a lot of potential in Hurd's L4 builds. I plan on buying up a bunch of FOSS hardware and applying the latest patches, and I plan to use it just for tinkering with HURD. Heck, maybe with the right hardware and patches, something great could come of it.

@Dremora
Ah, the anti-GNU phase. I too went through it. You have to realize that GNU makes up a good portion of most Linux distributions, and it really is about providing END-USER freedoms. Sure, BSD gives the developer more freedoms, but the GPL allows software to be entirely free for everyone You don't necessarily see it at first, but it's most definitely there.
A list of all GNU software:

> 

    * 3DLDF - 3D drawing package
    * ACM - Aerial combat simulation game
    * Abdabi - Service discovery system for DotGNU
    * Aetherspace - Project to produce a multiplayer game
    * Anubis - Processes outgoing mail
    * Archimedes - Software for designing and simulating submicron semiconductor devices
    * Aspell - Spell checker
    * Autoconf - Produces shell scripts which automatically configure source code
    * Autogen - Automated program and text generation
    * Automake - Generates Makefile.in files
    * BPEL2oWFN - translates a web service expressed in BPEL into an oWFN
    * Balsa - GNOME mail client
    * Barcode - Converts text strings to printed bars
    * Bash - Shell of the GNU operating system
    * Bayonne - GNU telephony server
    * Bazaar Version Control - distributed version control
    * Bc - Interactive algebraic language
    * Binutils - Collection of binary utilities
    * Bison - Replacement for the parser generator 'yacc'
    * Calendula - Fund-raising/contact management software for non-profits
    * Cfengine - Maintains configuration of a heterogenous UNIX network
    * Chess - Chess game
    * Common C++ - Highly portable C++ class library
    * Cpio - Archiver that handles various types of cpio and tar archives
    * DJGPP - GCC, G++, and GNU utilities for DOS
    * DMD - Service manager that's a replacement for SysV-init
    * Denemo - Graphical music notation program
    * Dia - GTK-based diagram drawing program
    * Diffutils - Finds differences between and among files
    * Dominion - Multi-player role-playing simulation
    * Double Choco Latte - System for tracking bugs, changes, enhancements, and requests for software
    * EDMA - Modular development environment
    * EPrints - Online information archiving system
    * Ecc - Elliptical curve class library
    * Ed - Line-oriented text editor
    * Electric - CAD electrical circuit design system
    * Emacs - Extensible, real-time editor
    * Epsilon - Strongly-typed omega-order programming language
    * Ffp - Free Film Project
    * Findutils - Tools to find files and to operate on groups of files
    * Forum - Web-based groupware system
    * FreeDink - Free enhancement of the Dink Smallwood game engine
    * Freefont - Free UCS outline fonts
    * GCC - GNU Compiler Collection
    * GCL - Compiler and interpreter for Common Lisp
    * GIFT - Content based image retrieval system
    * GIMP - GNU image manipulation program
    * GLPK - GNU Linear Programming Kit
    * GLUE - GNU Internet groupware project
    * GLib - Core library that forms the basis of GTK+ and GNOME
    * GNAT - A complete Ada95 compilation system
    * GNOWSYS - Hybrid database server with a kernel for semantic computing
    * GNU Alive - Automatic login and keep-alive utility for Internet connections.
    * GNU Classspathx - Unfinished free implementation of the Java extension libraries
    * GNU Enterprise - Unfinished project to develop a complete ERP system
    * GNU Font Editor - Graphical font editor
    * GNU GLOBAL - Source code tag system for C, C++, Java, and Yacc
    * GNU GRUB - GNU GRand Unified Bootloader
    * GNU Gnash - Flash Movie Player
    * GNU Libidn - Internationalized string preparation library
    * GNU MAC Changer - Is a utility to manipulate a MAC address
    * GNU Messenger - Secure messaging system
    * GNU PDF - set of libraries and programs to manage the PDF file format
    * GNU POC - manages smartcard passwords
    * GNU Pascal - Pascal compiler of the GNU Project
    * GNU Pipo - A GNU Bulletion Board System
    * GNU Proxyknife - Validate free proxies for users behind firewalls
    * GNU R - a language for statistical computing and graphics
    * GNU SASL - SASL network authentication library
    * GNU SQL - Database management system
    * GNU Smalltalk - Implementation of the Smalltalk object oriented language
    * GNU Solfege - Eartraining program for GNOME
    * GNU Songanizer - Script to organize a directory containing ogg and mp3 files.
    * GNU TeXmacs - Scientific text editor
    * GNU fdisk - Is a libparted-based partitioning tool
    * GNU ghostscript - Interpreter for the Postscript and PDF graphics languages
    * GNU go - Plays the game of Go
    * GNU libmatheval - Library for evaluating mathematical expressions
    * GNU lightning - Generates assembly language code at run-time
    * GNU robots - Real-time game
    * GNU sauce - Anti-spam server
    * GNU tar - Creates tar archives
    * GNU trueprint - Prints source code to PostScript printers
    * GNUCash - Personal and small business money-management software
    * GNUMP3d - A light-weight audio server
    * GNUMed - Software for a paperless medical practice
    * GNUbik - 3D Rubik's cube game
    * GNUcap - A general purpose circuit simulator
    * GNUjump - SDLjump is a simple game where your goal is to keep jumping to upper falling platforms in order to avoid touching the lower part of the screen.
    * GNUs - Emacs newsreader
    * GNUscape navigator - Web browser that runs under GNU Emacs
    * GNUstep - A graphical, object oriented programming environment
    * GNUtls - A library implementing TLS 1.0 and SSL 3.0 protocols
    * GOOPS - Object-oriented extension to 'guile'
    * GSL - Routines for numerical computing
    * GTK+ - GNU toolkit for X windows development
    * GTS - Functions for 3D surfaces meshed with interconnected triangles
    * GUSS - Hardware simulator for debugging
    * Gcal - Is a program for calculating and printing calendars, and is the GNU implementation of the universally known cal and calendar programs.
    * Gcompris - Educational suite for children from 2 to 10
    * Gcron - Replacement for Vixie cron
    * Gdb - GNU Debugger
    * Gdbm - Replacement for the 'dbm' and 'ndbm' libraries
    * Gengetopt - Generates a C function that parses and validates command line options
    * Gettext - Tools to produce multi-lingual messages
    * Ggradebook - Fully-featured GNU gradebook
    * Gnats - Bug tracking system
    * Gnatsweb - Web interface to the GNU bug management system
    * Gnochive - GUI frontend for multiple archivers
    * Gnome - The GNU desktop
    * Gnome-find - GUI version of the GNU 'find' utility
    * Gnotepad+ - HTML and text editor
    * Gnumeric - Math program intended to replace commercial spreadsheets
    * Gnutrition - Nutrition analysis software
    * Gnuzilla / IceCat - GNU version of popular web browser
    * Goldwater - Middleware component of the DotGNU project
    * Gorm - Graphic Object Relationship Modeler
    * Gperf - Generates a hash function
    * Greg - Software testing framework
    * Grep - Finds lines that match entered patterns
    * Gretl - Software for econometric analysis
    * Gtick - Digital metronome
    * Gtkeyboard - Graphical keyboard
    * Gtypist - Typing tutor program
    * Guile - GNU extensibility library
    * Guile-gnome - Helps Scheme programmers develop visual applications
    * Httptunnel - Creates a data path in HTTP requests
    * Hyperbole - Information and text management program
    * Idutils - Tools for indexing
    * Indent - C source beautifier
    * Inetutils - Collection of common network programs
    * Jacal - Mathematics program
    * Kawa - Scheme and Emacs Lisp on a Java VM
    * Less - Display paginator
    * LibCVS - Provides CVS functionality in library form
    * Libgcrypt - Cryptographic library
    * Libiconv - Converts between character encodings
    * Lilypond - Music typesetter
    * MH-E - Emacs interface to the MH mail system
    * Mailman - Manages discussion lists
    * Mailutils - A set of libraries and programs for handling e-mail messages
    * Melting - Nearest-neighbor compilation of nucleic acid hybridation
    * Metahtml - Programming language for the Web
    * Midnight Commander - Unix file manager
    * Mifluz - Full text inverted index query library
    * Mll2html - Converts a mailing lists file to an HTML file
    * Motti - Multiplayer, networked strategy game
    * Mtools - Lets Unix systems work with DOS files
    * Mule - Multilingual text editor for Emacs
    * Nana - Library for assertion checking and logging in GNU C/C++
    * Nano - Pico clone for *NIX
    * Nautilus - File manager and graphical shell
    * Ncurses - Displays and updates text on text-only terminals
    * Ninpaths - Paths Survey reporting program
    * Ocrad - OCR program based on feature extraction
    * Octave - High-level language for numerical computations
    * Oleo - Lightweight spreadsheet program
    * PCB - Designs printed circuit board layouts
    * PHP Groupware - Groupware suite
    * PIPS - Converts data between formats
    * PSPP - Statistics package
    * Panorama - Framework for 3D graphics production
    * Paperclips - Webserver and dynamic content container
    * Patch - Applies a patch to a file
    * Patchwork - Utility for rapid patch development and submission
    * Paxutils - Tool to manage file archives
    * Plotutils - Plotting and graphics utilities
    * Proto - Tools to find function prototypes
    * Pth - GNU Portable Threads library
    * Ptx - Index generator
    * Qexo - XQuery to Java compiler
    * Quagga - Back-end software for the FSF's Directory of Free Software
    * Queue - Batch processing and local rsh replacement system
    * RCS - Version control and project management software
    * Radius - Remote authentication and accounting system
    * Readline - Lets users edit command lines as they are typed in
    * Recode - Front end to the 'recode' translation library
    * SNACC - ASN.1 to C or C++ compiler
    * SXML - Defines and implements a mark-up language
    * Screen - Runs separate screens on a single terminal
    * Sed - A stream-oriented non-interactive text editor
    * Serveez - Server framework
    * Shared Memory Manager - access all shared memory
    * Sharutils - Creates and helps unpack shell archives
    * Shtool - The GNU portable shell tool
    * SmartEiffel - Eiffel compiler
    * Snug - Project to develop a free version of Java Swing
    * Sovix - PHP-based, semantic website revision system
    * SpeedX - Racing game
    * Termutils - Programs for controlling terminals
    * Texinfo - Produces manuals, ASCII text, and on-line documentation
    * Thales - IRC to MySQL gateway
    * The GNU Objective C Class Library - The GNU Objective C Class Library (libobjects) is a library of general-purpose, non-graphical Objective C objects
    * Time - Reports the user, system, and real time used by a process
    * ToutDoux - Project manager
    * Units - Unit conversion and calculation
    * VCD Imager - Free software (Super) video CD authoring solution
    * Wget - Retrieves files from the Web
    * Which - Prints out full path of execuatbles
    * Window Maker - Window manager for X Window System
    * Xboard - Graphical chessboard
    * Xhippo - Playlist manager
    * Xmorph - Image morphing program
    * Zebra - Implementation of routing protocols
    * a2ps - Any to PostScript filter
    * acct - GNU system accounting utilities
    * adns - Resolver library for C and C++ programs
    * aetherspace - Software to produce alternative energy systems
    * aroundme - Social networking and team interaction software
    * auctex - Integrated environment for editing LaTeX and TeX files
    * avl - Library for balanced binary trees
    * beacon - Simple date and category-driven Web publishing system
    * bool - Utility for matching boolean queries in text
    * ccaudio - Library and software for manipulating audio data
    * ccrtp - RTP stack
    * ccscript - C++ class framework for creating a virtual machine execution system
    * cflow - Charts control flow within source code
    * cgicc - C++ class library for writing CGI applications
    * cim - Compiler for the programming language Simula
    * classpath - Free core class libraries for the Java programming language
    * clisp - ANSI Common Lisp compiler, debugger, and interpreter
    * combine - Extensible file matching and filtering
    * cons - 'Make' replacement
    * coreutils - Collection of basic file, shell and text manipulation utilities
    * cssc - Free clone of SCCS
    * dap - Statistics and graphics package
    * ddd - Graphical front end for command line debuggers
    * ddrescue - Data recovery tool
    * dejaGnu - Framework to test programs
    * diction - Checks text for readability and bad usage
    * dr. geo - Builds geometric figures
    * emms - Emacs multimedia system
    * enscript - Converts ASCII files to PostScript
    * ferret - GNU data modeller
    * fhp - m4 macro for creating Web pages
    * fontutils - Converts between font formats and creates fonts
    * freeipmi - Intelligent platform management system
    * fribidi - Free implementation of the Unicode Bidirectional (BiDi) Algorithm
    * g++ - C++ compiler
    * gama - Geodetic network adjustment program
    * gawk - String manipulation language
    * gcjwebplugin - Browser plugin that executes Java applets
    * gengen - A parameterized-text-generator generator based on a template
    * gforth - Free implementation of the ANS Forth language
    * gfortran - Fortran compiler
    * gleem - Library of 3D widgets
    * gmp - The GNU Multiple Precision Arithmetic Library
    * gnome transcript - SQL database client
    * gnotary - Project to produce a digital notary service
    * gnu-arch - Revision control system
    * gnu-crypto - Project to produce a full set of Java cryptographic tools
    * gnubg - Plays and analyzes backgammon games and matches
    * gnubiff - Mail notification program
    * gnucomm - GNU telecommunications project
    * gnuit - Tools for simple, daily file and system management tasks
    * gnulib - GNU portability library
    * gnumach - Microkernel of the GNU system
    * gnunet - Anonymous peer-to-peer file-sharing
    * gnupg (GPG) - Complete implementation of the OpenPGP Internet standard
    * gnupod - Lets you use an iPod under GNU/Linux
    * gnuradio - Software to create digital radio signals
    * gnuschool - Is a web application for educators, students, and school administrators.
    * gnushogi - Japanese version of chess
    * gnuskies - Project to create a free version of the xephem program
    * gnusound - Multitrack sound editor for Gnome
    * gnusysutils - Planned group of utilities for system administrators
    * gpaint - GNOME paint program
    * gprolog - Prolog compiler
    * groff - Document formatting system
    * gss - Implementation of the Generic Security Service API
    * guile-dbi - Guile database abstraction layer
    * guile-gtk - Guile language bindings for Gtk+ version 1.2
    * gurgle - Formerly the GNU Report Generator
    * gv - Frontend for ghostscript
    * gvpe - Secure vpn network among multiple nodes over an untrusted network
    * gzip - Compresses and decompresses files
    * hOpla - Link between XML files and SQL databases
    * halifax - Client applications suite for fax applications
    * hello - GNU version of "Hello, world!"
    * hp2xx - Reads and converts HP-GL files to various formats
    * hurd - Project GNU's replacement for the Unix kernel
    * intlfonts - Fonts for all characters Emacs 20 can handle
    * java2html - Translates Java files to HTML
    * jel - Compiler for simple expressions into Java byte code
    * jwhois - Internet whois client
    * libQGLViewer - Library for development of 3D applications
    * libc - Library for use with GNU/Hurd and GNU/Linux
    * libcdio - Encapsulates CD-ROM reading and control
    * libextractor - Extracts metadata information from files
    * libmicrohttpd - GNU library
    * libopts - AutoOpts option parser library that supports stand alone config files
    * libsigsegv - Library for handling page faults
    * libtool - Generic library support script
    * libxmi - Library for rasterizing 2-D vector graphics
    * liquidwar6 - Liquid War 6 is a unique multiplayer wargame.
    * lsh - Free implementation of the SSH protocol
    * m4 - Macro processor
    * make - Generates executables and other non-source programs
    * marst - Algol to C translator
    * maverik - Virtual reality micro kernel
    * mcron - Vixie cron replacement
    * mcsim - Simulation software for designing, analyzing and calibrating mathematical models
    * mdk - Emulator and development environment for Knuth's MIX computer
    * miscfiles - Collection of various files
    * mit-scheme - MIT/GNU Scheme programming language
    * moe - A powerful and user-friendly text editor
    * muse - Emacs mode for publishing in various modes
    * octal - Free digital sound workstation for Unix-like systems
    * orgadoc - Helps organize documentation
    * osip - Library supporting the Session Initiation Protocol
    * p2c - Translates Pascal programs into C
    * parted - Manipulates disk partitions
    * phantom security - Home security system
    * phantom_home - Home automation system
    * phpgrabcomics - Retrieves and saves comics from the Web
    * polyxmass - Mass spectrometric framework for simulation and analysis of mass spectrometric data of (bio-)polymers
    * protoize - Creates or removes prototypes from C code
    * rottlog - Replacement for Red Hat's 'logrotate.'
    * sather - Object-oriented language
    * shishi - Free implementation of the Kerberos 5 network security system
    * slib - Portable scheme library
    * sourceinstaller - Graphical tool for source package configuration, installation, tracking and removal
    * spacechart - Displays the stars in space in 3D
    * speex - Speech compression format
    * spell - Spell checker
    * src-highlite - Turns source code into a file with syntax highlighting
    * stow - Manages installation process
    * superopt - Finds the shortest instruction sequence for a given function
    * swbis - Extensions to the POSIX packaging standard
    * talkfilters - Translates English text into dialects
    * tramp - Remote file editing software
    * unrtf - Converts from RTF to other formats
    * userv - Security boundary tool
    * uucp - File copying program
    * wdiff - Front end to GNU 'diff'
    * womb - Repository for homeless code
    * xaos - Real-time fractal zoomer
    * xlogmaster - Monitors logfiles and devices
    * xnee - Records, distributes, and replays X11 protocol data



---

### Post by hanzomon4 on 2008-11-02
I think Hurd is cool.... :(

---

### Post by DeadSuperHero on 2008-11-02
> **hanzomon4 said:**
> I think Hurd is cool.... :(

You and me both, buddy. You and me both. :KS

---

### Post by toupeiro on 2008-11-02
\\:d/

---

### Post by revanb on 2008-11-07
Linux as most people know it is actually a combination of Gnu applications and the Linux kernel, for those that don't know. This means when you use GNU/Linux (which is the correct name although I also just use Linux otherwise it just sounds stupid imo.) and you see your Gnome desktop and edit your photos with the GIMP then your basically using Gnu software. 

I think the FSF has done well, but personally I dont really see the point in continuing with the HURD kernel, since it has been a long road to get companies to accept and support Linux ito drivers and they are starting to deliver. 

Linux works very well as it is and I think it should be developed from here forward.


I don't want to go into too much of the politics, but if I pay good money for, for example, my new ATI top-of-the-range graphics card, then I don't see any reason for not being able to use a quality driver that they provide. Emphasis on quality since for me the open-source drivers for my ATI mobility radeon are better than the one ATI provides. That said companies like ATI should not be let of the hook so that they can just expect the open source community to support their hardware for free. I expect them to provide a quality driver compatible with current linux applications, so that open-source developers can focus on developing actual applications instead of trying to play catchup each time new hardware is released.

Linux is not a toy anymore and I won't support any hardware manufacturers that don't provide support under Linux.

...I prefer using Linux, not because I'm free to change the code, but because I think it is a quality operating system. It helps that I don't have to pay money for it.

---

### Post by techmarks on 2008-11-07
Gnu/Hurd is the riddle, wrapped in a mystery, inside an enigma.

---

### Post by Foster Grant on 2008-11-07
GNU/Hurd's all but dead. Good philosophy, bad execution. It happens. It  should have been abandoned when it became clear that ...


[LIST=1]
[*]it can't be fixed in a realistic amount of time, and
[*]the open-source software community had already developed a product that did the same thing and achieved dominance.
[/LIST]

Why hasn't it died out completely? RMS and a few other idealists are stubborn.

Honestly, y'all ... the "more GNU than thou" nonsense gets old. :-({|=

@teddks: Leaving us? OK. To each his own.):P

---

### Post by teddks on 2008-11-07
> **Foster Grant said:**
> GNU/Hurd's all but dead. Good philosophy, bad execution. It happens. It  should have been abandoned when it became clear that ...


[LIST=1]
[*]it can't be fixed in a realistic amount of time, and
[*]the open-source software community had already developed a product that did the same thing and achieved dominance.
[/LIST]

Why hasn't it died out completely? RMS and a few other idealists are stubborn.

Honestly, y'all ... the "more GNU than thou" nonsense gets old. :-({|=

@teddks: Leaving us? OK. To each his own.):P

Linux is not the same thing as HURD, and it hasn't anywhere near achieved dominance. HURD hasn't died out because a lot of people are interested in it and nobody is willing to say "nobody is ever allowed to work on HURD because Linus won, guyz." In addition, **Linux is tainted with non-free code and until that trend is reversed, there's no reason to put all bets on it.**

---

### Post by Delever on 2008-11-07
> **Foster Grant said:**
> GNU/Hurd's all but dead.

Maaan, Linux is SO DEAD, nobody uses it.

-------------
Windows User

:)

---

### Post by hanzomon4 on 2008-11-07
it's rotting....

---

### Post by init1 on 2008-11-07
Yeah, I've used Debian/Hurd, but there's very little that can be done with it and it hasn't been updated since 2001 or so.

---

### Post by DeadSuperHero on 2008-11-08
> **init1 said:**
> Yeah, I've used Debian/Hurd, but there's very little that can be done with it and it hasn't been updated since 2001 or so.

WRONG. Actually, there's code out there that dates back to 2006/2007.

---

### Post by bigbrovar on 2008-11-23
> **howlingmadhowie said:**
> they have been removed for very good reason. the aim of the free software movement was to create a complete fully-free operating system. when linus torvalds contributed his kernel to the project there was very little desire to complete the hurd. however, the linux kernel is still under gpl2, and the binary blobs in the kernel code are of dubious legality. 

a distribution such as gnewsense fulfills a number of purposes. To start with, it represents the current culmination of stallman's ideals. it is a totally free product. you can theoretically know everything the computer is doing. you can read the sourcecode for every piece of software on the computer. you can help yourself and also be helped by others. you can share everything with your friends without any risk of legal action being taken against you. 

you may not value these things. some people do value them very much. without these people there would be no ubuntu, there would be no open internet protocols, there would be no wikipedia or similar. these people are pushing for highest possible amount of freedom. their work is far from pointless.

this is on of the most thoughtful post i have seen in this path for quite a while.

---

### Post by SunnyRabbiera on 2008-11-23
But the thing is that the binary blobs are a necessary evil in a world that needs hardware compatibility.

---

### Post by YaroMan86 on 2008-11-23
You want my opinion?

I think the whole "Everything must be free" view, while noble, is a tad overzealous, and I can only really attribute it to Stallmanists who, as I'm sure most hackers would agree, don't really give Linux a good name.

It is only Stallmanists who truly want Linux to be called GNU/Linux despite the fact that, to me, that's nonsense, especially since I'm seeing more and more BSD tools in your average Linux distribution and less and less GNU tools. Plus I don't think the toolchain is what defines an operating system.

That, however is a debate that I cannot win, and I'll only mention it this once in this thread.

My problem with gNewSense is that it does follow the ludicrously-free philosophy, I'm working on game development in Linux, cross platofrm with Windows and Mac OS X. If I were to try that in gNewSense, I would fail dismally due to four important details RMS never addresses. Ever. Because it is something he can't solve in his limited wisdom.

1. I am developing a powerful rendering engine that has fully accelerated 3D graphics as one of its goals.
2. Most people use ATI or nVidia chipsets for their graphics acceleration.
3. The open source drivers for nVidia and ATI chipsets are crappy and lack acceleration features.
4. gNewSense doesn't support the proprietary drivers, which work much better than their open source counterparts.

I'm not about to tell people anticipating my technology "Oh, thanks to some extremely political hippie the renderer will not work except on Intel chipsets, screw you." Please.

So yeah. If you're a Stallmanist who just just plans to make typical GNU-style hacker tools for your programming experience, gNewSense is for you. Most anyone outside Stallmanist circles, however, who plans to do much more programming for that, I'll stick with a Linux distribution that isn't afraid that binary blobs "might" be questionable, despite no one outside Stallmanism caring.

The same goes for Gnash. It still doesn't cut it. And I'm not about to sacrifice my enjoyable web experience just so I can say "Free Software" in all-caps like RMS.

As for Hurd? I doubt it'll be very popular in the unlikely event it is ever finished. Likely to be obsolete the very moment of its release thanks to Linux and BSD actually... I don't know... finishing and improving?

---

### Post by bigbrovar on 2008-11-23
> SunnyRabbiera  	
Re: GNU/Hurd when it's finally ready think it'll be as widly used as GNU/Linux
But the thing is that the binary blobs are a necessary evil in a world that needs hardware compatibility. 

yeah if we are looking for a short term solution but on the long run they create more problems than they solve. take for example . must of the problems that face the linux desktops are very related to binary -closed sourced program. look at adobe flash,Nvidia,broadcom, etc  its legendary the amount of problems the linux desktop users face with flash. especially when viewing videos.. and Nvidia cards are a real pain. especially the 8 series cards. i never experienced X failing on me through out the time i used a laptop with an intel card. till i got a nvidia card laptop. the driver that came with ubuntu was old and dated. and it wasnt easy getting the latest driver from nvidia. even with envy. bad things still happens whenever i do a kernel update. u can go to the nvidia linux boards you would see lots of pple have problems with the card performance and stability wise... i think the issue with broadcom speaks volume so i wouldnt go there. this is why i decided to at least start by using hardware that support open source drivers. like intel. yeah it may not be the best when it comes to performance but i have my stability. and if there is a problem. i know i can take it to the community and it would be resolved easily. this are the essentials of free software. it allows collaboration and there is documentation. that is why i think its use should be encouraged as much as practicable.

---

### Post by DoctorMO on 2008-11-23
I give my respect and thanks to anyone who has helped me, help others. I owe my capabilities to all those who work, fight or play in the field of FOSS development.

But I will not see belligerent, disrespectful, non-developers attack those who they have gained from without cost. Especially when they talk such rubbish.

I think users who like to cause controversy by making a mountain out of an ant hill are the people that give Ubuntu and FOSS a bad name.

Anyone who is scared of idealism in others; may harbour far too much guilt. It's not about the subject they're upset with, but the idea that someone might possibly hold themselves to higher ideals. It's not that others think of themselves better that bothers them. It's that they think the ideal carries weight and feel themselves guilty for not living up to it.

Most hatred and the worst angers are wrought from and against the same soul.

---

### Post by YaroMan86 on 2008-11-23
So do I, and I'm not ingrateful.

I'm far from a non-developer. I've been developing eleven years.

Agreed. Tell those people to cut it out. Name me a single NON FSF server on the Internet running Linux that isn't using binary blobs, please. Businesses don't want to fuss over the politics of free software, they want a Linux system that works no matter the cost. They won't get that from gNewSense, they'll get it from Debian or Red Hat or any manner of Linux system that permits binary blobs. The ones giving Linux and FOSS a bad name are the ones being extremely noisy and trying to throw their politics in the face of those who don't care about 100% free software as much.

I don't fear the idealism of the FSF or the GPL. Hell, I *prefer* free software, I just won't go out of my way to the point of even disabling functionality in my system for it. It's wonderful, yes, but I prefer to use my computer, not make an idealist political statement about the software I use. Leave that to Richard Stallman, who I respect a lot for making the GNU tools. But I only give him credit for the GNU tools. NOT Linux. That belongs squarely on Linus Torvalds and developers who actually directly contribute to Linux. RMS is not one of them. He's GNU or nothing. Since the only thing Linux actually has to do with GNU exclusively is the license, I think that's more than fair.

I don't hate Richard Stallman, just his politics. It's actually more harmful to freedom of choice in software than you think: The overly-free philosophy that Stallmanists throw at non-Stallmanists in an extremely annoying holier-than-thou fashion is centered around "Choice as long as it is free software." I would much rather have "Choice, period."

---

### Post by bigbrovar on 2008-11-23
could not have said it better

---

### Post by DoctorMO on 2008-11-23
> I don't hate Richard Stallman, just his politics. It's actually more harmful to freedom of choice in software than you think: The overly-free philosophy that Stallmanists throw at non-Stallmanists in an extremely annoying holier-than-thou fashion is centered around "Choice as long as it is free software." I would much rather have "Choice, period."

You _hate_ his politics? I mean granted his attitude has a lot to be desired. But his politics fall mainly along the lines of "It'll be less painful in the long run to not bother with closed source" and the other point that causes anger, is the very idea that a person could appeal to a persons social elements, rather than to some selfish, self prophetic practicalism.

He's just point out that we _need_ each other as a community and society to not become complacent in demanding what we know to be bad in the long run.

Why is it that we have become so cynical of social movements? OK so the idealists may never get there, and it may be an impossible thing to ask for. But I respect peopel who stand by their principles, even if I don't agree with them.

---

### Post by YaroMan86 on 2008-11-23
> **DoctorMO said:**
> You _hate_ his politics? I mean granted his attitude has a lot to be desired. But his politics fall mainly along the lines of "It'll be less painful in the long run to not bother with closed source" and the other point that causes anger, is the very idea that a person could appeal to a persons social elements, rather than to some selfish, self prophetic practicalism.

Uh... RMS is NEVER that passive. Pay attention to his website or his speeches some day. Pay attention to his followers. It's not "Oh, it'll be better if we use free software in the long run." it is "Everyone MUST use free software or they're doing something very wrong." Don't let his eloquence fool you, that's what it all boils down to. He loves condemning even harmless companies purely because they are proprietary. If I were to form my own software company, and announce we're releasing proprietary software, even for a purely proprietary operating system, you're more likely to see RMS calling me an evil Satan-spawn (In friendlier terms.) than a friendly company.

> **DoctorMO said:**
> He's just point out that we _need_ each other as a community and society to not become complacent in demanding what we know to be bad in the long run.

I agree, community is *very* important. Part of the reason why Linux makes for a better system than Windows, because it's built by a community. However, I disagree that the community needs to tell me that proprietary software is bad. It's not a requirement for Linux to be good for me, personally, to be informed, in friendly and not-so-friendly terms, that proprietary software is bad.

> **DoctorMO said:**
> Why is it that we have become so cynical of social movements? OK so the idealists may never get there, and it may be an impossible thing to ask for. But I respect peopel who stand by their principles, even if I don't agree with them.

Again, I'm not against the Free Software movement, I'm just not the sort of FOSSie who thinks RMS' way is the only correct way. That's the problem with Stallmanists. They don't look at, say, proprietary nVidia drivers on someone's computer and say "That's okay, you're running a great system." They say "Get rid of that driver, it isn't free, it's going to rid you of your freedom.

And you're overlooking one small thing I've pointed out. If I were to follow that ideal that zealously, which I never will, I'd basically have to tell my expectant players to piss off, and also basically throw away some functionality I actually need.

Idealists like to preach, but their ideals frequently border on the impractical. And computers and operating systems are meant to be practical.

---

### Post by DoctorMO on 2008-11-23
> Don't let his eloquence fool you, that's what it all boils down to.

I don't like to let his attitude get in the way of the ideas. I live in Boston, I've met Stallman and I get on quite well with the guys at the FSF. The guys at the FSF know what a pain in the backside Stallman is, relentless and constantly trying to find a way of framing things into a fight. Belligerent is a word I'd use.

I wouldn't use that approach. It's not as productive to run screaming at those you oppose ideologically without any means to fight them and no chance to reason with them. Well not an argument you want to win anyway.

> Idealists like to preach, but their ideals frequently border on the impractical. And computers and operating systems are meant to be practical.

Enable the ideals through the use of the unideal. I use the nvidia driver, I don't like it and I support the free software replacement. But I'm not going to cut off my path to spite my position. We use these propritory elements because we need to and we understand the world isn't a perfect or ideal place.

All I want is for people to bare in mind what that ideal is. Why we think it's important from long term practical and social stand points (both are important in very different ways). Continue using what you need to get your work done, but help us work together to make the situation better from it.

The concern is that using closed source enabled complacency. The amount of work on the free nv driver is pitiful compared to how much it would have gotten if the proprietary driver hadn't existed. But again things like compiz would have been delayed by 3 or more years waiting for all this hardware support to catch up for other developers.

Eventually tho these closed drivers should be dropped because they are impractical. Even Torvald's when he's not faking ethical debates in his blog has admited how much pain comes from them. It isn't Stallman that prevents binary drivers, it's Torvald's. That should say an awful lot about how impractical they are.

---

### Post by YaroMan86 on 2008-11-23
I'll call them impractical when they don't work. Since they work, "impractical" is not the word I would use.

Sure, I can see how it would cause complacency. But I'm not about to blame nVidia for lazy idiots who don't develop the nv driver. Hardly nVidia's fault. Would be nice if nVidia opened up their drivers, but I'm not about to ask them to, and I'm not about to boycott them because of it like the typical Stallmanist would.

In a way, as much as I respect him, I don't think I'd care to meet Richard Stallman. As you say, there's reports from people in the FSF and the GNU Project who prefer to give him a wide berth. However, FSF/GNU members are not always Stallmanists.

Stallmanists are the guys who honestly do write open letters to and boycott companies that write a single line of proprietary code, and then start screaming and making a lot of irritating noise about how proprietary software is Evil (It's bad, sure, but I wouldn't call it evil.) and that me and anyone who thinks like I do are idiots for using proprietary ANYTHING in my Linux distribution.

There's only two proprietary things I use on Linux, myself, simply because their open counterparts are not far enough and aren't making much headway: The nvidia driver and Flash. A Stallmanist would insist that I use Gnash and nv to the point of really getting me extremely pissed off.

Not all FOSSies are like that, I am the type of FOSSie who really wants to help the movement, but I also recognize that I have to use my computer to its fullest, or would like to, and sometimes must use proprietary things.

I would LOVE to use an open flash player or video driver, but they prove impractical as of now. 

I'd call binary blobs impractical when they prove to be WORSE than their free alternatives. That is most proprietary software one could find for Linux. I wouldn't give up the GIMP for Photoshop even if it were free.

Stallmanists are just as bad for Linux's image as rabidly anti-Microsoft trolls who go flaiming Windows community forums.

---

### Post by Paqman on 2008-11-23
I don't really see the point of Hurd, but I can see why the FSF keep plodding along with it. 

At the end of the day they're not hurting anyone, and some of their code could be useful.

---

### Post by YaroMan86 on 2008-11-23
> **Paqman said:**
> I don't really see the point of Hurd, but I can see why the FSF keep plodding along with it. 

At the end of the day they're not hurting anyone, and some of their code could be useful.

That is true. But I'm still not sure I see Hurd going very far if/when it releases. I'm sure there's probably some dandy code in there. But unfortunately for Hurd there are at least two other open source kernels that are better that are complete and in use: The BSD and Linux kernels.

---

### Post by toupeiro on 2008-11-23
One of my personal theories on just about anything in life is that if you take an extremest approach at enforcing something like an ideology on the masses, it will be resisted, even if that ideology is freedom.  Freedom is a point of view.  If I want proprietary codecs, I should be free to choose them.  I don't subscribe to Stallmans vision of a "free" world.  I think he has done a lot of good, and I have a lot of respect for his contributions, but like any person of his influence and capabilities that takes extreme positions on things, needs to be on somewhat of a leash or he can go too far.

I think GNU/Hurd won't ever see the global absorption as Linux because of Stallmans tact and influence over the OSes future.

---

### Post by eragon100 on 2008-11-23
> **YaroMan86 said:**
> 

My problem with gNewSense is that it does follow the ludicrously-free philosophy, I'm working on game development in Linux, cross platofrm with Windows and Mac OS X. If I were to try that in gNewSense, I would fail dismally due to four important details RMS never addresses. Ever. Because it is something he can't solve in his limited wisdom.

1. I am developing a powerful rendering engine that has fully accelerated 3D graphics as one of its goals.
2. Most people use ATI or nVidia chipsets for their graphics acceleration.
3. The open source drivers for nVidia and ATI chipsets are crappy and lack acceleration features.
4. gNewSense doesn't support the proprietary drivers, which work much better than their open source counterparts.

I'm not about to tell people anticipating my technology "Oh, thanks to some extremely political hippie the renderer will not work except on Intel chipsets, screw you." Please.



It is even worse: GNewSence doesn't support 3d at all, not even with the open-source ati/intel drivers. They are very proud (!) to be the first distribution to remove GLX, because they were a few lines of code in it, somewhere around 12 years old, that where not under the GPL but were covered by another open-source license.

They really are crazy.

source (from the FAQ):

3. Aren't Ubuntu/Debian already free?

Neither Debian nor Ubuntu are fully free. Ubuntu installs non-free software by default. Debian provides non-free software through its repositories and includes non-free kernel drivers. We're also the first distribution to remove GLX^, which Debian has ignored for years. 

See 1 2 

^GLX is needed for hardware-accelerated 3d graphics in X. Recompiling X, and removing OpenGL, are required due to the non-free SGI Free B license.

---

### Post by oedipuss on 2008-11-23
> **toupeiro said:**
> One of my personal theories on just about anything in life is that if you take an extremest approach at enforcing something like an ideology on the masses, it will be resisted, even if that ideology is freedom.  Freedom is a point of view.  If I want proprietary codecs, I should be free to choose them.  I don't subscribe to Stallmans vision of a "free" world.  I think he has done a lot of good, and I have a lot of respect for his contributions, but like any person of his influence and capabilities that takes extreme positions on things, needs to be on somewhat of a leash or he can go too far.

I think GNU/Hurd won't ever see the global absorption as Linux because of Stallmans tact and influence over the OSes future.

However, the FSF is already a response resisting the dominant more or less extremist point of view. I think it's meant to be extremes on both sides, with the user or the non-idealist being in the middle. A mediocre approach to free software wouldn't go anywhere, if the extreme view hadn't made way for it.

---

### Post by Phreaker on 2008-11-23
I'm surprised that someone remembers about hurd

---

### Post by DoctorMO on 2008-11-23
> But I'm not about to blame nVidia for lazy idiots who don't develop the nv driver. Hardly nVidia's fault. Would be nice if nVidia opened up their drivers, but I'm not about to ask them to, and I'm not about to boycott them because of it like the typical Stallmanist would.

I'm not going to 'blame' nVidia, But I will call them out as serving their users badly. Their drivers _are_ insecure and are less practical just from historical incidence. Now serving users badly may seem a bit harsh, but that's because a great deal of the criticism that is due of nVidia instead goes to Ubuntu and Linux in general. We are powerless to fix nVidia drivers and yet when they fail, Ubuntu gets to be flamed.

nVidia gives FOSS a bad name.

Flash is the same, it's nice that Adobe is now providing 64bit support but we'd do better to be able to include it in Ubuntu by default and provide much better support for fixing problems and integration.

It's easy to praise any support at all. And praise is due, but limited in extent because of the amount of trouble it causes and the amount of developer time we waste trying to fix problems with these inaccessible pieces.

I notice that you keep on using terms such as 'Stallmanists', odd that.

---

### Post by toupeiro on 2008-11-23
> **oedipuss said:**
> However, the FSF is already a response resisting the dominant more or less extremist point of view. I think it's meant to be extremes on both sides, with the user or the non-idealist being in the middle. A mediocre approach to free software wouldn't go anywhere, if the extreme view hadn't made way for it.

Fair enough..  but .. its FSF is not exactly what I would consider the non-idealist.  And like I said, I give full credit where credit is due to RMS and the FSF, but there is approaching an idea like free software unobtrusively, promoting diversity by allowing proprietary code where free code and software has not caught up efficiency or performance or security wise, then substituting it out once it has. Then, there is strong-arming your ideas to the point you will sacrifice efficiency, productivity and diversity in order to achieve your goals because of their viewpoints on how software should be.  Thats just not for me.  Another way I try to explain this is that FSF and Microsoft are heads and tails of a quarter. In the real world, pennies nickels and dimes, denominations relative to software as FreeB,MS-PL,  CDDL or what have you, can give me equal value to that quarter.  The way FSF and Microsoft choose to approach these ideas are more like: exact change only, or no sale.  They want that quarter with their head or tail on it, and won't recognize anything else.  I'm aware MS-PL is an "open" Microsoft license, but is it one FSF would recognize?  Or, is it a good example of two entities playing their own version of "exact change only" against eachother with the same damn quarter?

---

### Post by YaroMan86 on 2008-11-23
> **eragon100 said:**
> It is even worse: GNewSence doesn't support 3d at all, not even with the open-source ati/intel drivers. They are very proud (!) to be the first distribution to remove GLX, because they were a few lines of code in it, somewhere around 12 years old, that where not under the GPL but were covered by another open-source license.

You can't be serious. because OpenGL/GLX had parts of it in an open source license that didn't agree with Richard Stallman's personal standard for "open" an entire distribution is reduced to being a mediocre slow-2D system? Now I DEFINITELY won't be developing on gNewSense.

---

### Post by eragon100 on 2008-11-23
> **YaroMan86 said:**
> You can't be serious. because OpenGL/GLX had parts of it in an open source license that didn't agree with Richard Stallman's personal standard for "open" an entire distribution is reduced to being a mediocre slow-2D system? Now I DEFINITELY won't be developing on gNewSense.

I really am serious, here is the link to the statement on their official site: [http://www.gnewsense.org/index.php?n=FAQ.FAQ#toc3](http://www.gnewsense.org/index.php?n=FAQ.FAQ#toc3)

Question number 3, it should be the upper one on the screen if you click on that link :wink:

---

### Post by cb951303 on 2008-11-23
> **eragon100 said:**
> I really am serious, here is the link to the statement on their official site: [http://www.gnewsense.org/index.php?n=FAQ.FAQ#toc3](http://www.gnewsense.org/index.php?n=FAQ.FAQ#toc3)

Question number 3, it should be the upper one on the screen if you click on that link :wink:

so it's basically gNewSense has no 3d support because glx is open source :D ??

---

### Post by eragon100 on 2008-11-23
> **cb951303 said:**
> so it's basically gNewSense has no 3d support because glx is open source :D ??

Exactly, because it's not RMS's license, but an open-source license from SGI. And offcourse, if RMS didn't make it, it's evil! :rolleyes:

EDIT: Not that it matters much, because that moron RMS is also against violent games, anyway: 07 December 2005 (People who play violent video games) 

"People who play violent video games become desensitized to violence, and this can be measured by their brain waves. 

There was a time when a copy of Doom was installed on a computer at MIT. Many of the students in the group that my office was in played the game, and needing a distraction, I played it too. But I discovered that I did not want to play it the same way they did. I treated the game as a challenge, and worked out how to pass each level with full health and ammunition without cheating. They seemed to simply like moving around shooting, using the cheat command as necessary. The gory corpses of enemies disgusted me, so I tuned them out in my mind, but the students seemed to revel in the gore of these imaginary deaths. Eventually I concluded that playing the game was having a deleterious effect on my mind, and stopped. 

Ever since then I have found myself uncomfortable with video games that seem to revel in imaginary death. I do not favor censorship of video games, any more than I do censorship of movies. But I would not have those video games or movies in my home--whether or not there were children in it. Children should see lovemaking, not violence."

Well, at least he doesn't want to ban them, and I really don't care about his opinion as long as I can keep playing. Still, this doesn't help to make him any more popular with me. I now hate him even more.

---

### Post by dmn_clown on 2008-11-23
> **eragon100 said:**
> Exactly, because it's not RMS's license, but an open-source license from SGI. And offcourse, if RMS didn't make it, it's evil! :rolleyes:

The Free Software B (v1.1) license in question required you to contact SGI whenever you noticed a license infraction.  If you didn't you were in violation of the license.  That is a bad license.  SGI recently removed that language from the license and released GLX under the free terms, so your argument is moot.

The sad part about this is that there are real issues with the FSF and GNU (as organizations) that aren't being met.  Both organizations are not run in a transparent, democratic manner and both are not open to outsiders.  GNU membership is by invite only, the FSF membership that you buy doesn't give you a say in how the organization is run, in effect keeping a class structure.  Both organizations miss the point that we should be improving free software rather than proselytizing to Apple's low level employees ;)

That is what is nice about Software in the Public Interest [http://www.spi-inc.org/](http://www.spi-inc.org/) 

No muss, no fuss, just create the better software and get on with life.

---

### Post by teddks on 2008-11-23
A lot of people seem to be sounding off in this thread without a full idea of what's been going on.

[list]
[*] "I'm not going to blame anyone for not developing nv": If I were you, I'd blame nvidia. Nvidia forced the **code obfuscation** of most of the essential parts of nv, so now, while the "source code" is there and it can be redistributed, it is effectively non-free.
[*] "I have a right to choose proprietary codecs if I want to": Actually, Stallman completely agrees with you. The codec issue **is a patent issue, not a free software issue.** You should NOT use things like mp3 because it is patented and free software developers or users could be sued for use of the patented product without a license. You SHOULD use things like Ogg because that is patent-free and has no chilling effects attached.
[*]"The GNU toolkit is great, but it isn't the whole system and I even use zsh now so why should I say GNU/Linux": This misses the point entirely. The reason why you should say GNU(/Linux) is because GNU is a **collective term** for the mostly-copylefted Free Software operating system. The GNU doesn't refer to GNU Coreutils/GNU Binutils/GNU EMACS/<other thousands of GNU Project sponsored packages>, it refers to that collective. Saying GNU/Linux is misleading, as Linux is not a collective term, but a specific program. The GNU operating system was always intended to have non-GNU Project-developed parts; see Stallman's essay in Open Sources (I believe, it's also in EMACS) for proof and expansion.
[*]"gNewSense took out OpenGLX because it wasn't under the GPL": This is an absurd and false claim. Parts of OpenGLX were licensed under **non-free terms, as explained in a previous post**. SGI modified its license to be fully free, and now it's coming back. Notice also that it was Theo de Raadt of OpenBSD who originally pointed out the non-freedom.
[*]"Not that his philosophies matter, he's against violent video games!": Look up "ad hominem" and while you're at it, "red herring".
[*]"I hate <RMS/``Stallmanists''(I have never heard that term before)/Free-software advocates>! They want to take my drivers!": They want your drivers to start being debugged by people outside of the Citadel of <ATI/Nvidia/Wherever>. They want them to not be backdoored by the NSA. They also are the only reason why you have any sort of GNU/Linux system. Linux would not have survived without the GPL. That isn't what Stallman or a ``Stallmanist'' said, that's what **Torvalds** says.
[/list]

---

### Post by DeadSuperHero on 2008-11-23
In any case, OpenGL has been put under a much more permissive license, and will most likely go back into gNewSense.

---

### Post by cb951303 on 2008-11-23
> **dmn_clown said:**
> The Free Software B (v1.1) license in question required you to contact SGI whenever you noticed a license infraction.  If you didn't you were in violation of the license.  That is a bad license.  SGI recently removed that language from the license and released GLX under the free terms, so your argument is moot.


does the license permit modification of the source code without notifying SGI? if so in my opinion that's all that matters.

---

### Post by Jengajam2 on 2008-11-23
I have hears about it on and off, but just one question: How usable is Debian/Hurd as far as installation and programs?

---

### Post by klange on 2008-11-23
"Due to the **non-free** SGI **Free** B **License**"

[FONT="monospace"]DOES NOT COMPUTE[/FONT]

And if this is the mindset of Hurd developers, then no, I don't think it will be widespread at all.

---

### Post by igknighted on 2008-11-23
> **DoctorMO said:**
> I don't like to let his attitude get in the way of the ideas. I live in Boston, I've met Stallman and I get on quite well with the guys at the FSF. The guys at the FSF know what a pain in the backside Stallman is, relentless and constantly trying to find a way of framing things into a fight. Belligerent is a word I'd use.

I wouldn't use that approach. It's not as productive to run screaming at those you oppose ideologically without any means to fight them and no chance to reason with them. Well not an argument you want to win anyway.



Enable the ideals through the use of the unideal. I use the nvidia driver, I don't like it and I support the free software replacement. But I'm not going to cut off my path to spite my position. We use these propritory elements because we need to and we understand the world isn't a perfect or ideal place.

All I want is for people to bare in mind what that ideal is. Why we think it's important from long term practical and social stand points (both are important in very different ways). Continue using what you need to get your work done, but help us work together to make the situation better from it.

The concern is that using closed source enabled complacency. The amount of work on the free nv driver is pitiful compared to how much it would have gotten if the proprietary driver hadn't existed. But again things like compiz would have been delayed by 3 or more years waiting for all this hardware support to catch up for other developers.

Eventually tho these closed drivers should be dropped because they are impractical. Even Torvald's when he's not faking ethical debates in his blog has admited how much pain comes from them. It isn't Stallman that prevents binary drivers, it's Torvald's. That should say an awful lot about how impractical they are.

People really need to chill out and listen to Dr. Mo.

I don't think even the FSF or Stallman really think that gnewsense is the distro all linux users should be using.  It's a prototype, or proof of concept.  See where all the holes are? That's where developers should be working to fill the gap.  It illustrates what is left to be done to achieve the goal of a totally usable, free OS.

I think we need that, because it is easy to be attracted to a project that glosses up the rough edges like Ubuntu.  But just because Ubuntu makes a usable desktop, does that mean that the goal is achieved?  I don't think so.  It may be the best there is today, but in the long run there is much to be desired.  So we really need both extremes.  One (Ubuntu) to draw people into the fold and show that there are options, and gnewsense to remind people that work isn't done.  That there are holes in free software that developers should work on.

---

### Post by eragon100 on 2008-11-23
> **teddks said:**
> A lot of people seem to be sounding off in this thread without a full idea of what's been going on.

[*]"I hate <RMS/``Stallmanists''(I have never heard that term before)/Free-software advocates>! They want to take my drivers!": They want your drivers to start being debugged by people outside of the Citadel of <ATI/Nvidia/Wherever>. They want them to not be backdoored by the NSA. They also are the only reason why you have any sort of GNU/Linux system. Linux would not have survived without the GPL. That isn't what Stallman or a ``Stallmanist'' said, that's what **Torvalds** says.


Nvidia can't open their code, there is third-party IP in there, they would get sued (physx is an example, right?) They also can't remove it, because that would (severely) decrease game/other 3d performance.

And whatever the reason, if RMS gets the nvidia binary driver forbidden in court, and nvidia can't/won't open up their driver, that would prevent me from using the drivers, right? And sorry, but no matter how much I
 hate windows (and not because it's closed-source, but simply, and only, because it doesn't work well), I will dump linux and switch back if I can't play a game / use google earth / have desktop effects on linux. PERIOD.

Reason: I Don't Care. I payed 830 euros for this computer, so I want it to **work**. Open or closed.

---

### Post by happysmileman on 2008-11-23
I hear Hurd will be awesome when it's finally released, apparently Duke Nukem Forever will run natively on it.

---

### Post by teddks on 2008-11-23
That's completely nonsensical to the snippet you've quoted. Why did you do that?

> **eragon100 said:**
> Nvidia can't open their code, there is third-party IP in there, they would get sued (physx is an example, right?) They also can't remove it, because that would (severely) decrease game/other 3d performance.

Nvidia's 3d drivers are not what is being talked about. My post only referred to 'nv', the 2d driver which Nvidia forced to change readable code into unreadable (and therefore unmodifiable and unstudiable) code. You can look at the "source code" of the 'nv' driver if you want to see for yourself.


> **eragon100 said:**
> And whatever the reason, if RMS gets the nvidia binary driver forbidden in court, and nvidia can't/won't open up their driver, that would prevent me from using the drivers, right? And sorry, but no matter how much I

Holy spurious newlines, Batman!

Where do you get the idea that RMS wants to 'get the nvidia binary driver forbidden in court'? To my knowledge he's never done anything to suggest he would, and furthermore, no court would order Nvidia to "stop distributing the driver unless it's free software" if Nvidia could not make the driver free software. This is a completely random argument and there's not even a point in going further.

> **eragon100 said:**
> 
 hate windows (and not because it's closed-source, but simply, and only, because it doesn't work well), I will dump linux and switch back if I can't play a game / use google earth / have desktop effects on linux. PERIOD.

If all you use your computer for is "ooooo shiny things", then go ahead, install Windows. It might be a Ubuntu position that stupid people should use GNU/Linux, but I'm a Gentoo guy first, and where I come from, if you can't optimize your CFLAGS, you need to read the damn handbook.

> **eragon100 said:**
> 
Reason: I Don't Care. I payed 830 euros for this computer, so I want it to **work**. Open or closed.

So you're angry that it won't work with free software (that's what I've inferred from your statements about how you omgNEED the 3d Nvidia driver), but you didn't do your research properly before dropping that much money? If you just buy things based on "oooo shiny", you're probably not going to get something that works with the system you have in mind. Building a system takes time and research. If you don't want to do that but want the system to run GNU/Linux, then buy from a vendor that certifies that the hardware will work with GNU/Linux. System76 is good, from what I've seen.

> does the license permit modification of the source code without notifying SGI? if so in my opinion that's all that matters. 

Well, in my opinion, I'm glad you aren't heading up the Debian legal team, the FSF legal team, or any other legal team, really.

---

### Post by Paqman on 2008-11-23
> **teddks said:**
> 
If all you use your computer for is "ooooo shiny things", then go ahead, install Windows.


What a ridiculous statement. Windows is the OS on more than 90% of all computers. Claiming it is only useful for frivolous tasks is just plain wrong. Get a grip.

---

### Post by eragon100 on 2008-11-23
> **teddks said:**
> That's completely nonsensical to the snippet you've quoted. Why did you do that?



Nvidia's 3d drivers are not what is being talked about. My post only referred to 'nv', the 2d driver which Nvidia forced to change readable code into unreadable (and therefore unmodifiable and unstudiable) code. You can look at the "source code" of the 'nv' driver if you want to see for yourself.




Holy spurious newlines, Batman!

Where do you get the idea that RMS wants to 'get the nvidia binary driver forbidden in court'? To my knowledge he's never done anything to suggest he would, and furthermore, no court would order Nvidia to "stop distributing the driver unless it's free software" if Nvidia could not make the driver free software. This is a completely random argument and there's not even a point in going further.



If all you use your computer for is "ooooo shiny things", then go ahead, install Windows. It might be a Ubuntu position that stupid people should use GNU/Linux, but I'm a Gentoo guy first, and where I come from, if you can't optimize your CFLAGS, you need to read the damn handbook.



So you're angry that it won't work with free software (that's what I've inferred from your statements about how you omgNEED the 3d Nvidia driver), but you didn't do your research properly before dropping that much money? If you just buy things based on "oooo shiny", you're probably not going to get something that works with the system you have in mind. Building a system takes time and research. If you don't want to do that but want the system to run GNU/Linux, then buy from a vendor that certifies that the hardware will work with GNU/Linux. System76 is good, from what I've seen.



Well, in my opinion, I'm glad you aren't heading up the Debian legal team, the FSF legal team, or any other legal team, really.

I am learning programming and going to study computer science, and ubuntu has a lot more shiny things than vista with compiz, it's just that I also want to play games, and so, I do require nvidia 3d driver. (intel onboard bad game performance). I just bought a new nvidia card because their closed drivers are better than ATI open ones :)

---

### Post by teddks on 2008-11-23
> **Paqman said:**
> What a ridiculous statement. Windows is the OS on more than 90% of all computers. Claiming it is only useful for frivolous tasks is just plain wrong. Get a grip.

I don't think I ever claimed it was **only** for frivolous tasks. I just said that if you **only use** your computer for frivolous tasks, then go ahead and use Windows. I don't see why you'd use GNU/Linux if that's all your interested in.

> **eragon100 said:**
> I am learning programming and going to study computer science, and ubuntu has a lot more shiny things than vista with compiz, it's just that I also want to play games, and so, I do require nvidia 3d driver. (intel onboard bad game performance). I just bought a new nvidia card because their closed drivers are better than ATI open ones :)

Great way to ignore everything else you said. You don't require binary drivers, because you don't require games. You 'want' games.

It's somewhat ironic, because with Hurd, you could have games that overrode certain parts of the kernel in order to maximize performance, and it'd end up being a lot more powerful. But you know, binary drivers. Hurd is dead.

---

### Post by cb951303 on 2008-11-23
> **teddks said:**
> 
Well, in my opinion, I'm glad you aren't heading up the Debian legal team, the FSF legal team, or any other legal team, really.

how do you knoe that I'm not :lolflag:

anyway, can you eloborate exactly how FSF or Debian can be sued by using a code licensed with "SGI free something"? I'm asking because I don't know anything about this license and I don't understand legal documents.

---

### Post by eragon100 on 2008-11-23
> **teddks said:**
> I don't think I ever claimed it was **only** for frivolous tasks. I just said that if you **only use** your computer for frivolous tasks, then go ahead and use Windows. I don't see why you'd use GNU/Linux if that's all your interested in.

Great way to ignore everything else you said. You don't require binary drivers, because you don't require games. You 'want' games.

It's somewhat ironic, because with Hurd, you could have games that overrode certain parts of the kernel in order to maximize performance, and it'd end up being a lot more powerful. But you know, binary drivers. Hurd is dead.

Top part: Because it doesn't cost money (and windows was not included on this pc), because it is more stable, because finding/installing software and updates is easier, because there are a lot of 0$ programs I like to use that don't run on windows (rhytmbox, gxine, brasero, f-spot and more), because the desktop effects are better, do I have to go on?

Middle: exactly, that's the point. I "want" to be able to play games.
I think there are more than enough open-source and commercial games available for linux (long live s2games, id software, and linux game publishing! :)), but if they would, for whatever reason, stop to work, I would, despite the reasons stated above, switch back to windows, even if the NSA can see what I am doing, something I highly doubt. I have been saving money for a nice gaming pc for almost a year, and I don't want all of that to have been for nothing, sorry.

Bottom: I didn't know the Hurd would allow games to function like that, but I do know that there are live-cd's out there, linux-gamers.net live DVD for example that are meant to run games. ONLY games, not even a text editor or webbrowser is included. Just games. There are also people who are thinking about delivering games on dedicated livecd's (me, for example. I am considering making some for a few open-source games. Battle for Wesnoth, nexuiz, or openarena would be first.)

Also, an OS optimized for gaming already exists: it's called a game console.

---

### Post by teddks on 2008-11-23
> **cb951303 said:**
> how do you knoe that I'm not :lolflag:

anyway, can you eloborate exactly how FSF or Debian can be sued by using a code licensed with "SGI free something"? I'm asking because I don't know anything about this license and I don't understand legal documents.

If the FSF spotted a violation of the license, then they would be contractually obligated to inform SGI. They entered into that contract by accepting the license by distributing code under that license (I'm not sure if it applies to use). This violates convention as to what licenses are free and what aren't. This was in no way a decision made solely by gNewSense; as I noted before, it was originally OpenBSD people who pointed out the non-freedom, and the FSF finally followed it up and got SGI to change the license. The code is now free, and it will be back in gNewSense sometime soon.

---

### Post by saulgoode on 2008-11-23
> **cb951303 said:**
> does the license permit modification of the source code without notifying SGI? if so in my opinion that's all that matters.

[It does now]("http://www.fsf.org/blogs/licensing/2008-09-sgi-announcement"), since a new version of the license has been released. OpenGL code to which SGI held the copyrights has been released under the new license; however, there is some OpenGL code which has other copyright holders and that code has yet to be updated to the new license (or otherwise removed/replaced).

---

### Post by teddks on 2008-11-23
> **eragon100 said:**
> 
Bottom: I didn't know the Hurd would allow games to function like that, but I do know that there are live-cd's out there, linux-gamers.net live DVD for example that are meant to run games. ONLY games, not even a text editor or webbrowser is included. Just games. There are also people who are thinking about delivering games on dedicated livecd's (me, for example. I am considering making some for a few open-source games. Battle for Wesnoth, nexuiz, or openarena would be first.)

Also, an OS optimized for gaming already exists: it's called a game console.

I doubt the operating system is very optimized for gaming on game consoles. Most modern game consoles are more general-purpose. I also doubt they would allow functionality like Hurd would, because that functionality (overriding kernel servers) is unique to microkernels, which aren't very popular.

This goes beyond games. For instance, one of the reasons why Photoshop runs better on OS X than on Windows is because on OS X, it can override the kernel's memory manager and handle that by itself. Since Photoshop knows photoshop better than Darwin knows Photoshop, it ends up being a lot better.

On Hurd, *every* application would be able to do that. Games, anything. That's another reason why GNU/Hurd will probably be as widely used (if not wider) than GNU/Linux (to take this thread back to the path from which it has very far diverged).

---

### Post by eragon100 on 2008-11-23
> **teddks said:**
> I doubt the operating system is very optimized for gaming on game consoles. Most modern game consoles are more general-purpose. I also doubt they would allow functionality like Hurd would, because that functionality (overriding kernel servers) is unique to microkernels, which aren't very popular.

This goes beyond games. For instance, one of the reasons why Photoshop runs better on OS X than on Windows is because on OS X, it can override the kernel's memory manager and handle that by itself. Since Photoshop knows photoshop better than Darwin knows Photoshop, it ends up being a lot better.

On Hurd, *every* application would be able to do that. Games, anything. That's another reason why GNU/Hurd will probably be as widely used (if not wider) than GNU/Linux (to take this thread back to the path from which it has very far diverged).

Unless offcourse when the hurd is finally done, OS's will have advanced so far it wouldn't have meaning anymore, or cloud computing will have taken over, with gaming happening on consoles which usually run on a propietary OS developed by the manufacterer.

With the exception of that new game console that appeared a few weeks ago running on a modified fedora (I forgot the name.) It has a "small" problem for a game console, however: the video card is an ATI HD 3200, which is terrible :(

---

### Post by teddks on 2008-11-23
> **eragon100 said:**
> Unless offcourse when the hurd is finally done, OS's will have advanced so far it wouldn't have meaning anymore, or cloud computing will have taken over, with gaming happening on consoles which usually run on a propietary OS developed by the manufacterer.

With the exception of that new game console that appeared a few weeks ago running on a modified fedora (I forgot the name.) It has a "small" problem for a game console, however: the video card is an ATI HD 3200, which is terrible :(

Operating systems haven't advanced very much in the last ten or so years. Cloud computing will be just as influential as any other fad that's been and gone.

As for gaming systems, [this](http://openpandora.org/) is a good indication of where things should be going.

---

### Post by eragon100 on 2008-11-23
> **teddks said:**
> Operating systems haven't advanced very much in the last ten or so years. Cloud computing will be just as influential as any other fad that's been and gone.

As for gaming systems, [this](http://openpandora.org/) is a good indication of where things should be going.

I hate handhelds, they have such a tiny screen, and even the pandora, tough it's impressive and can handle quake 3 arena, doesn't have the horsepower needed to display the kind of graphics that, say, ET:QW puts on the screen at 1680x1050 with 16 x anisotropic filtering and all effects on maximum. :popcorn:

I prefer that kind of graphics on a 20 inch  widescreen over 8 year old graphics on a 4 or something inch screen, even tough the latter may be a bit more portable.

---

### Post by YaroMan86 on 2008-11-23
> **teddks said:**
> A lot of people seem to be sounding off in this thread without a full idea of what's been going on.

[list]
[*] "I'm not going to blame anyone for not developing nv": If I were you, I'd blame nvidia. Nvidia forced the **code obfuscation** of most of the essential parts of nv, so now, while the "source code" is there and it can be redistributed, it is effectively non-free.
[*] "I have a right to choose proprietary codecs if I want to": Actually, Stallman completely agrees with you. The codec issue **is a patent issue, not a free software issue.** You should NOT use things like mp3 because it is patented and free software developers or users could be sued for use of the patented product without a license. You SHOULD use things like Ogg because that is patent-free and has no chilling effects attached.
[*]"The GNU toolkit is great, but it isn't the whole system and I even use zsh now so why should I say GNU/Linux": This misses the point entirely. The reason why you should say GNU(/Linux) is because GNU is a **collective term** for the mostly-copylefted Free Software operating system. The GNU doesn't refer to GNU Coreutils/GNU Binutils/GNU EMACS/<other thousands of GNU Project sponsored packages>, it refers to that collective. Saying GNU/Linux is misleading, as Linux is not a collective term, but a specific program. The GNU operating system was always intended to have non-GNU Project-developed parts; see Stallman's essay in Open Sources (I believe, it's also in EMACS) for proof and expansion.
[*]"gNewSense took out OpenGLX because it wasn't under the GPL": This is an absurd and false claim. Parts of OpenGLX were licensed under **non-free terms, as explained in a previous post**. SGI modified its license to be fully free, and now it's coming back. Notice also that it was Theo de Raadt of OpenBSD who originally pointed out the non-freedom.
[*]"Not that his philosophies matter, he's against violent video games!": Look up "ad hominem" and while you're at it, "red herring".
[*]"I hate <RMS/``Stallmanists''(I have never heard that term before)/Free-software advocates>! They want to take my drivers!": They want your drivers to start being debugged by people outside of the Citadel of <ATI/Nvidia/Wherever>. They want them to not be backdoored by the NSA. They also are the only reason why you have any sort of GNU/Linux system. Linux would not have survived without the GPL. That isn't what Stallman or a ``Stallmanist'' said, that's what **Torvalds** says.
[/list]

The obfuscation of most parts of nv is less because they're being evil and more because they're trying not to get sued. There's third-party technology licensed in nVidia firmware for the most part. This is why nVidia keeps their drivers proprietary becase they don't have certain rights to certain parts. No, I still blame the nv developers for not getting off their *** and reverse engineering what they don't have like the rest of the driver projects for Linux.

No he doesn't agree with the idea of people using ANYTHING proprietary in a free system. That's my point. He's been extremely vocal on that exact point. OTHER people in the FSF might agree, but RMS himself does not. It is true MP3 shouldn't be used for patent issues and not freedom issues, however, if you pay attention to the basic pattern of a company holding a patent who likes to sue: They like to sue other companies, not end users. The likelihood of an average end user for installing codecs that "violate" a patent is slim to none and people do it anyway. Note, of course, that installing a fully licensed package (Like the codec package you can buy from the partners on the Canonical website or a game for Linux that uses MP3 playback, such as the Source Engine when its port is completed.) that comes with those risky codecs are fully legit, meaning you could legally play MP3s with that codec.

You mean that if I use the GPL to license my software I have to call it GNU/Name of Software? Screw that. I'd make my own license if that's really the case. But there's a flaw in your argument: RMS wants entire Linxu distros called GNU/Linux. Remember there's plenty of non-GPL software that's part of most base distributions that are not GNU licenses, including X (Which is under MIT license.) or many of the low-level tools (Whisch are BSD licensed.). Note also that Linux itself is not a GNU kernel, in the sense that its not apart of the GNU project. And that's where the true definition of GNU software lies: Software made under the GNU project directly, not all software licensed under the GPL, that's called "GPL software." Your argument would work if RMS wanted us to call it GPL/Linux, but he's not, instead he's just trying to take credit for other people's work by insisting its called "GNU/Linux."

Pay attention to SGI's recent developments with OpenGL before speaking. They completely opened OpenGL and GLX years ago. This is again, just a case of RMS calling it non-open simply because it doesn't agree with his personal definition of open. Here's a news flash, RMS isn't the sole creator or definer of "open." In fact, I don't even believe he's the first. He got pissed off at the OSI, in fact, because THEY came up with their own more succinct idea of "open" that works better than his "open." ON TOP OF THIS, true open is actually public domain, where anyone can do anything to a work, period, no licensing for redistribution required.

This is a red herring, however, his arguments against violent video games is eerily Jack Thompson-ish, and is frankly an incorrect view. he has no evidence to back up his claims, and correlation is not causation. I play Half-Life 2 and Garry's Mod. I mow down people constantly in those games. It doesn't desensitize me to violence one bit. I still find senseless real life violence reprehensible and "icky." Perhaps Thompson and Stallman can't tell the difference between a video game and real life?

And Torvalds was (Gasp!) wrong. There were other free toolchains and compilers around even in 1991. It just happened to be what he used. Indeed, they were the *best* around, but that's beside the point. Even if the GNU tools *were* the only game in ton, there's one minor flaw in that argument: Stallman and the GNU project STILL DID NOT ACTUALLY CREATE LINUX! That alone is reason enough for them NOT to get credit for it. Richard Stallman was not the one who sat down and created the kernel, X, BSD tools, or all the non-GNU shells. That was due to those who actually did create them. Licensing is not a legal way to affix credit for something to the creator of the license. And by your reasoning, that means that Microsoft deserves credit for creating every Windows-exclusive program out there, because Microsoft (Supposedly.) created the tools used to make Windows software, thus it *must* be a Microsoft program.

No, sorry. It's not GNU, it's Linux, because its a completely different project that happens to make use of GNU tools, and not even Torvalds mistaken fixation of credit to the GNU project for why Linux exists notwithstanding.

By your and Stallman's logic, we should call Ubuntu MIT/GNU/BSD/Canonical/Linux.

---

### Post by eragon100 on 2008-11-23
If you have to think about RMS, I think everyone would get a little crazy and might need to let it out a bit :wink:

BTW, did you know that Jack Thompson has been disbarred? He isn't a laywrer anymore, and the punishment is for life!

He also had to pay $42000,- to the florida bar :KS

> **teddks said:**
> While I'm not anti-censorship.


Richard Stallman is against censorship, also when it comes too violent video games, he says so in the quote I got above. However, he also said he wouldn't want violent games in his home, not even if he had children.

In other words, he is against censoring violent games, and in the same sentence, he says he wouldn't allow his kids to play them. Huh? That sounds a bit contradictory, almost hypocrite.

To quote WindowsSucks from earlier in this thread:

DOES NOT COMPUTE


And please don't double post, especially not if they are this long :wink:

---

### Post by toupeiro on 2008-11-23
This thread is a perfect example of FOSS's single greatest strength and worst weakness..  Nobody can ever seen to be able to agree to disagree on this topic.  The only thing I foresee as being absolute is that this sort of bickering over definitions of "free" is going to hurt any free movement more than help it.  The self-righteousness really needs to die about this topic.

---

### Post by happysmileman on 2008-11-23
> **eragon100 said:**
> In other words, he is against censoring violent games, and in the same sentence, he says he wouldn't allow his kids to play them. Huh? That sounds a bit contradictory, almost hypocrite.

Not to me, there's a difference between "I don't want my kids playing violent games while they live in my house" and "I don't want anyone in the country playing violent games regardless of how old they are"

---

### Post by teddks on 2008-11-23
> **eragon100 said:**
> If you have to think about RMS, I think everyone would get a little crazy and might need to let it out a bit :wink:

BTW, did you know that Jack Thompson has been disbarred? He isn't a laywrer anymore, and the punishment is for life!

He also had to pay $42000,- to the florida bar :KS




Richard Stallman is against censorship, also when it comes too violent video games, he says so in the quote I got above. However, he also said he wouldn't want violent games in his home, not even if he had children.

In other words, he is against censoring violent games, and in the same sentence, he says he wouldn't allow his kids to play them. Huh? That sounds a bit contradictory, almost hypocrite.

To quote WindowsSucks from earlier in this thread:

DOES NOT COMPUTE


And please don't double post, especially not if they are this long :wink:

[list=#]
[*]Whenever I think about RMS, I don't get angry at all. I get inspired, and sometimes a little sad that I haven't done anything like what he's done in his life. Without him, there would be no Linux, or Free Software community at all. He wasn't the first person to do free software, but he was the first person to make an effort to raise awareness about it. Anyone using GNU/Linux owes him a huge debt, whether they like it or not. Getting angry while thinking about RMS is a sign of knowing that you're wrong.
[*]What the hell does Jack Thompson or whoever have to do with the Hurd?
[*]Actually, it looked more like what he said was that he wouldn't want violent video games in his home, *especially* if he had children *in his home*. RMS will never have children. That would be caving to the evils of natalism (google it). In any event, it isn't censorship at all (in the opinion of most) to not allow your kids to play violent video games/watch porn/etc. If you want to stand against that, you have a whole slew of other youth liberation causes you better pick up. None of them are appropriate in this thread.
[/list]

---

### Post by eragon100 on 2008-11-23
> **happysmileman said:**
> Not to me, there's a difference between "I don't want my kids playing violent games while they live in my house" and "I don't want anyone in the country playing violent games regardless of how old they are"

I suppose you are right :wink:

I am just happy that my parents allowed me to play quake 2 when I was 12 (or 13), and that I have been playing games since I got 10, with one of my first titles being "flying saucer", which, altought it's not very violent, is a flight-sim in which you pilot an UFO and have to blow a lot of stuff op. (and think, sometimes -- it's a real fun game!)

If my children (if/when I get any) want to play games, they can go right ahead, as long as they still do their homework, don't buy a real life gun, and don't bully others. My son will be allowed to play unreal tournament 2004 or age of conan when he is 12, too. (I figure I will make that minimum age for "bloody" violence).

EDIT: Crazy florida ex-lawyers have nothing to do with the Hurd, I just tought that YaroMan86 might want to hear the good news about thompson :)

EDIT 2: I have been playing nexuiz deathmatch a bit, but now I am going to bed. See you!

---

### Post by YaroMan86 on 2008-11-23
> **eragon100 said:**
> If you have to think about RMS, I think everyone would get a little crazy and might need to let it out a bit :wink:

BTW, did you know that Jack Thompson has been disbarred? He isn't a laywer anymore, and the punishment is for life!

Oh yes. I know. I partied. Muchly.

---

### Post by saulgoode on 2008-11-23
> **YaroMan86 said:**
> Pay attention to SGI's recent developments with OpenGL before speaking. They completely opened OpenGL and GLX years ago. This is again, just a case of RMS calling it non-open simply because it doesn't agree with his personal definition of open. Here's a news flash, RMS isn't the sole creator or definer of "open." In fact, I don't even believe he's the first. He got pissed off at the OSI, in fact, because THEY came up with their own more succinct idea of "open" that works better than his "open." 
The SGI Free License wasn't considered "free" by the Open Source Initiative either; nor by the Debian Free Software Guidelines. 

What makes you think that the FSF's definition of Free Software is inconsistent with that of the OSI? Those two groups' differences have nothing to do with the *definition* of the terms "Free Software" versus "Open Source Software"; it is merely the fact that the term "Open" in and of itself does not convey the principles important to advocates of Free Software (nor even the advocates of Open Source software).

And just to be pedantic, the Open Source Definition specifies ten criteria that need to be met, the FSF's definition only has four. "More succinct"? 

And just to be precise, nearly three quarters of all Free Software programs are distributed under the GNU GPL license. "Works better"?

---

### Post by DeadSuperHero on 2008-11-23
I just see lots of FUD flinging back and forth, I think this thread needs to be closed.

You people are free to believe what you want, but my goodness some of you really need to do your homework on the matter, otherwise you come across as people who argue for something without even an inkling of what they are arguing for.

---

### Post by cb951303 on 2008-11-24
> **saulgoode said:**
> The SGI Free License wasn't considered "free" by the Open Source Initiative either; nor by the Debian Free Software Guidelines. 


I still don't get this one. I *tried* to read SGI Free B 1.1 but really I understand nothing :D. Can someone point me to the part where it goes against FSF rules which are:
> 
    *  The freedom to run the program, for any purpose (freedom 0).
    * The freedom to study how the program works, and adapt it to your needs (freedom 1). Access to the source code is a precondition for this.
    * The freedom to redistribute copies so you can help your neighbor (freedom 2).
    * The freedom to improve the program, and release your improvements to the public, so that the whole community benefits (freedom 3). Access to the source code is a precondition for this.


---

### Post by saulgoode on 2008-11-24
> **cb951303 said:**
> I still don't get this one. I *tried* to read SGI Free B 1.1 but really I understand nothing :D. Can someone point me to the part where it goes against FSF rules which are:

The problem lay with [section 7]("http://www.xfree86.org/current/LICENSE9.html"):
[INDENT]**7. Claims of Infringement. If Recipient learns of any third party claim that any disposition of Covered Code and/or functionality wholly or partially infringes the third party's intellectual property rights, Recipient will promptly notify SGI of such claim.**[/INDENT]

An obligation was being placed on users to notify Silicon Graphics if the user knew of any infringement claims against the software. While some might consider this a fairly reasonable trade-off (the original Emacs licensing had a requirement that Richard Stallman be notified of any code changes), it meant software licensed under SGI Free B 1.1 did not meet the definition of "Free Software".

---

### Post by cb951303 on 2008-11-24
> **saulgoode said:**
> The problem lay with [section 7]("http://www.xfree86.org/current/LICENSE9.html"):
[INDENT]**7. Claims of Infringement. If Recipient learns of any third party claim that any disposition of Covered Code and/or functionality wholly or partially infringes the third party's intellectual property rights, Recipient will promptly notify SGI of such claim.**[/INDENT]

An obligation was being placed on users to notify Silicon Graphics if the user knew of any infringement claims against the software. While some might consider this a fairly reasonable trade-off (the original Emacs licensing had a requirement that Richard Stallman be notified of any code changes), it meant software licensed under SGI Free B 1.1 did not meet the definition of "Free Software".

and this is against which one of the 4 FSF rules?

---

### Post by teddks on 2008-11-24
> **cb951303 said:**
> and this is against which one of the 4 FSF rules?

All of them. It places an unreasonable restriction that under certain conditions cannot be fulfilled upon the user. If the user does not fulfill those restrictions, they don't have any of the four freedoms.

Also, I'd like to point out, AGAIN, that it was [originally the OpenBSD people that pointed the problem out to the FSF.](http://www.fsf.org/news/thank-you-sgi) This was **not**, as has been implied, some petty grudge of Stallman's. Everyone agreed that this was a problem, including even SGI.

---

### Post by Paqman on 2008-11-24
> **teddks said:**
> I don't think I ever claimed it was **only** for frivolous tasks. I just said that if you **only use** your computer for frivolous tasks, then go ahead and use Windows. I don't see why you'd use GNU/Linux if that's all your interested in.


Never heard of anyone installing Linux because the saw Compiz then?

---

### Post by teddks on 2008-11-24
> **Paqman said:**
> Never heard of anyone installing Linux because the saw Compiz then?

Actually, I've used that to get people to try GNU/Linux (Compiz needs a lot of non-linux libraries, so I don't think I have ever heard of anyone installing just Linux to try to use Compiz). It doesn't work. They run into an error somewhere, they're unwilling to learn, and they end up only using it until it breaks the first time, at which point they just go back to using whatever they were using before.

"ooo shiny" isn't enough motivation to make a change like that. The best motivation is, "You'll finally be free."

---

### Post by eragon100 on 2008-11-24
> **teddks said:**
> Actually, I've used that to get people to try GNU/Linux (Compiz needs a lot of non-linux libraries, so I don't think I have ever heard of anyone installing just Linux to try to use Compiz). It doesn't work. They run into an error somewhere, they're unwilling to learn, and they end up only using it until it breaks the first time, at which point they just go back to using whatever they were using before.

"ooo shiny" isn't enough motivation to make a change like that. The best motivation is, "You'll finally be free."

1: It never broke for me, and it FOSS is so good, it shouldn't either.

2: OOOO Shiney may not be enough motivation, but together with "ooohhh 10000 programs searchable and downloadable via add/remove and it's all free", might be :wink:

---

### Post by Paqman on 2008-11-25
> **teddks said:**
> The best motivation is, "You'll finally be free."

How many people *actually* give a monkey's about that though? I think the biggest pull-factors Linux has are the price, performance, package managers and security. Obscure geek software philosophy just goes over most people's heads. As Linux starts to creep onto a wider user-base (eg: netbooks), the hardcore FOSShead zealot percentage gets diluted more and more. Personally i'm not bothered by that, diversity is good.

---

### Post by swoll1980 on 2008-11-25
I don't know what's crazier, Stallman, or Hurd project.

---

### Post by DeadSuperHero on 2008-11-25
> **Paqman said:**
> How many people *actually* give a monkey's about that though?

I think that there is a large percentage of the Linux community that really does care about freedom. I certainly do!

> I don't know what's crazier, Stallman, or Hurd project.

Define crazy. Stallman may have had some overly ambitious goals and strict views over the years, but is that really something to fault someone for? At least he's doing something he believes in, which most of us aren't even capable of.

The HURD project is a little crazy, I must admit. As much as I want to like it, it's got a ways to go, and the constant switching from microkernel to microkernel makes for a frustrating wait. Mach is flawed, L4 lacks something, and Coyotos is in an entirely new language. Viengoos lacks documentation, and well, you get the idea...

I don't doubt that someday it will get a 1.0 release someday, but it will probably be a while.

---

### Post by teddks on 2008-11-25
> **Paqman said:**
> How many people *actually* give a monkey's about that though? I think the biggest pull-factors Linux has are the price, performance, package managers and security. Obscure geek software philosophy just goes over most people's heads. As Linux starts to creep onto a wider user-base (eg: netbooks), the hardcore FOSShead zealot percentage gets diluted more and more. Personally i'm not bothered by that, diversity is good.

"freedom is better than slavery" isn't really an "obscure geek software philosophy", it's fairly universal. I didn't say the most numerically quantifiable factor, however, I said the strongest. If you switch to GNU/Linux because "it's shinier", you'll go to OS X or Vista when they get shinier. If you switch because "it's faster", you'll do the same when they get faster. But freedom doesn't go away.

And if that "zealot" percentage gets diluted, say goodbye to free software. Linux is on the road to being mostly proprietary already, and with projects like Ubuntu trying to do whatever they can to get people to run GNU/Linux without educating them about freedom, I don't really see the awesome system that we have going now lasting.

This is when the HURD would be a Great Thing, though. And probably, when it will make a 1.0 release, and then a 2.0 release, and so on.

---

### Post by DeadSuperHero on 2008-11-25
As a happy plus note, it seems they are merging the old BD Debian wiki with all the HURD documentation with the official HURD site.

This is, of course, wonderful news.

---

### Post by dmn_clown on 2008-11-26
> **teddks said:**
> "freedom is better than slavery" isn't really an "obscure geek software philosophy", it's fairly universal. I didn't say the most numerically quantifiable factor, however, I said the strongest. If you switch to GNU/Linux because "it's shinier", you'll go to OS X or Vista when they get shinier. If you switch because "it's faster", you'll do the same when they get faster. But freedom doesn't go away.

You might consider thinking about your definition of freedom before you say that it never goes away.  Freedom means without restrictions, the GNU licenses create restrictions to "preserve" freedom and are a major PITA to work with because of those restrictions that are for the most part unnecessary to retain the end user's freedom.  :)

> Linux is on the road to being mostly proprietary already, and with projects like Ubuntu trying to do whatever they can to get people to run GNU/Linux without educating them about freedom, I don't really see the awesome system that we have going now lasting.

Which explains the massive amounts of software that can be purchased in all electronics stores for the Linux platform. ;)

Look, people will only migrate from an existing platform if the system they are migrating towards exceeds their current platform in some way, shape, or form.  This is why SGI's IRIX is now defunct, and why the bulk of the proprietary Unix platforms are being migrated to Linux.  Linux exceeds those platforms in most aspects.  The Hurd does not exceed Linux and, because of its design, it never will.

You won't see mass Hurd migrations happening from anyone just because of the license it is available under.

---

### Post by teddks on 2008-11-26
> **dmn_clown said:**
> You might consider thinking about your definition of freedom before you say that it never goes away.  Freedom means without restrictions, the GNU licenses create restrictions to "preserve" freedom and are a major PITA to work with because of those restrictions that are for the most part unnecessary to retain the end user's freedom.  :)


No, the GNU licenses create restrictions that do preserve freedom. Note that there's no "freedom to enslave". They're quite easy to work with; you just need to be supporting freedom. Freedom means without restrictions, but the GNU licenses create freedom for **everyone**, not just freedom for developers.

> **dmn_clown said:**
> 
Which explains the massive amounts of software that can be purchased in all electronics stores for the Linux platform. ;)

That software could easily be free. Nothing wrong about commercial free software. :)

> **dmn_clown said:**
> 
Look, people will only migrate from an existing platform if the system they are migrating towards exceeds their current platform in some way, shape, or form.  This is why SGI's IRIX is now defunct, and why the bulk of the proprietary Unix platforms are being migrated to Linux.  Linux exceeds those platforms in most aspects.  The Hurd does not exceed Linux and, because of its design, it never will.

You won't see mass Hurd migrations happening from anyone just because of the license it is available under.

You won't see corporations migrating to Hurd because it's more free than GNU/Linux. But you will see a **lot** of developer movement. And after that, you'll see a lot of general movement, because more developers = better software. :)

---

### Post by LinuxGuy1234 on 2008-11-26
GNU/Hurd needs a project manager. That's why GNU/Hurd doesn't work.

GNU/Hurd won't be much widely used when done.

---

### Post by DeadSuperHero on 2008-11-26
> GNU/Hurd needs a project manager. That's why GNU/Hurd doesn't work.

They already have one, if you look at their mailing lists. Thomas Bushnell is one of them.

> GNU/Hurd won't be much widely used when done.
Maybe not. Still, enthusiasts will be able to use it and be free, and
**_that_** is the point of it.

---

### Post by Yeti can't ski on 2008-12-03
> **Dremora said:**
> Removing hardware enabling drivers, and codecs for multimedia for no reason whatsoever is just lunacy.

RMS has zero credibility, especially after his attack on the XO Laptop and sending people to annoy Apple salespeople.

I was tempted to argue that without "lunatics" such as RMS there would be no Ubuntu and there would no forum like this one, but then I realized that all these posts smell just like flaming (sorry if they are not flaming, that was just my impression).

---

### Post by MikeTheC on 2008-12-03
Isn't it a bit redundant these days, anyhow? I mean, it seems like the GNU/Hurd's efforts are what basically gave birth to what we think of as Linux today. It's not like there isn't a massive amount of brain power being invested daily into Linux (erm, 'scuse me, "GNU/Linux"), and if nothing else there is a considerable amount of inertia in certain areas which no "free software or death!" screaming Herd developer is likely to change.

Debian is probably the best example I can think of for an OS distributor which is embraced by the Linux "general public" yet itself only embraces unencumbered software. They also have a reputation for successful delivery of über-stable software. For better or worse, the GNU/Hurd can't even begin to make the same claim.

[FONT=courier]"That" -> Pipe -> Smoke[/FONT]

---

