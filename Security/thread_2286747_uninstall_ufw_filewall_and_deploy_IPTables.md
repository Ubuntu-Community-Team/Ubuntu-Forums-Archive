---
title: "uninstall ufw filewall and deploy IPTables"
date: 2015-07-14
forum: Security
---

### Post by Shailesh_Jain on 2015-07-14
Hi All,

I want to deploy the IPTables on Ubuntu 14.04 LTS server and uninstall/complete remove ufw firewall from Ubuntu 14.04.

Please some one help me or provide the document.

Thanks,
Sjain

---

### Post by cariboo on 2015-07-15
Ufw is just a front end for iptables, you don't need to use it. You can safely remove it using the following commands:

```
sudo ufw disable && sudo apt-get purge ufw
```

---

