---
title: "ssh error in Ubuntu 9.10"
date: 2010-03-31
forum: Server Platforms
---

### Post by fugitive569 on 2010-03-31
#ssh localhost  on newly installed ubuntu 9.10 says 

ssh: connect to host localhost on port 22: Address family not supported by protocol.

---

### Post by cdenley on 2010-03-31
Post this output:
```

grep localhost /etc/hosts
ping -c 1 localhost
dpkg -l openssh-server
sudo netstat -tlnp

```

---

