---
title: "Compiling from the sources VS installing from a Personal Package Archive?"
date: 2015-05-23
forum: Ubuntu, Linux and OS Chat
---

### Post by remmas-sido on 2015-05-23
Hello guys 
I want your opinions on this specific subject. Which one you think is better? Which one you think is safer? Which one suits you better? What are the upsides and the downsides of each one of these two options?

---

### Post by hakermania on 2015-05-23
**Installing from source**:

Pros:
[LIST]
[*]Providing that you got the source from the official place, you know that it has not been altered.
[*]You can get the latest available version of the program easily. The official repositories are usually some versions behind the PPAs and the PPAs are behind the official source until they catch up.
[/LIST]
Cons:
[LIST]
[*]It takes much more time for the installation to complete, depending on how large the source code is and how much time it takes to compile.
[*]It usually requires installation of extra development libraries.
[*]It is a more technical way to install things, as it requires some knowledge of the terminal, like how to build from source using the 'make' command, how to read and interpret the error messages etc.
[*]It rarely comes with a scipt to uninstall things. 'make uninstall' should do this, but the uninstallation rule rarely is available. This leaves you with only one option in case you want to uninstall the software: search and manually remove the installation files. This usually ends up with you not deleting all your files and trash remaining inside your system.
[/LIST]

**Installing from a PPA**:

Pros:
[LIST]
[*]Easy way to keep up with the latest versions of programs.
[*]It's an install it and forget it thing. As new updates come into the PPA, they automatically appear on your manual software upgrades.
[*]They are easy to remove. The installation of a program through a PPA follows the same route as the installation of a program from the official software sources, so it comes with a DEB package which is easily uninstallable. The PPA itself can easily be removed from the graphical interface of the corresponding programs (i.e. Ubuntu Software Center for Ubuntu or Software Manager for Mint)
[/LIST]
Cons:
[LIST]
[*]You cannot always trust the publisher of the PPA. The publisher of the PPA can tamper with the official code and include their own malicious code. So you must be 100% sure that you trust the PPA's publisher. This isn't true for the official repositories and the official sites of the software, as the code there is being monitored in some level.
[*]The more PPAs you install, the more slower the update and upgrade progress gets. PPAs are generally installed through Launchpad which, from my experience, is much slower than the official servers.
[/LIST]

---

### Post by ajgreeny on 2015-05-23
Apart from having to compile and install ndiswrapper in 12.04 in order to get it to work some time ago for my old laptop, and using the latest version of hplip-3.13.8.run to automatically compile and install the latest version of hplip needed for a new printer I had, I have never needed to compile anything, nor do I believe that the system speed advantage that some speak of is worth all the extra bother.

In order to keep up-to-date I do use several PPAs, none of which have ever caused me any problems.

If you're going to do that all the time why not install gentoo or arch in the first place?  You will then see the BIG advantage of using a system that has pre-compiled packages.

---

### Post by Rob Sayer on 2015-05-23
I don't have a lot to add to the above answers except to say that I don't recommend either method to beginners unless there is absolutely no other way to do what ever it is you want with something that's in the tested repos.

If you want to play around, fine, no problem.  But I'd recommend doing that if you have more than one linux box.  Keep one vanilla and stable.

---

### Post by wildmanne39 on 2015-05-23
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by monkeybrain20122 on 2015-05-23
ppas are more convenient and software is usually automatically updated. Use the big and well known ones and the ones maintained by the developers , they are safe. Another thing is choose ppas for applications that don't have a lot of dependencies so you won't upgrade a whole bunch of things Finally ppa-purge is a handy tool if anything goes wrong and you want to roll back the packages.

Compile when there is either no ppa for the version (and be older or newer) or features you want. Ubuntu builds sometimes disable some features you may want.

---

### Post by monkeybrain20122 on 2015-05-23
> **Rob Sayer said:**
> 

If you want to play around, fine, no problem.  But I'd recommend doing that if you have more than one linux box.  Keep one vanilla and stable.

I think that is unnecessarily cautious, unless you are using test builds for system components.

---

### Post by kevdog on 2015-05-24
Honestly I think learning how to compile a program from source and stepping through having to shag down various developmental libraries is actually a very good exercise into learning how things work within linux.  I'm not saying it should be done regularly, however there are many programs that are really fun to try out, and the ability to pull them from a git archive, compile them and try them is really fun. One example of this would be the end-to-end google chrome extension.

---

