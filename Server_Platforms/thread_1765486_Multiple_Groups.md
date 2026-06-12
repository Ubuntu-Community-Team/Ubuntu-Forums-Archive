---
title: "Multiple Groups"
date: 2011-05-23
forum: Server Platforms
---

### Post by benzies on 2011-05-23
Hi There

Looking for a way to add multiple groups to a folder.  This feature is obviously available in most other platforms (Mac, Windows).

Why can't I find any reference to this, or better yet, why doesn't this feature exist?

Thanks in advance.

---

### Post by Lars Noodén on 2011-05-23
You can make a directory belong to multiple groups by mounting the relevant partition with POSIX Access Control Lists (ACL) activated.  There is really very little documentation on it probably because of the combination that few know about it and it is easy to do.

The programs to work with ACLs, once the file system is mounted to support them, are **getfacl** and **setfacl**.

[http://www.vanemery.com/Linux/ACL/linux-acl.html](http://www.vanemery.com/Linux/ACL/linux-acl.html)

[http://linuxmafia.com/faq/VALinux-kb/acls.html](http://linuxmafia.com/faq/VALinux-kb/acls.html)

---

### Post by HermanAB on 2011-05-23
Yup, ACLs.  However, these things are not used much since they are a PITA to manage when users come and go.  Maybe rather look at the features of AppArmor.

---

### Post by Lars Noodén on 2011-05-23
> **HermanAB said:**
> Yup, ACLs.  However, these things are not used much since they are a PITA to manage when users come and go.  Maybe rather look at the features of AppArmor.

Yep, it's about setting **group** permissions, not *user* permissions.  Setting things on a per-user basis is a quick way to make it a PITA, though.

ACLs are easy to use, just not (yet) part of the pool of common knowledge.

---

### Post by 1serveyou on 2011-06-04
> **Lars Noodén said:**
> Yep, it's about setting **group** permissions, not *user* permissions.  Setting things on a per-user basis is a quick way to make it a PITA, though.

ACLs are easy to use, just not (yet) part of the pool of common knowledge.

What is the best way for a home user budget, to control a network with under 10 users, but having some users see/access some files and others not. I'll be using Samba as there are Ubuntu/Mac OSX/Win 7 computers on this network. I have some situations where I have a folder called "music" but I only want some users to see some of the folders inside of it, and others to see all.

---

### Post by HermanAB on 2011-06-04
Make a group called music.  Set the folder to that.  Make certain users members of that group. La voila!

---

