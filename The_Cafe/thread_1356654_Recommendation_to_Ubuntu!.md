---
title: "Recommendation to Ubuntu!"
date: 2009-12-16
forum: The Cafe
---

### Post by Martial-law on 2009-12-16
I would recommend Ubuntu to add one more improvement to make the distro even more user friendly to the masses. And that is the applications installation process. Make it such that the users just have to download a single file or exe of an application and install it on their Ubuntu OS easily and even if they wish offline. Just as PC BSD guys have made it:


[http://www.youtube.com/watch?v=JOtYep8K0PI](http://www.youtube.com/watch?v=JOtYep8K0PI)


For advanced users keep the command option too. I hope this idea would get your attention.

---

### Post by bruno9779 on 2009-12-16
But .deb packages already do just that.

---

### Post by NoaHall on 2009-12-16
> **bruno9779 said:**
> but .deb packages already do just that.

+1.

---

### Post by RiceMonster on 2009-12-16
> **bruno9779 said:**
> But .deb packages already do just that.

It won't work offline because it needs to download dependencies. The file contains dependencies in .pbi.

---

### Post by Tibuda on 2009-12-16
There are many methods of how to install stuff on Ubuntu, including the option you have suggested.

- Easier way: Use Ubuntu Software Center
- Almost easier way: Use Synaptic
- Easy way: Download a deb file (eg [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/))
- "Blind" way: paste apt-get command at terminal
- Another "blind" way: click [apturl]("apt:ubuntu-restricted-extras")
- Hard way: compile from source code or install from strange installer

Psychocats cover all the easy methods: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by bruno9779 on 2009-12-16
So you want it to contain all the dependencies that it could possibly need?
that sounds impractical and space consuming.

---

### Post by NoaHall on 2009-12-16
> **bruno9779 said:**
> So you want it to contain all the dependencies that it could possibly need?
that sounds impractical and space consuming.

+1. You're on a roll, bruno.

---

### Post by P.KO on 2009-12-16
Hi,

But it might be a good idea for wireless drivers and firmware.

---

### Post by emigrant on 2009-12-16
anyway your name make me laugh :D . Thanks for the suggestion.

---

### Post by Grifulkin on 2009-12-16
> **Martial-law said:**
> I would recommend Ubuntu to add one more improvement to make the distro even more user friendly to the masses. And that is the applications installation process. Make it such that the users just have to download a single file or exe of an application and install it on their Ubuntu OS easily and even if they wish offline. Just as PC BSD guys have made it:


[http://www.youtube.com/watch?v=JOtYep8K0PI](http://www.youtube.com/watch?v=JOtYep8K0PI)


For advanced users keep the command option too. I hope this idea would get your attention.

LOL.  This is a joke yes?  First off we are not PC BSD and another thing we have .deb and if we have all the dependencies in said files, what makes that any different than windows.  Yes I understand that just because it is like Windows doesn't make it Windows.  But your idea of an easy install is heavily  influenced by Windows, I prefer the way I install things on Linux compared to Windows.  And I am sure there are more people that feel this way, nothing is hidden from you it's nice.

---

### Post by The Real Dave on 2009-12-16
> **P.KO said:**
> Hi,

But it might be a good idea for wireless drivers and firmware.

Depends on the Program. Some people running other WMs wouldn't like it when a .deb includes half of gnome. As far as the OP goes, it already does that, as stated, download a .deb, double click and gdebi will install and solve dependencies. If you want it to work perfectly offline, go download those dependencies and compile it.

---

### Post by Excedio on 2009-12-16
Correct me if I'm wrong, but isn't this decision up to the creator of the program?

---

### Post by Paqman on 2009-12-16
> **RiceMonster said:**
> It won't work offline because it needs to download dependencies.

You can get a certain amount of the dependencies from the disk. Granted this does leave you with a restricted range of software, but then you are offline, so you can't have it all.

---

### Post by RiceMonster on 2009-12-16
> **bruno9779 said:**
> So you want it to contain all the dependencies that it could possibly need?
that sounds impractical and space consuming.

Windows already does it without space problems, can't speak space wise for PC-BSD 'cause I haven't tried it. The fact that they already both do it also proves it's not impractical.

> **Paqman said:**
> You can get a certain amount of the dependencies from the disk. Granted this does leave you with a restricted range of software, but then you are offline, so you can't have it all.

Maybe I should have said "it won't work offline if you don't already have all the dependencies."

> **Excedio said:**
> Correct me if I'm wrong, but isn't this decision up to the creator of the program?

It's up to the packaging method they use.

---

### Post by bruno9779 on 2009-12-16
mmm

maybe a new .deb extension could be created, something like .debfull

so you could have the normal .deb and .debfull with packed any dependency it could possibly need.

I understand some need this functionality, but the amount of people that has ubuntu installed offline is minimal, so you can't really expect a change like this to be implemented on the base install

---

### Post by juancarlospaco on 2009-12-16
BTW You can include all dependencies on a single .deb
I already do that, a 10kb .py results an +6Mb .deb
Try it yourself, no skills needed at all: [http://python-packager.com/](http://python-packager.com/)
:)

---

### Post by Tibuda on 2009-12-16
> **bruno9779 said:**
> mmm

maybe a new .deb extension could be created, something like .debfull

so you could have the normal .deb and .debfull with packed any dependency it could possibly need.

I understand some need this functionality, but the amount of people that has ubuntu installed offline is minimal, so you can't really expect a change like this to be implemented on the base install

[http://code.google.com/p/superdeb/](http://code.google.com/p/superdeb/)

It is not official.

---

### Post by bruno9779 on 2009-12-16
> **juancarlospaco said:**
> BTW You can include all dependencies on a single .deb
I already do that, a 10kb .py results an +6Mb .deb
Try it yourself, no skills needed at all: [http://python-packager.com/](http://python-packager.com/)
:)

> **danielrmt said:**
> [http://code.google.com/p/superdeb/](http://code.google.com/p/superdeb/)

It is not official.

Nice, I like the direction this thread is taking

---

### Post by Martial-law on 2009-12-16
If something is a improvement it should not be opposed but should be supported. Why keep sticking to old methods. Here is some info about the PC BSD apps installation system:


"PC-BSD's package management system takes a different approach to installing software than many other Unix-like operating systems. Instead of using the FreeBSD ports tree directly (although it remains available), PC-BSD uses files with the .pbi filename extension which, when double-clicked, bring up an installation wizard program. An autobuild system tracks the FreeBSD ports collection and generates new PBI's daily. The generated PBI's are maintained at the PC-BSD software repository.
All software packages and dependencies are installed in their own self-contained directories in /Programs. This convention decreases confusion about where binary programs reside, removes the possibility of a package breaking if system libraries are upgraded or changed, and prevents dependency hell. The PC-BSD package manager also takes care of creating categorized links in the KDE menu and on the KDE desktop.
The PC-BSD package management system aims to be similar to that of major operating systems such as Microsoft Windows and Apple Mac OS X, where applications are installed from a single downloaded file with graphical prompts, rather than the traditional package management systems that many Unix-like systems use."


[http://en.wikipedia.org/wiki/Pc_bsd](http://en.wikipedia.org/wiki/Pc_bsd)

---

### Post by Tibuda on 2009-12-16
> **Martial-law said:**
> If something is a improvement it should not be opposed but should be supported. Why keep sticking to old methods. Here is some info about the PC BSD apps installation system:


"PC-BSD's package management system takes a different approach to installing software than many other Unix-like operating systems. Instead of using the FreeBSD ports tree directly (although it remains available), PC-BSD uses files with the .pbi filename extension which, when double-clicked, bring up an installation wizard program. An autobuild system tracks the FreeBSD ports collection and generates new PBI's daily. The generated PBI's are maintained at the PC-BSD software repository.
All software packages and dependencies are installed in their own self-contained directories in /Programs. This convention decreases confusion about where binary programs reside, removes the possibility of a package breaking if system libraries are upgraded or changed, and prevents dependency hell. The PC-BSD package manager also takes care of creating categorized links in the KDE menu and on the KDE desktop.
The PC-BSD package management system aims to be similar to that of major operating systems such as Microsoft Windows and Apple Mac OS X, where applications are installed from a single downloaded file with graphical prompts, rather than the traditional package management systems that many Unix-like systems use."


[http://en.wikipedia.org/wiki/Pc_bsd](http://en.wikipedia.org/wiki/Pc_bsd)

Apps in self-contained directories is not an improvement. It is not a regression too. It have its advantages and also disadvantages.

Applications can be installed on ubuntu "from a single downloaded file with graphical prompts". I already gave you an example: [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

---

### Post by Ylon on 2009-12-16
> **Martial-law said:**
> I would recommend Ubuntu to add one more improvement to make the distro even more user friendly to the masses. And that is the applications installation process. Make it such that the users just have to download a single file or exe of an application and install it on their Ubuntu OS easily and even if they wish offline. Just as PC BSD guys have made it:


[http://www.youtube.com/watch?v=JOtYep8K0PI](http://www.youtube.com/watch?v=JOtYep8K0PI)


For advanced users keep the command option too. I hope this idea would get your attention.

Nice thing to do offline, now.. when were talking back "online".


There's something that can be compared to **sudo apt-get upgrade**: I mean, have **all** your installed application updated to the last version.

Also, update dependencies updated (mean that your application improve even if the original team did stop working on it).


:guitar:



Anyway, it would be intresting to have one option which include possibility to install new software offline.


For example: after build a tree of dependencies which come by default with the system installation, common to all Koalas.

In order to install Abiword I had actually need all these dependeincies:
abiword, abiword-common, abiword-help, abiword-plugin-grammar, abiword-plugin-mathview, libaiksaurus-1.2-0c2a, libaiksaurus-1.2-data, libaiksaurusgtk-1.2-0c2a, libgdome2-0, libgdome2-cpp-smart0c2a, libgtkmathview0c2a, liblink-grammar4, libots0, libt1-5, libwv-1.2-3, link-grammar-dictionaries-en

An option that give me "put all in a package for offline install" (which dowload 'n' pack dependencies which I had already installed) which put everything in a tar.gz

This package will be quickly outdated, so it's main propouse should be intended for immediate use (let's say 2~3 month) or for install urgent software on newly installated system (as wifi firmware for particular hardware)

---

### Post by cariboo on 2009-12-16
There is an application in the repositories called aptoncd that does what you want.

There are also several ways to download the packages for use later on. you can use:

```
sudo apt-get -d install <packagename>
```

You can also use synaptic to select and download packages for later use.

---

