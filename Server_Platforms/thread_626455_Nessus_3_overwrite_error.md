---
title: "Nessus 3 overwrite error"
date: 2007-11-29
forum: Server Platforms
---

### Post by The Tronyx on 2007-11-29
Hello everyone, I was hoping to install the newest version of Nessus as the one in the repos is a bit dated, however I have run into some problems.
> 
sudo dpkg -i Nessus-3.0.6-debian3_i386.deb
(Reading database ... 134775 files and directories currently installed.)
Unpacking nessus (from Nessus-3.0.6-debian3_i386.deb) ...
dpkg: error processing Nessus-3.0.6-debian3_i386.deb (--install):
 trying to overwrite `/etc/init.d/nessusd', which is also in package nessusd
Errors were encountered while processing:
 Nessus-3.0.6-debian3_i386.deb

At the suggestion of another user I have tried "sudo apt-get install -f" but with no success.

I understand the error message (at least I think) but not why.  There is no /etc/init.d/nessusd on my system that I could find.  I might be overlooking the obvious on this one but a kick in the right direction would be much appreciated.

Thanks!

---

### Post by The Tronyx on 2007-11-29
Please disregard this post.

---

