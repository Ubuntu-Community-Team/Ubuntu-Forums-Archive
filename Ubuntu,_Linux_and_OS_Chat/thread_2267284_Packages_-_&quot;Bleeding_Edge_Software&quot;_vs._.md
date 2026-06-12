---
title: "Packages - &quot;Bleeding Edge Software&quot; vs. Stability/Security, mindset of a Linux user"
date: 2015-02-28
forum: Ubuntu, Linux and OS Chat
---

### Post by garycheng12 on 2015-02-28
Coming from Windows, users have the mindset of always updating their programs to the latest version available from the website. They have built-in updaters that make keep the programs automatically updated. I learned that packages from a distro's software center are always playing "catch-up" as they need to package the program specifically for not only their distro, but for their distro's version. 

1. What does packaging an application for a specific distro's version entail? How is this different from a tar.gz file (or whatever type of file that is labeled as a "Linux" version) available from the application's website, which seems to always be as up-to-date as its Windows counterpart? Are applications labeled for "Linux" safe to use in any distro? Can applications from a specific distro and distro version ever be used in another Linux distro (as in it works, but not "optimized", whatever that means), or do they literally do not work?

2. Are there any distros that allow users to always have the latest (stable, same version as the website) application like in Windows? 

3. I understand that a software center provides security for its users--packages that come from it has been through testing and are safe. Why do built-in updaters not exist or (or if they do, why are they not popular) as an alternative to the software center, since packages from the software center are generally not the latest versions available? 

4. Ubuntu is fortunate in that it has a huge community and are popular starting point for Windows users such that many applications have packages and they do not lag too far behind the latest stable version available for Windows. How do other distros (which may have a significantly smaller community or are much slower in deveopment) ensure their applications are up-to-date (or that they can use applications even if packages are not available for the distro)?

5. What exactly does "compiling from source" entail and are there ways to automate this process, or does a user need to manually compile from source every time an application is available? 

6. Some distros are described to be "bleeding-edge" in terms of the packages they deal with. What does this mean in context? It's almost as if it is something to avoid, but again, a Windows user has the mindset of always preferring the latest stable version.


There are several applications that I use that are available in both Windows and Linux and it would be awkward for the application on Windows to have a feature that is not yet (or will never be present) in Ubuntu or other Linux distros. 
Not sure if this is a good mindset to have--I would be happy to be taught what kind of a mindset an experienced Linux user would have.

---

### Post by deadflowr on 2015-02-28
Moved to Ubuntu,Linux, and OS chat

A lot of questions, but none pertaining to needed support.

---

### Post by ian-weisser on 2015-02-28
> **garycheng12 said:**
> 1. What does packaging an application for a specific distro's version entail?
5. What exactly does "compiling from source" entail and are there ways to automate this process[...]? 
There are entire libraries devoted to how to compile, the problem with compiling that led to pre-compiled binary tarballs, and the problems with tarballs that led to packages.
A short and incomplete answer is that a package includes all the distro-specific dependency, version, and install work so that the package 'just works' instead of sending you round with a dozen errors to manually troubleshoot and fix.
Compiling...well, try it a few times, and you will understand.

> **garycheng12 said:**
> 2. Are there any distros that allow users to always have the latest (stable, same version as the website) application like in Windows?
No. Part of packaging includes version-matching and testing...both of which take time and volunteer labor.
Individual sources are out there may have just-released, freshly-built packages, but they are usually not supported by the rest of the distro and might break your system. See "Bleeding-edge" below.

> **garycheng12 said:**
> 3. [...]Why do built-in updaters not exist[...]?
Why would a distro include a feature that, when used properly, is likely to break the package manager and/or system in new and unpredictable ways?

> **garycheng12 said:**
> 6. Some distros are described to be "bleeding-edge" in terms of the packages they deal with. What does this mean [...]? 
"Bleeding-edge" means new and UNstable. Not stable yet. Beware. May cause pain.

