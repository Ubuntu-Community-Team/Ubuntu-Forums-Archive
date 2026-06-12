---
title: "The idea behind using Linux repositories"
date: 2007-07-24
forum: The Cafe
---

### Post by fd9_ on 2007-07-24
Although I feel like I've read a lot about how to use repositories, I guess I sort of don't completely understand them. The Ubuntu documentation leaves some questions unanswered, such as:

1) What's the advantage of downloading program X from a repository versus downloading it from the developer's website, when I can get the newer version by downloading from the website?

2) Why are some programs, such as VirtualBox, not listed under any repository (main, universe, or otherwise)? 

3)  What's the advantage of adding a third-party repository? For example, VirtualBox is one example of a program that does not exist in any of the other repositories, but I can add it's own repository to my list. Does that mean I will automatically receive updates for it when they become available?

4) How do new Linux programs get added to the main and/or restricted repositories? In other words, how does it officially become supported by Ubuntu? Does it have to go through a rigorous testing cycle, and if so, by whom?

5) What are authentication keys? Is it similar to an MD5 checksum, or does it have to do with security?

---

### Post by DeadSuperHero on 2007-07-24
It's the difference between getting a book from an author, and going to the library to get it.

With repositories, the "author" can put his product in the "library" of information, thus giving it a better chance of getting it out to people. Also, it gives a nice uniform way of installing things, in a very simple manner.

---

### Post by eentonig on 2007-07-24
I don't think that's the main benefit for using the repo's.

The main benefits I see.

- Easy to find and install applications (apt-cache search or Synaptics search function)
- All applications are compiled, packaged to work for this specific distribution. All needed dependencies are configured automatically. So it's usually a lot easier to install from the repo then it is from the author's website.
- Applications from the repo's are actively being monitored for updates that become available in the repo. If an update is present, it gets installed semi-automatic. I don't have to waste time searching to see if application X has a newer version available.
- Safety. Applications in the repo's are trusted to be virus/trojan free. 


Benefits of adding repo's:
The same as above but for the applications provided by that repo.

Downsides of adding repo's:
Your trust is only as good as you can vouch for the repo's owner.
Downsides

---

### Post by KIAaze on 2007-07-24
> **fd9_ said:**
> 
1) What's the advantage of downloading program X from a repository versus downloading it from the developer's website, when I can get the newer version by downloading from the website?
-Automated updates.
-Easy installation/removal/administration
-Security

> **fd9_ said:**
> 2) Why are some programs, such as VirtualBox, not listed under any repository (main, universe, or otherwise)? 
I don't know. Maybe because it has a double license (proprietary/GPL).
But I don't see why the GPLed version shouldn't make it into the reositories.
QT libraries are in the repositories after all...

> **fd9_ said:**
> 3)  What's the advantage of adding a third-party repository? For example, VirtualBox is one example of a program that does not exist in any of the other repositories, but I can add it's own repository to my list. Does that mean I will automatically receive updates for it when they become available?
As far as I know, yes.
And even if it's not fully automatic, you can update manually more easily.

> **fd9_ said:**
> 4) How do new Linux programs get added to the main and/or restricted repositories? In other words, how does it officially become supported by Ubuntu? Does it have to go through a rigorous testing cycle, and if so, by whom?
Only the [Masters of the Universe]("https://wiki.ubuntu.com/MOTU") have the power to add packages to the official repositories. :D
So if you want to add a package like VirtualBox to the repositories, you have to contact a MOTU.
Here's how to proceed:
[https://wiki.ubuntu.com/MOTU/Packages/New]("https://wiki.ubuntu.com/MOTU/Packages/New")

> **fd9_ said:**
> 5) What are authentication keys? Is it similar to an MD5 checksum, or does it have to do with security?
No, it has to do with security.
Google for PGP and public/private keys systems to learn more.
MD5 checksums only check the integrity of downloaded files. (and they are used too for packages from the repositories)

Basically, with a public/private key authentication, you can make sure a file comes from the correct person.
With an MD5 checksum, you just check that it hasn't been damaged.

---

### Post by Jucato on 2007-07-24
1. Why use **Ubuntu's** repositories?
- Ease of software management: all dependencies, that is, the other packages that a program needs in order to run, are checked and installed automatically, no need to hunt them down; automatic updates; security updates and patches specific for Ubuntu.
- Stability: built and tested to run on a specific distribution and release
- Security: built and distributed by official Ubuntu packagers (related to questions 4 and 5)

