---
title: "Linux distributions and such?"
date: 2010-11-25
forum: The Cafe
---

### Post by HeZ on 2010-11-25
Hi all i'm new to the nix world. 
Just finished my first year of software engineering and thought it is high time to move away from Microsoft.

Can any1 give me the quick rundown of what distributions there are and how they differ?
Eg i know OSX runs on darwin
my maemo phone runs on fremantle
i have heard the names QT and redhat and all the *untu's and gentoo etc etc

Is a couple fundamental distributions that everything else is build on or are they all independent of each other?
The ones that are independent of each other, is there a great difference in the syntax of commands and such? 
like there is a huge difference between using the command prompt on win7 and x terminal on my phone.

I have Ubuntu installed on my laptop (the only 386 i own) but i would like to have a dual boot/use vm to use linux on my desktops/server which are all intel 64bit.
Can anyone suggest a good distribution to use?

Thanks
HeZ

---

### Post by Rondonjin on 2010-11-25
There's a brief description of each distro here:

[http://distrowatch.com/](http://distrowatch.com/)

Download a a few of the most popular LiveCDs and take them for a spin.

---

### Post by Sean Moran on 2010-11-25
> **HeZ said:**
> Hi all i'm new to the nix world. 
Just finished my first year of software engineering and thought it is high time to move away from Microsoft.

Can any1 give me the quick rundown of what distributions there are and how they differ?
Eg i know OSX runs on darwin
my maemo phone runs on fremantle
i have heard the names QT and redhat and all the *untu's and gentoo etc etc

Is a couple fundamental distributions that everything else is build on or are they all independent of each other?
The ones that are independent of each other, is there a great difference in the syntax of commands and such? 
like there is a huge difference between using the command prompt on win7 and x terminal on my phone.

I have Ubuntu installed on my laptop (the only 386 i own) but i would like to have a dual boot/use vm to use linux on my desktops/server which are all intel 64bit.
Can anyone suggest a good distribution to use?

Thanks
HeZ
There used to be a difference between the RedHat and Debian filesystem strucutures, but (although I'm no expert on the progressions over past years) Ubuntu seems to have embraced the Debian system with the RedHat filesystem that I recognise.

Basic terminal commands are roughly all the same.  Remember that Windows' 'dir' is 'ls' in Linux, and everything is a forward slash, rather than a backslash, and ALWAYS add a space after you type 'cd'. because 'cd..' works in Windows, but not in Linux.  Type 'cd' SPACE '..'.

That's about all there is to it to get by.


---o0o---

If at first you don't succeed, try "sudo nautilius" and you should have a nice 'explorer-like' file browser with ROOT privileges, so take care,

---

### Post by HeZ on 2010-11-25
Cool so i got ubuntu going on my laptop, just playing around with the terminal. Whats the deal with root and sudo root?
In osx (yuck i hate mac i wish i didn't know anything about it) i know you just type root and password to access the terminal with root privileges
But i try typing root in ubuntu it says its not installed...

---

### Post by 3Miro on 2010-11-25
DO NOT USE "SUDO NAUTILUS". For graphical applications the correct way is:
```
 gksudo nautilus 
```

---

### Post by Oxwivi on 2010-11-25
In the *buntus, there's no default root. Root level privileges are obtained by entering sudo before the command. You are asked to enter the password of admin user, and the command then runs at root-level.

You can also setup a root account, for that and everything about Linux, Google is your friend.

---

### Post by Verbeck on 2010-11-25
> **HeZ said:**
> Cool so i got ubuntu going on my laptop, just  playing around with the terminal. Whats the deal with root and sudo  root?
In osx (yuck i hate mac i wish i didn't know anything about it) i know  you just type root and password to access the terminal with root  privileges
But i try typing root in ubuntu it says its not installed...


you can access a root shell by 
```

sudo -i
```

---

### Post by HermanAB on 2010-11-25
Howdy,

Linux is Linux is Linux...

However, there are three package management systems in use which results in three families: Redhat, Slackware and Debian.  Ubuntu is in the Debian family.

---

### Post by kaldor on 2010-11-25
> **HeZ said:**
> Cool so i got ubuntu going on my laptop, just playing around with the terminal. Whats the deal with root and sudo root?
In osx (yuck i hate mac i wish i didn't know anything about it) i know you just type root and password to access the terminal with root privileges
But i try typing root in ubuntu it says its not installed...

Mac OS X is great; it's a _certified UNIX OS_. The terminal commands on OS X are very very similar to Linux's.

in Ubuntu, Root is disabled by default in favour of "sudo". Sudo allows normal users to execute commands as if they are root. When running CLI-only commands (mv, cp, rm, all that) use sudo if needed. For graphical applications, as stated before, use gksu; that runs a graphical program using sudo.

For a home/desktop PC, I recommend Ubuntu, Mint, Fedora or other desktop-oriented distros.

For a 64-bit server, try CentOS 5.5 (or better yet, wait a few weeks for CentOS 6) since it's a Free version of RedHat's Enterprise Linux OS and is the "industry standard" for Linux servers.

---

### Post by 3Miro on 2010-11-25
> **HermanAB said:**
> 
However, there are three package management systems in use which results in three families: Redhat, Slackware and Debian.  Ubuntu is in the Debian family.

There is also Arch's pacman system as well as Gentoo's portage and there are others. The different distros differ in more than just package management. OpenSusa is Slackware based, but it uses rpm packages.

Underlying file-system structure, different system tools and more importantly philosophy have more to do with defining a distro than the package system.

---

### Post by Johnsie on 2010-11-25
Jolicloud is  nice OS based on Ubuntu but better looking and easiser for beginners to use and install.

---

### Post by kaldor on 2010-11-25
> **3Miro said:**
>  OpenSusa is Slackware based, but it uses rpm packages.

SuSE was forked from Slackware so long ago that it is no longer considered Slackware-based. The current openSUSE release is based on a version of Slackware from the mid-90's. 

- Ubuntu takes a snapshot of Debian every 6 months and continues from that.

- RedHat takes a Fedora release, polishes it up, fixes stuff, adds features and releases it.

- SuSE was a German release of Slackware, but instead of using Slackware as a base it continued on its own way. It's not been a "Slackware variant" since the mid to late 90's. Distrowatch even has it listed as Independent.

;)

---

### Post by 3Miro on 2010-11-25
> **kaldor said:**
> 
- SuSE was a German release of Slackware, but instead of using Slackware as a base it continued on its own way. It's not been a "Slackware variant" since the mid to late 90's. Distrowatch even has it listed as Independent.


I saw that Susa was a Slack fork on Wikipedia's Linux distro three. I was a bit surprised, since I had seen no similarities between the two. Having been forked so long explains it.

Either way, Susa is a non RedHat distro using rmps.

---

### Post by Spice Weasel on 2010-11-25
Fun fact: PCLinuxOS forked from Mandrake, but this seems completely pointless because they changed nearly everything - even the package manager. Mandrake is a fork of Red Hat Linux (pre RHEL).

Slackware is a fork of SLS, which in turn was a fork of MCC Interim - the first GNU/Linux distro.

Innit funny how the world of free software works. :P

---