Your Windows experience is misleading you. Security is Security. New is New. Security does not always mean "upgrade to Newer". Newer versions may not be more secure.
Windows uses a consumer model. Debian and Ubuntu use a participant model.

---

### Post by Old_Grey_Wolf on 2015-02-28
That is not quit the experience I have as a Windows user.

> **garycheng12 said:**
> Coming from Windows, users have the mindset of always updating their programs to the latest version available from the website. 

If a program is open source I will update it. If I have to pay for the newer version I will use the old version until it no longer gets security support or I have a real need to upgrade the version.

> They have built-in updaters that make keep the programs automatically updated. 

I use several applications on Windows that don't have built in updaters. Linux does have applications that have built in updaters as well as PPAs. Some of the Windows applications with built in updaters don't update the version but only apply security patches. Some of the Linux repositories provide security updates provided the developer/maintainer of the application submits them.

---

### Post by MartyBuntu on 2015-02-28
I suppose many Linux users that are bitten with "*upgrade fever*" approach Linux and Ubuntu as a "*fun hobby*", but fall back on Windows for their main install because they "*need*" it, or don't see Ubuntu/Linux as a completely viable alternative for day-to-day computing.

---

### Post by bro2 on 2015-02-28
Latest versions on Linux could be considered beta releases on Windows.

Also, I can't advocate for stability (only been running for a day, but nothing exploded yet), but Arch does have those latest versions :)

---

### Post by gifford on 2015-02-28
Often developers and maintainers will offer stable and unstable ppa's for packages. The "unstable" can be considered "bleeding edge" and may cause issues with your system or have bugs that 
need to be worked out.

---

### Post by garycheng12 on 2015-02-28
Thanks for the responses, guys.

> **ian-weisser said:**
> 
Why would a distro include a feature that, when used properly, is likely to break the package manager and/or system in new and unpredictable ways?


I didn't know applications as tar.gz files can actually break your system. It seemed to me like a "portable application" in the context of using Windows where everything an application needed as extracted and there's no real installation to the system, so a built-in updater would only touch the files pertaining to the application.

