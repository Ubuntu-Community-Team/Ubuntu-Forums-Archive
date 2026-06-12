---
title: "UK's security branch says Ubuntu most secure OS"
date: 2014-01-17
forum: The Cafe
---

### Post by Linuxratty on 2014-01-17
No surprises here, that's for sure.

> Summary: CESG, the UK government's arm that assesses operating systems and software security, has published its findings for ‘End User Device’ operating systems. The most secure of the lot? Ubuntu 12.04.

[http://www.zdnet.com/uks-security-branch-says-ubuntu-most-secure-end-user-os-7000025312/]("http://www.zdnet.com/uks-security-branch-says-ubuntu-most-secure-end-user-os-7000025312/")

---

### Post by deadflowr on 2014-01-17
Why no Red Hat?

---

### Post by QIII on 2014-01-17
Red Hat is headquartered in the US.  Do you think a government agency in the UK is going to like that?

;)

---

### Post by deadflowr on 2014-01-17
> **QIII said:**
> Red Hat is headquartered in the US.  Do you think a government agency in the UK is going to like that?

;)

What about Microsoft, Google and Apple?

Anyway, though, I find Red Hat missing interesting.

---

### Post by WinterMadness on 2014-01-18
Well, I disagree that Ubuntu is the most secure. Though, I would say it certainly balances user friendliness and security very well.

---

### Post by corbin.loftis on 2014-01-19
Well, any Linux distro is more secure than OS X and Windows. And wouldn't Debian be up there since Ubuntu is based on it?

---

### Post by Dave_L on 2014-01-19
> **deadflowr said:**
> Why no Red Hat?

The article says "CESG looked at the security of the most popular end-user operating systems for desktops, smartphones, and tablets."

Maybe Red Hat doesn't fit in that group.

---

### Post by bertan2 on 2014-01-19
> **Dave_L said:**
> Maybe Red Hat doesn't fit in that group.

The list of ones they looked as is given in the link. Android 4.2, Android 4.2 on Samsung devices; iOS 6, Blackberry 10.1, Google's Chrome OS 26, Ubuntu 12.04, Windows 7 and 8; Windows 8 RT, and Windows Phone 8. RHEL wasn't part of their survey, and neither was any other flavor of Linux.

---

### Post by mips on 2014-01-19
OpenBSD?

---

### Post by moster on 2014-01-22
> **mips said:**
> OpenBSD?

They have other kind of problems. Something like paying for [electricity]("http://beta.slashdot.org/story/196883")! ;)

---

### Post by robin7 on 2014-01-22
> **bertan2 said:**
> The list of ones they looked as is given in the link. Android 4.2, Android 4.2 on Samsung devices; iOS 6, Blackberry 10.1, Google's Chrome OS 26, Ubuntu 12.04, Windows 7 and 8; Windows 8 RT, and Windows Phone 8. RHEL wasn't part of their survey, and neither was any other flavor of Linux.

Many would argue that SUDO is a potential security issue.  I'm sure Ubuntu isn't any more secure than most any other Linux distro, and someone might argue that without the SUDO factor, other distros are *more* secure than Ubuntu.

But it's cool that any Linux was considered against the others!

---

### Post by Jonor on 2014-01-22
Flattering that any non-Android Linux gets mentioned in a "most popular" list. We are the 1%.
I take it the Ubuntu did not have (NSA initiated) selinux activated. 
Remember, any trouble from Shuttleworth and we'll soon have his little home island surrounded !!! :D

---

### Post by deadflowr on 2014-01-22
> **robin7 said:**
> Many would argue that SUDO is a potential security issue.  I'm sure Ubuntu isn't any more secure than most any other Linux distro, and someone might argue that without the SUDO factor, other distros are *more* secure than Ubuntu.

But it's cool that any Linux was considered against the others!

What do you mean?
Any control/command that can give you root, is a security risk, potentially.

---

### Post by robin7 on 2014-01-22
I guess SUDO is a potential thread because of the way people are taught to use it by well-meaning folks on blog sites and such.  In reality it's little different from **su** in a terminal.

---

### Post by deadflowr on 2014-01-22
sudo and su are totally different.
su switches a user into root and stays as such until the user ends the session.
sudo runs per command, and has a timeout(something like fifteen minutes).

---

### Post by aysiu on 2014-01-22
Yeah, I'm not getting how *su* is inherently more secure than *sudo*. In terms of _practical use_, I like that *sudo* reminds me that I'm using an elevated command. I also like how it'll time out and require a password after a while. If I get in the habit of just switching to root with *su* (or, actually, in Ubuntu using *sudo -i*), then I might forget I'm using root and just issue a whole bunch of commands. That's me, of course.

