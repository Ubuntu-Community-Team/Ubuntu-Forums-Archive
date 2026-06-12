---
title: "Regressions everywhere"
date: 2016-04-24
forum: The Cafe
---

### Post by a2-3 on 2016-04-24
Hello.

I used the weekend to purge my Xubuntu 14.04 installations on three machines and to install a fresh 16.04 on them. To be honest: I'm deeply disappointed. I already heard that development for the desktop world stalled in favour to other battlefield. Well, okay, this is a different story... I mean, a stable OS is not a bad thing. When things are mature and only change slightly, I'm really fine with that. But what xenial brought, compared to trusty was nothing more than a pile of regressions. 

In trusty, I've seen lots of minor flaws. Not a single one is fixed. Not one. I mean, it begins with the installer with the not-that-perfect idea to let the user make partitioning before asking for the keyboard layout. Not a breaking issue, I admit. But if Redmond had came up with such an idea, we all would have laughed loudly about it. It was not fixed in the last two years. The UI style differs radically among Qt4/Qt5/Gtk2/Gtk3. There is no single convegent settings UI, which covers everything. There is no solid support for non-96dpi-screens. All workstation infrastructure (sound, networking, bluetooth, login-sessions, filesystem-mounts, ...) is somewhat buggy and serves you with random error phenomena instead of real operation if you click on the wrong stuff, or too fast, or in a bad order, or in the wrong situation. For some very common configuration aspects, no mature UI exist at all (e.g. filetype associations) in a default installation. There are tons of minor issues in trusty.

But it's not only that devs were not able to fix any of that bugs I saw in the last two years. They actually managed to bring in annoying new ones. My screen flickers weirdly at boot time. After password input, the 'Please enter password' reappears for half a second. My mouse cursor disappears when I lock the screen. The infrastructure is not able to install .deb packages graphically (!!!!) but just via good old dpkg. Some things are noticeable slower than before (how was that realized without really bringing anything new??). The xfce terminal window becomes blank black when I move it to another screen. And so forth and so forth... And this is just what I have seen after an hour or two.

I am very aware of the fact that many issues do not come from the Ubuntu team but from the various projects (Xfce, freedesktop, firefox, systemd, libreoffice, drivers, whatever). So this is not only about Ubuntu but maybe also about the FOSS ecosystem in general (if Ubuntu really sees itself as an actual part of it - I have some doubts after stuff like Mir, Unity, Snappy, ...). I love it that people voluntarily write software. I know that I don't have any legal claim for them to do anything. But why the hell is the whole community nuts about implementing obviously not-that-perfect stuff like integrations to non-free cloud services and not-really-working mobile convergence, while most of the infrastructure have (thereby increasing) flaws in its basic functionality?

Is this a problem which does not really exist and I just imagine? Or is this considered as an actual issue by other people as well? Are there any idea about countermeasures? I mean, of course it is mentioned to be an option to participate in all that projects by writing to mailing lists, filing bugs, writing patches, ... - and I admit that this could really work. But that would mean to spend a whole lifetime by doing other peoples' QA. And this is not as easy as it sounds. Ubuntu versions are always that old that bug reports to upstream get ignored. Fixing a bug in the source is merely a theoretical option, since many bugs are results of wrong decisions in the lowest-level infrastructure of a software (and lots of dirty not-really-working hacks on top of that). This is neither easy to fix nor easy to actually bring to upstream (I admit, if people would send me patches about my programs, which bring deep infrastructure changes, I would also be somewhat reserved).

This post should not only be some kind of bitching. Sorry, if it sounds this way. What are your strategies for participating somehow to FOSS software quality? I'm a bit helpless at the moment. I would do something, if I had the impression that it actually moves things forward. But all ways I know about are only some kind of occupational therapy, or they are not really seizable for non-project-members. What is a good way to patch Ubuntu's xfce (just for instance) without turning the entire system inside out? What is a good way to tell Gnome people that things like 'Client Side Decorations' are a really really bad idea? I mean, it break that much things (most of them admittedly not relevant for day-to-day usage, but also some relevant stuff about consistency) just for 'being modern'? And this is just one example which comes to my mind, while I see a very general trend towards those sad ideas.

For a minimal answer, please just tell me: Do you see this as a problem as well? Is there a general trend towards various ill directions while meaningful development largely stalled? Or have I developed an ill perspective of observation?


Greetings
Josef


PS: Dear admin: Hopefully it is now okay enough for you to not censor again. The original post contained some corollary adjectives which are not 'flowers and bees'-like and came from my frustration. I replaced them with flowers and bees. Due to broken forum software (only works with Javascript enabled) it also did not contain linebreaks. Immediate post removal for non-unlawful content is not entirely what I would expect from such a forum. Maybe, when you eventually remove it again, you could point me to the actual issue.

---

### Post by QIII on 2016-04-24
You would probably be better off addressing your complaints to developers, not users.
Developers don't hang out here, so this is not a good place to get their attention.

---

### Post by grahammechanical on 2016-04-24
I once heard a story about someone who complained to the Gnome developers about the direction they were taking Gnome and he was removed from the mailing list.

Criticisms about Xfce & Gnome should not really be laid at the door of the Xubuntu & Ubuntu developers. There is a small team of Xubuntu developers who work very hard. They could do with some help & there are small ways in which anyone can help. There is even a web site designed to help us find a place that suits each of us.

