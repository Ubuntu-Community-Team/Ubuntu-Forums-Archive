---
title: "howto? removing permissions from new user (access his account only)"
date: 2010-04-08
forum: Security
---

### Post by adhg on 2010-04-08
Hi there

I just added a new user to my ubuntu:

sudo adduser james

When james logs in he access his folder BUT he can also access other user's folders. How can I prevent his access to others? I wish to restrict his account to his folder only (he can read/write).

Thank you!

---

### Post by Cosma on 2010-04-08
check this link:
[https://help.ubuntu.com/9.10/serverguide/C/user-management.html](https://help.ubuntu.com/9.10/serverguide/C/user-management.html)

there is explained why new users can access other's home folders and how you can prevent that.

---

### Post by adhg on 2010-04-08
Thanks,

sudo chmod 0750 /home/james

will remove the 'r' and therefore no one can access this account (no one can access james) However, using this technic, I will have to go through all users and do that. Is there a way only to restrict 'james' from the other. So he will not be able to see other files not belong to him?

Thanks again

(ps, how to regain the r back to drwxr-xr-x)

---

### Post by cariboo on 2010-04-08
I set all home directory permissions to 700, that way only root and the owner have access.

---

### Post by EJeanmaire on 2010-04-08
> **adhg said:**
> Thanks,

sudo chmod 0750 /home/james

will remove the 'r' and therefore no one can access this account (no one can access james) However, using this technic, I will have to go through all users and do that.

You can do it only once by 'sudo chmod 0750 /home'

> **adhg said:**
> Is there a way only to restrict 'james' from the other. So he will not be able to see other files not belong to him?

No, there is no way to have "exclusions".  The way file permissions work is based on Owner, Group, or Everyone.  The problem is your /home files are set so that Everyone can read.

---

### Post by adhg on 2010-04-08
thank you all, I learned a great deal today.

---

