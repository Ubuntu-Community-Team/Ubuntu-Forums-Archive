---
title: "Question on all user having same roaming profile"
date: 2008-03-28
forum: Server Platforms
---

### Post by cpthk on 2008-03-28
I am trying to have all my clients having the same roaming profile. I set smb.conf
```
logon path = \\%N\profiles
```
And I have profiles share open. But seems like samba only allow the folder owner to read it no matter I chmod 777 -R all the files.

Anything I missed?

---

### Post by cpthk on 2008-03-31
Got the problem myself. It has to change the group policy -> Do not check for user ownership of roaming profile folders

---

