---
title: "Virtual Users for SSH"
date: 2008-10-29
forum: Server Platforms
---

### Post by Sid1980 on 2008-10-29
Is there any way to create virtual users for open-ssh server ??

Thx in advance:KS

---

### Post by Lars Noodén on 2008-10-30
What do you mean by "virtual"?  Aren't the users real?

---

### Post by Sid1980 on 2008-10-30
> **Lars Noodén said:**
> What do you mean by "virtual"?  Aren't the users real?

For virtual i mean users which are not local and cannot logon

---

### Post by Drezard on 2008-10-30
If you don't mind me asking, what exactly are you wanting to do? It would help us help you.

But if you want to create a user that can log on to your ftp or something like that but NOT be able to logon locally or through ssh just use:

> 
useradd -s /bin/false username


To create the user.

Daniel

---

