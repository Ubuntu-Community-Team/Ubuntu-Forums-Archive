---
title: "Why there is no full backup software integrated into ubuntu one"
date: 2012-11-29
forum: Ubuntu One (CLOSED)
---

### Post by Cenko on 2012-11-29
Hello,

This is not a issue, more of a general question mostly to developers. I use ubuntu one since some time, synced my Documents folder, and I'm quite happy with it.

I smashed my laptop to table 2 times this year(angry times you know, losing a game, slow internet etc.) both of which resulted with hard disk failures, and I had to replace HDD and reinstal ubuntu.

Whenever I install ubuntu, I run some commands that bring my usual system back. There is one line of "sudo apt-get ..." with all apps I need, then a script to sync my home folders from an external drive, then I manually set git to install some config files from my github, install some programs from source that don't exist in software center and finally I have to manually set all my desktop shortcuts (couldn't find a way to do it automatically)

The whole process takes few hours, and considering you don't reinstall ubuntu everyday, its not a huge deal.

However! I would like to be able to do all of these with 1 click. Why there is no backup software that is integrated with ubuntu one, that can do the following stuff:

- Backup keyboard shortcuts.
- Backup desktop settings (launcher behaviour, icons etc.)
- Backup .bash* like configuration files.
- Backup installed apps from software center (Only the names and software center links)

Then when we do a fresh install, you can open ubuntu one, click on "restore my ubuntu" and voaila!

It can be used to reinstall the current version of ubuntu, or upgrade to a newer version, to have a clean install (I prefer clean installs).

One thing that comes to my mind is when you backup in ubuntu 12.04 and restore in ubuntu 12.10, there may be some incompatibility due to version change (some apps not existing anyomore, change in desktop behaviour), but I don't see it as a huge problem.

I'm not a developer and there may be some other problems with what I propose, I'd be happy to hear all.

Note: As I remember linux mint has a backup solution that does some of these, but I don't know how good it works.

---

