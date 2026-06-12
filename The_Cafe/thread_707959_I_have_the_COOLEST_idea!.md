---
title: "I have the COOLEST idea!"
date: 2008-02-25
forum: The Cafe
---

### Post by Masterj15 on 2008-02-25
Whats the one thing that window user have at their feet while linux user have to learn how to do it the hard way? The installation of programs. Sure, we have deb. and stuff but what about the programs that you have to install using the terminal? That would be very hard thing to do sometimes. (like installing the ps2 emulator)


I have an idea called archive installer! It a program wgere you can install pure linux programs through a gui like with windows and their installer. If we had this it would make all linux programs a breaze to install. Unfortonatly I don't know a lick of C++ to get started on such a easy seeming program.

Wouldn't this be a good idea? discus.

---

### Post by icechen1 on 2008-02-25
> **Masterj15 said:**
>  Sure, we have deb. and stuff but what about the programs that you have to install using the terminal? .
You mean compiling program?

By the way,an existing solution to make an app run on all distro is autopackage but it is not very popular,yet.

---

### Post by jpittack on 2008-02-25
I personally dislike the windows installer.  A gui different from it would be fine.  Install this program? Yes.  Password? ****.  Closes out.  The idea here being that its not deb, and resolves all dependencies.

---

### Post by aimran on 2008-02-25
Isn't that what we call Synaptic?

---

### Post by hhhhhx on 2008-02-25
i think that the op's talking about a program that you can literaly put the directory containing all the code for a program and it outputs everything were it should be right?

---

### Post by icechen1 on 2008-02-25
> **xhhux said:**
> i think that the op's talking about a program that you can literaly put the directory containing all the code for a program and it puts everything were it should be right?

Oh i get it,like Loki installer,some .bin .run installers(like Google earth) that has to be run from the terminal for root permission.

---

### Post by Ocxic on 2008-02-25
that would be sweet
and easy since most program are just ./configure, make, make install
it's the dependencies that would be the hard part.

---

### Post by macogw on 2008-02-25
Windows users think it's easy to install software?  My brother and sister still asked me to install their games for them until they were like 14.  My mom and dad never figured it out.

---

### Post by luisito on 2008-02-25
Super COOL idea.

Luckily many other people had that idea before. i.e. Synaptic.

