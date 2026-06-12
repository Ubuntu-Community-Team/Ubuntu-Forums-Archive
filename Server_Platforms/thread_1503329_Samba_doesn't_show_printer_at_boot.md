---
title: "Samba doesn't show printer at boot"
date: 2010-06-06
forum: Server Platforms
---

### Post by srivo on 2010-06-06
Hi,

Each time I boot I have to restart samba to see the shared printer on other windows machine. I tought it was the cups problem listed on the forum, but I'm not sure anymore if it's related!

Could it be related to the service sequence? I don't know how to look at the service load sequence in ubuntu?

Anyone have the same issue?

---

### Post by srivo on 2010-06-07
What I found from now is that it could be related to upstart, when I look into to initctl list I can see cups?

I'm starting to think that the problem is related to upstart!

---

### Post by srivo on 2010-06-12
I try to reinstall samba but it doesn't solved the problem! When the server boot I see the shared drive but not the shared printer! When I restart samba everything work?

Anyone have the same problem?

---

### Post by srivo on 2010-06-12
It's a bug if find it in launchpadd cups start before samba!

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141)

There is a temporary workaround on launchpad:
add
 sleep 10
 just after "pre start script" in /etc/init/smbd.conf and /etc/init/nmbd.conf

---

### Post by llawwehttam on 2010-06-12
in arch there is an /etc/rc.conf that can be modified to change the order that daemons launch. Not sure if there is sonthing similar in ubuntu.

---

### Post by srivo on 2010-06-15
Yes I know, I use and love Arch! This is the arch way. Thing are comming more complicated in ubuntu!

---

