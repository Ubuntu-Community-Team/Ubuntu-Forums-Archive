---
title: "Snare on Ubuntu"
date: 2010-01-13
forum: Security
---

### Post by stevebu56 on 2010-01-13
Is there a Snare package or equivalent in Ubuntu?  I'm looking for a system auditing package and most likely it will need to pipe it's log files to a Snare server just because that's what is already in place.  The Snare project only seems to support Red Hat based distros.  Any reason for this? 

Any help would be appreciated.  
Thanks.

---

### Post by running_rabbit07 on 2010-01-13
Probably because RedHat wrote it and they get paid for the program.

---

### Post by adam814 on 2010-01-13
[http://sourceforge.net/projects/snare/](http://sourceforge.net/projects/snare/)

Doesn't seem to be RedHat only based on that page anyway.  There might not be a ready-made deb package for it though.  Have you tried compiling from source?

---

### Post by Pev on 2010-08-19
Hi I just got Snare 1.5.1 working on Ubuntu 10.04-desktop-amd64.

I compiled Snare for the source code tar ball.

I needed to install the packages
    auditd and
    libaudit-dev (libaudit-dev may not be needed).

I also needed to change the MakeFile contained in Sanre changing "./Installer.sh"; to "bash ./Installer.sh". There where two occurrences.

I then followed the instruction at: [http://www.intersectalliance.com/projects/SnareLinux/index.html](http://www.intersectalliance.com/projects/SnareLinux/index.html) To be able to view and modify using the http server.

---

### Post by alphaamanitin on 2010-08-19
can't you use alien to convert the redhat to deb?  Yes, I am relatively new so I may be completely wrong.

AlphaA

---

### Post by bodhi.zazen on 2010-08-19
> **alphaamanitin said:**
> can't you use alien to convert the redhat to deb?  Yes, I am relatively new so I may be completely wrong.

AlphaA

You can use alien, but it is safer to compile from source as alien can overwrite shared libs without permission which results in a broken system.

It takes some time to learn to compile from source, but it is no too hard.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Typically it is 

```
./configure --prefix=/usr/local
make
sudo make install
```

Most errors are due to missing dependencies.

---

### Post by Red_Phoenix on 2010-10-27
Sorry for the slow reply guys - I've only just spotted this thread.

RRabbit: The audit subsystem is originally selinux, the redhat guys came up with the audit daemon that communicates between kernel and userspace, but Snare itself is independent of any distro.

We've packaged it for redhat since (for better or worse) most of the supported clients tend to ask for it, but I run ubuntu on my desktop & dev boxes.

Let me know if you still need a hand getting it to run.

Regards,

Leigh. (Snare dev, InterSect Alliance)

---

