---
title: "Chkrootkit Results--Compromised??"
date: 2012-10-02
forum: Security
---

### Post by abimael08 on 2012-10-02
Hmmm, Ive ran Rkhunter and Chkrootkit plenty of times and never came up with this output at the end. 


Can anyone help?

---

### Post by Laiquendi on 2012-10-04
It's **probably** chkutmp **false** positive. Common bug a few years ago, but I couldn't find any solution to this.
Run another rootkit scanner to be sure.
If it's false, try to find the solution for this false positive.

EDIT:
I've found the solution here
```
https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=513029
```

---

### Post by Stonecold1995 on 2012-10-04
It looks like a bug.

[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/623144]("https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/623144")

---

