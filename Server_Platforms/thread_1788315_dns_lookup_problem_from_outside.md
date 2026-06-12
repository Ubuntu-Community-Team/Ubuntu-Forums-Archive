---
title: "dns lookup problem from outside"
date: 2011-06-22
forum: Server Platforms
---

### Post by bsaidus on 2011-06-22
hello friends .
I have installed fresh ubuntu server 10.04.2 and configured bind9 
all works fine (from winxp I can resolve the dns with  nslookup )
so since I have installed IRedMAil in this distro ..:( I cant resolve the dns from outside
(nslookup from outside dont work [-X ) but works in ubuntu .
even when i disable uwf 
help me please ....

---

### Post by arrrghhh on 2011-06-22
> **bsaidus said:**
> hello friends .
I have installed fresh ubuntu server 10.04.2 and configured bind9 
all works fine (from winxp I can resolve the dns with  nslookup )
so since I have installed IRedMAil in this distro ..:( I cant resolve the dns from outside
(nslookup from outside dont work [-X ) but works in ubuntu .
even when i disable uwf 
help me please ....

BIND9 only works as local DNS.  You'll need a provider or domain host to do the DNS magic on the WAN side.  Do you have a domain name?

---

### Post by bsaidus on 2011-06-22
> **arrrghhh said:**
> BIND9 only works as local DNS.  You'll need a provider or domain host to do the DNS magic on the WAN side.  Do you have a domain name?

Yes I know but .. in a LAN for example I frequentely provide the IP adress of the Ubuntu machine (server ) as DNS Primary for others machines (PC -winxp ) and i do nslookup from ... as i want ... and i works well ..
problems begins when I installed iRedMail ..:(

---

### Post by arrrghhh on 2011-06-22
> **bsaidus said:**
> Yes I know but .. in a LAN for example I frequentely provide the IP adress of the Ubuntu machine (server ) as DNS Primary for others machines (PC -winxp ) and i do nslookup from ... as i want ... and i works well ..
problems begins when I installed iRedMail ..:(

Perhaps I'm not following.  You're saying that DNS does not work even on your LAN after iRedMail...?  I have never heard of iRedMail, sorry...  Quick Google search served me well.  Perhaps you should ask on their forums?  If the DNS resolution worked before iRedMail, and now does not... I would investigate iRedMail further.  They have [forums](http://www.iredmail.org/forum/)...

---

### Post by bsaidus on 2011-06-22
thanks :p ...

---

### Post by e79 on 2011-06-22
> **bsaidus said:**
> hello friends .
I have installed fresh ubuntu server 10.04.2 and configured bind9 
all works fine (from winxp I can resolve the dns with  nslookup )
so since I have installed IRedMAil in this distro ..:( I cant resolve the dns from outside
(nslookup from outside dont work [-X ) but works in ubuntu .
even when i disable uwf 
help me please ....

If I understand well what is being said here (that you want to use/publish your IRedMail on the web) ...

The resolution of the FQDN of your mail server has to be done at the ISP/DNS hoster level (the company from which you bought your domain name). Your Bind9 installation should not answer (most of the time) to queries coming from the web.

So first here is what I'd do (this is an example only):

1. Log in to your DNS provider and create a 'Host Record (A record) having the name 'mail' and pointing to your External IP address.
2.Then create a 'Mail Record (MX record)' having the name '@' and pointing to your 'mail' Host record.
3. Open port 25 (SMTP) on your router and redirect it to your Ubuntu server IP address.
4. Open PoP3(s), IMAP(s) and/or Webmail ports from your router and also redirect them to your Ubuntu server IP address.

These simple steps should make your mail server reachable from anywhere outside you LAN and a NSlookup from outside your network should resolve to your External IP address.
Once completed, try this from outside :
```
# nslookup
# set q=MX
# yourdomainname.com
```Again, these are basics only of netwroking and mail server, we're not talking about making everything secured, I'll leave that to you as it is another completely different topic  :p

For the local DNS resolution, if it still does not work, try to paste here the result of :

your 'named.conf.local'
```
cat /etc/bind/named.conf.local
```and perhaps your 'db.domain'
```
cat /etc/bind/db.domain
``` (obviously replacing 'domain' with the actual file you've created')

Hope this helps

---

