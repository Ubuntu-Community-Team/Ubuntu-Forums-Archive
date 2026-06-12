---
title: "Guest additions  in Virtualbox"
date: 2019-07-09
forum: Virtualisation
---

### Post by oilyfish on 2019-07-09
SOLVED

[LIST]
[*]Run the Windows VM
[*]click "Devices" -> "Install Guest Additions..."
[*]click "Run VBoxWindowsAdditions.exe", click on stuff to install the stuff
[/LIST]

I was trying to  install guest additions  outside the VM environment

---

### Post by TheFu on 2019-07-09
You are really new to Linux.  You don't know what you don't know at this stage, but you are learning in an effective, if not efficient, way.
yum is the package manager for Redhat-based distros. It isn't used by Debian or Debian-based distros like Ubuntu.

There are multiple versions of virtualbox, so you should install the same version of the guest additions into the client VM as the hostOS is running.  There is also an extensive User's Guide for VirtualBox.  [https://www.virtualbox.org/manual/ch01.html](https://www.virtualbox.org/manual/ch01.html)  

When describing issues with virtualization, please try to be extremely clear about what is happening on the hostOS and what is happening inside the GuestVM.  I can't tell which crashed your system or where you were trying to install guest additions. It isn't clear and I don't want to assume the expected answer, head down the wrong path for 3 days only to find it was a bad assumption.

I have no idea what you mean by "Perl driver modules" - and I'm a perl developer.  Perl has NOTHING to do with virtualbox.

Be careful following instructions from random sites online.  If you are working in Ubuntu, then it is best to follow Ubuntu-specific instructions.  Also recommended to search by the exact release you are running too.

While we're here, probably best to stress that people new to Ubuntu should run the current LTS release, 18.04.x and not newer releases.

APT is the package manager for Debian systems.  There are a few different front-ends to it - apt, apt-get, aptitude, synaptic, ... probably a few others. These are just front-ends, so, in theory, they will have similar outcomes for installing/removing packages.

BTW, searching for guides/how-tos online, it is best to include "ubuntu" in the search.  If that doesn't find something relevant, use "linux"  --- so "linux yum" would find lots of stuff about yum.  Hint: until you are an expert at package management, don't use yum or .rpm packages on Debian systems.  The philosophy in package management between the different distros is slightly different.  Redhat has a different idea than Debian/Ubuntu do. 

And one more thing.  Every command on a Unix system should have a manpage which explains what it does, what the options are and any warnings about using it.  **man apt** is a good place to start.

---

