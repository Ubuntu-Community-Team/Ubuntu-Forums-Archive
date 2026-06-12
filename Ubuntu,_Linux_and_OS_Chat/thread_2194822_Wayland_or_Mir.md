---
title: "Wayland or Mir"
date: 2013-12-20
forum: Ubuntu, Linux and OS Chat
---

### Post by seanmoir99 on 2013-12-20
Now I was just wondering why does Canonical plan to use Mir instead or Wayland ?

---

### Post by TheFu on 2013-12-20
I can only guess that it is to improve GPU performance for gaming.  See, for the last 20+ yrs, Linux GUIs have been based on X/Windows which is A-M-A-Z-I-N-G with all sorts of fantastic features that noobs don't use too much.  OTOH, long-time UNIX folks use these features daily like remotely displaying programs on different systems.  That is built-into X/Windows from the ground up and has been there since the 1980s.  This network-layer slows things down.  X/Windows is some of the cruftiest code still being used in the world today. Lots of bugs, inefficiencies, memory leaks, .... sorta like Windows GDI ... probably about the same cruft levels and memory leaks. I'd prefer a re-write of X11 with low-bandwidth and high-performance modules added myself. Using a profiler, it should be possible to determine where all most of the slowdowns happen and take advantage of newer protocol techniques like NX or/and SPICE.

In short - performance.
Just a guess.  I really haven't a clue.  It could be their attempt to create a walled-garden like Apple has. I dunno.

I'm not a fan of either upstart or systemd ... the init.d/ scripts have worked for 30+ yrs, good enough for me AND well understood. Don't fix what isn't broke, I always say.

---

### Post by seanmoir99 on 2013-12-20
OK If Ubutnu does ever make a walled garden then I am definitely jumping ship,  I came to Linux for a few reason and that is more configuration, Stability and Security, Not to have a OS X wannabe operating system, but I don't think its gonna be a walled garden, but whats wrong with systemd rather than being rather new

---

### Post by TheFu on 2013-12-20
> **seanmoir99 said:**
> OK If Ubutnu does ever make a walled garden then I am definitely jumping ship,  I came to Linux for a few reason and that is more configuration, Stability and Security, Not to have a OS X wannabe operating system, but I don't think its gonna be a walled garden, but whats wrong with systemd rather than being rather new

I haven't a clue - this is just the "chat" area. ;)

I don't see the point of systemd ...  init.d/ scripts have worked fine for everything that I've needed the last 30+ yrs. Ain't broke. Newer doesn't mean better - I run LTS releases for a reason.  More discussion on this: [http://www.linuxquestions.org/questions/linux-general-1/what-are-the-advantages-disadvantages-of-using-systemd-versus-sysvinit-4175422544/](http://www.linuxquestions.org/questions/linux-general-1/what-are-the-advantages-disadvantages-of-using-systemd-versus-sysvinit-4175422544/)

---

### Post by 3rdalbum on 2013-12-21
> **seanmoir99 said:**
> Now I was just wondering why does Canonical plan to use Mir instead or Wayland, I know they have done this sort of thing before with the initialization scripts where they moved to there own developed Upstart instead of the more Linux generic Systemd

Upstart: Initial release	24 August 2006
Systemd: Initial release	30 March 2010

I don't know who it was who started telling people that Systemd was developed before Upstart, but you've definitely fallen for their FUD. Systemd is not "more Linux-generic", it's just a forwards-approach to bootup where Upstart is a backwards-approach. Both inits are available in the repositories of most distros.

> OK If Ubuntu does ever make a walled garden then I am definitely jumping ship, I came to Linux for a few reason and that is more configuration, Stability and Security

More FUD; programs generally need NO modification to run on X11, Wayland or Mir as long as the underlying toolkit supports the different display servers. As Ubuntu's repositories are basically dumped from Debian's repositories, you'll have Xorg and Wayland in the repositories as well as Mir. They'll only be an apt-get away. Worst-case scenario: They'll only be a PPA away.

People who have various axes to grind about Ubuntu have been spreading quite a few outright lies to anyone who will listen. Don't listen to the haters, make up your own mind and do your own research.

---

### Post by seanmoir99 on 2013-12-21
Oh I thought upstart was ubuntu only and I thought upstart had only been around since 2011 oh well, but why would you want to initialize things backward wouldn't you want to do it forward (systematically)

---

### Post by 3rdalbum on 2013-12-21
> **seanmoir99 said:**
> Oh I thought upstart was ubuntu only and I thought upstart had only been around since 2011 oh well, but why would you want to initialize things backward wouldn't you want to do it forward (systematically)

I'm not an expert on init systems, and I'm not very familiar with Systemd, so this might be "the blind leading the blind".

SysVInit and Systemd both focus on starting the lowest-level services first: USB support, drivers, networking - before starting the higher-level services such as Network Time Protocol, filesystem mounting, file sharing, and the graphical desktop. This makes sense, because you need to have networking up in order to get NTP to start, and you need to have USB up before you can mount any USB filesystems, and you need to have a lot of things running before you can start X. If you do things in the wrong order, some parts of the system just won't come up; as a result, the order is selected very conservatively, with an emphasis on "bring everything up to avoid failures, whether it's really needed or not". It's all very cobbled-together and inflexible.

Systemd is a bit more intelligent here to deal with these kinds of situations, I'm sure, but both Systemd and SysVInit focus on the journey.

Upstart takes a different approach. It looks at what high-level services need to be running at the end, and runs some code to 'start' them. In the process of 'starting' the service, Upstart also knows what lower-level services are prerequisites ("dependencies") for each higher-level service, and starts those dependencies. And so on, and so on. Upstart focuses more on the destination.

To put it another way, when you install a package, the Apt system also makes sure it installs the dependencies for that package, and ONLY those dependencies that are required. Upstart is like Apt. Imagine if your Apt system installed every single possible dependency onto your system, in case you decided to install a package that needed just one of them. That's like how SysVInit works, and to a lesser extent how Systemd works.

---

### Post by seanmoir99 on 2013-12-21
thanks 3rdalbum I much better understand upstart now I guess they both have there ups and downs, I used systemd a bit when I tried out Arch Linux for a bit. :)

