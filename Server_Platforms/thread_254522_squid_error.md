---
title: "squid error"
date: 2006-09-10
forum: Server Platforms
---

### Post by debasishg on 2006-09-10
hi, 

when i'm trying to run squid, it comes with a error msg as follows
```
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.5.STABLE10): Terminated abnormally.
CPU Usage: 0.007 seconds = 0.004 user + 0.003 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
```

how do i resolve this error.

could someone do me a favor? i need a squid.conf file with following requirments. i'm providing my data also
my machine IP [local] ::: 192.168.0.111
my machine name       ::: mandriva

requirement::
1) If clients will use 192.168.0.111 ::: 3128
all the clients requests should go to/re-directed to 
HTTP  ::: ip_add :: port_add
SSL   ::: ip_add :: port_add
FTP   ::: ip_add :: port_add
SOCKS ::: ip_add :: port_add

2)If clients will use 192.168.0.111 ::: 8213
It will allow to get internet.

it will be gr8 help for me.

---

### Post by nesman89 on 2006-09-11
you need to edit your squid.conf.  
add this to your conf file

visible_hostname "yourdomainname" (i.e.  myhomebox.com)

i had this same problem a couple of days ago and when i added this line i was able to use Squid again.

---

### Post by debasishg on 2006-09-18
done.... but still waiting for my second help

---

