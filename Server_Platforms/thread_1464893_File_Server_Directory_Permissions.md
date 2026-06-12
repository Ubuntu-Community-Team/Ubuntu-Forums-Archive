---
title: "File Server Directory Permissions"
date: 2010-04-28
forum: Server Platforms
---

### Post by wjmj on 2010-04-28
I'm setting up an office file server and need to change the way Ubuntu 9.10 applies default permissions. I have a public share served up by Samba and Netatalk.

Structure is:
/home/public/ (Samba share)
   /sales
   /development
   /shared

I have three groups, users, development and sales. Users has access to public and shared, devel to devel, sales to sales.

The idea is to restrict access to the directories by group, which is working fine, sales can't get to devel and vice versa.

The problem I have is that if one user creates/copies a folder or file to the share, the other users can't edit or delete the files.

Is there a way to apply a default behaviour to this so that if one user (of the same group) creates a file, somebody else can edit it without having to change the permissions every time?

TIA

---

