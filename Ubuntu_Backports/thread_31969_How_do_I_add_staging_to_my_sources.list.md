---
title: "How do I add staging to my sources.list?"
date: 2005-05-05
forum: Ubuntu Backports
---

### Post by Tracey Lowndes on 2005-05-05
Hi, I'd like to get some packages from staging in the Hoary backports. How do I edit my sources.list to enable me to do so?

At the moment my backports repositories look like these:

```
deb http://backports.ubuntuforums.org/backports/ hoary-backports main universe multiverse restricted 
deb http://backports.ubuntuforums.org/backports/ hoary-extras main universe multiverse restricted 

```

Thanks in advance.

Tracey Lowndes.

---

### Post by bored2k on 2005-05-05
Open a terminal and type:
```
sudo cat deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-backports-staging main universe multiverse restricted >> /etc/apt/sources.list && sudo cat deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras-staging main universe multiverse restricted >> /etc/apt/sources.list && sudo apt-get update ; echo That is it
```

That should work :-|

---

### Post by XDevHald on 2005-05-05
bored2k, I have searched all over for this error and can't seem to find it myself

W: Duplicate sources.list entry [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages)

I must not being looking hard enough?

**Edit$ ~ **Ok Found it :D

---

### Post by bored2k on 2005-05-05
[QUOTE=BB]bored2k, I have searched all over for this error and can't seem to find it myself

W: Duplicate sources.list entry [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages)

I must not being looking hard enough?

**Edit$ ~ **Ok Found it :D[/QUOTE]
 I lost my Magic Guessing Repository Wand, so could you post your sources.list ?  :-)

---

### Post by XDevHald on 2005-05-05
> **bored2k]Open a terminal and type:
```
sudo cat deb [http://backports.ubuntuforums.org/backports/]("http://backports.ubuntuforums.org/backports/") hoary-backports-staging main universe multiverse restricted >> /etc/apt/sources.list && sudo cat deb [http://backports.ubuntuforums.org/backports/]("http://backports.ubuntuforums.org/backports/") hoary-extras-staging main universe multiverse restricted >> /etc/apt/sources.list && sudo apt-get update  said:**
> 
 Hey bored2k, here's the post again lol.

I get the following error when updating...

> W: Duplicate sources.list entry [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages)

I feel like a n00b but I am really lost when trying to fix this, I don't want to mess anything up, even if I know where it's at.

Also, here is my sources.list.

[quote]deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") stable main
deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") unstable main
deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") testing main

deb [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-extras main universe multiverse restricted

deb [http://backports.ubuntuforums.org/backports/]("http://backports.ubuntuforums.org/backports/") hoary-backports-staging main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports/]("http://backports.ubuntuforums.org/backports/") hoary-extras-staging main universe multiverse restricted

**Edit$ ~ Ok fixed it :D**

---

### Post by jdong on 2005-05-05
Don't worry about that error -- it just means that you somehow included Universe twice in the sources.list.

You can safely ignore it -- nothing bad will happen!

---

