---
title: "restrict ssh/scp access to specific  ip addresses"
date: 2008-05-20
forum: Security
---

### Post by boondocks on 2008-05-20
I have a Ubuntu 8.04 desktop running at a remote location.
It is directly connected to an ADSL modem.

I have sudo access to this system.
I am able to access via ssh/scp too.

Now I want to limit ONLY the ssh/scp access to a few ip addresses.

In other words, keep everything else as-is ...
http, ftp, ... accessible by anyone
BUT
scp/scp ... accessible by 3 specific ip addresses only

How can I do this?

---

### Post by nunki on 2008-05-20
> **boondocks said:**
> I have a Ubuntu 8.04 desktop running at a remote location.
It is directly connected to an ADSL modem.

I have sudo access to this system.
I am able to access via ssh/scp too.

Now I want to limit ONLY the ssh/scp access to a few ip addresses.

In other words, keep everything else as-is ...
http, ftp, ... accessible by anyone
BUT
scp/scp ... accessible by 3 specific ip addresses only

How can I do this?

Probably easier to setup a firewall rule something like
```
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 22 --source [accepted ip address here] -j ACCEPT 

```

---

### Post by boondocks on 2008-05-20
Rather than make changes to iptables, it there some other ssh-specific way to do this?

---

### Post by brian_p on 2008-05-20
> **boondocks said:**
> 
Now I want to limit ONLY the ssh/scp access to a few ip addresses.

In other words, keep everything else as-is ...
http, ftp, ... accessible by anyone
BUT
scp/scp ... accessible by 3 specific ip addresses only

How can I do this?

The AllowUsers option for sshd_config is the easiest route if you know who the users are. Alternatively, there is the equally easy tcp_wrappers way (/etc/hosts.allow and /etc/hosts.deny).

---

### Post by Dr Small on 2008-05-20
Why not add in your /etc/host.allow:
```
sshd: IPADDRESS, IPADRRESS
```

---

### Post by The Cog on 2008-05-20
Something like this in /etc/ssh/sshd_config perhaps?

```
AllowUsers andy@192.168.1.*,1.2.3.4,5.6.7.8 billy@192.168.1.* charlie@192.168.1.*
```

---

