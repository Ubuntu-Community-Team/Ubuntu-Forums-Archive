---
title: "Network problem (ping fails)"
date: 2005-01-10
forum: Server Platforms
---

### Post by Benn on 2005-01-10
Hi, recently i've installed Ubuntu on my domestic-gateway-firewal-proxy-nat server  :D . I like it a lot! Really. 
My Network is something like this:

                     _[ Gateway **SERVER** running Ubuntu - **192.168.0.1** ]_


_[   Windows **CLIENT** machine **192.168.0.2** ] _      _[   VAIO Windows **CLIENT** machine **192.168.0.3** ]_

Both Windows machines *access to Internet correctly*. But, Today, when i tried to run SAMBA I got a big/bad surprise.

I can't acces from **192.168.0.1** to **192.168.0.3**. Then I done a 'ping', and I realized that was a networking problem (it don't ping to VAIO machine). The thing is that the problem is *only from **192.168.0.1** to **192.168.0.3***.

I've checked both windows machines Network configurations and they are exactly the same!!! (obiously not the IP  :!: )

Does anyone knows what can I do about it ?

Thank You!

Greetz from Mexico!

---

### Post by jdodson on 2005-01-10
[QUOTE=Benn]Hi, recently i've installed Ubuntu on my domestic-gateway-firewal-proxy-nat server  :D . I like it a lot! Really. 
My Network is something like this:

                     _[ Gateway **SERVER** running Ubuntu - **192.168.0.1** ]_


_[   Windows **CLIENT** machine **192.168.0.2** ] _      _[   VAIO Windows **CLIENT** machine **192.168.0.3** ]_

Both Windows machines *access to Internet correctly*. But, Today, when i tried to run SAMBA I got a big/bad surprise.

I can't acces from **192.168.0.1** to **192.168.0.3**. Then I done a 'ping', and I realized that was a networking problem (it don't ping to VAIO machine). The thing is that the problem is *only from **192.168.0.1** to **192.168.0.3***.

I've checked both windows machines Network configurations and they are exactly the same!!! (obiously not the IP  :!: )

Does anyone knows what can I do about it ?

Thank You!

Greetz from Mexico![/QUOTE]

if you are physically connected to the same switch or hub and the ip scheme is the same, i.e. ip/mask then you should be able to ping ANY machine that allows you to.... for instance a windows firewall might be blocking the ping request or ubuntu might not be responding to a ping request.

anyways, this really isnt a windows help forum.... if you are having windows client issues, i would recommend a windows forum.

---

### Post by Benn on 2005-01-10
Thanks! I've fix this issue by desactivating "**Panda AV - Firewall**"

SeeYa!

---

