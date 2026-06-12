---
title: "share one folder on server 9.04"
date: 2009-06-01
forum: Server Platforms
---

### Post by Heeter on 2009-06-01
Hi all,

I installed 9.04 server 64bit on my tower. I installed Samba and disabled apparmor. I would to share the /srv folder over a small windows network, read and write access.

I have forgotten how to edit my smb.conf file. And if I need to do anything else.

Any help will be greatly appreciated. 

Thanks

Heeter

---

### Post by madverb on 2009-06-01
Just look at the smb.conf. Down the bottom it gives you examples of how to share files.

---

### Post by Heeter on 2009-06-01
Hey, Thanks for the response.

Do I need to chmod or anything else to the /srv folder?

Thanks again

Heeter

---

### Post by Iowan on 2009-06-01
Probably depends on how it's currently set up (who owns it).

---

