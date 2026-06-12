---
title: "Is there a hidden port filtering for unusual ports ? LAN-servername DNS resolving IP?"
date: 2010-01-14
forum: Security
---

### Post by pstein on 2010-01-14
I have no problems to connect from local Firefox browser to Internet over default port 80. e.g. [http://www.google.com](http://www.google.com)
 
However when I try to connect to some unusual ports and inhouse servers like
 
[http://testohio:7780/..../index.jsp](http://testohio:7780/..../index.jsp)
 
then cannot connect.
 
Firefox tells me: "Server not found".
 
The server exists ! I can connect from other computers (e.g. from WinXP).
 
So why does Ubuntu hav problems to connect.
 
Is there somewhere a port filtering which allows (by default) only outgoing connections to port 80?
 
So I have to enter somewhere something to resolve inhouse LAN computer "testohio"?
 
Either as assignment <computername> <IP>
or an additional inhouse DNS server?
 
Peter

---

### Post by cdenley on 2010-01-14
How is "testohio" resolved to an IP?
```

host testohio

```

Is your DNS server supposed to resolve it?
```

dig testohio

```

If it is a netbios name, then of course ubuntu will not resolve it by default. You would have to install and configure winbind. A simpler solution would be to add an entry in /etc/hosts, or just use the IP.

---

### Post by Sarmacid on 2010-01-14
It may be a firewall issue. Post the output of the command ```
sudo iptables -L
```

---

