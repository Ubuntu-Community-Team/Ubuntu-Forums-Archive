---
title: "Squid 2.7.STABLE3 transparent proxy + NTLM"
date: 2008-11-06
forum: Server Platforms
---

### Post by blastik on 2008-11-06
Hello all,


I'm trying to setup a transparent proxy with squid and NTLM authentication. It looks like everything its fine but i cannot find the error.
squid.conf as follows:

```

#basic config
http_port 8080 transparent
visible_hostname *********
cache_mgr        *********

#ntlm auth
auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
auth_param ntlm children 10
#auth_param ntlm max_challenge_reuses 0
#auth_param ntlm max_challenge_lifetime 2 minutes
#auth_param ntlm use_ntlm_negotiate off
auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic
auth_param basic children 5
auth_param basic realm Domain Proxy Server
auth_param basic credentialsttl 2 hours
auth_param basic casesensitive off
authenticate_cache_garbage_interval 10 seconds

# Credentials past their TTL are removed from memory
authenticate_ttl 0 seconds

#accept only authenticated users
acl lcl src 192.168.1.0/24
acl auth  proxy_auth REQUIRED
http_access allow lcl auth
http_access deny all
miss_access allow all
icp_access deny all

```

iptables as follows:

```

iptables -t nat -A PREROUTING -s 192.168.1.202 (squidip) -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A POSTROUTING -j MASQUERADE

```

I have only one interface (eth0):

ip fija: 192.168.1.202
dns: 192.168.1.2 / 192.168.1.12
gw: 192.168.1.9 (router's ip)

When i try to access to google for example i get this on the access.log file:

```

TCP_DENIED/403 1518 GET http://www.google.com/ - NONE/- text/html

```

Thanks in advance!

---

### Post by srinu.mca5 on 2011-02-04
**Hello sir** am using normal proxy now it is working fine..now I want to create transparent proxy, please help me.
my sources: squid 2.7,ubuntu 9.04

---

