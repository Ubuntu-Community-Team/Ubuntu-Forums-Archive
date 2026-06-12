---
title: "why can't they use bin files as universal distro install files?"
date: 2009-06-14
forum: The Cafe
---

### Post by Dustin2128 on 2009-06-14
a ***lot*** of linux software is put in bin files, like google earth, regnum online, ect. why isn't that the universal linux install file. also, a good thing for 9.10 would be to have a terminal macro that automatically executes the bin file, rather than chmod +x bin.bin, ./bin.bin

---

### Post by Mehall on 2009-06-14
You mean like running the following instead:

sh bin.bin

?

Go on, try it.

---

### Post by jonian_g on 2009-06-14
Make it executable, rename it to .sh and double click it. I think that using .bin files is not good because it needs user interaction during the install, while deb and rpm are more "automatic".
Also there is no way for bin installers to install dependencies, thats why all the dependencies are bundled into bin installers, but this will make programs take more disk space like in windows.

---

### Post by MikeTheC on 2009-06-14
I just don't get why you folks have problems with how things are handled now. Distro maintainers serve as a very good filter and screen for so many other potential problems. The route your talking about is basically a means of shortcutting that process.

---

### Post by MaxIBoy on 2009-06-14
> **MikeTheC said:**
> I just don't get why you folks have problems with how things are handled now. Distro maintainers serve as a very good filter and screen for so many other potential problems. The route your talking about is basically a means of shortcutting that process.+1

Also, binary files don't handle dependencies.

Finally, binary files are a bit more "unsafe," although admittedly not by a big margin.

---

### Post by perce on 2009-06-14
Because all deb packages installed in your computer are indexed so that whatever package manager you use always knows what is installed. This makes easier to handle dependencies, upgrades and uninstalling software. Installing programs in the Windows way would make Linux a mess as Windows is.

---

### Post by markharding557 on 2009-06-14
> **Dustin2128 said:**
> a ***lot*** of linux software is put in bin files, like google earth, regnum online, ect. why isn't that the universal linux install file. also, a good thing for 9.10 would be to have a terminal macro that automatically executes the bin file, rather than chmod +x bin.bin, ./bin.bin

because .deb is a better,safer and allows the removal of dependencies in an automated way

---

### Post by Firestem4 on 2009-06-14
Generally a good packaged .bin file includes an uninstall script that removes *all* files that were installed by the binary in first place. Savage2 includes an uninstall script that does this.

---

### Post by MaxIBoy on 2009-06-15
Picture this:

Program X, which is written in the Befunge programming language, naturally requires a Befunge interpreter. It also requires the SDL, Ncurses, and openAL bindings for the Befunge programming language. 

You install program X using the .bin installer. Program X then fails with an error. You Google your error, and discover that the error results from the fact that you need the SDL bindings for Befunge. You install those using a .bin program, and try program X again. Now you get a different error, which results from the missing Ncurses bindings. Repeat until program X now works.

After a few days, you no longer need program X, so you uninstall it. You then forget all about it.

A few years later, you're running low on disk space, mostly due to a bunch of decencies you don't need anymore anyway. You figure out that this is probably true, but you don't know which programs you should uninstall and which ones you should keep. Sure, the .bin programs all left uninstaller utilities, but you don't know which ones can be safely uninstalled.

Or, in yet another scenario, program X required a *newer* version of an *already-installed* library, but you didn't know that it was already installed. The error you get might make it seem like it was not there to begin with, even though it was. So when you remove program X, you uninstall this library, and wind up breaking half the programs on your system. For example, a naive user might get an error involving libc6, and conclude that he doesn't have libc6 installed. He will then download and install the latest version of libc6. For the sake of an argument, we'll assume that this new version of libc6 is backwards compatible and doesn't break his system when he installs it (not always true.) Now the program works, but when this user removes it, he thinks it's safe to remove libc6 as well. In fact, if you remove libc6, you're in very, very deep trouble.

Or alternately, maybe you diligently removed all those libraries you didn't need anymore, and nothing bad happened, but it took a few minutes of your precious time-- who really wants to deal with that?

---

### Post by H2SO_four on 2009-06-15
> **markharding557 said:**
> because .deb is a better,safer and allows the removal of dependencies in an automated way

+1 for .deb.  Much easier

---

