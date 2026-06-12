---
title: "UFW rule question"
date: 2010-05-30
forum: Security
---

### Post by sisyphus1978 on 2010-05-30
I'm trying to get to grips with UFW. I have a home network with a few ubuntu based computers (NFS & SSH). UFW rule on each of them is
> 
$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    192.168.1.0/24
Is this safe? Each computer has a static IP, so I could set it for each client (but I wasn't sure how to do that).

Thanks.

---

### Post by CharlesA on 2010-05-30
You should be fine with that rule.

---

### Post by sisyphus1978 on 2010-05-31
Seems to be working okay. I'll stick with it and see how I get on.

---