[https://community.ubuntu.com/contribute/find-a-task/#!/toplevel/quality](https://community.ubuntu.com/contribute/find-a-task/#!/toplevel/quality)

It does not require much skill to do ISO image testing & install testing and then report bugs. Some of us are already running the development version (code name Yakkety Yak) of the next release (16.10). Install it. Use it daily. Update daily. If something breaks a utility will detect the crash and notify the user with a request to report the crash. The utility does all the work of collecting log files and reporting the crash. It really is that simple. And we can do that with Ubuntu & all the flavours.

[http://community.ubuntu.com/contribute/quality/](http://community.ubuntu.com/contribute/quality/)

Regards.

---

### Post by user1397 on 2016-04-25
I hear you.  No OS is perfect.  In fact, every OS has major flaws, and they all sort of suck in some ways.  Now, it could be that may of your issues are directly related to the hardware you have, which isn't an excuse in itself but at least it can show you how many, many people can have almost no issues with 1604 on their hardware while you have a bunch of problems.  Try running an unsupported version of Windows on a Windows 10 laptop.  I bought a Windows 10 laptop and disliked Windows 10 so I tried to install Windows 7 (and on my manufacturer's website it even had Windows 7 drivers for my model), but major things like WiFi and standby didn't work at all, so I had to reinstall Windows 10.

I do sympathize with you though.  It does seem like a lot of times in the Linux world they're just trying to push cool, new features instead of fixing age-old bugs.  This applies to every OS though, even Windows and OS X.  There is a careful balance that developers and project leaders must make to balance new features (which a lot of times they are implementing because of competition from rival OSs) and stability.  Some OS's and distributions are all about stability, some are all about new features or the latest packages, and some are more in the middle, like Ubuntu.

Ubuntu works for millions of people, but that does't mean it works 100% of the time for 100% of hardware.  So yes, it sucks that you had a painful experience.  But you cannot generalize your experience and think that 16.04 is like that for everybody.  I myself did a clean install of 16.04 (regular ubuntu - unity) and have had 0 problems so far (so far being the key words).  At the same time, my work requires some windows-only software right now so I'm not even spending much time on ubuntu these last couple of months. 

I also sympathize with what you said about everyone needing to do QA to make ubuntu or linux in general higher quality and more stable, and how that would take a lot of man hours and who has time for that?  Working people rarely care enough to do more "work" without any pay.  I realize that Linux is free and that no one is forcing me to use it, so I don't complain and say "Linux should be like this or like that" but rather "hmm I would like Linux to be like this or that, and hopefully they work towards that in the near future" but I don't demand anything, because that is hypocritical of me since I don't actively participate in Linux development in any shape or form.

A list of desktop linux problems I recently encountered might give you assurance that others sympathize with you as well.  Here it is: [http://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html](http://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html)  I actually posted that here in the cafe like a month ago, got a lot of responses.

That guy also has one about Windows 10, iOS, and Android.

Anyways, good luck and cheers.

---

### Post by Geoffrey_Arndt on 2016-04-25
a2-3:    

Well, I forced myself to read your entire rambling generalization of complaints, until I nearly got sick.    Then, once again, I noticed this appears to be your only thread (as it so often is with rants like this).   

With all the DIRE scenarios you describe in your epistle, I would think you'd have at least 3, 4 or 5 DOZEN other threads about the specific issue(s), with evidence that you're actively involved in trying to fix at least a few.    

Enough said.

---

### Post by deadflowr on 2016-04-25
>  I mean, it begins with the installer with the not-that-perfect idea to let the user make partitioning before asking for the keyboard layout. Not a breaking issue, I admit. But if Redmond had came up with such an idea, we all would have laughed loudly about it

That would be funny, if that was only the first time the installer asked for the layout.
It is not.
It asked for the layout before you even began at the boot menu, remember?
That is for the setting used during installation setup.

The second time is for userland settings for when the system is installed, and which don't need to be installed until much later in the installation.
The reason it's set like that is because the user who is installing it might understand one language, but the person who will use it might only understand a different one.
Example: I install in English, but the user wants it in French. So I get to install in English, but the user can instantly boot into French.
Simple as that.

---

### Post by buzzingrobot on 2016-04-26
AFIAK, some of these things are essentially out of the hands of any given distribution:

> **a2-3 said:**
> 


... let the user make partitioning before asking for the keyboard layout.

Yes, setting language and keyboard should be done first thing. Some distros also set default fonts that lack characters for certain languages.

 > The UI style differs radically among Qt4/Qt5/Gtk2/Gtk3. There is no single convegent settings UI, which covers everything.

KDE did use QT4, now it uses QT5.  XFCE uses GTK2 and says the next version will be GTK3.  Mate initially was GTK2 and is now GTK2 or GTK3 depending on how a distribution decides to build it.  Gnome and Unity use GTK3. 

And there are ancient apps that don't use any of those.

It would be lovely to have a "single convergent settings UI" but that awaits creation and acceptance of a "single convergent GUI toolset" across Linux, which seems entirely unrealistic.  It's do-able, in effect, if a distribution only uses packages based on one toolset. 


 > There is no solid support for non-96dpi-screens. 

Pretty sure X assumes everything is 96dpi. Another reason to wish it gone.

---

