---
title: "Ubuntu versus Arch terminal syntax"
date: 2018-06-11
forum: Ubuntu, Linux and OS Chat
---

### Post by scotrod on 2018-06-11
Hello,

 im 2-3 months Linux newbie that is still learning the curves and i'd like to give Arch Linux a try. I want to ask if the terminal syntax is the same on both OS. Same for working with programs inside of the terminal, are the commands the same?

Thanks.

---

### Post by spjackson on 2018-06-11
Welcome to the forums.

By and large, for most purposes, yes the syntax is the same: both use bash by default. The main difference is package management where Ubuntu uses apt/dpkg and Arch uses pacman. There may be some more differences in the area of querying/manipulating the system.

---

### Post by grier-devon on 2018-06-12
> **spjackson said:**
> Welcome to the forums.

By and large, for most purposes, yes the syntax is the same: both use bash by default. The main difference is package management where Ubuntu uses apt/dpkg and Arch uses pacman. There may be some more differences in the area of querying/manipulating the system.
  
+1

Package management should be it, so you would just have to learn how to use Pacman and if you decide to enable yaourt for community repositories, which I do recommend. Bash uses the same syntax across any OS which ships the product. Two other differences you may experience depending on how deep you dive into the command line and Arch is terminal application and file systems. 

So syntax will be the same but Ubuntu may use different command line utilities to complete the same task, in those cases you learn to use the command line utility that Arch has or just install the one that Ubuntu uses. An example of this is Ubuntu might ship a command line text editor called Nano and Arch may opt for Vim instead. You can either learn Vim or just install Nano. Disclaimer - This is just an example, I believe they both ship Nano but just wanted to use something I could think of which I have found in different distributions.

Secondly, file system. Since Arch is pretty much a custom install you decide this yourself but if you go with something different then Ubuntu's filesystem you may notice your root directory looking a little different.

Other then that, should be good.

---

### Post by nik.charles on 2018-08-26
For package managers, Arch wiki has a cross-reference list of commands

[https://wiki.archlinux.org/index.php/Pacman/Rosetta](https://wiki.archlinux.org/index.php/Pacman/Rosetta)

If you want to learn about Arch and Linux in general, you may like ArcoLinux for a structured learning process

I have been using Manjaro for few years now. Easier way to get a working Arch-based system whilst still learning terminal commands

---

