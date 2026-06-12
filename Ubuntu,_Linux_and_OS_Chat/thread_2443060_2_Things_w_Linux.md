---
title: "2 Things w/ Linux"
date: 2020-05-10
forum: Ubuntu, Linux and OS Chat
---

### Post by bionic3epl on 2020-05-10
1. Is the Linux Kernel the Core of all the Linux Distros?

2. Is the Ubuntu Kernel broken again because it seems like they are falling behind again.

---

### Post by wildmanne39 on 2020-05-10
The answer to your first question is here:

[https://askubuntu.com/questions/172927/do-all-linux-distros-use-the-same-kernel](https://askubuntu.com/questions/172927/do-all-linux-distros-use-the-same-kernel)

>  2. Is the Ubuntu Kernel broken again because it seems like they are falling behind again. 

If you are having an issue you need to be more specific, a lot of people are using Ubuntu including myself so no I do not believe it is broken, I do not think anyone is falling behind, we do not know who they are, if you mean the developers then they do not work on our schedule, so no they are not falling behind.

---

### Post by 1clue on 2020-05-11
1. Yes. 

2. This is a simple question with a complicated answer. I'll start as simply as I can and then get more detailed. When your eyes glaze over you can stop reading.

Ubuntu kernel is not broken AFAICT. By "broken" and "falling behind" I assume you mean that the kernel version does not match the version released by kernel.org?  It never has and never will, by design.

Unless something else pops into my head, the rest of my post concerns the concept of "release cycle." You can look it up and likely get a better description than what I can give you.

Software is written and released, and at that point it has bugs in it and probably some security vulnerabilities, and some inefficiencies or whatever other kind of fault. Many of these won't be found for years, if ever. Over time the software is tested and whatever bugs that are found are fixed. New features are added, new bugs created and found. Eventually the software may become obsolete and will be abandoned in favor of a newer version of the same thing, or some other package altogether. That's the release cycle. Mostly when discussing distros and updates, only a small part of this cycle is important. The new features and bug fixes/security updates are looked at as 3 separate ideas. "bleeding edge" gets all 3 sections, but "stable" only gets bug fixes and security updates. In some cases a branch might only have security updates.

Now, you need to understand that in the software world there is a balance between "new" and "stable." They are mutually exclusive. The newest software out there is by definition unstable, and the stable software is not new. The discussion on why this must be true and the details of it will fill a whole day for you, I won't go into it here.

Linux is the kernel itself. When you load a distro like Ubuntu, you get a kernel and a whole lot of other software, some of which only runs on Linux and others which run on many different operating systems. Including Windows and Mac OS X in some cases. Each software project has a team of developers, testers, documenters and whatever else is needed. These teams are called "upstream." The maintainers of a distro (In Ubuntu's case it's a company called Canonical) will choose which software packages to include in their distro, and which versions of the various packages to use.

Most Linux distributions -- especially ones intended for commercial or "mainstream" use -- run on a scheduled release plan. That means that most people will be running the "stable" version of Linux. Scheduled releases can follow different rules, but for Ubuntu and its main variants this means that every so many months the maintainers will "freeze" the software version (no more feature updates) and from that point only accept bug fixes or security updates into that release. But the truth is that the concept of "bleeding edge" vs "stable"  applies to the kernel, each individual package, and the release version  of the distro itself, together and separately.

The other approach is called a rolling release. A rolling release is closer to "bleeding edge." In this case the software in the distro's database is roughly synchronized with the software coming from "upstream." There is however a lag because the distro maintainers will still have to build the software to their own requirements, test and debug it for awhile before releasing it to the mainstream users. There is a whole book of steps involved in that, and I've oversimplified dramatically. But with a rolling release you are rejecting the "stable" idea and mostly taking software from upstream shortly after it is released.

Pretty sure I've muddied the water enough for someone not familiar with these ideas. So good luck, and I'll try to clarify any other questions you might have.  :)

---

### Post by grahammechanical on 2020-05-12
Let the Linux developers explain things.

[https://www.kernel.org/category/releases.html](https://www.kernel.org/category/releases.html)

And the Ubuntu developers explain their method

[https://ubuntu.com/kernel](https://ubuntu.com/kernel)

If there is a bug connected with the Linux kernel then the Ubuntu developers need to know which kernel the bug applies to. There is the reason for the Ubuntu naming convention.

Latest kernel on my 18.04: 5.3.0-51-generic

Latest kernel on Ubuntu 20.10 development version: 5.4.0.28-generic

Not broken or falling behind. Just a policy of having a stable distribution for users.

Regards

---

