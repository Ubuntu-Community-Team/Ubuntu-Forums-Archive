---
title: "/dev/tty Ownership"
date: 2005-01-24
forum: Server Platforms
---

### Post by EternalNewbie on 2005-01-24
Hi,
    I am having a bit of trouble running the Poplog Virtual Machine on Warty.

[http://www.cs.bham.ac.uk/research/poplog/freepoplog.html](http://www.cs.bham.ac.uk/research/poplog/freepoplog.html)

    It can access its files OK but has trouble running commands from the terminal, not a lot of trouble but enough. I have installed it on Debian Unstable and it is OK there.

     I have gone through the configuration files for terminals, shells etc.  and the only thing I noticed is that when I login and look at /dev

Debian  -------   agley agley   tty0
                       agley tty       tty1

Warty    --------   root root      tty0
                        root root      tty1

    Why don't I get ownership of the terminal on Warty ? Is it because of the sudo business or do the newer set-ups only use /dev/pts , I am confused !

                                                          Thanks for any help,
                                                                  John Duncan

---

