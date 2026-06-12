---
title: "A Root-kit ?"
date: 2010-10-28
forum: Security
---

### Post by kliq on 2010-10-28
I have heard of root-kit viruses (I am no techie - BTW)
So looking at *top *for some other reason a short while ago I was concerned to see:
2662 rtkit     21   1 22900 1176  984 S  0.0  0.1   0:00.02 rtkit-daemon   
running not as user root or ubuntu, but as user **rtkit**
What's that all about ? !!

---

### Post by sisco311 on 2010-10-28
rtkit = RealtimeKit

[http://packages.ubuntu.com/maverick/admin/rtkit](http://packages.ubuntu.com/maverick/admin/rtkit)

---

### Post by phaed on 2010-10-28
Do you think a rootkit would advertize itself as such?  If you had a rootkit, it would probably be running as one of those gvfsd's.

---

