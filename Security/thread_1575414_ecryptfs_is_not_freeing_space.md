---
title: "ecryptfs is not freeing space?"
date: 2010-09-15
forum: Security
---

### Post by damatta on 2010-09-15
I used ecryptfs on a Private directory. It has about 5GB of data, but no matter what I do I can't free space in there. I have tried to delete some GBs to no avail. System monitor still shows me 5GB.
Is this a bug or something?

---

### Post by FuturePilot on 2010-09-15
Yes, it is a bug in a way. When you have a single directory encrypted with ecryptfs, such as ~/Private, it is not able to display files that have been moved to trash in the trash. You'll have to manually delete them from ~/Private/.Trash

---

### Post by damatta on 2010-09-15
Problem solved, thanks!

---

### Post by cavva on 2011-05-26
Dear [damatta]("http://ubuntuforums.org/member.php?u=350623"),
how have you solved?
I am experiencing the same issue about ecryptfs but I do not find any .Trash in Ubuntu 11.04.
Thank you in advance

---

