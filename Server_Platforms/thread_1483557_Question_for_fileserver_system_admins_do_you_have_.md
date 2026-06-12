---
title: "Question for fileserver system admins: do you have group naming conventions?"
date: 2010-05-14
forum: Server Platforms
---

### Post by samosamo on 2010-05-14
At work we make use of UNIX filesystem permissions to define who can read/write.  Over the years, these groups have gotten kind of messy.  There are ~100 groups and no naming convention. It's hard to determine exactly what the group is and where on the filesystem is the data that belongs to it.

Do any system admins have any naming conventions they use when creating groups? For backwards compatibility with older Solaris applications we stick to the legal length of 8 characters, so we must keep this in mind.

For example, we have a server that a marketing office uses. The group that has write access is called "marketng".  Who came up with that?  I have no idea.  The Managers directory within it, that only the managers can write to?  The group is called "mktgmgrs".  There are ~100 examples and they are all ugly because there is no standard to naming them.  We are planning on expanding and it's going to get even worse if these 100 groups turn into 200 or 300 within the next year.

---

### Post by lavinog on 2010-05-16
I would standardize the names to where chars 1-4 is a dept code (MKTG). 5 can be for special authority like M for management, N for none. 6-8 can be a location, phone extension, extra ID (in case a department splits up later) or other info that might be handy.

---

