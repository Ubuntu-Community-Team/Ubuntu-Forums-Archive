---
title: "Error after install ufw"
date: 2022-02-01
forum: Server Platforms
---

### Post by alexswamp on 2022-02-01
Hi all,

I installed fresh new ufw and i want to start it, but i got error.
I using ubuntu 22.04.

```


username@websrv:~$ sudo ufw enable


Command may disrupt existing ssh connections. Proceed with operation (y|n)?
Aborted
sanyi@websrv:~$ sudo ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
ERROR: problem running ufw-init
ip6tables-restore v1.8.7 (nf_tables): unknown option "--icmpv6-type"
Error occurred at line: 36
Try `ip6tables-restore -h' or 'ip6tables-restore --help' for more information.


Problem running '/etc/ufw/before6.rules'



```

---

### Post by MAFoElffen on 2022-02-01
it is saying there is a problem with starting the ip6tables...
```
ip6tables-restore v1.8.7 (nf_tables): unknown option "--icmpv6-type"
```
Do you even use IPv6? If you configured rules for your ipv6 tables, check your syntax. You didn't add that option in your config did you? 
```
Problem running '/etc/ufw/before6.rules'
```
If not, do what it said and try to restore the ip6tables...
```
Try `ip6tables-restore -h' or 'ip6tables-restore --help' for more information.
```

---

