---
title: "LTSP Server lts.conf clarification on LDM_DIRECTX"
date: 2018-07-23
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2018-07-23
Probably a dumb question, maybe I've already got it figured out but want to be sure. I don't expect my pxe machines to be speed demons, but I think they can be faster. Currently my lts.conf is like this. I want the encrypted ssh disabled. Don't need the encryption for my purposes. Is this correct or should I have LDM_DIRECTX set to false?

```
[Default]    
    LDM_DIRECTX = "true"
    RCFILE_01 = "/etc/ltsp/crontabs"
    KEEP_SYSTEM_SERVICES = "ssh"
    CRONTAB_01 = "00 00 * * 7    /bin/echo 3 > /proc/sys/vm/drop_caches"
    CRONTAB_02 = "00 00 * * 7    /sbin/swapoff -a && /sbin/swapon -a"
```

---

