---
title: "MX Record"
date: 2012-09-07
forum: Server Platforms
---

### Post by IvanMP on 2012-09-07
Hi all

i need help 

i have the following zone files and im trying to add MX record to them ... 

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     tm.example.com.cm. root.tm.example.com.cm. (
                             22         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.tm.example.com.cm.
@       IN      A       192.168.100.131
@       IN      AAAA    ::1

```

and the revers zone file is 

```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     tm.example.com.cm. root.tm.example.com.cm. (
                             16         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.tm.example.com.cm.
131     IN      PTR     ns.tm.example.com.cm.

```

so when i add a MX record, on named-checkzone i always get an error like "mail (out of zone) has no addresses records (A or AAAA)"  

Can some one pls help me and tell me how to put the MX record ... because i try on all ways and nothing ... i need this  

The "tm.example.com.cm" is like example.com.cm ... "tm" is short for TestMail


TNX in advance

---

### Post by darkod on 2012-09-07
I don't see any MX or A records related to email.

First you need to create one A record that will be called mail for example, and point it to the server IP.

Then you create the MX record pointing to mail.example.com or in your case maybe mail.tm.example.com depending what your basic domain is.

The point with MX records is that they can't point to an IP directly, they have to point to a host. That's why you first create the A record (host) which is pointing to the IP.

---

### Post by IvanMP on 2012-09-10
Hi darkod,

tnx for the reply i try to modify like you say so here it is ....

> $ttl 38400
tm.example.com.cm.    IN      SOA     tm.example.com.cm. ivan.tm.example.com.cm. (
                        1347276249
                        10800
                        3600
                        604800
                        38400 )
tm.example.com.cm.    IN      NS      tm.example.com.cm.
tm.example.com.cm.    IN      MX      10 tm.example.com.cm
tm.example.com.cm.    IN      A       192.168.100.131


and the revers 

> $ttl 38400
131.100.168.192.in-addr.arpa.   IN      SOA     tm.example.com.cm. ivan.tm.example.com.cm. (
                        1347276298
                        10800
                        3600
                        604800
                        38400 )
131.100.168.192.in-addr.arpa.   IN      NS      tm.example.com.cm.
131.100.168.192.in-addr.arpa.   IN      PTR     tm.example.com.cm.


So now when i try nslookup for tm.example.com.cm its ok ... but when i try the revers nslookup fro example nslookup 192.168.100.131 i get this error 

;; Got SERVFAIL reply from 192.168.100.131, trying next server

He goes to the next dns server and who know about Ubuntu server (this server tm.example.com.cm) so he back the name the hostname of it ... i dont know why he cant back the answer of its own ... 


Here its the output of named-chekzone 

> root@tm:/etc/bind# named-checkzone db.192 db.192
db.192:2: ignoring out-of-zone data (131.100.168.192.in-addr.arpa)
db.192:8: ignoring out-of-zone data (131.100.168.192.in-addr.arpa)
db.192:9: ignoring out-of-zone data (131.100.168.192.in-addr.arpa)
zone db.192/IN: has 0 SOA records
zone db.192/IN: has no NS records
zone db.192/IN: not loaded due to errors.


but i cant understand what im doing wrong 

sorry for bad language  i hope you understand if not pls ask me ... 

Tnx in advance ....

---

### Post by Bachstelze on 2012-09-10
```
$ttl 38400
100.168.192.in-addr.arpa. IN SOA tm.example.com.cm. ivan.tm.example.com.cm. (
    1347276298
    10800
    3600
    604800
    38400 )

100.168.192.in-addr.arpa.     IN NS   tm.example.com.cm.
131.100.168.192.in-addr.arpa. IN PTR  tm.example.com.cm.
```

---

### Post by darkod on 2012-09-10
Hold on. Is your domain example.com.cm or tm.example.com.cm?

It looks like the tm in front is a host. Is it a part of the domain name or not? Because there is big difference.

---

### Post by IvanMP on 2012-09-10
> **darkod said:**
> Hold on. Is your domain example.com.cm or tm.example.com.cm?

It looks like the tm in front is a host. Is it a part of the domain name or not? Because there is big difference.

TM is like a synonym of TestMail, so yes it is a domain.

And now i have the following files i changed some thins ...

named.conf.options
> 
forwarders {
                192.168.100.131; - Ubuntu server
               192.168.100.16; - Other (win DNS server)
               8.8.8.8; - google ....
         };


named.conf.local

> 
zone "tm.example.com.cm" {
             type master;
             file "/etc/bind/db.tm.example.com.cm";
        };

zone "100.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};



the zone files are:

db.tm.example.com.cm
> 
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     tm.example.com.cm. root.tm.example.com.cm. (
                             23         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.tm.example.com.cm.
@       IN      A       192.168.100.131
@       IN      AAAA    ::1
www     IN      A       192.168.100.131
        IN      MX 10   mail.tm.example.com.cm.
mail    IN      A       192.168.100.131



and revers zone
> 
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     tm.example.com.cm. root.tm.example.com.cm. (
                             15         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
131     IN      PTR     tm.example.com.cm.


The error i got when i use named-checkzone is:

> 

zone db.tm.example.com.cm/IN: [www.db.tm.example.com.cm/MX](www.db.tm.example.com.cm/MX) 'mail.tm.example.com.cm' (out of zone) has no addresses records (A or AAAA)

root@tm:/etc/bind# named-checkzone tm.example.com.cm db.tm.example.com.cm
zone tm.example.com.cm/IN: NS 'ns.tm.example.com.cm' has no address records (A or AAAA)
zone tm.example.com.cm/IN: not loaded due to errors.
root@tm:/etc/bind#


... i try all week to do something , changing the zone files change the name etc... but no result and i need this ... 

and now its different ... nsllookup for 192.168.100.131 works ok but for tm.example.com.cm wont give an answer, it give me error like 

Server:         192.168.100.131
Address:        192.168.100.131#53

** server can't find tm.makpetrol.com.mk: SERVFAIL


TNX in advance !

---

### Post by Bachstelze on 2012-09-10
I believe I gave you a correct reverse zone file. Why ask a question if you are going to ignore answers? And your other zone file worked, so why did you change it?

---

### Post by IvanMP on 2012-09-10
> **Bachstelze said:**
> I believe I gave you a correct reverse zone file. Why ask a question if you are going to ignore answers? And your other zone file worked, so why did you change it?

Sorry Bachstelze i didn't reply to you, i try your way and revers did't give me error but the db.tm.example.com.cm give me the same error for MX record that has no address records (A or AAAA).

So i thing, and asking ... because in our company we have a domain example.com.cm and on that domain we have Microsoft Exchange mail server, so there is already mail.example.com.cm ...so im trying to build linux mail server "Postfix" and put it on test phase ... so i install the Ubuntu server and starting to configure bind ... and i did this ... so in the main windows server i put the tm.makpetrol.com.mk domain and its ok, he can back info of nslookup, but why the Ubuntu server cant find him self on nslookup ? What im doing wrong ?

Once again Bachstelze sorry i didn't reply to you . 
And tnx for the reply on all and in advance !

---

### Post by Bachstelze on 2012-09-10
```

$TTL 604800
tm.example.com.cm. IN SOA tm.example.com.cm. root.tm.example.com.cm. (
    23 ; Serial
    604800 ; Refresh
    86400 ; Retry
    2419200 ; Expire
    604800 ) ; Negative Cache TTL
;

$ORIGIN tm.example.com.cm.
@     IN NS    ns.tm.example.com.cm.
@     IN A     192.168.100.131
@     IN AAAA  ::1
www   IN A     192.168.100.131
@     IN MX 10 mail.tm.example.com.cm.
mail  IN A     192.168.100.131
ns    IN A     192.168.100.131
```

Added $ORIGIN because using relative names without it makes things ambiguous. It is quite clear that you have no real idea what you are doing, so you should really read more about DNS and BIND (O'Reilly has a good book about them).

---

### Post by darkod on 2012-09-10
On top of what is already said, I wonder whether you need this at all.

I see you are trying to use a private IP for the server. Is this just not to show the real public IP or you plan to use it like that? You can't use the mail server with private IP, nobody will be able to send mail to it.

Besides, your domain is registered somewhere, right? Usually they will have a nice control panel where you can create the MX record very easy. Why setting up your own dns server?

A mail server needs to have a public IP so that mail can reach it. Do you have one to use? And if you do, why setting up your dns server with a private IP for the MX record.

---

