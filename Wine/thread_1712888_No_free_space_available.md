---
title: "No free space available"
date: 2011-03-23
forum: Wine
---

### Post by Iliya Gurov on 2011-03-23
Hello,

I have a fresh copy installation of wine and I am trying to run win version of matlab 2009 under ubuntu 10.10. The problem is that the installation GUI of the program shows that I have 0MB available space, even though the output of df is:

/dev/sda3             24849528  15733548   7853696  67% /
none                    507148       300    506848   1% /dev
none                    512748      2612    510136   1% /dev/shm
none                    512748       264    512484   1% /var/run
none                    512748         0    512748   0% /var/lock
none                  24849528  15733560   7853684  67% /var/lib/ureadahead/debugfs
/dev/sda1             32394596   5926324  26468272  19% /media/35D0EBA8E9A783F9


Any held would be appreciated. Thanks in advance!
Iliya

---

### Post by cogadh on 2011-03-23
It's a known bug in Wine:
[http://bugs.winehq.org/show_bug.cgi?id=25451](http://bugs.winehq.org/show_bug.cgi?id=25451)

---