---

### Post by monkeybrain20122 on 2013-12-21
Redhat itself used upstart for several years before it came up with systemd and rams it down everyone's throat so it becomes 'the standard'. :) There are quite a bit of complaints about systemd and at least one distro bit the dust because of it (Fuduntu)

---

### Post by grahammechanical on 2013-12-21
Has anyone mentioned that MIR is Free and Open Source Software? Ubuntu is a walled garden without any walls. As for the reasoning behind the decision

[https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec](https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec)

Ubuntu Touch 1.0 for phones and tablets is already running on Mir and Unity 8. Notice these quotes from the KDE developers

> [COLOR=#2E3436][FONT=Open Sans]Starting a new Wayland compositor would mean to stop the work on the X11 window manager, which would be a bad move as we cannot know yet whether Wayland will succeed and will be supported on all hardware. [/FONT][/COLOR]

> [COLOR=#2E3436][FONT=Open Sans]Writing a new Wayland Compositor would require to rewrite the complete X11 workspace in one go. This includes not only the Window Manager, but also parts of Plasma, KDM, Screen Locker and many, many more. This would take a long development time and the transition would not be smooth, very likely buggy and with regressions like the 4.0 introduction. We do not want to break the desktop![/FONT][/COLOR]

[http://community.kde.org/KWin/Wayland](http://community.kde.org/KWin/Wayland)

It is often not known or forgotten that Wayland is only a protocol. There needs to be Window compositor written to that protocol. Also keep in mind that Ubuntu does not block the installation of a Wayland compositor in Ubuntu. There are Wayland libraries in Ubuntu. Trusty Tahr has these libraries installed:

Wayland Compositor Infrastructure - client library
Wayland Compositor Infrastructure - server library
Wayland Compositor Infrastructure - cursor library

in the software Centre there is Unity System Compositor which is described as "System compositor used by Mir display server in Ubuntu . If Unity System Compositor can't start  LightDM will fallback to plain Xorg display server." Oh, by the way, Unity System Compositor is not installed by default but those Wayland libraries are installed by default.  No walled garden on the Ubuntu desktop.

Regards.

---

### Post by ian-weisser on 2013-12-21
> **seanmoir99 said:**
>  but why would you want to initialize things backward wouldn't you want to do it forward (systematically)

In Upstart, you can work both forward and backward easily and simultaneously. Whatever your job needs.
Do you need help parsing a requirement or a job config?


> **seanmoir99 said:**
> I don't think its gonna be a walled garden, but whats wrong with systemd rather than being rather new

Nothing is wrong with systemd.
Systemd is in the Ubuntu repositories. You can use systemd instead of Upstart if you wish...though Ubuntu is not tested with systemd, and you may need to generate some of the systemd configuration files.
If you are asking why Ubuntu uses Upstart instead of systemd, it's the usual - the reasons to keep Upstart outweigh the reasons to switch to something else.

---