2. Why is this package not in the repositories?
- The most common reason is that because no one has simply packaged it yet, and until someone volunteers to take responsibility for that package, it will remain unpackaged. Kinda harsh, but that's how it works. We're all volunteers in this world.
- It's illegal to distribute in some countries. This is the situation with w32codecs and libdvdcss. But this is not the reason while VirtualBox isn't included. More probably, it's because of the first.

3. The advantage of a 3rd-party repository...
- Most probably, more recent versions. Sometimes, Ubuntu lags behind the most recent version a bit, like in WINE. Sometimes, Ubuntu catches up after some time, through other "semi-official" repositories, like -backports and kubuntu.org
- faster updates to the most recent versions, depending on the 3rd-party packager

There are some disadvantages, of course:
- The latest and greatest has a possibility of breaking your system if untested to work on a particular distribution and release
- You have to trust the owner of the repository (question #5)
- It can mess up the stable dependencies of packages, leaving you with a broken system. (It has happened)

Not that I'm discouraging 3rd-party repositories, but always exercise caution. Try to determine if you really need the latest version before adding repositories left and right.

4. Adding packages to repositories
KIAaze is only half right. You see, there are 4 official repositories, which can be grouped into two, depending on who packages them and whether they are officially supported by Ubuntu **and** Canonical or whether they are just supported by the Ubuntu community.

main and restricted comprise the first group, supported by Ubuntu/Canonical. Only the core developers (core-devs) can upload/add/remove to this repository. universe and multiverse are the community packages, and the MOTU are the ones responsible for maintaining them (of course, core-devs are also able to do so). While only these 2 groups of packagers/developers have the ability to add/remove from repositories, anyone who is able to make a package can have his package sponsored and uploaded to the repositories.

5. Authentication keys.
- basically the answer KIAaze gave cover it. :D

---

### Post by forrestcupp on 2007-07-24
About the repository version not being as up to date as the developer's website, that's what 3rd party repos are for.  You can't just trust anyone's repository, but some can be trusted.  For instance, the Feisty version of Wine is not as up to date as the one on winehq.org.  So if you want to install the latest from them, you go to the Get Wine Now section.  Guess how you get it.  They tell you how to add their 3rd party repo, and you'll always have the latest Wine.

Most (but not all) reputable projects will have some kind of repo for you instead of just having you download a file.  Especially if you use a popular distro like Ubuntu.  This makes it easier to keep up to date.

---

### Post by az on 2007-07-24
> **fd9_ said:**
> Although I feel like I've read a lot about how to use repositories, I guess I sort of don't completely understand them. The Ubuntu documentation leaves some questions unanswered, such as:

1) What's the advantage of downloading program X from a repository versus downloading it from the developer's website, when I can get the newer version by downloading from the website?

2) Why are some programs, such as VirtualBox, not listed under any repository (main, universe, or otherwise)? 

3)  What's the advantage of adding a third-party repository? For example, VirtualBox is one example of a program that does not exist in any of the other repositories, but I can add it's own repository to my list. Does that mean I will automatically receive updates for it when they become available?

4) How do new Linux programs get added to the main and/or restricted repositories? In other words, how does it officially become supported by Ubuntu? Does it have to go through a rigorous testing cycle, and if so, by whom?

5) What are authentication keys? Is it similar to an MD5 checksum, or does it have to do with security?

1)  Free-libre open source software is not binary-compatible software.  It's compatible on the source level.  That means that you cannot download a binary (in windows, a binary is an exe, for example) and run it on any linux system.  The advantages of source-level compatibility versus binary-compatibility are that the development is a lot easier to do.  There are also security advantages as a by-product.

Can you get the newest version directly from upstream?  Probably, but there is no guarantee that it is properly built for your distro.

Your distro is responsible for providing you with binaries and security updates/bugfix updates.

2) in order for a package to be in the repos, it needs a maintainer.  No one has yet offered to maintain virtualbox.

For a package to be in the main or universe repos, it must be DFSG-compliant (Debian free software guidelines - basically GPL-compliant)  For it to be in the multiverse repo, it must be redistributable.

For a person to be able to maintain a package, they must go through a rigorous process.  Not just anyone can upload a package to the archives.

3)  Yes, but there is no guarantee that they will work.  See above.

4)  It has to be licensed appropriately and someone has to want to maintain it.

5)  Authentication means that you are you.  A signed package means that the files that were uploaded are indeed from the person who they say they are from.  Using cryptography, this is a very reliable way of knowing that.

You cannot create a package and claim it is an official package unless you are able to cryptographically sign the package.  This assures the user that they are downloading the packaged from a trusted source.

---

