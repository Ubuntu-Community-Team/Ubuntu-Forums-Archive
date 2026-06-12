---
title: "Authentication reason: Too many authentication failures"
date: 2018-01-28
forum: Security
---

### Post by mahsamozi on 2018-01-28
Hello!
I have for a while now, received the error "Authentication reason: Too  many authentication failures" when I am trying to login into my Ubuntu  server via tightVNC.
I do have to restart the server every time I need to enter it, I am afraid that someone is trying to hack my server. 

Is there any way to fix this problem? Thanks!

Btw, I do have googled it and did not find anything useful!

---

### Post by TheFu on 2018-01-28
VNC shouldn't be available on the public internet. It isn't encrypted well enough and a single plain password is a total failure in 2018.  Only run the vncserver with the --local option and force the use of either a VPN or ssh-tunnel for access.

Or ... switch to **x2go**, which is 2-3x faster and uses ssh by default.  Use the x2go PPA for client and server sides. Setup ssh first and follow the best practices for securing it.
* no remote root
* ssh-keys only
* fail2ban or denyhosts to block brute-force attacks
* .... about 5 other ssh settings.

---

