---
title: "smb_auth for squid3 and 2008 Windows Server"
date: 2012-10-17
forum: Server Platforms
---

### Post by user365 on 2012-10-17
Hi,

In the past we have used ubuntu server 8.04 LTS as Squid/Dansguardian filtering proxy servers.  I am trying to set up the equivalent using 12.4 and running into a few issues.

We use the Squid Proxy auth system for windows users to authenticate to squid.  When running  

/usr/lib/squid3/smb_auth -W DOMAINNAME -d

it returns

Domain name: DOMAINNAME
Pass-through authentication: no
Query address options:
Domain controller IP address: 192.168.1.162
Domain controller NETBIOS name: SERVERNAME
Contents of //SERVERNAME/NETLOGON/proxyauth:
ERR

So it cannot read the contents of the proxyauth file.

Can any one point me in the right direction?  Is this likely to be a Windows Server Security Policy or is there something else I need to change on the ubuntu?

Thanks in advance

Matt

---