---

### Post by monkeybrain20122 on 2014-01-22
> **robin7 said:**
> Many would argue that SUDO is a potential security issue.  I'm sure Ubuntu isn't any more secure than most any other Linux distro, and someone might argue that without the SUDO factor, other distros are *more* secure than Ubuntu.



Who are the "many" that argue that? It is the other way around. It is less secure to su to root or log in as root than to invoke root privilege only on per command basis.

---

### Post by Dave_L on 2014-01-22
I don't think either su or sudo is inherently safer than the other.  It just depends on how you use them.

---

### Post by robin7 on 2014-01-22
You got me!  In another Linux forum referencing that same article some folks were arguing about SUDO.  From what you guys have said, though, it seems to me to be *more* secure than the alternatives.

---

### Post by monkeybrain20122 on 2014-01-22
> **Jonor said:**
> .
I take it the Ubuntu did not have (NSA initiated) selinux activated. 


Dude, I hope you are not serious about selinux. The NSA's job is not just to spy on people, it has other mandates too, like preventing others to spy on the U.S, so it doesn't follow that anything they touch represents a security loophole. If selinux has been compromised it would be known and the U.S. govt wouldn't be using it.

---

### Post by linuxyogi on 2014-01-22
There's something that I noticed about gufw on 13.10.

On 12.04 if you turn on the gufw all ports show as stealth at grc.com but under 13.10 which has a newer version of gufw some ports are steath while some ports are closed.

As you know people who are behind their router's firewall wont be able to realize this but guys like me who configure their DSL connection via network manager can see the difference.

I really wonder why this change ?

As a workaround I installed ipkungfu and configured it and now all ports are stealth.

---

### Post by iulian X on 2014-01-23
> **Linuxratty said:**
> No surprises here, that's for sure.
[http://www.zdnet.com/uks-security-branch-says-ubuntu-most-secure-end-user-os-7000025312/](http://www.zdnet.com/uks-security-branch-says-ubuntu-most-secure-end-user-os-7000025312/)

Same thing on the Ubuntu site : [http://insights.ubuntu.com/resources/article/ubuntu-scores-highest-in-uk-gov-security-assessment/](http://insights.ubuntu.com/resources/article/ubuntu-scores-highest-in-uk-gov-security-assessment/)

This is the pdf : [http://insights.ubuntu.com/wp-content/uploads/UK-Gov-Report-Summary.pdf](http://insights.ubuntu.com/wp-content/uploads/UK-Gov-Report-Summary.pdf)

[IMG]https://dl.dropboxusercontent.com/u/17279480/%3F/Test-securitate.png[/IMG]

---

### Post by coffeecat on 2014-01-23
> **linuxyogi said:**
> 
On 12.04 if you turn on the gufw all ports show as stealth at grc.com but under 13.10 which has a newer version of gufw some ports are steath while some ports are closed.


Instead of judging the performance of gufw by what grc.com tells you, you might be interested in what a couple of knowledgeable forum members say about grc.com and the so-called "stealth" concept.

[http://ubuntuforums.org/showthread.php?t=1912957](http://ubuntuforums.org/showthread.php?t=1912957)

[http://ubuntuforums.org/showthread.php?t=1916336](http://ubuntuforums.org/showthread.php?t=1916336)

The link in post #9 of the second thread is interesting. I offer no judgements about the validity of the claims there myself, but thought you might be interested in making your own.

---

### Post by nomenkultur on 2014-01-27
+1

 there are only 2 operating systems I trust.

 blackberry os and ubuntu.

 I'm sure there are people saying fedora and the like are as secure as ubuntu is... explain this to me then:

[https://blogs.rsa.com/rsa-peeks-into-the-bits-of-new-linux-based-trojan-hand-of-thief/](https://blogs.rsa.com/rsa-peeks-into-the-bits-of-new-linux-based-trojan-hand-of-thief/)

---

### Post by SeijiSensei on 2014-01-27
I recommend reading the paper on Ubuntu:  

[https://www.gov.uk/government/publications/end-user-devices-security-guidance-ubuntu-1204/end-user-devices-security-guidance-ubuntu-1204](https://www.gov.uk/government/publications/end-user-devices-security-guidance-ubuntu-1204/end-user-devices-security-guidance-ubuntu-1204)

particularly Sections 6-8 on the specifics of creating an Ubuntu system that meets the CESG's requirements.  They give very detailed instructions for modifying a stock Ubuntu 12.04 distribution.

Ubuntu uses AppArmor, not SELinux, to manage application security.  The presence of AppArmor enables Ubuntu to qualify in the platform integrity and application sandboxing category.

---

