---
title: "This software Komodo Edit need working on all versions of Ubuntu...why?"
date: 2022-02-08
forum: Ubuntu Development Version
---

### Post by aleksandrposs on 2022-02-08
[ATTACH=CONFIG]289986[/ATTACH]
Komodo Edit (last version is 12) - this software need for web-development on linux operation systems...And in internet people can download this software last 12 years..now 2022 year.
This software Komodo Edit need working on all versions of Ubuntu..and need can install from deb packages on all Ubuntu versions (and Xubuntu, Kubuntu, Lubuntu)...

Why I can't install Komodo Edit 12 on Ubuntu 22.04 (beta) from deb-package with next command:
> apt install komodo-edit
?

---

### Post by howefield on 2022-02-08
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by schragge on 2022-02-08
Because it's not in the repos, and [the PPA ceased to provide packages after Xenial]("https://launchpad.net/~mystic-mirage/+archive/ubuntu/komodo-edit"):
> Update 2016-08-26:
Sorry, guys! No more updates here.  I'm not using Komodo Edit anymore and today I am not able to build a  new version of Komodo Edit. And I have no time to solve this. It has  become too hard to support this PPA.
If you feel this is an important piece of software that must be present in Ubuntu, package it yourself.

---

### Post by aleksandrposs on 2022-02-10
And is NetBeans software for web-development on linux (and ubuntu) operation systems.....Great situation will be in world..if on my ubuntu (xubuntu, kubunu, lubuntu, etc) I can start NetBeans web-development editor and this is great for world if more linux users can start and use **NetBeans** on last versions of Linux operation systems as "**install from deb-package**".

---

### Post by QIII on 2022-02-10
What is available in the repo for any given release of Ubuntu is fixed at release time unless there is a security update.  Ubuntu is not a rolling release, so version updates of software do not show up in the repos.

If you want the latest, you can download the installation file at [https://netbeans.apache.org/](https://netbeans.apache.org/)

You seem to have the misapprehension that Canonical is under obligation to provide any and every application anyone could want in their repositories.  They are under no such obligation.

---