There is also klik ([http://klik.atekon.de/](http://klik.atekon.de/)) that I have never tried but sounds interesting.

---

### Post by Superkoop on 2008-02-25
> **Masterj15 said:**
>  Unfortonatly I don't know a lick of C++ to get started on such a easy seeming program..

I don't either, but I don't think it would be very easy to program, because if it was, it would already be done. And when I think about it, I don't think it's really possible to make a program compile source, satisfy all dependencies, place it in the correct place, etc, etc. And still be guaranteed to have a working program.

---

### Post by TBOL3 on 2008-02-25
The main difference between ubuntu's install system, and windows install system is where you install the files.  In ubuntu, it's pre chosen, which has good and bad points (good because everything is organized, and you only need one set of dependencies system wide, but bad because you need to know where packages are stored in order to modify them).  In windows, you choose where to install packages.  Which is good because you know where files are, but it leads to a cluttered system, and you may have to have the same dependency installed 5 times.   (OH NO 5 MORE MEGABYTES!!! :lolflag: )

---

### Post by sumguy231 on 2008-02-25
The problem with the idea is that not all programs distributed as source tarballs compile the same way. There could be a utiltity which would try to guess how to compile the program, but in the end the only guaranteed thing to do is read the documentation included.

---

### Post by lespaul_rentals on 2008-02-25
Your idea is great, and I really think you are a good person for wanting to help others.  But shouldn't we have people learn how to compile and install from source instead of giving them a GUI?  Linux may become as nooby as Windows.  Just think about that.

However, I have an idea to make it work.  What if we were to somehow make the program output the terminal feedback to a file or string that would then be read.  Very dumbed-down, here is what I am thinking:

**Ideal situation:**

User input in GUI >> terminal.  Terminal then guesses the method to configure and make the installer.  Once it determines it, it then runs and installs using the script.

**Not ideal -- dependencies not met:**

User input in GUI >> terminal.  Terminal then guesses the method to configure and make the installer.  However, a dependency is not met.  Terminal output >> log file.  Log file is then searched by the program for a list of known libraries and dependencies.  Let's say it finds a dependency called "lib-language" that cannot be found on the system.  It then downloads and installs this necessary dependency from the Ubuntu repositories, and runs the configure and make again.

---

### Post by macogw on 2008-02-26
> **lespaul_rentals said:**
> Your idea is great, and I really think you are a good person for wanting to help others.  But shouldn't we have people learn how to compile and install from source instead of giving them a GUI?  Linux may become as nooby as Windows.  Just think about that.

However, I have an idea to make it work.  What if we were to somehow make the program output the terminal feedback to a file or string that would then be read.  Very dumbed-down, here is what I am thinking:

**Ideal situation:**

User input in GUI >> terminal.  Terminal then guesses the method to configure and make the installer.  Once it determines it, it then runs and installs using the script.

**Not ideal -- dependencies not met:**

User input in GUI >> terminal.  Terminal then guesses the method to configure and make the installer.  However, a dependency is not met.  Terminal output >> log file.  Log file is then searched by the program for a list of known libraries and dependencies.  Let's say it finds a dependency called "lib-language" that cannot be found on the system.  It then downloads and installs this necessary dependency from the Ubuntu repositories, and runs the configure and make again.
I think you just described Portage.

---

### Post by Paqman on 2008-02-26
I actually think installing and removing software is much easier in Linux than Windows. Package managers are awesome. How often do you really have to compile yourself anyway?

For an autocompiling system to work though, you'd have to come up with a standard format for the source to be presented in. If you're going to go to those lengths, why not just package it up?

I think we could do without having multiple different package formats though. Standardising to either .deb or .rpm would be a good move, IMO.

---

### Post by 3rdalbum on 2008-02-26
> **Paqman said:**
> 
For an autocompiling system to work though, you'd have to come up with a standard format for the source to be presented in. If you're going to go to those lengths, why not just package it up?

Two reasons:

1. If you package up a program, that involves compiling it for a particular architecture. People running Linux on other architectures wouldn't be able to use the package. Also, if the person who packaged the program was on a 64-bit operating system, you wouldn't be able to use it on a 32-bit operating system.

2. The packager would be making the decisions about what options to pass to the configure script, whereas I think the user should have the choice.

---

### Post by Masterj15 on 2008-02-27
> **xhhux said:**
> i think that the op's talking about a program that you can literaly put the directory containing all the code for a program and it outputs everything were it should be right?
basically, yes. :)

> **Superkoop said:**
> I don't either, but I don't think it would be very easy to program, because if it was, it would already be done. And when I think about it, I don't think it's really possible to make a program compile source, satisfy all dependencies, place it in the correct place, etc, etc. And still be guaranteed to have a working program.
Well some windows people I knkow view linux harder because of "the terminal". They view it as some smart guy, C++ knowing, god and I want them to feel as if they don't have to be nervous running the terminal. If Some guy could create a gui program that basically did every thing the terminal does for installing a program, then it wouldn't be so scary. I wish I knew how to make pictures to show you guys what I mean. 

> **sumguy231 said:**
> The problem with the idea is that not all programs distributed as source tarballs compile the same way. There could be a utiltity which would try to guess how to compile the program, but in the end the only guaranteed thing to do is read the documentation included.
Thats another feature I wanted. I want the program to show the user to readme file as well. So when their installing, they can see the readme right in front of their face.

> **lespaul_rentals said:**
> Your idea is great, and I really think you are a good person for wanting to help others.  But shouldn't we have people learn how to compile and install from source instead of giving them a GUI?  Linux may become as nooby as Windows.  Just think about that.

However, I have an idea to make it work.  What if we were to somehow make the program output the terminal feedback to a file or string that would then be read.  Very dumbed-down, here is what I am thinking:

**Ideal situation:**

User input in GUI >> terminal.  Terminal then guesses the method to configure and make the installer.  Once it determines it, it then runs and installs using the script.

**Not ideal -- dependencies not met:**

User input in GUI >> terminal.  Terminal then guesses the method to configure and make the installer.  However, a dependency is not met.  Terminal output >> log file.  Log file is then searched by the program for a list of known libraries and dependencies.  Let's say it finds a dependency called "lib-language" that cannot be found on the system.  It then downloads and installs this necessary dependency from the Ubuntu repositories, and runs the configure and make again.

Don't we want linux to look more "nooby like"? We want to make people feel as if they can learn linux, not the other way around. I'm no 31337 when it comes to computer but, I learned linux and I want people to feel the same way. :)

