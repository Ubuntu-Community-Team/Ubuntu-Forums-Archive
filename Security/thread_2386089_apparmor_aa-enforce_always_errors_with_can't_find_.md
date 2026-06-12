---
title: "apparmor aa-enforce always errors with can't find dhcpd.d"
date: 2018-02-28
forum: Security
---

### Post by ingenium2 on 2018-02-28
I'm trying to enable some custom AppArmor profiles, however anytime I run aa-enforce I get the following error:
```
ERROR: Include file /etc/apparmor.d/dhcpd.d not found
```

I've tried using aa-enforce with some of the stock profiles, and they also give the same error. I recursively grepped /etc/apparmor.d and /etc/apparmor for dhcpd.d and nothing is returned. 

aa-status does show processes in enforce mode, along with some in complain mode. So AppArmor is working, I just can't enable new profiles.

Is there a master config file for AppArmor somewhere that might reference this include? I'm guessing perhaps an old config file is left around from an older version of Ubuntu.

Is there something else that could be causing this? I'm not sure where AppArmor is seeing this include.

I'm running Ubuntu 16.04.

---

### Post by wildmanne39 on 2018-02-28
*Thread moved to **Security, a more appropriate forum**.*

---

