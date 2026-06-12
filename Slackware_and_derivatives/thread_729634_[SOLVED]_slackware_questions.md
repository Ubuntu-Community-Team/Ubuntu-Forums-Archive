---
title: "[SOLVED] slackware questions"
date: 2008-03-20
forum: Slackware and derivatives
---

### Post by myusername on 2008-03-20
i have a few questions about slackware

do you have to write code for all the programs you use or can you use a package manager like synaptic?

does it use any binary packages like .deb?

how hard is it compared to arch?

is there any speed increases compared to ubuntu?

---

### Post by bonzodog on 2008-03-20
> **myusername said:**
> i have a few questions about slackware

*Do you have to write code for all the programs you use or can you use a package manager like synaptic?*
No, you do not need to write code of any sort. If however, you mean, compiling the programs yourself,(configure, make, make install), then you may have to do that with some of them. However, Slackware does have package management of a sort.

*Does it use any binary packages like .deb?*
Yes, it does. It uses the .tgz extension for them, and a lot of pre built progs can be found at linuxpackages.net, and slacky.it. However, it does not have a proper repo system as such, although GSlapt (a slackware version of Synaptic), does use a repository based around linuxpackages.net. Also, dependency resolution is very thin on the ground, although GSlapt has recently had this enabled, but it only works on packages that have the correct dep scripts with them.

*How hard is it compared to arch?*
I would say it is easier than arch in a lot of ways -- installation for one.
It uses the same bsd-like init scripts, but arch requires a little bit more work to get some programs configured properly. Arch however is far superior when it comes to package management, and I would dare to say that Arch's Pacman is actually superior to apt.

*is there any speed increases compared to ubuntu?*
um, yes, definitely. Arch and Slackware are a lot faster IMO than Ubuntu, due to the fact that generally, they tend to be more exact installs, as they give you package choices at install, and you can have a system that runs as light or heavy as you want it to be. Also, they both use 'vanilla' packaging, and vanilla kernels (ok, so arch does have a couple of small patches), which means unpatched, as the program developers intended them to be.

---

### Post by Junglizer on 2008-03-21
> **bonzodog said:**
> 
*Does it use any binary packages like .deb?*
Yes, it does. It uses the .tgz extension for them, and a lot of pre built progs can be found at linuxpackages.net, and slacky.it. However, it does not have a proper repo system as such, although GSlapt (a slackware version of Synaptic), does use a repository based around linuxpackages.net. Also, dependency resolution is very thin on the ground, although GSlapt has recently had this enabled, but it only works on packages that have the correct dep scripts with them.


I would agree with you on all except for this point. 

To clarify .tgz is simply a form of compression, similar to .rar or .zip as one would find on Windows. The compiling of source as previously mentioned would be the most common way to install programs, and said source code is usually packaged in <filename>.tgz like packages.

---

### Post by myusername on 2008-03-21
so i would install things by extracting them and running ./programname ?

---

### Post by Junglizer on 2008-03-21
> **myusername said:**
> so i would install things by extracting them and running ./programname ?

Common procedure would be as such:

Extract file from gunzipped tarball: ```
tar xvf <file>.tar.gz
```
This should then create a folder with the same name, which you should then enter: ```
cd <filename-directory>
```
From here, if you list the contents ```
ls
``` you should see several files, one of which is named 'configure'

Use this to check and make sure you have the requirements to install the program using the following: ```
./configure
``` (./ is execute or run) After that runs through a checklist it should put you back to your regular shell prompt. From here you will want to compile the program which can be done with ```
make
```
Finally you'll want to 'install' the program, or rather copy the right executable files and system files to the right locations within your system. This final step needs to be done as root if you've done the previous as your regular user: ```
make install
```

You can then safely delete the <filename-directory> as well as the <file>.tar.gz as the program has been compiled and installed onto your system fully.

---

### Post by saulgoode on 2008-03-21
> **Junglizer said:**
> I would agree with you on all except for this point. 

To clarify .tgz is simply a form of compression, similar to .rar or .zip as one would find on Windows. The compiling of source as previously mentioned would be the most common way to install programs, and said source code is usually packaged in <filename>.tgz like packages.

Slackers discourage the use of .tgz as a synonym for .tar.gz -- the .tgz extension is reserved for Slackware packages, which contain a package description and post-installation script (along with all of the binary files). Almost everybody honors this convention.

I haven't seen .tgz used for generic gzipped tarballs since the days of Minix, when the practice was a bit more common owing to the DOS-inspired 8.3 filename limitations.

---

### Post by Junglizer on 2008-03-21
> **saulgoode said:**
> Slackers discourage the use of .tgz as a synonym for .tar.gz -- the .tgz extension is reserved for Slackware packages, which contain a package description and post-installation script (along with all of the binary files). Almost everybody honors this convention.

I haven't seen .tgz used for generic gzipped tarballs since the days of Minix, when the practice was a bit more common owing to the DOS-inspired 8.3 filename limitations.

Yeah you're right I must have just misread it. But you'll still be compiling from source if you're adding something, well more then likely, I've never been much for the Slackware package-managers. Mostly b/c I don't need too many programs out of the default install for whatever I'm using the box for.

---

### Post by Bachstelze on 2008-03-21
Moved to the Slackware subsection.

---

### Post by tommcd on 2008-03-25
> **myusername said:**
> so i would install things by extracting them and running ./programname ?

A great place to get extra software for Slackware is [http://slackbuilds.org/](http://slackbuilds.org/). These are build scripts that allow you to convert source code packages to Slackware .tgz packages that you can install with "installpkg package_name.tgz". I have used a few of them to compile programs for Slackware on my laptop and they work very well. Read the how to: [http://slackbuilds.org/howto/](http://slackbuilds.org/howto/) It is not hard to do at all.

---

