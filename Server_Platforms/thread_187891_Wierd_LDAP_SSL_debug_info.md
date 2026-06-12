---
title: "Wierd LDAP/ SSL debug info"
date: 2006-06-03
forum: Server Platforms
---

### Post by [Yatta] on 2006-06-03
Ok i thought i had LDAP working with SSL fine..... after going back to it after 2 weeks all is not well.

First off LDAP runs perfect with out SSL no Problem.... I turn on TLS **ldapsearch** with options **-Z** and **-ZZ** still brings up information.
 BUT when i look at this information while running ldap in debug mode i get
```
 sudo /usr/sbin/slapd -h 'ldap:/// ldaps:///' -d 1
```

```
TLS trace: SSL_accept:SSLv3 flush data
TLS trace: SSL_accept:error in SSLv3 read client certificate A
TLS trace: SSL_accept:error in SSLv3 read client certificate A
connection_get(12): got connid=0
connection_read(12): checking for input on id=0
TLS trace: SSL_accept:SSLv3 read client key exchange A
TLS trace: SSL_accept:SSLv3 read finished A
TLS trace: SSL_accept:SSLv3 write change cipher spec A
TLS trace: SSL_accept:SSLv3 write finished A
TLS trace: SSL_accept:SSLv3 flush data
connection_read(12): unable to get TLS client DN, error=49 id=0
```

I do the same search with:
```
sudo /usr/sbin/slapd -h 'ldap:/// ldaps:///' -d 127
```
I get gibberish
```
TLS trace: SSL_accept:SSLv3 write change cipher spec A
TLS trace: SSL_accept:SSLv3 write finished A
tls_write: want=59, written=59
  0000:  14 03 01 00 01 01 16 03  01 00 30 43 06 f5 6e ee   ..........0C..n.  
  0010:  24 1e d9 01 32 97 c9 27  84 dc ed 51 90 78 c9 e9   $...2..'...Q.x..  
  0020:  68 2d e8 3e c5 46 61 c8  1f 84 8b 66 64 d6 6b 53   h-.>.Fa....fd.kS  
  0030:  79 07 6a b9 29 72 84 6d  d1 7b 6c                  y.j.)r.m.{l       
TLS trace: SSL_accept:SSLv3 flush data
connection_read(12): unable to get TLS client DN, error=49 id=0
daemon: select: listen=6 active_threads=0 tvp=NULL

```
Now looking at this output i know there is some encryption going on... but i guess not fully??
My mistake.... as i was looking at the outputs more closley while writing this.. i notice they both say :
connection_read(12): unable to get TLS client DN, error=49 id=0

I've googled till mi weak haven't been able to solve this issue. The thing is i left it a few weeks ago workin no prob??
PLEASE any  one have any cluw what is going on or what that error message REALLY means?
TIA

---

