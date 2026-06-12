---
title: "No password SU when ssh'd"
date: 2008-09-03
forum: Server Platforms
---

### Post by jazee on 2008-09-03
Is there a way that once I'm SSH'd over to a server I can su into another account without needing to no that persons account password. Ideally it would be great if all I had to do was transfer the 1st accounts pub key into the 2nd accounts auth keys file to enable the 1st account ability to su into the 2nd account.

The whole login sinario would look something like:

%> ssh [email]user1@server1.com[/email]
* RSA Keyed used to login
%> su user2
* No password used. ssh-agent or whatever used my key to log me in

---

### Post by cariboo on 2008-09-03
If it is your server why don't you have the other users password, after all you set up the accounts.

Jim

---

### Post by jazee on 2008-09-03
I have the passwords and everything. It just a matter of me not wanting to have to type in 50 million passwords as I jump around in a cluster of servers.

---

### Post by schettj on 2008-09-03
> **jazee said:**
> I have the passwords and everything. It just a matter of me not wanting to have to type in 50 million passwords as I jump around in a cluster of servers.

su to root, root can su to any user without a password.

---

