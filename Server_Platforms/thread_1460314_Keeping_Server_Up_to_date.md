---
title: "Keeping Server Up to date"
date: 2010-04-22
forum: Server Platforms
---

### Post by stevetmlp on 2010-04-22
Hello all,

Fairly new to Ubuntu server. Was curious about keeping a running system up to date. Can any harm come from running the following:

sudo apt-get update

sudo apt-get upgrade

What I mean is, is it possible that doing the above could cause a perfectly healthy system to go foobar? If so, what's the best way to prepare a system for a recovery. The Server in question is a Hardy BIND server. In the past, I've seen some ugly things happen to Windows systems after running updates, so I'd like to err on the side of caution.

Thanks,

---

### Post by jaco223 on 2010-04-22
I know a lot of people here will maintain a separate partition for system
backup purposes, but AFAIK I don't think you could go wrong with the
upgrade command as long as you're not getting the *bleeding edge *stuff
by using non-standard repositories.

Hope this helps.

Jaco

---

### Post by BobVila on 2010-04-22
It's always *a possibility *that something could go wrong, but it's far from likely. You'll probably find yourself being less fanatical about updating in practice than you are in theory, as well. 

IMO, comparing an apt-get upgrade to running a round of Windows Updates is like comparing a teeth cleaning to a root canal.

---

### Post by amauk on 2010-04-22
There's almost zero risk when doing SRUs (Stable release updates)
Upgrading to a newer release is more time consuming, but again relatively pain free

Make sure you tell users before hand before doing any updates (it's always a good idea to do things out of hours anyway), as some updates will restart services (Samba, Apache, MySQL, etc.)
so you want to make sure no-ones doing anything important at the time

Also, keep a backup of /etc so if you need to rollback, you can also rollback your config files

---

### Post by tgalati4 on 2010-04-22
There are several ways to approach this:

Upgrade once every 6 months--that results in hundreds of updates which increase the chance of breakage.

Upgrade weekly--If it breaks, you may know right away, and you will have narrowed down the suspects.  You only need to reboot with kernel and xorg updates.  Just about everything else can be done while in production mode.

Plan some down time to handle any potential breaks.  You will need time to search the internet, the forums, file a bug if necessary.  Don't perform a hundred updates on a Friday afternoon, then leave the office for the weekend.  That will guarantee a busy weekend.

If you stick with an LTS, then the updates tend to be farther apart in the out years.

It's helpful to define tests (or procedures) that test your system after a bunch of updates to make sure that all your business services are still working.

---

