---
title: "Sendmail adding .org after some addresses"
date: 2011-09-25
forum: Server Platforms
---

### Post by prauttt on 2011-09-25
Hello, 
 We run a mailing list and on our server sendmail is adding .org after some addresses, e.g. the first and third entries below in the process listing: 
 
```
root      1528  0.0  0.1  11764  6524 ?        Ss   Sep21   0:01  sendmail: ./p8NMgM0X031218 dimaventures.com.org.: user open 
root       825  0.0  0.1  11796  6872 ?        Ss   Sep23   0:00  sendmail: ./p8MMBTHR000323 alltel.net.: user open 
root     31759  0.0  0.1  11752  7008 ?        Ss   Sep23   0:00  sendmail: ./p8NITSQI029831 wrightinst.edu.org.: user open 
```Could this be related to the "subdomain name $m = org" as in the sendmail config below? If so, why does it adds .org only to some addresses?
 ```

# sendmail -d0.1 -bv 
 Version 8.13.8 
  Compiled with: DNSMAP HESIOD HES_GETMAILHOST LDAPMAP LOG MAP_REGEX 
                 MATCHGECOS MILTER MIME7TO8 MIME8TO7 NAMED_BIND NETINET 
 NETINET6 
                 NETUNIX NEWDB NIS PIPELINING SASLv2 SCANF SOCKETMAP 
 STARTTLS 
                 TCPWRAPPERS USERDB USE_LDAP_INIT 
 
============ SYSTEM IDENTITY (after readcf) ============ 
       (short domain name) $w = foobar 
   (canonical domain name) $j = foobar.org 
          (subdomain name) $m = org 
               (node name) $k = foobar.org 
 ======================================================== 

```If this is the problem, how do I fix this? We have a single host in our organization, so it's not host1.foobar.org, host2.foobar.org. It's just foobar.org.

Also, some sendmail processes have been around for more than two days (e.g. the first process in the process listing above). How do I make sure that a process does its job and not hangs around. 
 
Thanks for your help!

---

