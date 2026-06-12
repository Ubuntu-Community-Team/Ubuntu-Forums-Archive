---
title: "mod-security and owncloud - 403 forbidden"
date: 2013-05-04
forum: Server Platforms
---

### Post by matt_symes on 2013-05-04
Hi.

I'm trying to set up owncloud on my test server. 

I have mod-security installed and i have configured owncloud.

When i try to access owncloud, mod-security is blocking it with this error

```

server1:/var/log/apache2 % tail -f error.log

[Sat May 04 20:39:13 2013] [error] [client 192.168.0.100] 
ModSecurity: Access denied with code 403 (phase 1). 
Match of "streq %{SESSION.IP_HASH}" against "TX:ip_hash" required. 
[file "/etc/modsecurity/activated_rules/modsecurity_crs_16_session_hijacking.conf"] 
[line "35"] [id "981059"] 
[msg "Warning - Sticky SessionID Data Changed - IP Address Mismatch."] 
[hostname "server1"] [uri "/owncloud/"] 
[unique_id "UYVj4X8AAQEAAAeNDW0AAAAF"]

```

It seems to think it's a session hijack. I could just disable the rule but i am loathed to do this.

I have the core set rules installed

```
server1:/var/log/apache2 % dpkg -l | grep modsec
ii  libapache2-modsecurity               2.6.3-1ubuntu0.2                    Tighten web applications security for Apache
ii  modsecurity-crs                      2.2.0-1                             modsecurity's Core Rule Set
server1:/var/log/apache2 % 
```

I have no rules for iptables.
```

server1:/var/log/apache2 % sudo !!
sudo iptables -L
[sudo] password for matthew: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
server1:/var/log/apache2 % 
```

If a disable mod-security then i can access the owncloud pages.

Does anybody have an idea why this crs rule is forbidding me from accessing the pages ?

Thanks in advance for any help.

Kind regards

---

### Post by sandyd on 2013-05-04
Try updating the crs rules
[http://marc.info/?l=mod-security-users&m=131127886501688&w=2](http://marc.info/?l=mod-security-users&m=131127886501688&w=2)

---