There is an application that I need to use (IntelliJ IDEA IDE) that is not available in the software center nor is it available via PPA. Could I use it safely (so that it wouldn't break the package manager/system)? Are there steps I need to take to prevent this or is a risk that I should/shouldn't take?

---

### Post by ian-weisser on 2015-02-28
> **garycheng12 said:**
> There is an application that I need to use (IntelliJ IDEA IDE) that is not available in the software center nor is it available via PPA. Could I use it safely (so that it wouldn't break the package manager/system)?

Yes, you can use it safely...IF you have the skills to identify and repair any damage that the non-packaged application causes to the package-provided files and applications.
Lots of people mingle packaged and tarball and compiled applications quite safely. Others promptly cripple their systems.

There's no simple trick to it. It's a moderately complex learned skill that requires patience and practice to acquire. You must learn how package management works, what dpkg does, what apt does, the details of dependencies and repositories and sources, what the dpkg/apt error messages mean, what it means to upgrade an application, how to use the apt-cache command, etc.

---

### Post by Bucky Ball on 2015-02-28
[This]("http://cdimage.ubuntu.com/daily-live/current/") is bleeding edge. Expect breakage. 15.04 is not due until April.

I personally go for an LTS release that offers the best chance of stability and productivity. I can't have breakages on my main install (but have three others to break, if I feel the urge). ;)

---

### Post by grahammechanical on 2015-03-01
If you are interested in intellij idea on Ubuntu then you might be interested in Ubuntu Make - Ubuntu loves developers concept.

[http://blog.didrocks.fr/post/Ubuntu-Make-0.3-brings-Intellij-IDEA-and-Pycharm-support](http://blog.didrocks.fr/post/Ubuntu-Make-0.3-brings-Intellij-IDEA-and-Pycharm-support)

Ubuntu Make is now at version 0.4 with go support

> [COLOR=#333333][FONT=Arial]For those not familiar with Ubuntu Make, this is a command line tool created by Canonical, which allows developers to install various development tools / IDEs. Initially, the tool targeted Android developers, making it easy to install Android Studio in Ubuntu. Later, Ubuntu Make also got support for Pycharm, Eclipse and intellij IDEA.[/FONT][/COLOR]

[http://www.webupd8.org/2015/01/ubuntu-make-04-released-with-go-support.html](http://www.webupd8.org/2015/01/ubuntu-make-04-released-with-go-support.html)

It is under continued development and so could turn into a really useful tool for developers. If it is not already. And it is official. And tested. It will be in the Ubuntu 15.04 Software Centre. On older versions of Ubuntu it is installed through a ppa.

Regards.

---

### Post by garycheng12 on 2015-03-02
Actually, I was told that IntelliJ IDEA IDE for Linux is fine because it  is pre-compiled and no actual installation takes place (you just  download the tar.gz file, extract it, then ./idea.sh, as stated in the readme file). Therefore, I can use it safely, right? It seems like I had some confusion between source files, packaged files, manually-compiled files, and pre-compiled files. Please correct me if I'm wrong and be nitpicky about it--I need a good understanding of this (I have like 15 tabs open about dependencies/packaging in Linux):

1. Source files are files that need to be compiled to a specific distro and its specific version.
2. Packaged files are the packages you get from the software center/repositories that are fully supported by the package management system.
3. Manually-compiled files are the applications need ./configure, make, sudo make install. **These are the ones that will mess up the dependencie****s/package management system**.
4. Pre-compiled binary files can be used *safely* because it doesn't actually install anything on the system (although it still depends on some dependencies and will not run if dependencies are not installed). Examples include **Intellij IDEA** and **Firefox**. One may prefer pre-compiled binary version of Firefox *over* installing the Firefox package for Ubuntu because the pre-compiled binary version is a 100% working version of the *latest stable version available*.

---

### Post by ian-weisser on 2015-03-03
> **garycheng12 said:**
> I was told that IntelliJ IDEA IDE for Linux is fine because it  is pre-compiled and no actual installation takes place (you just  download the tar.gz file, extract it, [...]

No, your IntelliJ install should be fine because the installer script is unlikely to overwrite your existing data, nor change your settings. It might do those things; I've never tried it.
Any makefile or installer *could* horribly break your system if poorly written. You are trusting the authors of the installer to have considered that.
The debian package system is *specifically designed* to prevent many of the most common horrible-breakage scenarios.

I'm not sure how relevant all the different types of installations are. The install instructions at [https://www.jetbrains.com/idea/help/basics-and-installation.html](https://www.jetbrains.com/idea/help/basics-and-installation.html) seem fairly clear and offer you only one installation path. Backup your data, walk that installation path, and see where it takes you. The absolute worst case is that it doesn't work. Show us the error messages if it doesn't work.

---

### Post by kevdog on 2015-03-03
If you want to run a distro with a rolling release with the most recent updates than can be offered via a package manager rather than by source -- just run Arch.  There are not quite as many packages in their base release as their are in Ubuntu -- so even it depends on something called the AUR which is kind of analogous to Ubuntu's PPA system.  Even running something like Arch however is prone to breakage -- they change a core database and the entire system can go haywire.  Admitedly however almost anything is fixable if you have the time, patience, and know how how to search and ask appropriate questions.  As a trade off, you could run Ubuntu LTS.  Not quite as new version of packages, or the linux kernel, however I've never had the LTS version crash on me after an upgrade -- maybe I'm lucky but usually that is what you get when running an older version with older packages.  Critical security backports -- for example the OpenSSL with heartbleed -- were made available to the LTS version within 24 hours of discovery -- just slightly longer than something like Arch -- so really if there is a large bug, it's not like your not going to receive an update in a timely manner.  

In terms of compiling -- I'd just say try it.  I've done it many times from git sources.  It's kind of fun and personally I've never experienced breakage from a compiled package however I'm not compiling any core linux kernel stuff.  I'll admit however, that after awhile, it gets kind of old when the package author changes something major and then you spend a few hours researching what dependent packages are needed -- and then you have to compile these dependent packages -- which some of these need further compiled dependent newer packages -- round and round you go -- sometimes about 5 to 6 levels deep of compiling dependent packages just to make your new package run.  After a while you kind of just say forget it -- just let the package manager do it's thing.

---

### Post by Nosphky on 2015-03-03
I've a lot of sympathy for the questions of the OP.  I've been on linux for less than a year so I'm still finding out (slowly) how it all works.  I find a fair bit of frustration with less than latest packages so I decided to have a go at the ' ./configure/make/make install' stuff.

I was pretty lucky I suppose, that my first attempts did provide a good, working later version of a package for me. But what I also found was that my latest version got installed in /usr/local/....  part of the file system whereas the distro's not-quite-up-to-date version is installed in /usr/....  part of the file system (ie a level higher in the file system).   This did not seem to give me any grief or hardship so perhaps I just consider myself lucky.

My current frustration is connected with encryption software.  The ubuntu distros have the gnupg 1.4.xx original branch installed with the later more modular gnupg 2.0.xx package available to install from software center if needed, albeit not in the latest version.  The problem I have now in this area is that a 'modern' branch has been developed by gnupg : 2.1.x.  This modern branch introduces a significant new change : new encryption algorithms for elliptic curve cryptology and more and more users are moving to encrypting or just signing their emails with ECC.  This breaks the encryption cycle for the others still on 1.4.xx and 2.0.xx.

These advanced users are building their own from source or using an 'experimental' package from Debian.  I don't mind breaking my os so I've tried building on ubuntu but without success.  I guess I'm still not knowledgeable enough.   But given that the distros are still not up to the latest releases in the 1.4.xx and 2.0.xx branches of gnupg, I expect there is little hope that they will provide a gnupg 2.1.2 package any time soon.

---

### Post by jdeca57 on 2015-03-03
> **kevdog said:**
> If you want to run a distro with a rolling release with the most recent updates than can be offered via a package manager rather than by source -- just run Arch. 
I had some good experience with Manjaro, an Arch based distribution that has a user-friendly installer. In Arch you will have to do everything, Manjaro brings you to a desktop. The software follows Arch with a slight delay - they test it first on stability. And then you have the latest, the most bleeding edge software while remaining relatively stable.

---

### Post by buzzingrobot on 2015-03-03
> **garycheng12 said:**
> 

1. What does packaging an application for a specific distro's version entail? How is this different from a tar.gz file (or whatever type of file that is labeled as a "Linux" version) available from the application's website, which seems to always be as up-to-date as its Windows counterpart? Are applications labeled for "Linux" safe to use in any distro? Can applications from a specific distro and distro version ever be used in another Linux distro (as in it works, but not "optimized", whatever that means), or do they literally do not work? 

A "package" is a compressed archive containing multiple files, as is a ".tar.gz" file.  In addition, a "package" contains scripts and other tools that automate the correct installation of its components. Your Linux system contains a package manager that tracks the packages that are installed, is aware of newer versions available in the repositories your system uses and offers them as updates, and uses data embedded in a package to ensure that any other packages required by the specific package being installed are also downloaded and installed *or* issue an error message if something precludes that.

The repositories your system uses are listed in files in the /etc/apt directory.  Regardless of the tool you use to install packages -- Software Center, Synaptic, apt-get, etc. -- all packages are retrieved from one of those repositories.

In Linux, software distributed in ".tar.gz" format is most often uncompiled source code.  This format is primarily used by developers as a standard way of making their source code available to other developers. While a user can also expand the files in that archive and attempt to compile and install them, doing that requires knowing how to use the appropriate development tools, knowing how to identify and manually install any required dependent files, knowing how to install those compiled components in the correct locations in the file system, set correct permissions, etc.  In other words, the user is left to perform all the tasks that are handled by a typical Linux package manager.

In addition, software that is manually installed in this fashion is typically invisible to the package manager and, hence, will not be updated automatically.

That said, you may occasionally come across compiled executables that are distributed as ".tar.gz" archives. In my experience, these are very often simple attempts to port Windows games or drivers to Linux. They may be distribution-specific, or even specific to a particular release of a particular distribution.  You need to check them out before trying to install them.  And, again, your package manager will be unaware of their existence, leaving you to manually update them, if and when the develop provides updates.

Packages and package managers in Linux use two primary formats: "rpm" and "deb" packages. Ubuntu uses the "deb" format. "deb" packges cannot be directly installed on an "rpm" system, and vice versa.  A few tools exist that may, or may not, successfully convert the simplest packages from one format to another. (The scripts contained in a package are specific to that package type and are not rewritten by these conversion tools.)

So, the bottom line is to use and rely on your package manager to install, manage and update software.

> 2. Are there any distros that allow users to always have the latest (stable, same version as the website) application like in Windows? 

These are called "rolling release" distributions.  They make software available very soon after is is released by its "upstream" developers. (Arch is the most well-known rolling release.) These distributions also package their software, make it available on their repositories, and rely on their own package managers to handle installation and updates.

Inevitable trade offs exist between stability and the very latest software. It is simply impractical for Linux developers to test and maintain multiple versions of their software that work correctly on all of the hundreds of Linux distributions.  *The primary role of a distribution is to test, potentially alter,  and package software that is known to work correctly on that distribution.* 


> 3. I understand that a software center provides security for its users--packages that come from it has been through testing and are safe. Why do built-in updaters not exist or (or if they do, why are they not popular) as an alternative to the software center, since packages from the software center are generally not the latest versions available? 


Updaters do exist and are a function of the package manager.  Used correctly, they will update packages to the current version in that distribution's repositories. Whether or not these packages are the absolute very latest as provided by developers depends on many factors. It is pointless for a distribution to package and offer software that is so new that it is incompatible with the other components of that distribution.


> 6. ''... always preferring the latest stable version."

The word "stable" is crucial. In Linux, the very latest version is very often not intended to be stable.  It's typically intended to be used for testing and bug-discovery purposes. It is assumed that anyone installing that software is either a developer or a user who knowingly assumes the risks involved and wants to contribute to the development process.  


In the early years of Linux, package managers and such were not available.  Users were left with the tasks of building their software, then identifying and locating and building all the other software it depended on, and then doing the same thing for each of those dependencies, and on and on and on... This was clearly untenable if Linux was going to be something other than a plaything for a hardcore fringe. Package managers and packages were created for a reason. Use them. Fixating on the very latest developer releases very often is more trouble than it's worth.

---

### Post by ian-weisser on 2015-03-03
> **Nosphky said:**
> My current frustration is connected with encryption software.  The ubuntu distros have the gnupg 1.4.xx original branch installed with the later more modular gnupg 2.0.xx package available to install from software center if needed, albeit not in the latest version.  The problem I have now in this area is that a 'modern' branch has been developed by gnupg : 2.1.x.[...]But given that the distros are still not up to the latest releases in the 1.4.xx and 2.0.xx branches of gnupg, I expect there is little hope that they will provide a gnupg 2.1.2 package any time soon.

Looking at their release frequency, it seems unlikely that Debian or Ubuntu will ever be on the latest release.
And looking at the many bug reports for 2.1.2, it doesn't seem ready for Debian Testing nor Ubuntu quite yet.

This looks like a classic case of bleeding-edge.

And "they" are really "we". Debian participants, including Ubuntu users, test and fix and patch those new packages.

---

### Post by oldos2er on 2015-03-03
> **Nosphky said:**
> I was pretty lucky I suppose, that my first attempts did provide a good, working later version of a package for me. But what I also found was that my latest version got installed in /usr/local/....  part of the file system whereas the distro's not-quite-up-to-date version is installed in /usr/....  part of the file system (ie a level higher in the file system).   This did not seem to give me any grief or hardship so perhaps I just consider myself lucky.


This is done by design. You, the user, know that the apps in /usr/local/* were installed by you, outside of the package management system. Good configure scripts, not luck, are the reason.   :)

---

