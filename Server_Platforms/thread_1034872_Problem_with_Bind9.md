---
title: "Problem with Bind9"
date: 2009-01-09
forum: Server Platforms
---

### Post by eufran on 2009-01-09
Hello. I have installed Bind9 and works perfect, but i have a problem.


My file zone is:

SIZE="1"];
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     fran.es. root.fran.es. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      iesbenicassim.es.
@       IN      A       192.168.1.250
@       IN      AAAA    ::1
fsserver        IN      A       192.168.1.250
ccserver        IN      A       192.168.1.251
aulavirtual     IN      A       192.168.1.250[/SIZE]


The problem is when a client goes to [http://www.fran.es](http://www.fran.es).
The bind9 will to redirecto to Fowaders but no works!!!!


whats is the problem???

---

### Post by thedarkwinter on 2009-01-09
Hi

* You should (probably?) start with an $ORIGIN
* Your Serial number should be in the format YYYYMMDDVV (VV=version)
* Your MNAME (in SOA) is fran.es which doesn't have a corresponding NS record (though that is also probably acceptable)

* You do not have an A record for www, and since this will answer the request authoritatively, your client will not look at the second nameserver (iesbenicassim.es). You can use NS records for www if you want it to:

* Also "; BIND data file for local loopback interface" I'm assuming this is because you copied the file, and not that you have overwritten db.local?

```

$ORIGIN fran.es.
$TTL 604800
@ IN SOA fran.es. root.fran.es. (
2008010901 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS iesbenicassim.es.
@ IN A 192.168.1.250
@ IN AAAA ::1
fsserver IN A 192.168.1.250
ccserver IN A 192.168.1.251
aulavirtual IN A 192.168.1.250

www IN A 192.168.100.100
; OR
www IN NS iesbenicassim.es.

```

Hope this help...
Cheers,
Michael

---

### Post by eufran on 2009-01-12
Thankssssssss


Now when a clients request [www.iesfran.es](www.iesfran.es)  bind server goes to fowarders.
Perfect.

And other question.  Can i do the same when a client goes to mail.iesfran.es ???


thanks a lot

(sorry for my english, i´m from spain)

---

### Post by thedarkwinter on 2009-01-12
Glad to hear its working...

You can have as many records as you like. You can also use a wildcard record to "catch-all" - *. This will catch anything that is NOT defined elsewhere. So in the below example, anything will resolve to 192.168.0.200 except for mail and webmaill.

```

mail IN A 192.168.0.123
webmail IN A 192.168.0.124
* IN A 192.168.0.200

```

Cheers,
Michael

---

