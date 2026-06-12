---
title: "LTSP reboot"
date: 2013-08-17
forum: Server Platforms
---

### Post by sean5 on 2013-08-17
Hi i might be setting up a ltsp server for staff where i work

Just want to know when happens is a user tries to reboot from their client... 

I imagine root and users in the sudoers file will be able to reboot the server and users without sudo permissions will not be able to?

---

### Post by newbie-user on 2013-08-17
Yes, this is correct. The most that unprivileged users can do is log out and maybe shutdown the thin client. They can't do anything to the server.

---

