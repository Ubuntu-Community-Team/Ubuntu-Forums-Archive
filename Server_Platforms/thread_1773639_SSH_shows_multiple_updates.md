---
title: "SSH shows multiple updates"
date: 2011-06-02
forum: Server Platforms
---

### Post by joms on 2011-06-02
Hi,

When I log into my Ubuntu server via SSH it usually gives me the number of available updates. But a while ago it started saying this multiple times, and with different numbers. I've tried to install the updates. But one of the messages about updates always says there's updates available. Also the number seem to be static and never change.

Example: 
```
login as: user
user@domain's password:
Linux Inceptor 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_                                                    64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

24 packages can be updated.
24 updates are security updates.

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

30 packages can be updated.
18 updates are security updates.

Last login: Wed Jun  1 21:57:26 2011 from Somewhere

```Anyone have an idea why this is happening? And how to solve it? 

Thanks!
-JoMs

---

### Post by CharlesA on 2011-06-02
It's a bug that causes motd.tail to be overwritten (or something along those lines).

Delete/rename /etc/motd.tail and it'll go back to normal.

---

### Post by joms on 2011-06-02
> **CharlesA said:**
> It's a bug that causes motd.tail to be overwritten (or something along those lines).

Delete/rename /etc/motd.tail and it'll go back to normal.

Thanks! Solved my problem :)

---

### Post by JGSD on 2011-07-12
I had this problem but I did not have an /etc/motd.tail only an /etc/motd but thanks anyway, as your post pointed me in the right direction.

I renamed /etc/motd to something else and then logged out/in and renamed it back to /etc/motd and now the motd is being displayed with up-to-date details :-)

---