---

### Post by lespaul_rentals on 2008-02-27
Basically, Masterj15 is thinking about the MSI installer that Windows has.  Unfortunately, everyone is right when they say that the source will have to be distributed in a static manner according to specifications to make it work with all packages.  However, if you programmed a package generator that a programmer could run his or her source through, then you might have something going.

Might as well just stick with the DEBs and RPMs if it comes down to that.

---

### Post by Masterj15 on 2008-02-27
I don't get what you guys mean? I mean, if it has specific stuff or a specific type of installation, then the program can still run it. Like, when you run the terminal and want to install something that is specific. If the terminal can do it then why not a program? It doesn't have to have a generator if the program has "Linux" specific instructions. Its almost like as if the program is like the terminal. The only goal is to make things less confusion for the average windows user.

---

### Post by funrider on 2008-02-27
just write a simple script with all the "sudo apt-get install [programA...B]' 

this will do the job on any machine

---

### Post by kool_kat_os on 2008-02-27
> **aimran said:**
> Isn't that what we call Synaptic?

ya....i think it is

---

### Post by Masterj15 on 2008-02-27
> **funrider said:**
> just write a simple script with all the "sudo apt-get install [programA...B]' 

this will do the job on any machine

Some people got what I am talking about and some people don't. Its hard to explain what I mean on a forum. (or in typing. lolols) 

Let me make this clear. I AM NOT TALKING ABOUT SNPATIC PROGRAMS OR DEB PACKAGES WHAT SO EVER. I'M TALKING ABOUT PROGRAMS THAT YOU CAN'T USE A SUDO APT-GET INSTALL FOR. I'M TALKING ABOUT WHOLE LINUX PROGRAMS. A PROGRAM THAT CAN RUN ON ANY LINUX FORMAT. YOU KNOW WHAT I MEAN. PACKAGED PROGRAMS THAT MAKE YOU HAVE TO TYPE MAKE, INSTALL, BUILD AND ALL THAT OTHER CRAP.

---

### Post by sumguy231 on 2008-02-27
Please don't yell.
As I said, there is probably no reason you couldn't make a small utility to assist users in building packages from source. But because there is no standard defined way to distribute source packages (though most follow the same format) there would be no guarantee that all source packages would work with said utility.

---

### Post by igknighted on 2008-02-27
> **Masterj15 said:**
> Some people got what I am talking about and some people don't. Its hard to explain what I mean on a forum. (or in typing. lolols) 

Let me make this clear. I AM NOT TALKING ABOUT SNPATIC PROGRAMS OR DEB PACKAGES WHAT SO EVER. I'M TALKING ABOUT PROGRAMS THAT YOU CAN'T USE A SUDO APT-GET INSTALL FOR. I'M TALKING ABOUT WHOLE LINUX PROGRAMS. A PROGRAM THAT CAN RUN ON ANY LINUX FORMAT. YOU KNOW WHAT I MEAN. PACKAGED PROGRAMS THAT MAKE YOU HAVE TO TYPE MAKE, INSTALL, BUILD AND ALL THAT OTHER CRAP.

