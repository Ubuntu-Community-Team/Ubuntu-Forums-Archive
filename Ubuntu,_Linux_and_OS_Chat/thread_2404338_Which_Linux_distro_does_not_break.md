---
title: "Which Linux distro does not break ?"
date: 2018-10-23
forum: Ubuntu, Linux and OS Chat
---

### Post by automate-stuff on 2018-10-23
I have tried many distros and most of them break easily, is there a distro which does not break ? when people say, for instance, Debian is very stable, does that mean it does not break easily ?

---

### Post by deadflowr on 2018-10-23
*Thread moved to **Ubuntu, Linux and OS Chat***

---

### Post by QIII on 2018-10-23
I have broken every distro I've tried.

There is nothing that humans make that doesn't break.

---

### Post by deanr2 on 2018-10-23
Tried Mint 18.3? Not that, as indeed pointed out, anything is unbreakable. Darn solid though.

---

### Post by again? on 2018-10-23
It really depends on what you do and how much you know that determines how easily you break things.
My recommendation is to use a simpler desktop not under heavy development and for ubuntu variants chose LTS releases.
I've jumped off the gnome-shell desktop as for me it feels like a beta product.
Using Xubuntu 18.04.

---

### Post by 1clue on 2018-10-23
I have broken every operating system I've ever touched for a sufficient length of time, including DOS 2.11 and up (some versions skipped), Windows 2.03 and up (some versions skipped), Mac OS from 1984 and up, some versions skipped. A/UX (Apple's first UNIX), A/IX (IBM's UNIX), IBM OS/400 (which actually can lock up completely from bad Java), plus a plethora of pre-Windows monitors from the early to mid 80s from Apple, Atari, Commodore and more. And PDP something, maybe PDP-11? That one in just 2 days of trying to code.

Eventually somebody will explain the development cycle and the balance between newness of software and its stability. I guess I'd just as well be the one.

[https://www.ubuntu.com/about/release-cycle](https://www.ubuntu.com/about/release-cycle)

All software has bugs. It doesn't matter how old the software is or who wrote it, the only question is have the bugs been found, and do they actually impact the usability of the code in some significant way.

A bleeding edge piece of software has a significant amount of bugs, and if the software is sizable you can bet that some of those bugs are a big deal. Any operating system or application based on bleeding edge code has more bugs in it than a mature product.

Let me explain what a mature product means: Let's take the Linux Kernel. They develop new features for awhile, and that goes into a new version of Linux. At some point they flip a metaphorical switch, and stop adding new features to the "master" branch of the official source repository. (What the "official source repository" is is a very complicated question when it comes to Linux, but I'm just going to say that it's what the official kernels are built from on kernel.org.

At any rate, when that metaphorical switch is flipped, the master branch only gets bug fixes. Someone following the bleeding edge -- especially if they are getting their source directly from the master branch and building it themselves -- will get a bunch of untested code, or at best minimally tested code. When they stop adding features and only take bug fixes, the bug rate goes down, and hopefully most of the really big ones are fixed before any distro actually takes it and releases it to their users. When enough people have tested a specific image enough that there is some confidence in its reliability, they will release it as a "bleeding edge" versioned kernel in their repository.

This goes on for not just the kernel, but for every package being built everywhere.

A bleeding edge distro is based on the latest released software from "upstream." For the kernel, "upstream" is kernel.org. For Apache2 web server, it's apache.org. The latest features means the least tested, and the least fixed.

Ubuntu normal releases are more tested than that. They have a release cycle which allows for significant testing of proposed versions of software. Which means they choose a version for each package, and from that point forward they only apply bug fixes, no new features, for the entire length of time that the released version of Ubuntu is supported. Then at the end of the release cycle, you download the next version and install it and the process continues.

For people who want a more stable operating system, there are the LTS (long-term support) releases. It's the same idea: They choose a point and freeze the versions of every package, and only apply the bug fixes from that point forward, only in this case it's for years, not just months.

The key here is that the more tested and stable the software, the older the software is.

If you want the "most stable" Linux, you need to go to one of the enterprise Linux distributions. Ubuntu is what I would call halfway there. They shoot for stability with their LTS releases, but something like RHEL or Suse take it to a further extreme. You'll get older kernels, older software and a lot more patches for security and stability.

So the one bitter pill here is this: Even after all this freezing and patching, there are no guarantees that the software will be crash proof. Creators and developers of enterprise-class systems, especially mainframes, spend a ton of money and a massive amount of time trying to test every aspect that they can find to prevent any badness from happening. But there's always something. Back in the 90s I found a bug like that on an AS/400. I worked in the plant that built them, but I was a programmer for a support web site, doing Java apps. They just got through telling us that the AS/400 was uncrashable, and I brought one down hard. They fixed the problem, but it's an illustration of the point.

Every time I get on a plane, I can't help but think of all those computer systems that keep the bird in the air. And I think about Java on the AS/400 in the 90s. I don't fly well.

---

### Post by mastablasta on 2018-10-23
> **1clue said:**
> 
For people who want a more stable operating system, there are the LTS (long-term support) releases. It's the same idea: They choose a point and freeze the versions of every package, and only apply the bug fixes from that point forward, only in this case it's for years, not just months.


in other words "stable" means it "stays the same". as in *stable *vs *changing.*

---

### Post by 1clue on 2018-10-23
> **mastablasta said:**
> in other words "stable" means it "stays the same". as in *stable *vs *changing.*

Clever. You maybe got that from the dictionary? :D

---

### Post by kansasnoob on 2018-10-23
I'm curious as to what exactly breaks? Generally speaking if I stick with the first point release of Ubuntu's LTS releases (eg; 16.04.1 or 18.04.1) I experience no actual breakage. There are occasional bugs but more frequently design changes that drive me a bit crazy until I get used to the change. Most of the breakage I encounter fixing other peoples computers is the result of operator error - most frequently due to following some BAD instructions in an attempt to achieve some behavior or another (sort of like tweaking a new car to try and improve performance).

---

### Post by 1clue on 2018-10-23
@kansasnoob,

You never know what breaks, but chances are it's broken from the point where it was written, or from when a patch was applied to fix bug A, thereby causing bug B.

It's generally considered best practice to stay with the latest security and stability updates for the release. That way they give you fixes for recent hacks, crashes and whatever the rest of the world discovered that was wrong with the original release point.

---

### Post by kansasnoob on 2018-10-23
> **1clue said:**
> @kansasnoob,

You never know what breaks, but chances are it's broken from the point where it was written, or from when a patch was applied to fix bug A, thereby causing bug B.

It's generally considered best practice to stay with the latest security and stability updates for the release. That way they give you fixes for recent hacks, crashes and whatever the rest of the world discovered that was wrong with the original release point.

But without seeing actual examples of what broke and when it broke it's impossible to give a reasonable reply. I maintain computers for over 50 people and 99% of "breakage" is the result of "tweaking" things improperly - frequently by adding PPA's without understanding exactly what they're doing. No doubt kernel upgrades will occasionally "break" functionality on certain hardware, but its not a frequent occurrence.

---

### Post by ajgreeny on 2018-10-23
The only useful answer to your original question is another question back to you: what do you mean by "most of them break easily"?

I have been using Ubuntu or a derivative of it with different DE for over 13 years now with no major breakage; I have had some bugs, but not as many as I had when last using Windows, in its XP days, so I wonder what you're doing that manages to break your OS quite so easily as you seem to be suggesting.

---

### Post by poorguy on 2018-10-23
> **QIII said:**
> I have broken every distro I've tried.
Learn by doing.

> **QIII said:**
> There is nothing that humans make that doesn't break.
Ain't that the truth.

---

### Post by TheFu on 2018-10-23
> **automate-stuff said:**
> I have tried many distros and most of them break easily, is there a distro which does not break ? when people say, for instance, Debian is very stable, does that mean it does not break easily ?

What do you mean by "break easily"?  Be specific.  

Some fringe project or almost any GUI tool can appear to break things, but it might just be the GUI that isn't working as expected.  If the kernel doesn't crash, then the OS is still running.  Switch to a different console and recover.  The bigger the GUI used, the more likely it will fail, but that is just the GUI, not the OS or the distro.

I routinely see 30+ days of uptime on my Linux systems.  In the 1990s, before we had to patch for security issues all the time, I had a system up well over 400 days.

If you copy/paste sudo commands from untrustworthy sources, any Unix OS is easy to break.  I can give you 1 command that will totally trash a system, assuming the account running them can gain elevated privileges.

---

### Post by 1clue on 2018-10-23
For the sake of clarity on my prior "I've broken everything I touched" post: For me the minimum qualification for "broken" is that the system was unresponsive and I had no means of fixing it without a hardware reset or power-off.

TheFu brings up an interesting point about breakage and reliability related to uptime. I used to be what's called an uptime junkie. I would leave systems up and running for as long as possible. Back before Redhat went public, I had a Redhat box with over 2 years of uptime, on an active server that was working fine. When I noticed the uptime I thought, "Hmm, maybe I should reboot?" So I did, and the system was very, very broken. Would not boot. I extracted relevant data from another Linux box it was so broken.

The reliability of a system requires that the software which is running be consistent with the software on the disk. With Linux you can have a service running, update the disk and potentially the stuff on the disk is completely incompatible with what's running. That's what happened with my Redhat box. I had been doing updates all this time, didn't yet know about this issue so I figured everything was good. The filesystems had not been checked in at least 2 years, and with a lot of server activity the data had some corruption in that time, so I lost some information.

If you get an update to a package, it's best if all instances of that software be killed and then restarted. That goes for everything from the kernel to your web browser. It seems that Ubuntu today takes care of at least some of that for you, but if you get core updates like glibc or the kernel you should really restart right away.

---

### Post by 23dornot23d on 2018-10-23
[h=1][Which Linux distro does not break ?]("https://ubuntuforums.org/showthread.php?t=2404338&page=2")[/h]
The one you do not mess around with (most Live CD/DVDs) - but then again if you did not mess around - where would all the fun be in sorting out the problems.

Always the options too of restoring from a backup - once you get used to making backups on a regular basis .......

The other option - keep many distros going on one hard drive - think I have around 30 now ........... the ones that break - you go back to and fix - or use Timeshift to bring back a restore point - and try and try again to break it .........

---

### Post by pauljw on 2018-10-23
> **automate-stuff said:**
> I have tried many distros and most of them break easily, is there a distro which does not break ? when people say, for instance, Debian is very stable, does that mean it does not break easily ?

Use an LTS release, stick to installing only software from the repositories and don't try to make linux act like windows and you shouldn't have any problems.  I haven't broken a system in about 10yrs.  If you want to play with the latest and greatest stuff, install virtualbox and load new distros as virtual machines.  Then, should you break it, delete it and reinstall it.  Keeping your host system safe and stable.  JMHO

---

