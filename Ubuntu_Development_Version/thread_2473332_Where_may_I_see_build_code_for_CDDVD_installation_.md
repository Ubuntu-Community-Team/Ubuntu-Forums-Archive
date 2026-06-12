---
title: "Where may I see build code for CD/DVD installation media?"
date: 2022-04-01
forum: Ubuntu Development Version
---

### Post by and-account on 2022-04-01
Hi!

In what a repos may I find a code which is in use for CD/DVD packaging of development version of Ubuntu or derivatives?

There are good articles at [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) and [https://wiki.debian.org/](https://wiki.debian.org/)
It works, I built my custom ISO.

However, I'm curious - where is stored code to be used for packaging of Ubuntu ISO images? Want to have a look and compare.

Thank you!

---

### Post by guiverc on 2022-04-01
Ubuntu ISOs are build on [launchpad]("https://launchpad.net/ubuntu-cdimage") which are kicked on by request or *cron* job, and use seed files, eg. [https://people.canonical.com/~ubuntu-archive/seeds/lubuntu.jammy/desktop](https://people.canonical.com/~ubuntu-archive/seeds/lubuntu.jammy/desktop) is the Lubuntu seed.

You'll find some code in the link I provided if you look, but *launchpad* is a system in itself, so it's rather *complex*. If I need to find, or look at something, I generally just follow a guide/doc, but there are many of those - each geared for the team they're written for.

---

