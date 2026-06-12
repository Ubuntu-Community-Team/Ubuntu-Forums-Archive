---
title: "How can I resize a linux hdd with centos6.4(virtual) on a windows machine"
date: 2013-10-09
forum: Virtualisation
---

### Post by YH6x6Qp on 2013-10-09
Not sure if this is the right section to post this(new member)

I'm trying to shrink a linux hdd (450GB with 23GB used)so later I can clone it to another hdd. I've tried using I think most popular windows software that supposedly can read linux hdd, some do but unable to shrink or increase the partitions & space. 
Right now I'm trying to mount the 2nd hdd with linux with centos running as virtual on a windows 7 machine. Is that possible?

Thanks in advance for any replies.

---

### Post by btindie on 2013-10-10
Take a look at [GParted]("http://gparted.sourceforge.net/") which should allow you to shrink the disk. Depending on how you've got the disk laid out you may also need to move the partitions to shrink it. Just download the ISO and boot into that.

---

