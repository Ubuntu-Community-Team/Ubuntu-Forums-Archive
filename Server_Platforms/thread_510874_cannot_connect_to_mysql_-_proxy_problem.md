---
title: "cannot connect to mysql - proxy problem?"
date: 2007-07-27
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-07-27
Hi!!!
I installed a Virtual Machine with a 6.0.6 LAMP server
I configured MySQL to work on port xyz

```
netstat -at
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 bella:xyz              *:*                     LISTEN  
```

Everything seems to function and there's no problem connecting directly to the internet (without proxy)

```
netstat -at
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 bella:xyz              *:*                     LISTEN     
tcp        0      0 bella:xyz              adsl-ull-38-166.4:50096 TIME_WAIT  
tcp        0      0 bella:xyz              adsl-ull-38-166.4:50097 ESTABLISHED
```

However if I try to use my evil proxy :mad: the connection doesn't open
on the proxy I use delegate with a rule that seems absolutely similar to other already functioning on different servers

```
/usr/local/bin/delegated -P716 SERVER=tcprelay://194.126.ip1.ip2:xyz/ PERMIT="*:*:-/." 2> /dev/null
```

this is another similar rule without problems
```
/usr/local/bin/delegated -P3546 SERVER=tcprelay://194.126.ip3.ip4:xyz2/ PERMIT="*:*:-/." 2> /dev/null
```

the proxy seems listening and ready for both the connections
```
tcp        0      0 *:716                   *:*                     LISTEN  
tcp        0      0 *:3546                  *:*                     LISTEN 
```

How to debug a situation like this?
Any ideas for a solution?

---