The solution is to get those applications that aren't in the repo's into the repos and/or built as debs.  Look at the opensuse build program.  You upload the source, it builds the packages and creates a repo for you.  You can then add the repo and install the proper way.  See [http://software.opensuse.org/search](http://software.opensuse.org/search) and the one click install, this seems like what you want.

---

### Post by macogw on 2008-02-27
> **Masterj15 said:**
> Some people got what I am talking about and some people don't. Its hard to explain what I mean on a forum. (or in typing. lolols) 

Let me make this clear. I AM NOT TALKING ABOUT SNPATIC PROGRAMS OR DEB PACKAGES WHAT SO EVER. I'M TALKING ABOUT PROGRAMS THAT YOU CAN'T USE A SUDO APT-GET INSTALL FOR. I'M TALKING ABOUT WHOLE LINUX PROGRAMS. A PROGRAM THAT CAN RUN ON ANY LINUX FORMAT. YOU KNOW WHAT I MEAN. PACKAGED PROGRAMS THAT MAKE YOU HAVE TO TYPE MAKE, INSTALL, BUILD AND ALL THAT OTHER CRAP.

Those aren't packaged programs.  They're just a pile of source code.  Not all of them do ./configure, make, make install.  Some have ./autogen involved too.  There are a lot of build dependencies to be satisfied as well.  Writing something like this would require a language parser that can understand error messages about which libraries are missing and then figure out what package has those and then install that package and then start the./configure all over again about 20 times til it gets everything.  Just like a human.  On top of that, there are plenty of things that DO NOT give errors when compiling because whether or not your system has the dependency for a certain feature determines whether or not that feature is compiled in.  It's not an error if it's not.  You seem to want some magical cross-distro version of Portage that somehow has no database of dependencies.  It can't happen.

---

### Post by Masterj15 on 2008-02-27
> **sumguy231 said:**
> Please don't yell.
As I said, there is probably no reason you couldn't make a small utility to assist users in building packages from source. But because there is no standard defined way to distribute source packages (though most follow the same format) there would be no guarantee that all source packages would work with said utility.
sorry about yelling.
I'll esxpin what I mean (if I can). :)

> **igknighted said:**
> The solution is to get those applications that aren't in the repo's into the repos and/or built as debs.  Look at the opensuse build program.  You upload the source, it builds the packages and creates a repo for you.  You can then add the repo and install the proper way.  See [http://software.opensuse.org/search](http://software.opensuse.org/search) and the one click install, this seems like what you want.
that looks awesomesause!

> **macogw said:**
> Those aren't packaged programs.  They're just a pile of source code.  Not all of them do ./configure, make, make install.  Some have ./autogen involved too.  There are a lot of build dependencies to be satisfied as well.  Writing something like this would require a language parser that can understand error messages about which libraries are missing and then figure out what package has those and then install that package and then start the./configure all over again about 20 times til it gets everything.  Just like a human.  On top of that, there are plenty of things that DO NOT give errors when compiling because whether or not your system has the dependency for a certain feature determines whether or not that feature is compiled in.  It's not an error if it's not.  You seem to want some magical cross-distro version of Portage that somehow has no database of dependencies.  It can't happen.
no, no. I mean....................hmmmmmm. I understand what your saying but................ 

OK, This is the best way to explain it. But first I need some question answered (if you can please).

Isn't the normal way to install source code through the terminal? If so, doesn't it have a set of rules in the readme file or install file? Also, doesn't the source code know its own dependencies against you computer?

---

### Post by sp0nge on 2008-02-27
This is the single issue that had me on the fence for so long about ditching windows permanantly. I was terrified of the command line at first, but I started playing with it. I even forced myself to understand DOS, installing programs was always scary to me.

Once I started doing it, I started to enjoy it. I would much rather install from the command line now rather than mess with the windows setup wizzard!

---

### Post by sumguy231 on 2008-02-27
> Isn't the normal way to install source code through the terminal? If so, doesn't it have a set of rules in the readme file or install file? Also, doesn't the source code know its own dependencies against you computer?
This depends on your definition of "normal". I would actually define "normal" as installing a binary package through the package manager.
But no, there are no set rules. Most people who distribute software as source code distribute them in similar ways (./configure, make, make install, etc) but sometimes other build methods are used (automake, autogen, etc).
It is usually the job of the configure script to determine if dependencies are met but not all configure scripts report missing dependencies in the same way, and not all programs come with configure scripts. Clearly you can make something that covers most source packages fairly well (like SuSE's build service but locally) but I don't think it would be all that easy and in the end it might be better to make a coordinated effort to package more programs in the first place.

---

### Post by macogw on 2008-02-28
> **Masterj15 said:**
> 
OK, This is the best way to explain it. But first I need some question answered (if you can please).

Isn't the normal way to install source code through the terminal? If so, doesn't it have a set of rules in the readme file or install file? Also, doesn't the source code know its own dependencies against you computer?

READMEs are usually in plain English, often in paragraphs and including suggestions for troubleshooting, maybe a few dependencies, probably a lot of "oh such and such still needs to be fixed, i know, but here's a workaround you can try....", credits, release notes, etc.  Good luck muddling through all that with just a dumb computer and no human brain.

---

### Post by cardinals_fan on 2008-02-28
As a Zenwalk user, I'm used to doing LOTS of compiling from source :)
It really isn't a problem.  I have long since begun to use [buildpkg]("http://wiki.zenwalk.org/index.php?title=Buildpkg").  Though it was hard to learn at first, this process is actually quite easy and I now handle most of my source packages this way.

---

### Post by odiseo77 on 2008-02-28
I personally feel comfortable with .deb packages, synaptic, apt-get, dpkg, etc. Autopackage may be useful in certain situations (eg. when there's not a package for your distro yet), but I always try to avoid it (as well as *run and *.bin files, unless it's strictly necessary).

I also don't have problems installing stuff from source, but I recognize it might be hard or annoying sometimes -specially for newcomers-. I don't think there's an easy solution when the software you need/want is not available in a nice package for your distro... The only solution that comes to my mind is creating/according some general standards for a unified type of package that can run on different distros, but I guess it can have technical issues since the many distros branches around differ from each other (not only in the packaging system, but also in the library naming conventions, and this can be a problem when it comes to dependencies...).

---

### Post by sumguy231 on 2008-02-28
I suppose this isn't 100% relevant, but I thought I should mention for anyone that didn't already know that checkinstall makes compiling from source way less messy.

---

### Post by aysiu on 2008-02-28
I think you should read these threads:
[Unified Package Manager (Autopackage and other ideas)](http://ubuntuforums.org/showthread.php?t=388305)
[Easier way to install source tarballs etc.](http://ubuntuforums.org/showthread.php?t=271107)
[Have these projects already been undertaken?](http://ubuntuforums.org/showthread.php?t=231834)
[Autodeb, a tool for automated building and .deb creation from source](http://ubuntuforums.org/showthread.php?t=90602)

---

### Post by toupeiro on 2008-02-28
I spent a good portion of my IT career as a windows software packager, and MSI is incredibly customizable and robust.  RPM and DEB are also very good packaging platforms.  Now Installshield, Wise,  and InstallAnywhere (pretty much the biggest packaging players for the windows platform) have linux based GUI INstallation contexts, but I have not been overly impressed with them.  In my opinion, its hard for a player like installshield or Wise to come into linux and do package management better than RPM or deb.  Windows was greatly lacking standards for installation methodology until .msi was formed.

Personally.. my feeling in regard to ANOTHER attempt at a linux package management standard is, don't.  Make rpm and deb more transparent with eachother (Like Wise, Installshield and InstallAnywhere are), maybe simplify the steps to write rpm and deb packages for app developers, but IMHO some other ground up GUI installer is not the answer.

---

### Post by LightB on 2008-02-28
On ubuntu I prefer to make and install deb with checkinstall, which is generally set up correctly to do this by default.

---

### Post by RJ Hythloday on 2008-02-28
[SIZE=2][quote=icechen][/SIZE]
 
[SIZE=2][IMG]http://ubuntuforums.org/customavatars/avatar262595_1.gif[/IMG][/quote][/SIZE]
 
[SIZE=2]Totally ot but I love your avatar![/SIZE]

---

### Post by Vitamin-Carrot on 2008-02-28
my 24 year old ex couldnt figure out how to install the sims on a machine i gave her

@_@

I like to think i helped at least once in that relationship

:KS

---

