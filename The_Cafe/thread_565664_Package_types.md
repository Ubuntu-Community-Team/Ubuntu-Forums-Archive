---
title: "Package types"
date: 2007-10-02
forum: The Cafe
---

### Post by Puppy fam on 2007-10-02
So in Ubuntu if you were not to use apt-get and you were to go off onto the Internet and download a .deb package. When you opened it there would be an installer that would install it for you (graphical installer). This is the same for .package types. So in other distros is it as easy for you to install packages (not in the add/remove program)?

Why I am asking is if it was this way a programmer then could just make one file type and any Linux distro will be able to install it very easily without going through the command line. Or is Ubuntu special with the .deb and .package installers?

But lets say that there is not a package type that would work on any distro, Won't it be good to have one? Then a Linux noobie on any distro could (if a program is not in their add/remove program) be able to download and install any Linux program without having to go into the command-line to install it.

Could someone help me understand?
-Puppy fam (please talk in English, I am very new to Linux)

---

### Post by jrusso2 on 2007-10-02
> **Puppy fam said:**
> So in Ubuntu if you were not to use apt-get and you were to go off onto the Internet and download a .deb package. When you opened it there would be an installer that would install it for you (graphical installer). This is the same for .package types. So in other distros is it as easy for you to install packages (not in the add/remove program)?

Why I am asking is if it was this way a programmer then could just make one file type and any Linux distro will be able to install it very easily without going through the command line. Or is Ubuntu special with the .deb and .package installers?

But lets say that there is not a package type that would work on any distro, Won't it be good to have one? Then a Linux noobie on any distro could (if a program is not in their add/remove program) be able to download and install any Linux program without having to go into the command-line to install it.

Could someone help me understand?
-Puppy fam (please talk in English, I am very new to Linux)

Often there a dependency's that have to worked out when you install a package.  And different distros put them in different places and their are different versions of the libraries.

---

### Post by happysmileman on 2007-10-02
> **Puppy fam said:**
> So in Ubuntu if you were not to use apt-get and you were to go off onto the Internet and download a .deb package. When you opened it there would be an installer that would install it for you (graphical installer). This is the same for .package types. So in other distros is it as easy for you to install packages (not in the add/remove program)?

Why I am asking is if it was this way a programmer then could just make one file type and any Linux distro will be able to install it very easily without going through the command line. Or is Ubuntu special with the .deb and .package installers?

But lets say that there is not a package type that would work on any distro, Won't it be good to have one? Then a Linux noobie on any distro could (if a program is not in their add/remove program) be able to download and install any Linux program without having to go into the command-line to install it.

Could someone help me understand?
-Puppy fam (please talk in English, I am very new to Linux)

Depends entirely on the distro, ".package" is supposed to be a standard, and most distros will work with it, though a few (especially the not-so-popular ones) won't work with it.

I'm not too sure about why DEB, RPM etc... all exist, but it seems to be difficult to install a DEB file onto a distro that uses RPM.

If you make a ".package" file it should be supported by most, adn all distros could easily installer whatever is required for it ias it is distro-neutral.

---

### Post by SunnyRabbiera on 2007-10-02
well here on PCLinux I use kpackage, of course despite it being a rpm based distro we have basically the same setup here as ubuntu as we have synaptic and apt.

---

### Post by az on 2007-10-02
> **Puppy fam said:**
> Won't it be good to have one? 

Not really.

The best of the best would be for the source to be available to anyone and for your distro to do the work of providing you with binaries.

GNU/Linux is not binary-compatible.  That means that something compiled for one distribution would not automatically work for another.  It *is* source-compatible, though and that's the key to why this software is here and so great.

Binary-compatibility is a detriment to development.  When things are made as simple as they can be for others to contribute, you get the maximum out of your development pool.  

Binary-compatibility also removes your right to chose.  For example, if you take a look at what binary-compatibility has done for MS Windows, it is the sole reason why you can't ever fix the vulnerabilities that are exploited by viruses, and that the only way to deal with it is to scan for them.

Binary-compatibility has led to Sun Solaris to offer very poor performance.  Solaris guarantees backward-compatibility for all it's applications.  It is impossible to provide software that will perform competitively if you have that handicap (When Dapper was released, the version that ran on the new Sun Niagara servers was, by far, the OS which offered the best performance.)

Many have tried to implement some sort of binary-compatibility on Linux.  Just look up Autopackage.  Autopackage has not taken GNU/linux by storm, simply because it requires all of upstream to write their code using autopackage's libraries and you will never be able to oblige free software to do something like that.  Not to mention that very few people would see the benefit of autopackage.

The benefit of source-level compatibility is that everyone has the right to chose what software they install and run.  Sure, it's more complicated, but you can't argue that browsing the internet and installing third-party applications on your machine is a sane way to keep your computer safe.

Your distribution is what provides you with the layer of security, only providing you with apps which have a sound security history.

---

### Post by Puppy fam on 2007-10-03
Thank you for helping me understand!

---

