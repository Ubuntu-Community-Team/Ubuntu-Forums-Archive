---
title: "Landscape: Ubuntu Desktop client not registering"
date: 2018-01-11
forum: Ubuntu Cloud and Juju
---

### Post by rdkls on 2018-01-11
Running on-prem Landscape.

Two *servers* registered with the landscape server just fine after finding [this thread]("https://ubuntuforums.org/showthread.php?t=2263964") about copying the cert and then running the registration process, which I also did for a 16.04 *desktop* however the Landscape server never sees the registration request.

What do I need to provide for assistance?

---

### Post by rdkls on 2018-01-12
My issue was mDNS, my client machine could not ping the landscape.*domain.local*, but could ping 'landscape' by itself. Since the server & ping addresses were configured with *domain.local*, I just removed mDNS from /etc/nsswitch.conf and it immediately registered.

**/etc/nsswitch.conf**
```
hosts:          files dns
#hosts:          files mdns4_minimal [NOTFOUND=return] dns
```

---

