---
title: "Any Oses that use linux kernel but not the linux system itself?"
date: 2006-05-02
forum: The Cafe
---

### Post by dmb on 2006-05-02
Is there any oses out there that use the linux kernel, but not the unix enviorment itself(gnu stuff)?

---

### Post by prizrak on 2006-05-02
I would guess alot of embedded stuff. Although I do suspect that many of those still contain gcc and libraries just because it's alot easier to take what is there instead of making something new.

---

### Post by TheCaptain on 2006-05-02
Linux is the kernel, everything else is not Linux. It's not really compatible with anything not GNU mostly because nothing not GNU isn't directly compatable with Linux.

What are you trying to do? Or what are you looking for?

If you are looking beyond GNU stuff there are the *BSD's, NetBSD is very nice and will run on your old C64 as well as any other computer known to man, OpenBSD is as secure as it gets and an excellent server system, FreeBSD is desktop stuff with an excellent package manager.

OpenSolaris pretty much sucks in it's current state and since you don't like GNU, Nexenta isn't for you, otherwise, it's an up and go system (licencing issues aside).

---

### Post by ComplexNumber on 2006-05-02
[quote=dmb]Is there any oses out there that use the linux kernel, but not the unix enviorment itself(gnu stuff)?[/quote] most recent motorola non smartphone mobile phones use the linux kernel but the user interface and the rest is propriatory. these include the models v3x, ROKR E2 and a range of others. [this]("http://uk.gizmodo.com/2006/04/18/motorola_rokr_e2_with_itunes.html") is the E2.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=prizrak]I would guess alot of embedded stuff. Although I do suspect that many of those still contain gcc and libraries just because it's alot easier to take what is there instead of making something new.[/QUOTE]

Probably not GCC but probably mostly GPL stuff, it's going to stay that way since you'll either run glibc and then you're stuck since linking anything to that requires it to be GPL or you'll run another libc and then the linking to the kernel will ruin the licencing scheme.

It'd be nice if Linux was truly free but it's not.

---

### Post by dmb on 2006-05-02
I just mean, if there is any os(yes, i know linux is technically the os, but in this situation i mean kernel+other programs that help with management of the hardware), that uses JUST the linux kernel, and not the unix(like)envoirment that linux is typically packed with. This is just a question of curiosity, im not really trying to do anything.

---

### Post by ComplexNumber on 2006-05-02
[quote=dmb]I just mean, if there is any os(yes, i know linux is technically the os, but in this situation i mean kernel+other programs that help with management of the hardware), that uses JUST the linux kernel, and not the unix(like)envoirment that linux is typically packed with. This is just a question of curiosity, im not really trying to do anything.[/quote] in addition to the ones that i've mentioned above, there are many many many examples. the linux kernel alone is extremely popular in the embedded market etc. you'll find it in virtually everything and anything. there are even toy penguins that run on the linux kernel.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=dmb]I just mean, if there is any os(yes, i know linux is technically the os, but in this situation i mean kernel+other programs that help with management of the hardware), that uses JUST the linux kernel, and not the unix(like)envoirment that linux is typically packed with. This is just a question of curiosity, im not really trying to do anything.[/QUOTE]

1. Linux is not technically the OS, Linux is the kernel, the OS is the Kernel and the libc along with the basic function executables which makes up the shell you need to be able to use the kernel for whatever purpose you intend to use it for, this varies greatly from a full blown distro to a rescue cd that only runs one proggie to a firewall to an imbedded implementation.

2. Kernel contains the drivers, hence management of the hardware, it's included if you include it in the kernel, if you don't, you'll need modules and a way to load them.

If you mean Linux kernel in specific implementations, it's quite common in imbedded appliances ranging from furnaces to refrigirators to tv's to dvd players to phones to ... believe it or not... shoes.

---

### Post by drogoh on 2006-05-02
[QUOTE=TheCaptain]

If you are looking beyond GNU stuff there are the *BSD's, NetBSD is very nice and will run on your old C64 as well as any other computer known to man, OpenBSD is as secure as it gets and an excellent server system, FreeBSD is desktop stuff with an excellent package manager.

[/QUOTE]

For clarification, FreeBSD isn't "desktop stuff", and Net, Open, Free, etc. all use their own "ports" system.  There is no "package manager".  FreeBSD is more "enterprise server operating environment without the ungodly overhead" than "desktop".  Some people try to make things work with FreeBSD on the desktop end because it is by far the largest active BSD project out there and would therefore get more testing.  There are some FreeBSD forks that cater and dedicate to the desktop, but FreeBSD in itself is, at heart, a server operating environment with the desktop part being secondary.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=drogoh]For clarification, FreeBSD isn't "desktop stuff", and Net, Open, Free, etc. all use their own "ports" system.  There is no "package manager".  FreeBSD is more "enterprise server operating environment without the ungodly overhead" than "desktop".  Some people try to make things work with FreeBSD on the desktop end because it is by far the largest active BSD project out there and would therefore get more testing.  There are some FreeBSD forks that cater and dedicate to the desktop, but FreeBSD in itself is, at heart, a server operating environment with the desktop part being secondary.[/QUOTE]

