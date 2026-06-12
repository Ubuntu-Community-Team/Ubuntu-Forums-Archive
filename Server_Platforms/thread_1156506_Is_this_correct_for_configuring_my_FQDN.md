---
title: "Is this correct for configuring my FQDN?"
date: 2009-05-11
forum: Server Platforms
---

### Post by R.Bucky on 2009-05-11
Is this the correct configuration of my /etc/hosts? I host my server using Ubuntu Server 8.04 with an internal ip of 10.1.10.122 with a static IP. buckyserver is my hostname, while buckycomputing.net is my domain name. Anyone have alternative configuration suggestions?
```

127.0.0.1 localhost
127.0.1.1 buckyserver
10.1.10.122 buckycomputing.net buckyserver
```

---

### Post by drave on 2009-05-12
> **R.Bucky said:**
> Is this the correct configuration of my /etc/hosts? I host my server using Ubuntu Server 8.04 with an internal ip of 10.1.10.122 with a static IP. buckyserver is my hostname, while buckycomputing.net is my domain name. Anyone have alternative configuration suggestions?
```

127.0.0.1 localhost
127.0.1.1 buckyserver
10.1.10.122 buckycomputing.net buckyserver
```

dont know about that "127.0.1.1 buckyserver", everything else looks ok.  see "man hosts"

---

### Post by bluefrog on 2009-05-12
10.1.10.122 buckyserver.buckycomputing.net buckyserver

127.0.1.1 is just another address for your localhost named buckyserver. you could have on the same line

127.0.0.1 localhost.localdomain localhost buckyserver

---

