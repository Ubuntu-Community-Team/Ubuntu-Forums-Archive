---
title: "problems in istalling wine 1.2.2 on ubuntu 10.10"
date: 2011-04-09
forum: Wine
---

### Post by fedbuntu on 2011-04-09
Hello everyone. Am new to this forum and need some help.
Was installing wine 1.2.2 on ubuntu 10.10 
my home folder had 60GB of free space before the installation started
I chose to install manually.
I installed all the dependencies. Then compiled wine 1.2.2 from the source code using
./configue
make
While running the 'make' process my 60GB home folder ran out of disk space. The make process was non ending. Ultimately it got aborted due to lack of space.
Can't retrieve disk space that was lost since then. Tried with terminal commands like
apt-get clean
apt-get autoclean
apt-get autoremove
Even tried to get into the wine source folder from terminal and use 'make uninstall'
Nothing works and I now have only 50Mb of disk space on my home folder

Please help me
Thanks to all in advance.......

---

### Post by howefield on 2011-04-09
Thread moved to the "*Wine*" forum.

---

### Post by IHeequ5i on 2011-04-09
IIRC /tmp contains temporary files created when the system needs them. Someone PLEASE correct me if I'm mistaken.

If I'm right, you might want to cd to /tmp and manually delete everything there.

But why were you trying to compile wine yourself rather than download the package from the WineHQ page?

---

### Post by cwwilson721 on 2011-04-09
> **Doomspark said:**
> IIRC /tmp contains temporary files created when the system needs them. Someone PLEASE correct me if I'm mistaken.

If I'm right, you might want to cd to /tmp and manually delete everything there.

[COLOR="Red"]But why were you trying to compile wine yourself rather than download the package from the WineHQ page?[/COLOR]

Or, even easier, from the Software Center?

---

