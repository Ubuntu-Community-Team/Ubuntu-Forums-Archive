---
title: "Unifying Linux Package Management"
date: 2004-11-23
forum: The Cafe
---

### Post by ubuntu_demon on 2004-11-23
Unifying Linux Package Management :

[http://linux.slashdot.org/linux/04/11/23/1835258.shtml?tid=190&tid=185&tid=106](http://linux.slashdot.org/linux/04/11/23/1835258.shtml?tid=190&tid=185&tid=106)

Job Diogenes Ribeiro Borges writes "The Smart Package Manager is an intelligent tool that works on the 'dependency hell' of software upgrading and installation on linux. Works with all major distributions (APT, APT-RPM, YUM, URPMI, etc), supporting multiple sources and technologies concurrently. Yes, you could install from multiple sources, from deb, rpm, tgz at same time! Smart Package Manager is being developed by Conectiva and is the tool that makes the Magic of CrossPlatform package management, behind the recently announced 'Four Linux Vendors Agree On An LSB Implementation.' You can get screenshots here (portuguese texts) and a README here."

Will/should ubuntu do something with this ?

---

### Post by jdong on 2004-11-23
Err, cool concept, but never going to work in real life.
 
 The truth is that each distro's packages like to install things in different places -- take a look at where Fedora installs Firefox versus Debian. Things are **bound** to be screwed up sooner or later!

---

### Post by ubuntu_demon on 2004-11-23
Maybe the algorithms are worth looking at? According to the readme and the case studies they show they've got better algorithms.

---

### Post by pdamoc on 2004-11-24
[http://0install.net/](http://0install.net/)

now that's something I would like to see Ubuntu using but... I doubt it will ever be accepted.

ZeroInstall has been around for some time and I have absolutly no clue why isn't it used.

---

### Post by mark on 2004-11-25
[QUOTE=jdong]Err, cool concept, but never going to work in real life.
 
 The truth is that each distro's packages like to install things in different places -- take a look at where Fedora installs Firefox versus Debian. Things are **bound** to be screwed up sooner or later![/QUOTE] jdong - *sshhhh!* Don't tell anybody!  Maybe they won't notice that it "can't be done" and they'll go ahead and do it! ;-)

---

### Post by retype on 2004-12-13
They have done it [Smart PM](http://www.smartpm.org/) but you can't mix fedora and debian packages, but you can use it in both fedora and debian. I have used it in ubuntu and it works nicely.

---

### Post by TravisNewman on 2004-12-13
I'd like to see more synchronization between distributions (like installing things in the same place, for example) so that stuff like this would work much better. That's the only way unified package management will ever work.

---

### Post by Lovechild on 2004-12-13
To mimic a known statement:

STANDARDS, STANDARDS, STANDARDS!!!

---

### Post by EdCrypt on 2004-12-13
>  Notice that this project is **not** a magical bridge between every distribution in the planet. Instead, this is a software offering **better package management** for these distributions, even when working with their **own packages**
 ;-)

---

### Post by EdCrypt on 2004-12-13
[QUOTE=jdong]Err, cool concept, but never going to work in real life.[/QUOTE]
As was said here, it already works.  And is better than apt! Just see the cases studies from the [README](http://linux-br.conectiva.com.br/~niemeyer/smart/doc/README.html#case-studies).
Ubuntu **really** need this.

---

### Post by Paqman on 2012-03-04
> **ubuntu_demon said:**
> an intelligent tool that works on the 'dependency hell' of software upgrading and installation on linux.

Er, sort of trying to solve a problem from the dark ages, isn't it? When was the last time anyone running a modern distro got stuck in dependency hell?

---

### Post by duncan12 on 2012-03-04
[IMG]http://cache.gizmodo.com/assets/images/4/2011/07/standards.png[/IMG]

Too true - let's not make it more complicated :popcorn:

---

### Post by nothingspecial on 2012-03-04
Unfortunately a spammer bumped this thread to the top.

It needs to be put back to sleep.

Closed.

---

