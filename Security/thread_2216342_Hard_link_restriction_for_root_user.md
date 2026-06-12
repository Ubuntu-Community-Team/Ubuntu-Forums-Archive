---
title: "Hard link restriction for root user"
date: 2014-04-11
forum: Security
---

### Post by lisandro78 on 2014-04-11
I had trouble yesterday making a [Cassandra snapshot]("http://wiki.apache.org/cassandra/NodeTool"), which would fail due to an "Operation not permitted" FS error when trying to hard-link files. This used to work until recently.

The solution was to temporarily disable [FONT=courier new]kernel.yama.protected_nonaccess_hardlinks[/FONT] as suggested [here]("http://stackoverflow.com/a/22032658/442724").

Explanation about this restriction I found [here]("https://wiki.ubuntu.com/Security/Features#Hardlink_restrictions"):

> [COLOR=#333333][FONT=Ubuntu Beta]In Ubuntu 10.10 and later, hardlinks cannot be created to files that the user would be unable to read and write originally, or are otherwise sensitive.[/FONT][/COLOR]

I ran nodetool as root user, to act on files stored in [FONT=courier new]/var/lib/cassandra/data[/FONT], owned by user [FONT=courier new]cassandra[/FONT]. My question is this: **why am I unable to hard link these files as root?**

---

### Post by Danger_Monkey on 2014-04-21
Are your snapshots in a different file system?  If they are, the OS will get confused on the inode numbers, and won't permit it.  I was trying to do the same thing from /opt to /var...

---

### Post by lisandro78 on 2014-08-06
@Danger_Monkey, thanks for your reply and sorry for not noticing it before.

> **Danger_Monkey said:**
> Are your snapshots in a different file system? If they are, the OS will get confused on the inode numbers, and won't permit it. I was trying to do the same thing from /opt to /var...

As it turns out, there were a few files deep beneath [FONT=courier new]/var/lib/cassandra/data[/FONT] that were root-owned, hence the hard link protection issue. I wonder how did those get in there...

Anyway, the issue is solved. Maybe this helps others.

---

