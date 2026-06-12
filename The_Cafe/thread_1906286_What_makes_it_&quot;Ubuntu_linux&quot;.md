---
title: "What makes it &quot;Ubuntu linux&quot;?"
date: 2012-01-08
forum: The Cafe
---

### Post by Learning Linux 2011 on 2012-01-08
I downloaded Debian last night and installed it in a virtual machine and it looks and works just like Ubuntu.  I know Ubuntu is based on Debian, but I guess I am wondering what makes it "Ubuntu"?  Is it the color scheme?  The choice of programs?  The technical support?

---

### Post by Ctrl-Alt-F1 on 2012-01-08
> **Learning Linux 2011 said:**
> I downloaded Debian last night and installed it in a virtual machine and it looks and works just like Ubuntu.  I know Ubuntu is based on Debian, but I guess I am wondering what makes it "Ubuntu"?  Is it the color scheme?  The choice of programs?  The technical support?
Linux distributions are just the GNU/Linux operating system with a default set of programs or applications installed.  Because Gnome is the default desktop environment for both Ubuntu and Debian, they look very similar.  Similarly, Ubuntu uses debian (.deb) files for package installation so it can borrow many of it's programs from the Debian repositories.

In my mind what makes Ubuntu, Ubuntu, is that it is designed to be easy to use for the end user.  This means that Canonical has put a lot of work into things like video card driver installation, fonts, etc.  It seems a little bit nicer and more polished.

Furthermore, Ubuntu has a great community of users.  The users themselves are what make Ubuntu what it is.  I've found these forums very useful for learning how to use GNU/Linux effectively, and most of the people that help out here are just users.

So to answer your question, software wise, yes the difference is mostly in what programs are installed in a default installation.  For Debian, Ubuntu, Fedora and many others this includes the Gnome Desktop Environment which heavily determines how almost everything looks.  Other distributions use other desktop environments.  There are also configuration differences that go on behind the scenes but are less noticeable to people who aren't power users.

One other difference is that Ubuntu has a shorter release cycle.  This means that it releases a new version more often (new programs).  That makes it usually more cutting edge, but there is a trade-off against stability for that.  Debian stable is usually a pretty rock solid OS.

---

### Post by 1clue on 2012-01-08
If you install Gentoo or Arch or any other distro and then put Gnome on it, it will look pretty much the same.  The look has more to do with Gnome than the distribution.

Take a look at [http://www.canonical.com](http://www.canonical.com) to get some background on the guys who make Ubuntu what it is.

Linux is the kernel and modules.  The kernel is what makes it Linux.  There are a bunch of other apps and tools you can put on it, and that makes the operating system.

The different distributions start by choosing how to build the apps and how to manage the system.  They decide the main goals they want to achieve and then go about reaching them.

To some degree, they might choose where to put certain types of files, but anymore there are standards about that and mostly the distributions follow them.

They choose what hardware they will support (intel, PPC, mainframes, atom, etc) and they decide what sort of loggers and other tools they want to use.  The kernel can be compiled to use various techniques to perform many of the tasks, and those things matter to how the system is configured.  They almost always pick a package manager.  They choose whether to use rolling releases or not.

Debian has chosen to devote a huge amount of effort to be compatible with a lot of hardware.  They choose stability and wide support, they have written a bunch of drivers over the years.

Ubuntu is based on Debian, but they choose to support less hardware and make the user experience very stable and very commercially viable while remaining free.

The thing is, I'm sure the Debian guys will have pulled some of the work Ubuntu back into Debian.  If there were anything wrong with that then it would be wrong for Ubuntu to base its work on Debian in the first place.  The exchange makes everything better.

I could go on for hours about this, but that's the core of it in my opinion.  You really need to try some significantly different distros for awhile to really start to get it.

Keep asking this question to yourself and come up with more questions relating to this to ask others.  You're taking an important step toward understanding Open Source and how it works, and WHY it's such a strong philosophy.

---

### Post by grahammechanical on 2012-01-08
I think there is another difference between Debian and Ubuntu that has not been mentioned. It is only a slight difference. See this link:

[http://www.debian.org/social_contract#guidelines]("http://www.debian.org/social_contract#guidelines")

Note the section on Works that do not meet our free software standards and also the section on source code.

The difference? According to my understanding Ubuntu is just as free and open source as Debian because both organizations hold to the same ethical standard but Ubuntu makes it easier to install non-free, non open source, proprietary software such as drivers.

Can anybody confirm that there is an Additional Drivers utility in Debian?

Regards.

---

### Post by 1clue on 2012-01-08
There's an additional drivers capability in the kernel.  Every distro has the ability to use a non-free driver or any properly made driver which does not come with the kernel.  Nearly every package manager has the ability to add in a different repository, which may contain free, unstable or non-free software.

That said, that's one of the many things that a distribution decides -- how easy it is to incorporate unsupported or external software.  Ubuntu makes it easy, which is important to me.

There is what I consider to be an extreme view on Open Source which believes that every piece of software should comply to their idea of Free Software.  Some distributions consider that to be important, and it drives their packaging strategy.

I personally believe that there is plenty of room in this world for commercial and free software to work well, either separately or in conjunction.  I assert that to insist that all software be free or for it to all be non-free is an extremist viewpoint and that neither will ever happen in any society where individual choice matters.

---

### Post by Ctrl-Alt-F1 on 2012-01-08
> **1clue said:**
> I personally believe that there is plenty of room in this world for commercial and free software to work well, either separately or in conjunction.  I assert that to insist that all software be free or for it to all be non-free is an extremist viewpoint and that neither will ever happen in any society where individual choice matters.

Agree 100%.

---

