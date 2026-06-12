---
title: "How are the default permissions handled in vanilla Ubuntu?"
date: 2013-08-08
forum: Security
---

### Post by Ranko Kohime on 2013-08-08
When using a LiveUSB/CD/DVD or fresh installation of Ubuntu desktop, the first user can, without authentication, (i.e., not elevating to root privileges), connect and disconnect the network via nm-applet, change network settings, mount and un-mount USB drives, and a variety of other tasks which cannot be done on an installation from the mini ISO without authentication.

So what exactly grants permissions to the user?  I've read a variety of conflicting information via Google, (likely some of it out of date), regarding polkit and ConsoleKit.

My question is regarding 13.04, but I would be interested in knowing how far back the current scheme goes.

---

### Post by Cheesemill on 2013-08-08
The user does need to authenticate and gain root privileges to carry out any of the tasks that you expect, however, because the user has a blank password then this happens without a password prompt appearing.

---

### Post by Ranko Kohime on 2013-08-08
Well, this occurs on an installation, where a password is set, as well.  The primary user can mount/un-mount USB drives, change network settings, etc., without being prompted for their password.

---