*sigh*

There is one in every forum, FreeBSD is focused on speed and usability, that spells d.e.s.k.t.o.p to me.

The ports system with it's tools portinstall, portsnap, portupgrade IS the package management as emerge is the package management for Gentoo, if you want pure packages... pkg_add -r <package name> will add the package pkg_delete will remove it, if you want more you can use portupgrade -Pp to just use packages, if this isn't package management then neither is apt-get.

FreeBSD in it's latest version isn't anything but designed for desktop speed, you can call it what you like but that is what it's designed for.

OpenBSD is designed for other purposes and so is NetBSD, both of them make better server systems than FreeBSD which doesn't really thrive in a server role but rather as a destop system (hence the package management and the multitude of desktop programs installed by default).

---

### Post by TheCaptain on 2006-05-02
Oh, and Net and OpenBSD don't use the ports system. they both use the package source system, which, btw is also available for slackware if you ever really feel like compiling it.

---

### Post by drogoh on 2006-05-03
[QUOTE=TheCaptain]*sigh*

There is one in every forum, FreeBSD is focused on speed and usability, that spells d.e.s.k.t.o.p to me.
[/quote]
"one in every forum"?  I was merely trying to point out what seemed like ill-gotten information.

> The ports system with it's tools portinstall, portsnap, portupgrade IS the package management as emerge is the package management for Gentoo, if you want pure packages... pkg_add -r <package name> will add the package pkg_delete will remove it, if you want more you can use portupgrade -Pp to just use packages, if this isn't package management then neither is apt-get.
pkg-tools is a third-party suite, while portsnap is an alternative to CVSup.

> FreeBSD in it's latest version isn't anything but designed for desktop speed, you can call it what you like but that is what it's designed for.
6.0 was actually developed with NDIS in mind, as NDIS was the highlight.

> OpenBSD is designed for other purposes and so is NetBSD, both of them make better server systems than FreeBSD which doesn't really thrive in a server role but rather as a destop system (hence the package management and the multitude of desktop programs installed by default).
OpenBSD has one purpose other than severe zealotry and that is super mega ultra heavy duty security, not exactly a server role.  NetBSD is all about "run BSD on your toaster!".  Again, not exactly a server role, and both projects pale in comparison to FreeBSD's server user base.  If FreeBSD doesn't thrive in a server role, how is it Yahoo!, NTT/Verio, SAVVIS, etc. use it in server environments?  I myself have FreeBSD in a production server environment and have been using it for several years with no problems.

I am not trying to start a flame war, it just seemed like there was some inaccurate information.

P.S.  Yes, Open uses ports.  It used ports when I used it, and FAQ 15.3.1 says "it exists, we borrowed it from Free, we suggest you use binaries, but it's for advanced users if you want".  So I was wrong on Net about them using ports, I don't use Net.  I stick to Free.

---

### Post by TheCaptain on 2006-05-03
[QUOTE=drogoh]"one in every forum"?  I was merely trying to point out what seemed like ill-gotten information.[/QUOTE]

As a dev in FreeBSD i hardly need you to point out anything, thank you.

> pkg-tools is a third-party suite, while portsnap is an alternative to CVSup. 

*sigh* the pkgtools are installed by default in FreeBSD (pkg-tools is a slackware thing), it's used by sysinstall during the installation too. The portutils are installed if you don't choose to do a minimal installation. (wait for the real funny when he claims that OpenBSD uses ports while you have to jump through hoops and go beyond anything supported to use it, ah, the people who have to be right even when they are so obviously wrong... )


> 6.0 was actually developed with NDIS in mind, as NDIS was the highlight.

And THAT is why we added the multitude of improvements for individual user memory management on site. Well that and the X-connect performance improvements, we did that with ONLY NDIS in mind. Have you ever benchmarked 5.3 and 6.0 in X? You should, we did, this was the single most important improvement we made.


> OpenBSD has one purpose other than severe zealotry and that is super mega ultra heavy duty security, not exactly a server role.  NetBSD is all about "run BSD on your toaster!".  Again, not exactly a server role, and both projects pale in comparison to FreeBSD's server user base.  If FreeBSD doesn't thrive in a server role, how is it Yahoo!, NTT/Verio, SAVVIS, etc. use it in server environments?  I myself have FreeBSD in a production server environment and have been using it for several years with no problems.

