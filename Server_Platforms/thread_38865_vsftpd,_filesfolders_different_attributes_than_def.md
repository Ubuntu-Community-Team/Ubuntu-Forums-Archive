---
title: "vsftpd, files/folders different attributes than default"
date: 2005-06-02
forum: Server Platforms
---

### Post by CrustyDOD on 2005-06-02
Anyone has an idea how to change so that files uploaded are 644 and not 600, cause noone can't access them..

This is done by: 
local_umask=077
if am not mistaken, but instead of 077 what should be there? 
Command: man umask doesn't work.. so i have no idea how to set it!

---

### Post by LordHunter317 on 2005-06-02
man umask doesn't work as it's a shell builtin (use help umask instead).  umask is supposed to be a concept you understand natively, as lots of things use it; it's fundamental to UNIX permissions.  A umask is the bits you **don't** want on newly created files/directories.  So in your case, you want:```
local_umask=022
```which prevents group/world write access to newly created files/directories.

---

