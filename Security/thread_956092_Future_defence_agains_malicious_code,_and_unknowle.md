---
title: "Future defence agains malicious code, and unknowledgable users"
date: 2008-10-22
forum: Security
---

### Post by dagoth_pie on 2008-10-22
I've been thinking/reading about Linux viruses, and we all know that no virus, or even cracker, can harm anymore than your home folder without knowing your password, and the only way a virus can affect your system files is if you give it permission, which once people, with no knowledge of security, file permissions, and malicious code start using it there are two sorts of installers worth mentioning, there are ones from the ubuntu repositories, which we all know are from trustworthy sources and screen for malicious code, but there is also, source code and binary installers, source code isn't much of a problem, as a novice user won't be able to get their head round it (I would know, took me months to understand) but binary installers are common for proprietary games, drivers, all sorts of stuff, and seeing as not only, but most specifically, Ubuntu is focused on a user friendly experience, we will end up with graphical tools for installing binaries, a user friendly work-around for the terminal. Now the whole point I've been leading up to, is a suggestion, of having, a sort of semi powerful root account, to go alongside the users, and control a branch of the filesystem, specifically for untrusted programs to go into, requiring a password to change stuff, so it would be just as secure as something owned by root, but if something was installed to it, wouldn't expose the system to any danger. I guess I have been looking for a project to work on to train up my coding skills, so is there a project like this already being done, or am I the first to think of it, any suggestions/critisisms accepted

---

### Post by cariboo on 2008-10-23
Installing a malicious binary can be done right now, there are a lot of newbies out scouring the internet for drivers for their video, sound and wireless cards, because most of them don't know enough to check the repositories, or even to come here for help.

There is no need for another account, the new user has a hard enough time just dealing with not being an administrator all the time, like in windows. 

Instead of giving users easier tools to install programs, I feel there should be room made on the LiveCD for an Introductory presentation or video showing new users where and how to get drivers for their devices and how to find and install programs that are available in the repositories.

One thing to think about is that the cracker/script kiddie is always going to go with the easiest target, most of the people out there trying to break into systems are not skilled enough to create a binary that looks convincing and carries a malicious payload, If there is then it doesn't matter how skilled you are, they are going to get past most defenses.

The thing to stop the kind of problems your are envisioning, is education, not adding more layers of security.

Jim

---

### Post by dagoth_pie on 2008-10-23
I see your point, although just out of curiosity are there currently any projects to come up with simpler ways of installing binaries, with installers, i think its libgtk2-dev that brings up a graphical installer, but there is no way of installing it into a system directory and having it automatically set up launchers in the menus, although to a certain extent thats a good thing, and I completly agree, when you boot up Ubuntu you should see an irritatingly obvious "take a tour" icon... even a simple word document of quick pointers would get the job done i guess

---

### Post by hyper_ch on 2008-10-23
the only way that should be used to install software is through (trusted) repositories. If you use anything else, you put yourself at risk of installing malware.

And I think installing from the repositories is very, very simple... just search and select in synaptic - for those who don't want to use the cli.

---

### Post by dagoth_pie on 2008-10-23
yes but what about games, or even, eventually if/when massive ammounts of commercial software is made for linux, they won't neccesarily package it in deb files, or give the source code for someone else to do it, although if that were the case it would probably be on a cd, and come with its own graphical installer, it'd also mean that anyone who wanted to illegally download software would need to understand how to use a command line to install things, hmm to be honest I'm dreading the day we need a cd key to install stuff on Linux

---

### Post by Dave_Connor on 2008-10-23
> **dagoth_pie said:**
> yes but what about games, or even, eventually if/when massive ammounts of commercial software is made for linux, they won't neccesarily package it in deb files, or give the source code for someone else to do it, although if that were the case it would probably be on a cd, and come with its own graphical installer, it'd also mean that anyone who wanted to illegally download software would need to understand how to use a command line to install things, hmm to be honest I'm dreading the day we need a cd key to install stuff on Linux

If software like that is made then there will eventually be an open source alt to that program that doesn't require all the corperate paranoia bs.

---

### Post by hyper_ch on 2008-10-23
> **dagoth_pie said:**
> anyone who wanted to illegally download software
Illegal behaviour is not supported on this forum.

---

### Post by cdenley on 2008-10-23
If people are going to package software in binary installers, and instruct users to run it as root (or their user), there isn't much ubuntu can do about it. The user can install it as another non-priveleged user, but probably won't unless instructed to do so by whoever they got the software from. You can install software in a chroot, but if you let that software run as root, it can easily break out.

---

