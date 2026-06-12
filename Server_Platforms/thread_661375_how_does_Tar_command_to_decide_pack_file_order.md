---
title: "how does Tar command to decide pack file order?"
date: 2008-01-07
forum: Server Platforms
---

### Post by steveneo on 2008-01-07
I was using Ubuntu server6.04 to run my subversion.  I used "tar czvf" to create daily backup, In 6.04, the tar always zip file in very
reasonable order,
such as
......
svn/revprops/53
svn/revprops/54
..........
svn/revs/57
svn/revs/58
svn/revs/59
svn/revs/60
svn/revs/61
.......


But whatever in ubuntu 7.04 and 7.10, tar always pack file in
unpredictable order, such as:

..........
dependencies/db/revs/94
dependencies/db/revs/98
dependencies/db/revs/53
dependencies/db/revs/117
dependencies/db/revs/62
dependencies/db/revs/122
dependencies/db/revs/1


I even copy tar command file from 6.04 to replace current one, it is
no help. It seems tar is dependent on other program or configuration
to decide the order of package.  How can I set it up?

in 6.04, tar is not simply pack in date or size order, it retrieve per
directory and for per directory, it seems using ls -ltr order.

---

### Post by steveneo on 2008-01-09
is it a tough question? seems nobody knows answer:guitar:

---

