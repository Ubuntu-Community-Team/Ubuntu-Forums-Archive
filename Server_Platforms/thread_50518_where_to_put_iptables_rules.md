---
title: "where to put iptables rules?"
date: 2005-07-20
forum: Server Platforms
---

### Post by ivomans on 2005-07-20
I've defined a couple of iptable rules to function as a firewall.
On my previous Redhat system I had a file **/etc/sysconfig/iptables**. When the system was booting it was automagically used for a  ```
iptables-restore < /etc/sysconfig/iptables
```

So far I couldn't find a similar file-location, to have the iptables set up on boot for my Ubuntu server.
Could anybody point me to the right place?

---

### Post by dataw0lf on 2005-07-20
/etc/init.d/ is probably the best place.

---

### Post by ivomans on 2005-07-20
> /etc/init.d/ is probably the best place. 
I'm aware of the possibility to write a script overthere. I just consider the config-file concept more charming.

Should I read your reply as "there is no such thing in Ubuntu: user has to take care of this on it's own"?

---

