---
title: "Ubuntu 10.04 mail server getting high load of SASL SMTP authentications"
date: 2010-11-15
forum: Security
---

### Post by hawk2010 on 2010-11-15
Hi,

Recently I have encountered sustained attacks via using SASL SMTP authentication on my Ubuntu 10.04 Mail server. A total of 200 odd failiure attempts were recorded. Any idea of getting SASL to only make the connection it from trusted IP? My DSL router has flooded because of the increase in traffic..

---

### Post by cariboo on 2010-11-15
You can use denyhosts to limit the number of connection attempts, it will also blacklist the ip address, after the specified number of attempts is made. The default is 5 attempts.

---

