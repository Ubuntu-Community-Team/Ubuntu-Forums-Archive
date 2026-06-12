---
title: "clamav antivirus outdated (dapper 6.06)"
date: 2006-12-26
forum: Server Platforms
---

### Post by siili on 2006-12-26
After an update and upgrade, clamav is still at version 0.88.4.  Using Debian volatile repositories ([http://volatile.debian.net/debian-volatile](http://volatile.debian.net/debian-volatile) sarge/volatile main contrib) would bring clamav to a respectable 0.88.7 but it fails to install due to dependency problems:

The following packages have unmet dependencies:
  clamav: Depends: libclamav1 (>= 0.88.7) but 0.88.4-1ubuntu2 is to be installed
E: Broken packages

And then trying to install libclamav1 yields:

The following packages have unmet dependencies:
  libclamav1: Depends: libgmp3 but it is not installable
E: Broken packages

However, libgmp3 is indeed installed. Any solutions to getting and keeping Ubuntu up to date with clamav?

Regards,
David Koski

---

### Post by dbbolton on 2006-12-26
did you use synaptic for this upgrade ?

in the mean time, i don't think you'll have *too *many viruses to worry about ;)

---

### Post by kcallis on 2006-12-29
> **dbbolton said:**
> did you use synaptic for this upgrade ?

in the mean time, i don't think you'll have *too *many viruses to worry about ;)


That is true if you are using clamav for stickly a linux only environment, but could be major problems if you using clamav to cover not only Linux deployment but Windows as well!](*,)

---

### Post by siili on 2006-12-30
No, I do not use synaptic as this a server and has no GUI. apt-get is the tool. And this is not about Linux scurity as I don't need to be concerned about viruses on *my* system of course. But I install mail servers and make recommendations for many environments including using Linux/clamav as a mail proxy to protect Windows systems. As it is now, Ubuntu looks like a poor choice for that. Debian volatile repositories work for Debian installs in my experience.

If anyone has a solution for this I would appreciate some input.

Regards,
David Koski

---

### Post by duckmannz on 2007-01-08
Is there any resolution on this yet? I'm looking at putting Debian Etch (yes, I'm aware that it's still in testing!) in to resolve it but would rather keep the current installation...

---

### Post by jimwillsher on 2007-01-25
I wish there was. I'm in the same boat, with my Dapper box being my mailserver for 5 LAN Windows PCs. So whilst I have NOD32 on the Windows PCs I'd also like an up-to-date AV solution on the mailserver.


Jim

---

### Post by eldorel on 2007-01-29
I am currently updating the bug report for this issue in launchpad, and would appreciate if all of you lurkers would leave a comment here to show that this issue is affecting you as well.

If we can show a large enough affected user base, then we have a better chance of finding a solution. (I really don't feel like moving 30+ servers back to debian, so if nothing else leave a comment for my sake)

For those who would like to comment directly here's a link to the bug report. 

[https://launchpad.net/ubuntu/+source/clamav/+bug/53856](https://launchpad.net/ubuntu/+source/clamav/+bug/53856)

---

### Post by jimwillsher on 2007-01-29
I'm afraid I got fed up waiting and just compiled it myself (which was easier than I expected).

It's such a shame though, that an operating system that makes itself out to be secure, and an organisation (Ubuntu) whch appears to be at the leading edge, is let down by one of the core components of security - up to date antivirus.


Jim

---

### Post by chrisfay on 2007-01-29
> t's such a shame though, that an operating system that makes itself out to be secure, and an organisation (Ubuntu) whch appears to be at the leading edge, is let down by one of the core components of security - up to date antivirus.

That's ridiculous.... You are aware that there's a multitude of other AV packages, right? You're dependency on ClamAV, and apt-get for that matter, shouldn't black mark the OS.

---

### Post by eldorel on 2007-01-29
We have way too many systems to maintain, there is no way we're going to start manually compiling the package on every system everytime clamav updates.

Maybe i should look into taking over maintenance of the package, or creating my own local repository.

---

### Post by eldorel on 2007-01-29
> **chrisfay said:**
> That's ridiculous.... You are aware that there's a multitude of other AV packages, right? You're dependency on ClamAV, and apt-get for that matter, shouldn't black mark the OS.

The dependency isn't because of an overwhelming preference for clamav, it's because it''s the most commonly supported Av software for most 3rd party packages. There is a compatible plugin for almost every service you can think of, and it's not unreasonable to expect that it be kept up-to-date.

 As for Apt-get, yes I do depend on it, and package management is one of the main reasons that we use ubuntu. It makes life easier.

---

### Post by chrisfay on 2007-01-29
> As for Apt-get, yes I do depend on it, and package management is one of the main reasons that we use ubuntu. It makes life easier.

Though I agree with you for the most part, it seems counterintuitive to rely on apt-get in situations where you demand absolute up-to-date status, as you obviously do for AV. There will always be a delay between the repository status and that of the actual developer's release; including security updates. 

In critical apps, we always require the packages to be manually checked and compiled before installation/updating anyway. My point being, yes, the repositories should be updated, but the post I was responding too cast the entire Ubuntu OS as insecure based an easily avoidable issue; and on a single box that a five minute compilation could have solved.  As an admin, or anyone responsible for maintaining important hardware, our job is to adapt to different situations. This hardly seems like one worthy of total disappointment in the entire Ubuntu OS IMHO.

---

