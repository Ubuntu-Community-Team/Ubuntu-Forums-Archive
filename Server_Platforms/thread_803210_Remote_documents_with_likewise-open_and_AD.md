---
title: "Remote documents with likewise-open and AD"
date: 2008-05-22
forum: Server Platforms
---

### Post by ruiruas on 2008-05-22
I run my school's network with a windows DC and active directory and I'm trying to integrate ubuntu desktops in the network (I think its time our students learn about open-source.. :) ).

The problem is **we have a windows fileserver in wich we have the personal documents** of all users.

Likewise-open makes it very easy to join machines to the domain and integrate users, but **I can't seem to find a way to automatically mount the remote share for personal documents**.

This is important, because our students are 11-16 years old and I want to make it easy for them to use ubuntu.

Can anyone help me out?

---

### Post by shibu on 2008-05-22
try this ... you need to have samba and smbfs installed on client machine.


mount //ip-address-of-share/share-name /test/ -o username=NTdomain-name/NT-username

you can add this command to /etc/rc.local so that it runs on next reboot and it will ask NT-user password.
:)

---

### Post by ruiruas on 2008-05-23
Hi,
thanks but it didn work...
I think the problem is normal AD users aren't "admins" and therefore they can't mount devices in the system. Otherwise we could run a script to do it upon login.

Does anyone have other ideas?

Thanks

---