I am not trying to start a flame war, it just seemed like there was some inaccurate information.

P.S.  Yes, Open uses ports.  It used ports when I used it, and FAQ 15.3.1 says "it exists, we borrowed it from Free, we suggest you use binaries, but it's for advanced users if you want".  So I was wrong on Net about them using ports, I don't use Net.  I stick to Free.


You yourself has FreeBSD on a production server and don't have a clue about it, i hope your employer doesn't find out...

And no, Open doesn't use ports more than Fedora uses apt, yes, it CAN be used but you'll have to work around it and it's not recommended.

What are you, the energizer bunny? Do i really have to keep proving you wrong time and time again until you stop?

---

### Post by agger on 2006-05-03
[QUOTE=drogoh]For clarification, FreeBSD isn't "desktop stuff", and Net, Open, Free, etc. all use their own "ports" system.  There is no "package manager".  FreeBSD is more "enterprise server operating environment without the ungodly overhead" than "desktop".  Some people try to make things work with FreeBSD on the desktop end because it is by far the largest active BSD project out there and would therefore get more testing.  There are some FreeBSD forks that cater and dedicate to the desktop, but FreeBSD in itself is, at heart, a server operating environment with the desktop part being secondary.[/QUOTE]
However, I had FreeBSD running GNOME, Firefox and a lot of apps on my (old) desktop for six months or so, and it did just fine for Internet + office like stuff. If you just need a basic desktop + office applications, FreeBSD is fine and performs excellently. 

It is not, however, as slick or as complete as Ubuntu, and most new applications need to be downloaded as source code and rebuilt, which in some cases is quite time consuming.

---

### Post by TheCaptain on 2006-05-03
[QUOTE=agger]However, I had FreeBSD running GNOME, Firefox and a lot of apps on my (old) desktop for six months or so, and it did just fine for Internet + office like stuff. If you just need a basic desktop + office applications, FreeBSD is fine and performs excellently. 

It is not, however, as slick or as complete as Ubuntu, and most new applications need to be downloaded as source code and rebuilt, which in some cases is quite time consuming.[/QUOTE]

Actually packages are built pretty swiftly, it just depends if you want to wait a week or not, hey, this is CURRENT we are talking about, it's not that hard to wait a week and use -Pp or pkg_add is it? ;)

Yeah, i know, i don't wait either, hey, it's just sitting there doing nothing, might as well use the CPU power i have. ;)

---

### Post by helpme on 2006-05-03
[QUOTE=TheCaptain]As a dev in FreeBSD i hardly need you to point out anything, thank you.
[/QUOTE]
How about showing us some code, commits, to prove that you are a Dev and not some little troll giving out incorrect information?

---

### Post by tribaal on 2006-05-03
> it's just sitting there doing nothing, might as well use the CPU power i have

Don't hesitate to join [the cause]("http://boinc.bakerlab.org/rosetta/")!

:)

Sorry I couldn't resist, it happends every time I hear about unused computing power :mrgreen: . Not sure they have BSD clients handy, on top of that.

- trib'

---

### Post by TheCaptain on 2006-05-03
To clarify, i'd say FreeBSD is to BSD as Ubuntu is to Linux.

If you'd want to set up a server in Linux, you probably wouldn't choose ubuntu, personally i would choose Slackware but that's just because i love the bsd init, or CentOS, in BSD, OpenBSD is for your server tasks, NetBSD is for portability and it's a very flexible OS, for a Webserver i would probably use NetBSD, for a desktop, FreeBSD, can you beat it on the desktop speed? nah, can you beat it's PACKAGE MANAGEMENT? nah, it's better than apt and that does mean something, if it runs on any *nix, it runs on FreeBSD, and even though they are running through a layer, MOST linux apps run faster on the desktop of FreeBSD than on Linux.

And Linus keep ragging on us because we implement unneccessary optimizations... heh.

FreeBSD is the fastest desktop you can run bar NONE. (yayayay, ok, win 3.1 is faster)

---

### Post by TheCaptain on 2006-05-03
[QUOTE=tribaal]Don't hesitate to join [the cause]("http://boinc.bakerlab.org/rosetta/")!

:)

Sorry I couldn't resist, it happends every time I hear about unused computing power :mrgreen: . Not sure they have BSD clients handy, on top of that.

- trib'[/QUOTE]

hehe, i'd join if i hadn't already, not in BSD though, i could probably get it to run through the compat layer though...

Whoa, project coming. :D

Actually, i'm not kidding.

---

### Post by tribaal on 2006-05-03
> Actually, i'm not kidding.

Glad to hear another machine will be used for the cause. ;)
And if you have time, I'm sure some could use your expertise at making Rosetta run on *BSD :)

- trib'

---

