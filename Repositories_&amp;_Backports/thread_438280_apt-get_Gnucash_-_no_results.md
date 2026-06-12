---
title: "apt-get Gnucash - no results"
date: 2007-05-09
forum: Repositories &amp; Backports
---

### Post by AthurDent on 2007-05-09
when I try to use apt to install gnucash I get the following:

marco@ubuntu:~/Installs/gnucash-2.0.5$ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnucash

It does not seem to be in my repositories.

How do I remedy?

- Marco

---

### Post by mazirian on 2007-05-09
gnucash is the package name, perhaps you don't have all the repositories enabled in your /etc/apt/sources.list.  You need to enable the "universe" packages.  After doing so, you'll need to run aptitude update.

---

### Post by AthurDent on 2007-05-11
Thanks it worked. Only it installed GNUCash version  1.8.12 while the latest stable release according to the website is 2.0.5. Normally I would not be to hung-up on versions until I know what I'm doing, but they say there is a lot of bug fixes done in the new release and I already see a couple of irritating bugs!

---

### Post by mazirian on 2007-05-11
That old version is not even in the feisty package repository.  Apt is not configured correctly for you somehow or you packages pinned oddly.  Would you post your sources.list please?  

You certainly do want version 2 of gnucash, as it's a vast improvement over the old.  The stable version for feisty is 2.0.2 which is fine.  You may compile 2.0.5 if you think it addresses a recent bug that is critical, but I don't think that is the case.

---

