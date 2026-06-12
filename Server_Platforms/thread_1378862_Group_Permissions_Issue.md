---
title: "Group Permissions Issue"
date: 2010-01-11
forum: Server Platforms
---

### Post by PCNewb on 2010-01-11
Hey guys.  First time poster.  

I'm new to Linux and Ubuntu and have recently set up a server for a client needing simple, secure file sharing.  I created separate user accounts and a group which they all belong to.  I made a shared folder on one of there accounts and set group ownership and a umask of 0007 which should make it so new files are created with createrowner:  Full, Group:  Full, Other:  None.  I have tried a few dozen walkthroughs and believe it should work as it's set up, yet for some reason newly added files have the following permissions:  createrowner:  Full, Group:  Read, Other:  Read.  I need them to all be able to read, write and execute.  Any suggestions would be much appreciated.  Thank you.  

Dave.

---

