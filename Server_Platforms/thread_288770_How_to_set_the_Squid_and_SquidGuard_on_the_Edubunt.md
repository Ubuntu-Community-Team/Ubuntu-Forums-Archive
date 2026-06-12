---
title: "How to set the Squid and SquidGuard on the Edubuntu."
date: 2006-10-30
forum: Server Platforms
---

### Post by sshgz on 2006-10-30
I have installed Edubuntu 6.10 with ltsp squid squidguard. The Edubuntu server connects the internet by the ADSL . 
I want to filter some websites with the squid and squidguard and set the squid and squidguard.
But i find that i can not filter these websites when i login into the thin client.

I am waiting for you help.

Thanks.

---

### Post by yaa13 on 2006-10-30
> 
But i find that i can not filter these websites when i login into the thin client.

Are you have blocking sites for localhost (127.0.0.1) in /etc/squid/squidGuard.conf?
Read [http://www.squidguard.org/config/](http://www.squidguard.org/config/)

---

### Post by hartunnoo on 2006-10-30
Is squidguard is different from squid?

I found out squidquard is more difficult to configure than the normal squid. hmm...

---

### Post by sshgz on 2006-10-30
Thanks **yaa13**.
I am new for the SquidGuard.
Could you tell me how to set the SquidGuard for blocking sites for localhost.

Thanks.

---

### Post by yaa13 on 2006-11-01
> **sshgz said:**
> 
Could you tell me how to set the SquidGuard for blocking sites for localhost.
Thanks.
[My config](http://tolikzilla.googlepages.com/mysquidguard.html), but  strongly recommended read about SquidGuard on [http://www.squidguard.org/config/](http://www.squidguard.org/config/)

---

