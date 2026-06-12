---
title: "ssh issue"
date: 2010-01-05
forum: Security
---

### Post by cromble1 on 2010-01-05
Hello,

I'm having trouble finding a way to force ssh clients to load their shell (as per /etc/passwd) upon connecting and authenticating to a server.

Without getting into the details of why this is important for this situation is there actually a way to overcome clients using the ssh -N option to bypass loading their shell yet staying connected?

Thanks.

---

### Post by BkkBonanza on 2010-01-06
Users typically do that when they are using port forwarding / proxying. There is  options in sshd_config called AllowTcpForwarding and AllowTunnels you can set to No to prevent that.

---

### Post by cromble1 on 2010-01-06
Thanks for the reply

---

