---
title: "Samba Permissions Issue 8.04 Server"
date: 2009-03-08
forum: Server Platforms
---

### Post by twinpeaksr on 2009-03-08
I have somehow managed to create a 80% functional Samba Server Despite being new to Linux (with no GUI!) however I am still having some permissions problems.  I have 2 users, Myself is one and user 2 is the other, and each of us has a directory.  Problem is that I can access my directory, and user 2's but user 2 can not access their own directory.  I have the shares setup with the same options (Using Webmin for access) only difference is the users that are able to have access to the directories, User 2 is added to their directory.

User 2 can read from the directory but not right, I can write to user 2 directory without issue.  Any idea what is wrong?  I am concerned it is not with Samba, but with the permissions on the directory since I originally created that directory.

Any help would be appreciated.  Thanks!

---

### Post by Iowan on 2009-03-08
I'd suggest checking the permissions at the directory level, but this will mean getting up-close-and-personal with the CLI - you willing?

---

### Post by twinpeaksr on 2009-03-15
I am always up for a challenge...

---

