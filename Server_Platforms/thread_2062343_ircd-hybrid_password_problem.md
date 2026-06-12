---
title: "ircd-hybrid password problem"
date: 2012-09-24
forum: Server Platforms
---

### Post by marinuso on 2012-09-24
I have installed ircd-hybrid from the Ubuntu repo. It is version 7.2.2. I can't get password protection to work. If I add a password= line to the auth block, it just doesn't allow any connections at all anymore. I have tried both a plaintext password and an encryped password (with mkpasswd), neither works. If I leave the password= line out, the server works fine (except for the password, obviously).

I'm using Ubuntu 10.04. Please don't tell me to upgrade to 12, the 'server' has only 256MB RAM.

---

### Post by jstableford on 2012-10-04
I'm having the same issue. I did a little digging and found in the example.conf, the following flag:

flags = need_password;

I added it, and now it won't accept any password. What gives?

---

