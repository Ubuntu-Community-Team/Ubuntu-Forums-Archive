---
title: "i would like to know if slackware is part of linux?"
date: 2016-01-18
forum: Ubuntu, Linux and OS Chat
---

### Post by openation1 on 2016-01-18
Hello everyone. A friend of mine was telling me about slackware, he says is a very good distro but i dont know whether to use it or not. can any one please advice me about this distro? i would appreciated very much and thank you

---

### Post by deadflowr on 2016-01-18
Moved to Ubuntu Linux and OS Chat

---

### Post by grahammechanical on 2016-01-18
Yes, Slackware is a Linux distribution

[https://en.wikipedia.org/wiki/Slackware](https://en.wikipedia.org/wiki/Slackware)

[https://store.slackware.com/cgi-bin/store/slack14.1?id=axcbqXwN&mv_pc=103](https://store.slackware.com/cgi-bin/store/slack14.1?id=axcbqXwN&mv_pc=103)

---

### Post by Bucky Ball on 2016-01-18
Did you [have a look]("http://www.slackware.com/info/")? Plenty of info about slackware out there. ;)

Best way to find out is just try it. What's a 'great distro' for one person is not necessarily going to fit the purposes of someone else. A linux distro is definitely not a one-size-fits-all thing. Lucky there are so many and they are so customisable.

---

### Post by 1clue on 2016-01-19
Slack has been around for a long time. It's an old-school community oriented distro, not like ubuntu which is maintained by Canonical which has a for-profit intent and commercial funding.

---

### Post by mastablasta on 2016-01-19
Slackware is old school but as I read they do help the user with setup and guidance. it is known for stability and is like the opposite of Arch. it also gives you a lot of freedom and you need to setup plenty of things by yourself.

for example here is an interesting review. : [http://distrowatch.com/weekly.php?issue=20121015#feature](http://distrowatch.com/weekly.php?issue=20121015#feature)

---

### Post by buzzingrobot on 2016-01-19
Slackware is more than 20 years old.  It wasn't the first Linux distribution, but I believe it is the oldest surviving Linux distribution. 

I do not recommend Slackware to anyone without at least a moderate amount of experience using command line tools to administer Linux.

Slackware hasn't changed much in those 20 years.  It is a conservative distro. The installer is ncurses graphical, so it will look ugly and blocky to people accustomed to today's polish GUI's.  There's no partitioner, automatic or otherwise, in the installer.  Users need to partition there drive(s) before using the installer. 

After installation, Slackware boots to the command line.  If a user wants to automatically boot to a GUI, the user needs to edit an init file.  

The installer does not create an ordinary user.  You'll log in as root until you manually create a user.

Slackware installs with a kernel that includes many device drivers.  After installation, users are advised to switch to a leaner "generic" kernel.  That requires the user to create the inititrd ("initial ram disk") which is typically supplied by other distributions.  Then, the bootloader configuration file must be edited and the bootloader reinstalled.

The current release is 14.1, and it's from 2013.  A beta has recently been announced for 14.2.  KDE is the primary interface, with XFCE 4.10 on offer, plus a few traditional window managers.  KDE is at 4.10 in 14.1 and will be, I think, 14.4.3 in 14.2.  

Packages are *not* upgraded after release.  Security and bug fixes are pushed out, of course.  

The kernel in 14.1 is from the 3.10 series, and it s 4.4 in the 14.2 beta.

There is a package manager of sorts.  It's not a GUI. Everything happens at the command line. No dependency resolution. (Slackware dates to the era before packages, package managers and dependency resolvers existed.) Packages that are not included in the default installation are available in sites and repos maintained by other individuals.  The usual routine is to download a build script, and the source code, and then run the build script to create an installable package. (After previously installing any dependencies in the same way.)

Slackware is a one-person release, the same person for it's entire lifetime.  It's supported by a small cluster of other developers.   Documentation is reasonably useful and current, but it is scattered across several independent sites.

I believe Slackware's approach was influential in the creation of Arch.

---

### Post by Habitual on 2016-01-19
> **buzzingrobot said:**
> No dependency resolution.
That's a Biggie.

---

### Post by yoshii on 2016-01-19
I like Buzzingrobot's thorough reply.  I agree about not recommending it for beginners or even intermediate users.  It's just not user-friendly enough to the average user unless they really want to tackle all that manual configuring and be on the learning curve.  

This reminds me of how odd it is when people recommend some of these odd old linuxes to beginners.  It's no wonder then, that some people get the wrong idea about linux thinking that all the distros are as difficult as those.  In reality, a lot of distros are very user friendly in modern times.

---

### Post by 1clue on 2016-01-19
Actually if you want to know what all of Linux was like back when I started, it was pretty much exactly like what buzzingrobot said.

Add to that, xfree86 (the xorg of the time) was beta software, many Linux people didn't use it or put up with a huge amount of bugs.

While the description of slack doesn't intimidate me and since I did my first distros that way I can assert that it's possible to learn Linux that way, I think something more mainstream would be a better idea.

If you want the 'community-based' experience then I recommend something like debian.  Ubuntu is basically debian with commercial backing.  If you want to learn the nitty gritty, then Gentoo comes to mind.  Gentoo is not generally considered to be a beginner distro.

---

### Post by buzzingrobot on 2016-01-20
> **1clue said:**
> Actually if you want to know what all of Linux was like back when I started, it was pretty much exactly like what buzzingrobot said.



I think the first Slackware I installed was a 3.Something release,  way back when.  Pretty sure there were not any actual packages, just thinly disguised tar archives. It's changed very little. It's lean and fast, and can be made leaner and faster if you know what you are doing.  But, I don't really see the advantages, educational or otherwise, in slogging through that manual labor. Following instructions for fdisk by rote, for example, isn't going to teach anyone about partitions any more than using a well-designed GUI. If someone wants to know what a partition is, and why they exist, they need to go out and read something. Diito for all the DIY distros.

---

### Post by moseley on 2016-07-28
Slackware has a long history. The supposed difficulties are not difficulties. It is very flexible and just plain easy to use. Package building is script based and easy to use. Sure there are manual things to do but don't let that scare you. GUI's are nice but not always needed. I was intimidated by the thought of Slackware for a long time....... Then I tried it. I've personally never regretted it.  As far as on PC hardware? I have never had any issues. The Ncurses based installer is very straight forward and simple. If you need help or have questions, go here: [http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)
Eric Hameleers, better known as Alien Bob is one of the Slackware developers and is active in forums. He also does a bit of other Slackware related stuff that you can read about here: [http://alien.slackbook.org/blog/](http://alien.slackbook.org/blog/)
Don't stay hooked on the ease of use crap, go try it out. I swear you will like it. You can do anything with Slackware. =)

---

### Post by fromwin2lin on 2016-08-05
I have never tried Slackware, but I heard at one point that the project was abandoned. But last month, a new Slackware version came out.

---

### Post by uNoubu8a on 2016-08-05
> **fromwin2lin said:**
> I have never tried Slackware, but I heard at one point that the project was abandoned. But last month, a new Slackware version came out.

I think the demise of Slackware was greatly exaggerated (and just plain false).

---

