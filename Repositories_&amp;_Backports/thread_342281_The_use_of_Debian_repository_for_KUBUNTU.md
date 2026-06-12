---
title: "The use of Debian repository for KUBUNTU"
date: 2007-01-19
forum: Repositories &amp; Backports
---

### Post by Andrew Panin on 2007-01-19
Good day, community! :-)

The situation is as the following:
1. I have Kubuntu 6.06 installed on my PC
2. I need to extend the collection of existed
   software.

Possible ways:
1. Do this via Internet
2. Use a set of two DVD with Debian that I have.
   They contains a huge collection of .deb packages.

But I met a problem for the each of way:
1. I configured KPPP properly (specified modem settings,
   my login and password), but it fails to establish connection.
   Suppose some configuration files in /etc/ppp to be edited.
   I tried to use WVDIAL. Helps, but anyway the speed is too slow
   even to get the packages list (sudo apt-get update).

   So, the only way for me is to try to use Debian DVDs. But:

2. I used "sudo apt-cdrom add" for each DVD. Then, run aptitude.
   And I saw a lot of warning messages, that the packages are from
   "untrusted source" and so on. On a whole, I couldn't install anything.

Can you help me? I'd like to know whether it's possible to use that
Debian software collection, or Kubuntu refuses it? If they can be
used, then how (briefly)?

Thanks before.

---

### Post by aysiu on 2007-01-20
The "untrusted source" thing has nothing to do with it being Debian (as opposed to Ubuntu). It has to do with keys that are signed... don't worry about that for now.

Can you use Debian repositories in Ubuntu? Well, the general consensus is that you can but that your system will eventually break if you keep updating, but since you don't have an internet connection, you probably won't keep updating.

To be safe, I'd [back up your current installation](http://www.psychocats.net/ubuntu/backup), then use the Debian DVDs. If it breaks, you can restore the backup. If not, you can keep using it.

If it does break, though, I would just go ahead and install Debian. Why not?

---

