---
title: "How to quickly find out which packages are causing the partial upgrades?"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prusswan on 2012-02-16
I would like to learn how to check on the build progress of those packages, like some are evidently capable of doing from time to time :p

---

### Post by xajeiw9I on 2012-02-16
When I do a "apt-get upgrade", it shows that 28 packages were not upgraded. Does it mean they have problems with broken dependencies, like they need newer packages that are only coming in the future? I did a dist-upgrade previously that broke things like the Software Center, but I managed to reinstall it after some regular upgrades.

I am wondering if these packages are still broken or if this is normal. "apt-get check" doesn't detect any broken dependency.

---

### Post by ratcheer on 2012-02-16
When I have these kinds of questions, I run the aptitude application. It divides the updates into several categories, including one called "Upgradable Packages" or something like that. Click on the category and it will show a list of packages that are waiting to be upgraded. Then, in that list, each package can be clicked and it will show you what other packages it is waiting for, and why.

Since I do not have any packages waiting right now, I cannot show you examples. Just run "aptitude" from the command line with no parameters.

Tim

---

### Post by grahammechanical on 2012-02-16
I have just booted and coming to Ubuntu+1 is the second thing that I have done. The first thing I did was to run Update Manager. I ignore the offer of a partial update. I do not always get this dialog but I always ignore it when I do get it.

In Update Manager is a list of Distribution Updates and Other Updates (LP-PPA-unity-team). Some of these packages have a tick mark against them and would download if I clicked Install Updates. Other packages do not have a tick mark against them. These packages are not yet ready to be part of the Update but they will come.

So, I now know that in a day or two there will be an update to Compiz, Unity 2D, another update to the Linux kernel, Gnome Control Center and other stuff.

Installing the packages marked for updating will not break my system. I am confident of that. Running the partial update most likely will damage my system because the update will fail to find those packages that are not marked for update.

Regards.

---

### Post by prusswan on 2012-02-16
> **ratcheer said:**
> When I have these kinds of questions, I run the aptitude application. It divides the updates into several categories, including one called "Upgradable Packages" or something like that. Click on the category and it will show a list of packages that are waiting to be upgraded. Then, in that list, each package can be clicked and it will show you what other packages it is waiting for, and why.

Since I do not have any packages waiting right now, I cannot show you examples. Just run "aptitude" from the command line with no parameters.

Tim

yes, I can see which packages are being held, but for what reasons? that's what I am interested in

---

### Post by prusswan on 2012-02-16
> **grahammechanical said:**
> 
Other packages do not have a tick mark against them. These packages are not yet ready to be part of the Update but they will come.


I am interested in this part, it seems that sometimes people know exactly which dependent package is still building in progress, and I wonder how they figure that out

---

### Post by xajeiw9I on 2012-02-16
So, those packages that are marked for "not upgrading" are just packages that are going to be upgraded soon, and not a problem caused by broken dependencies?

---

### Post by cariboo on 2012-02-16
You can search Launchpad for the status of packages.

---

### Post by effenberg0x0 on 2012-02-16
NOTE: Most users know this but since partial updates are a frequent issue, less informed users that land here on a search might find this post useful.

**WHAT ARE DEPENDENCIES - WHY DO THEY BREAK - WHY ARE PACKAGES "ON HOLD"?**
When you create a program using a programming language (let's say C, for example) usually you won't create functions for all the tasks it will perform from scratch. Read config files, display something on screen, interact with other programs, make a sound, etc. It would not be productive to code everything every time you program. So you can use pre-made functions that were coded by other people to perform specific tasks. These pre-made functions are coded considering performance, stability, etc and tested extensively, so a programmer would take a lot of time to reach such good coding from scratch. Most of the times it's easier and safer to use them. 

Let's say I want my program to read it's configuration from a XML-formatted config file in the user home directory or from /etc/some-config-file.conf. I can make my program load another file, coded by another programmer, which has a set of functions specialized in reading and writing to XML files.  

In Unix/Linux, this is referred to as "using shared libraries" and libs usually have their name starting with lib and ending with .a or .so. Like libxml.so (another fictitious example). Take a look at your /lib or /usr/lib and you'll find many libs there.

The problem is: When I developed my program and decided to use the xml lib, I looked at the lib specifications carefully and developed my code in a way to _exactly match_ those specs. Doing so, I can be sure that as long as my program is run is an OS that has that exact same lib, it will work exactly as I coded it to. That lib now became a _dependency_ to my program: My program does not work without it, it depends on it. If a user installs my program, hopefully his OS software manager will also download the required xml lib (if he doesn't already have it installed). Otherwise he will have to get and install that lib manually or he wont be able to use my program.

However, libs are also under development and so they change, they get fixed and improved by other developers and the community: New versions of it are released. But if my program was designed to the specs of the xml lib version 1.0, will it work exactly as I want it to with libxml 1.1? Probably, but, in reality, results are unpredictable until I test it, compare the new version of the lib to the old and sometimes even debug it. My program may succeed with working with different versions of the library, but it might also fail just as well. 

Another (more) common issue: What if I update my program to work with the libxml 1.1, but Operating Systems like Ubuntu are still distributing libxml 1.0? If my program relied on features of versions 1.1 which are not present on 1.0, we can definitely have a crash there. 

To avoid such confusion and potential breakage, the notion of "dependency" is extended to also include versions. So programs not only depend on other programs and libs, but on specific versions of them. So I can say that version 1.0 of my program depends on version 1.0 of libxml and that version 1.1 of my program depends on version 1.1 of libxml, but version 1.1 of my program will not work with version 1.0 of libxml. 

What if I update my program to work with the specs of version 1.1 of the xml lib and release it to Ubuntu, but Ubuntu still doesn't have version 1.1 of the xml lib in its repositories? Then dependencies for my program are now broken. So, the new version of my program is now a package on hold, until lib xml 1.1 becomes available and replaces lib xml 1.0. If you force apt-get/aptitude, etc and update my program to the new version, it might work, as well as it might not work - it's unpredictable, as I said previously.

What if the developers of the fictitious libxml lib decide they will wait a couple days before releasing the code for libxml 1.1, because they are too busy testing it, because the main developer got the flu, etc? Well, version 1.1 of my program will continue on hold. Until the code for its dependencies is released by its developers and until packagers get that code, transform it into Ubuntu packages and upload them so they become available on Ubuntu repos, dependencies are broken for MyProgram v1.1. 

OBS: This was a _very_ simplistic example. Is a modern Operating System, I  actually _have to_ use some libs if I want to interact with certain  OS processes. Many programs use a lot of libs and keeping track of dependencies is complex. 

[B]HOW TO CHECK DEPENDENCIES FOR A PROGRAM?
[/B]```
dpkg -s <package>
```
It will show you all dependencies of that program, the versions needed and if the package is installed, half installed, etc.
Another command of interest for this issue:
```
dpkg-query -s <package>
```
Will show you brief status information about a package.

Regards,
Effenberg

---

### Post by ratcheer on 2012-02-23
> **prusswan said:**
> yes, I can see which packages are being held, but for what reasons? that's what I am interested in

I think I said to click on a package that is being held, then it will open up with more info about why it is being held. Actually, I guess you need to double-click it to open it up.

However, I am getting a GUI display of aptitude in Precise (which I just now installed). I am used to getting an ncurses display. I do not really understand the GUI display, yet, and I am unsure whether it provides all the info I am used to seeing.

Tim

---

