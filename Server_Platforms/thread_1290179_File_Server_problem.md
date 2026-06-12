---
title: "File Server problem"
date: 2009-10-13
forum: Server Platforms
---

### Post by paparadzi on 2009-10-13
Hi!
 
 First of all, sorry about my English.
 
 I created a New file server 
 
 Server OS: Ubuntu 9.04
  Samba version 3.0.28a
  Auth server: Windows 2003 AD
 
 The Authentication is working perfect. 
 
 My problem is, I need to configure the file server so, that the Users can't create a new folder (only few person) only files.
 
 Please is you have any idea, who can I solve this problem, than let me know.

---

### Post by Iowan on 2009-10-13
Hope I'm wrong, but since everything in Linux looks like a file - if a user can create a file, they can probably create a directory (folder).

---

### Post by lukeiamyourfather on 2009-10-13
What about making the root of the share write accessible to only a few users, and make the sub folders write accessible to everyone. That way the root of the share will stay organized and under control of just a few users. Not sure if that'll work for your situation or not. Cheers!

---

### Post by paparadzi on 2009-10-14
THX the help I will try it.

I found out that my boss had this idei from a Windows server. :(

---

### Post by CharlesA on 2009-10-14
I don't remember being able to limit a person to just creating files but not folders on WS2003.

---

