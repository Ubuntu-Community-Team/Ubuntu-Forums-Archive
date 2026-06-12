---
title: "best backup solution"
date: 2017-08-17
forum: Security
---

### Post by davidtuti2 on 2017-08-17
Hi,
I would like to make a backup/restore point of my ubuntu. What is the best solution?
I think to make a clonezilla image but I don't know if there is best way.

Thanks and sorry for my English!

---

### Post by TheFu on 2017-08-17
"Best" is highly subjective.  

There are best practices for backups and making an image is NOT the best practice.

Backups should be:
* stable - works every time
* automatic
* versioned
* different storage media
* efficient (storage, network)
* encrypted
* verified/tested restores

Images don't really work with versioned backups.  They eat too much storage, they aren't efficient to make or to store.  To make an image, booting from alternate media (almost always) is required.

This question has been asked and answered here many, many, times.  
[https://askubuntu.com/questions/2596/comparison-of-backup-tools](https://askubuntu.com/questions/2596/comparison-of-backup-tools) has some options.  There is also a Community Backup Page - which I disagree with.  rsync and tar aren't not good system backup choices for a number of reasons.

If you review some of the existing threads and have specific questions about a tool, perhaps someone can answer.

For most end-users, making a backup of your HOME and /etc/ is about all that is needed. It doesn't get everything, but it does get most things.  Only Windows has an idea of a "restore point" - that isn't how any other OS works.

---

### Post by martialartist81 on 2017-09-05
A little late to answer this, but I'll toss in my two cents:

- If you're on 16.04 or later (Desktop), they've got a built-in "Backups" program that will assist you in creating and helping to use to restore backups of your machine.  That's the simplest, less "manual" process that I'm aware of.
- If you're willing to dig a little, read and test, Veeam now offers a Linux Backup version.  I've been using Veeam for the Enterprise (backing up Server and Desktop VMs as well as bare-metal servers) for a couple of years now (bare-metal was just recently released).  It's fantastic.  [Here]("https://www.veeam.com/linux-backup-free.html") is the site for it.

---

### Post by HermanAB on 2017-09-07
First of all, backup your data.

Backing up the whole Linux system is not very useful, since it is very easy to install a fresh system.  It is actually easier to re-install a new system than to restore an old tired outdated system from a full backup.

---

