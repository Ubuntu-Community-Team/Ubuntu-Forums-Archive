---
title: "fail2ban question"
date: 2007-05-24
forum: Server Platforms
---

### Post by nomb on 2007-05-24
Hey guys, 

I was following a tutorial on getting fail2ban installed. The tutorial catered to an older version because it said that there is already an ssh config in /etc/fail2ban.conf which works out of the box.

The one I installed doesn't store the connections in the fail2ban.conf file anymore. Each protocol has its own conf file in a directory under /etc/fail2ban/.

So I installed it and it is running. I tried to logging in about 20 times with wrong passwords and I never got banned. Is there more you have to do 'out-of-the-box' now to get it to work? Or, was I just not quick enough.

Thanks,
nomb

---

### Post by joselin on 2007-05-24
I used [this tutorial]("http://www.howtoforge.com/fail2ban_debian_etch") and works fine. Check it.

---

### Post by nomb on 2007-05-28
That worked great, thanks.

---

