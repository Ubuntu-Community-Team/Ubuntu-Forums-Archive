---
title: "root account disabled automatically?"
date: 2009-01-12
forum: Server Platforms
---

### Post by benton on 2009-01-12
Hi there, 

I installed Ubuntu Sever 8.04 about ten days ago. I enabled the root account by issuing "sudo passwd root" and creating a password. Since then I was using the root account to login until yesterday. Today the password is rejected and I cannot login anymore.

Is the root account disabled automatically after some time in Ubuntu? What could have happened?

Regards,

-Benton

---

### Post by pdtpatrick on 2009-01-12
No the root account is not disabled after some time. when you were installing the system, at some point it must have asked you to create a username or choose a username. Use that username to login and you can then change the password for the root (since the username will be part of the sudoers group automatically after install). 

You might want to check that the root account is not locked. 

If all else fails then log into single user mode (requires no login or password) and in here you can change the password for root or just create a username with sudo access. The latter would be a better idea.

---

