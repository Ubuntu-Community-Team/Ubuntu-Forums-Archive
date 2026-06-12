---
title: "Console messages on every boot and shutdown"
date: 2024-06-07
forum: Security
---

### Post by currentshaft on 2024-06-07
2

---

### Post by #&amp;thj^% on 2024-06-07
Disable sssd from starting on systems "where" it's not needed.
Fix #1:
```

sudo systemctl stop sssd
sudo systemctl disable sssd
```

Fix #2:
```

sudo cp /usr/lib/x86_64-linux-gnu/sssd/conf/sssd.conf /etc/sssd/.
sudo chmod 600 /etc/sssd/sssd.conf 
sudo systemctl enable sssd
sudo systemctl start sssd
```


Fix #3:

Properly configure sssd, using /etc/sssd/sssd.conf, to your site's specific needs. See man sssd.conf for more information.

Please have a look at this: [https://ubuntu.com/server/docs/introduction-to-network-user-authentication-with-sssd](https://ubuntu.com/server/docs/introduction-to-network-user-authentication-with-sssd)

Your "cryptsetup: WARNING:" are new to me, but maybe "vg" related possibly, or logical volumes renames??? IJDK

Hope this helps a bit.

---

