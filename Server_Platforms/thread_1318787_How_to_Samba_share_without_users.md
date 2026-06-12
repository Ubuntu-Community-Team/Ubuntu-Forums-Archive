---
title: "How to Samba share without users"
date: 2009-11-07
forum: Server Platforms
---

### Post by Masteroc on 2009-11-07
Pardon me if any of this is noobish, as im fairly new to server admining. What I am trying to do is have ubuntu server (using samba) share its raid array with my whole house network. At the moment I really don't have much need for security as far as permissions for users to read/write to shared folders. What I want to know is how to set up samba to not care who is using it. This will be for my parents to use as well and they don't like using passwords and logging in just to save or view a file. I tried not having an allowed users parameter in the smb.conf, but I still get "Access Denied" when trying to create a folder on the share from XP (even when I log in). Any ideas?

---

### Post by Masteroc on 2009-11-07
Solved my own problem. Realized that everyone on my network could read and execute, but I hadn't set the folder so that everyone could write to it. Again, pretty new to server admining...especially via the cli.

Thanks again for your time!

---

