---
title: "squid ntlm ttl credentials"
date: 2010-03-03
forum: Server Platforms
---

### Post by SGWW on 2010-03-03
Hi! squid_ntlm_group authentication is working fine. The problem comes when I change the group that allows the users to surf the net. That change in LDAP is not reflected in Squid immediately, forcing me to restart Squid. I've tried different parameters, but no luck so far. (auth_param basic credentialsttl seems to be not working).
   
  Squid Cache: Version 2.7.STABLE3
   
  Here is my squid.conf 
   
```
http_port 8080
  cache_dir ufs /home/squidcache 10240 16 256
  cache_effective_user squid
  cache_effective_group squid
   
  access_log /var/log/squid/access.log squid
   
  authenticate_ttl 1 minutes
   
  auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp --require-membership-of=S-1-5-21-687514919-1370150841-4167779082-2610
   
  auth_param ntlm children 30
  auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic  --require-membership-of=S-1-5-21-687514919-1370150841-4167779082-2610
   
  auth_param basic children 5
  auth_param basic realm Squid proxy-caching web server
  auth_param basic credentialsttl 2 hours
   
  acl AuthorizedUsers proxy_auth REQUIRED
  acl all src 0.0.0.0/0.0.0.0
  acl icq dstdom_regex .icq.com .aol.com
   
  http_access allow AuthorizedUsers icq
  http_access deny  all

```Thanks in advance

---

### Post by lunatico on 2010-03-18
I have no answer for your question. But maybe you can point me to find the info I need. Basically I'm trying to get ntlm authentication working against an AD 2008 server... but can't seem to find an easy solution.

---

### Post by SGWW on 2010-03-19
Do you enable ntlm on Windows Server ... default instalation does not support ntlm ... The principle is the same for both server systems (2003 and 2008)

PS ... for your problem the best decision is to use kerberos.

---

