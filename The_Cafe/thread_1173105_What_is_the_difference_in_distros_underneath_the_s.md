---
title: "What is the difference in distros underneath the surface?"
date: 2009-05-29
forum: The Cafe
---

### Post by gamelord12 on 2009-05-29
I know that Red Hat-based distros use a different package manager than Debian- or Novell-based distros, but why do they need different package managers?  What is inherently different between distributions on a low level?

---

### Post by aysiu on 2009-05-29
Distros can differ in the following ways: [list][*]File/folder structure[*]Package management[*]Release cycles[*]Development staffing structure / payment[*]Community support[*]Default packages installed[/list] In terms of why some distros use a particular software packaging over another, I don't know enough about the details to say, but I'm guessing it's simply a matter of preference.

Gentoo practically compiles each package from source. GoboLinux unpacks binaries into separate application folders. And most other distros simply copy a bunch of files to different places and change some settings and services (if necessary).

Sometimes you can use *alien* to convert a .rpm file to .deb, but sometimes the .rpm-based distros have a slightly different file structure, so the *alien*ing won't work in Ubuntu or other Debian-based distros.

---

### Post by gamelord12 on 2009-05-30
Can anyone go into detail on how the file/folder structures and package managers differ?

---

### Post by MaxIBoy on 2009-05-30
The package management difference is a bit more than personal preference. Different package management strategies are geared toward different types of users (automatic compiling as in slackware, or simply copying files to the correct destination as in APT or RPM.) APT and RPM are very similar in terms of how they work. The difference is that APT is easier to work with and technically superior, whereas RPM is included in the LSB (Linux Standard Base,) and is therefore supposed to be the standard package format.



There are other differences besides package management. A shining example is the boot process, which varies a lot between distros. Most distros use the old "System V Init" process. Ubuntu has moved onto upstart, but upstart is compatible with sysvinit and handles initscripts the same way. In Debian, and Debian-based distros like Ubuntu, runlevels 2, 3, 4, and 5 are identical, and the default is runlevel 2. Meanwhile, other distros (notably Arch) use the BSD-style init framework.

---

### Post by mamamia88 on 2009-05-30
> **gamelord12 said:**
> I know that Red Hat-based distros use a different package manager than Debian- or Novell-based distros, but why do they need different package managers?  What is inherently different between distributions on a low level?

isn't red hat a novell based distro?

---

### Post by kk0sse54 on 2009-05-30
> **mamamia88 said:**
> isn't red hat a novell based distro?

Red Hat is Red Hat based :p

---

### Post by Icehuck on 2009-05-30
> **mamamia88 said:**
> isn't red hat a novell based distro?

Red Hat Enterprise is made by Red Hat Inc. 
Novell makes SuSE enterprise.

---

### Post by mamamia88 on 2009-05-30
> **Icehuck said:**
> Red Hat Enterprise is made by Red Hat Inc. 
Novell makes SuSE enterprise.

i'm confused does novell own red hat?

---

### Post by kk0sse54 on 2009-05-30
> **mamamia88 said:**
> i'm confused does novell own red hat?

No, Novell and Red Hat are two seperate companies which today are the top leading corporate linux companies.

Check this out if you want to know a little bit about their origins [http://libreamoi.com/images/linuxdistrotimeline.png](http://libreamoi.com/images/linuxdistrotimeline.png)

---

### Post by mamamia88 on 2009-05-30
> **C!oud said:**
> No

cool thanks for clearing that up you learn something new every day

---

### Post by dspari1 on 2009-05-31
> **gamelord12 said:**
> I know that Red Hat-based distros use a different package manager than Debian- or Novell-based distros, but why do they need different package managers?  What is inherently different between distributions on a low level?

What is most noticeable is the default theme, preinstalled applications, package management, and configuration tools.

---

### Post by SomeGuyDude on 2009-05-31
Lots of things.

Config files are HUGE. I didn't realize this until I was shown how Arch is kinda BSD-like in its use of config files.

Package managers are another big one. They each try to find what they think is the best way to have the user interact with installing/updating software. For GUI-types, Synaptic is king IMO. However, pacman works better overall.

Release schedule is another. Working with a rolling release distro versus upgrade-type is HUGE, and both have their pros and cons.

Some also patch their kernels and other files. Others, like Slackware, use straight vanilla packages so all "Slackware" becomes is an organization of everything.

Repos are big, too. One reason some people don't like this or that distro is the repos don't have enough in them.

---

### Post by juancarlospaco on 2009-05-31
Others, dont have, and dont need a Package manager or packages, example: Vyatta

---

