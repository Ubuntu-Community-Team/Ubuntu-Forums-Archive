---
title: "Screen saver locking account, cannot unlock account."
date: 2020-01-10
forum: Security
---

### Post by steve keating on 2020-01-10
Hello

I am configuring Ubuntu 16.04 LTS security on a laptop, and have run into a problem. It seems that when the screen saver starts, the account that was logged in gets locked and cannot be unlocked. Say I am logged in as Dave, which is a member of the root group, and the screen saver kicks on, then Dave is locked. When I try to back login, the login shows Account locked after "X" failed logins. If I log in with another account that also has root privileges, I cannot unlock the Dave account using usermod -U. I have checked the owner of  /etc/shadow, and it is - r - - r - - - - 1 root shadow 1940 Jan 10 13:16  /etc/shadow. Is there some way to way to unlock the account, short of deleting the account and setting it up again?   

Thanks
Stephen Keating

---

