---
title: "Should I be worried about a lack of updates?"
date: 2006-02-10
forum: Server Platforms
---

### Post by jimwillsher on 2006-02-10
Hi all,

I'm running Breezy as a server, no GUI.

In the past I've used CentOs, and was used to getting frequent updates to the server via yum.

My Breezy server has been running for about a month now, and I run apt-get update and apt-get upgrade on a regular basis. However, I've NEVER had any updates available.

Am I doing something wrong, or am I expecting updates when there just aren't any updates available?

What's prompted this today is that I notice clamAV is outdated, but it was installed via apt, so I'd have imagined there would be updates to at least *some* of my packages?

I'm running:

mysql-server-4.1
apache
PHP4
clamav
postfix
squirrelmail
spamassassin
ssh
dovecot
vsftpd

etc., al of which were installed via apt.

Many thanks!


Jim

---

### Post by az on 2006-02-10
Do you have the breezy-security and breezy-updates repositories enabled?

---

### Post by jimwillsher on 2006-02-10
Very good question, how can I check? My /etc/apt/sources.list contains:

```

deb cdrom:[Ubuntu-Server 5.10 _Breezy Badger_ - Release i386 (20051013)]/ breezy main restricted


deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiver$

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```

as per the notes at [http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

Cheers,



Jim

---

### Post by jimwillsher on 2006-02-10
I should add: when I run apt-get update and apt-get upgrade I get:

```

root@myserver:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-686 linux-restricted-modules-686
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```


Jim

---

### Post by snowjunkie on 2006-02-10
Don't know if you should do this on a server, but when that happens me I normally apt-get them separately.

For example: sudo apt-get install linux-image-686

---

### Post by public_void on 2006-02-10
When that happens I just "sudo dist-upgrade", that seems to apply the updates. I'm not sure for a server install.

---

### Post by jimwillsher on 2006-02-10
I thought dist-upgrade would only apply if going between releases, e.g. Breezy to Dapper?

I just do *apt-get update *followed by *apt-get upgrade *- is this the correct thing to do?

Thanks everyone,



Jim

---

### Post by dejitarob on 2006-02-10
No I always run dist-upgade. From 'man apt':

> dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.
Actually, here is the contents of my update script I run:
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoclean

```

[This thread]("http://ubuntuforums.org/showthread.php?t=85917") on picking the right kernel might be useful.

---

### Post by jimwillsher on 2006-02-10
Excellent, thank you! I've just run your four commands (apt-get update, apt-get dist-upgrade, apt-get clean, apt-get autoclean) and apt downlaoded the latest kernel for me (2.6.12-10-686).

No other packages though, so I guess that means things like clamAV don't updates in the repositories.


Jim

---

### Post by imagine on 2006-02-10
[QUOTE=jimwillsher]My Breezy server has been running for about a month now, and I run apt-get update and apt-get upgrade on a regular basis. However, I've NEVER had any updates available.[/QUOTE]
The Ubuntu releases are (tested) snapshots of the development process, made in April and November. They aren't modified, except to fix security holes.
By upgrading to the next stable release every six months you then get all the new software from the last half year at once.

[QUOTE=jimwillsher]I thought dist-upgrade would only apply if going between releases, e.g. Breezy to Dapper?[/QUOTE]
No, **apt-get dist-upgrade** got nothing to do with switching from one Ubuntu release to another. Maybe the name is a bit misleading. If you would want to switch to Dapper or whatever, then you'd have to change your repositories in sources.list at first.

**apt-get dist-upgrade** upgrades packages like **apt-get upgrade** does, but *additionally* also changes the install status of packages if necessary, ie to satisfy dependencies it may install packages which were previously not installed and uninstall packages which were previously installed.

Example: You have the packages aaa and ccc installed, none of them have any dependencies. Now a new version of aaa shows up in the repositories, but this new version of aaa depends on package bbb, which isn't installed on your system, and aaa also has a new dependency that package ccc must not be installed.
Running **apt-get upgrade** won't do anything now, because it does neither install currently not installed packages nor does it uninstall currently installed packages. And because it cannot satisfy the dependencies of the new version of aaa, it will keep it back.
Running **apt-get dist-upgrade** on the other hand probably will install the new package bbb, uninstall ccc and then update aaa.



I don't use upgrade at home, but only dist-upgrade, since there's nothing "out-of-the-box" on my Breezy machine, ie I happily take whatever the MOTUs put in the repositories.
If you're unsure whether dist-upgrade might do something that you don't like, you can use the -s switch to simulate the process: **sudo apt-get -s dist-upgrade**

---

### Post by LordHunter317 on 2006-02-10
There's no need to simulate when it gives you a summary of exactly what it'll do, and prompts you anyway.  Just learn to read all that text first, and if you don't understand it, ask someone.

If you can't manage that, then you shouldn't be using APT at all.

---

### Post by XDevHald on 2006-02-11
[quote=LordHunter317]There's no need to simulate when it gives you a summary of exactly what it'll do, and prompts you anyway.  Just learn to read all that text first, and if you don't understand it, ask someone.

If you can't manage that, then you shouldn't be using APT at all.[/quote]


In all respect to this quote above, it's deffinently not the way to make a user feel comfortable when needing help.

The best way to understand the application, code, command or anything in general when dealing with linux, is to research your question.

No worries though, I did do the research and found this: [https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo]("https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo")

This guide will show you everything you need to know on how to use the control commands of apt-get. Just a little tip, you don't always need to know when you have updates available, just open a terminal apt-get update as root and it will do it for you, or just open the update manager and do it from there.

The update notice on the gnome-panel is useful but not always going to tell you exactly when there are updates, it does have a server respond time to when it's ready for the updates to be shown, then the icon will appear which usually takes a little bit.

Just a quick tip, be sure to do some research for your question. For your question I simple typed "How to use APT on Ubuntu" or you can easily goto: [http://wiki.ubuntu.com/]("http://wiki.ubuntu.com/")

And use the search tool on the top right corner for the keywords you need to help find your answers.

Good luck :)

---

### Post by jimwillsher on 2006-02-11
Thanks Steve.

Unfortunately much of the advice re: Ubuntu points people to options within the GUI, but I'm running Ubuntu as a webserver and mailserver so I don't have a GUI installed.

But I'm happy now that I understand the dist-upgrade. To me it sounds like it will upgrade the distribution (e.g. Breezy to Dapper) but I misunderstood it.

Thanks all!


Jim

---

### Post by LordHunter317 on 2006-02-11
[QUOTE=Steve Myers]In all respect to this quote above, it's deffinently not the way to make a user feel comfortable when needing help.[/quote]How so?  If you, as a user, are too stupid (and that's what you're being) to ask for help when you see something you don't understand, you deserve the consequences.

This is simple.  If you run a command and don't understand what it's doing, you ask.   My other point was true as well: there's no need to simulate since APT always. provides a summary of what it's going to do except in one simple case.

> No worries though, I did do the research and found this: [https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo]("https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo")

This guide will show you everything you need to know on how to use the control commands of apt-get.No, it's woefully inadequate.  It fails to explain the differences between upgrade and dist-upgrade adequately, it doesn't explain how to correct broken packages on the command line, it doesn't explain why a front-end can make life eaiser.

---

