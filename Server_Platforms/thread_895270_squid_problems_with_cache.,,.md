---
title: "squid problems with cache.,,"
date: 2008-08-20
forum: Server Platforms
---

### Post by klcom on 2008-08-20
Hi, i have some problems with the squid all work but sometimes, the squid hangs, and return this messages.

```

The requested URL could not be retrieved

--------------------------------------------------------------------------------

While trying to retrieve the URL: http://www.google.es/ 

The following error was encountered: 

Unable to determine IP address from host name for www.google.es 
The dnsserver returned: 

Server Failure: The name server was unable to process this query. 
This means that: 

 The cache was not able to resolve the hostname presented in the URL. 
 Check if the address is correct. 

```

The logs are normals, but the access.log are this messages:

1219207397.011  15076 192.9.201.59 TCP_MISS/503 1542 OPTIONS [http://ccr/](http://ccr/) - DIRECT/ccr text/html

This means that que squid can't resolv the adress throw the cache.

restarting the squid all come allright. but this isn't the solution becouse it neet be restarted 2 or 3 times a day.

Any idea!?  solution!?

Thks!

---

### Post by erwall on 2008-08-20
> **klcom said:**
> Hi, i have some problems with the squid all work but sometimes, the squid hangs, and return this messages.

```

The requested URL could not be retrieved

--------------------------------------------------------------------------------

While trying to retrieve the URL: http://www.google.es/ 

The following error was encountered: 

Unable to determine IP address from host name for www.google.es 
The dnsserver returned: 

Server Failure: The name server was unable to process this query. 
This means that: 

 The cache was not able to resolve the hostname presented in the URL. 
 Check if the address is correct. 

```

The logs are normals, but the access.log are this messages:

1219207397.011  15076 192.9.201.59 TCP_MISS/503 1542 OPTIONS [http://ccr/](http://ccr/) - DIRECT/ccr text/html

This means that que squid can't resolv the adress throw the cache.

restarting the squid all come allright. but this isn't the solution becouse it neet be restarted 2 or 3 times a day.

Any idea!?  solution!?

Thks!
Are you running bind on this box?  Are you specifying a dns server in the nameserver option in squid.conf?  What's in your /etc/resolv.conf?

For the moment, comment out any nameserver= in squid.conf.  Then make /etc/resolv.conf look like this:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

then restart squid and see how it does.

---

### Post by klcom on 2008-08-21
thanks for the answer but... i think the problem is from the cache configuration... , how i can know what is the best squid cache configuration, for the best rendiment of the sistem?

Thks!

---

### Post by zey on 2010-01-27
> **klcom said:**
> thanks for the answer but... i think the problem is from the cache configuration... , how i can know what is the best squid cache configuration, for the best rendiment of the sistem?

Thks!

I have the same problem with you..
I have to restart squid over and over again in a day..

---

