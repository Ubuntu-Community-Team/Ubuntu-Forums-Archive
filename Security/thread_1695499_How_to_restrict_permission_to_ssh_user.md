---
title: "How to restrict permission to ssh user"
date: 2011-02-26
forum: Security
---

### Post by tapas_mishra on 2011-02-26
Hi,

I would like to allow a user to login through SSH but with different
permission coming from different ipaddress.

For example, a user "tester" login to SSH through 192.168.1.1 and
another user login with the same login id "tester" but from different
ip 192.168.1.2.

How do I restrict 192.168.1.2 to only allow for viewing the content in
the home directory while giving 192.168.1.1 full access?


I got a suggestion from some one

Approach 1)
 Based on the ip you change the shell. If it's just for read only a
jail would be fine.

but how do I change shell based on IP?

Approach 2)

 to have two ssh instances. Let's say port 22 and port 24. Port 22 is
for read only, while port 24 is for full access

so how can it be possible to give port 22 only read only access to SSH

Or if there is any other approach let me know?

---

### Post by SeijiSensei on 2011-02-26
The answer to the second question is that the "secure shell" protocol gives the user a shell.  If you want to restrict the user, you'll have to direct them into a chroot jail or something similar.

Frankly, if you're going to give someone shell access, you should be ready to live with the consequences.  If it's someone you trust, then perhaps you'll be fine.  If you can't trust the person, don't give him or her SSH access.  Find another, more secure, solution for their needs.

---

