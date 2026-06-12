---
title: "Deny Directory To A Specific User?"
date: 2006-12-07
forum: Server Platforms
---

### Post by maikoherajin on 2006-12-07
This is more of a general Linux security question. N00b alert. :!: 

Let's say I want to have a certain directory set up like the following:

Owned by... whoever. It probably doesn't matter.
Owner has rwx.
Group has rwx.
Others have rx.
BUT. I want to have a few regular users, obviously ones not in the group, have no access to the directory whatsoever.

I could set the group to something special and then give all the reading users membership to that group, but then they would all have write access to, which isn't what I want. In windows, I would just add the username to the directory and deny them permissions. Is there an equivilence in Linux, or some sort of workaround to achieve this? Thanks very much in advance!

---

### Post by nagilum on 2006-12-09
Since some time there exists a more advanced ACL system (POSIX Access control lists) that can do exactly what you need. It works with Ext2/Ext3 and XFS filesystems as far as I know, might also be available with some others. Here's a short tutorial I just found, hope that helps: [http://tlug.dnho.net/?q=node/171](http://tlug.dnho.net/?q=node/171)

---

