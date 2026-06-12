---
title: "Local DNS not resolving"
date: 2012-01-14
forum: Server Platforms
---

### Post by umniah on 2012-01-14
Hi every one
I hope you can help me with this problem because I've been stuck for days and have no idea what I'm doing wrong!

I'm trying to configure a local DNS, Mail and Web servers on a local network, no internet access is required for now.

I started with the DNS server and I followed several tutorials, all have the same steps and redid it many times still its not working as I expected.

I'm working on ubuntu server 10.04 install on virtual box.

The settings I'm using are:

in the interfaces file :```

address 10.0.2.1
mask 255.255.255.0
network 10.0.2.0
gateway 10.0.2.2

```


the hosts file :
```

127.0.0.1 localhost
10.0.2.1  ns.test.com  ns

```

the named.conf.local:
```

zone test.com {
type master;
file "etc/bind/db.test.com";
};

zone 2.0.10.in-addr.arpa {
type master;
file "/etc/bind/db.10";
};

```

the db.test.com :

```

; 
; BIND data file 
; 
$TTL 604800
@      IN      SOA      ns.test.com. root.test.com. ( 
                        3; Serial 
                        604800
                        86400 
                        2419200
                        604800 
                        
) 

@                  IN     NS    ns.test.com 
@                  IN     A     127.0.0.1
@                  IN     A     10.0.2.1 
web.test.com       IN     A     10.0.2.3 
ns                 IN     A     10.0.2.1 

```
 the db.10 file :
```

; 
; BIND reverse zone
; 
$TTL 604800
@ IN SOA ns.test.com. admin.test.com. ( 
                        2      ; Serial  
                        604800;
                        86400; 
                        2419200; 
                        604800 
) 
;
@       IN      NS      ns.test.com. 
1       IN      PTR     test.edu 
1       IN      PTR     ns.test.com 
3       IN      PTR     web.test.com 

```

and finally, the resolv.conf file :
```

search test.com
nameserver 10.0.2.1

```


now when I run 
```

dig test.com

```

I get a response (not sure if it is correct!)

and when I ping test.com or web.test.com I get a host unknown message.

please help me figure out what I'm doing wrong. or if I'm doing anything right :D

Thank you.

---

### Post by CharlesA on 2012-01-14
Will this be on a large network? If not, I would suggest using DNSMASQ instead of a full blown BIND server.. easier to configure and easier to manage imo.

---

### Post by umniah on 2012-01-15
Thank you for replying. the network should include at least 50 users. I know its not much but still I would like to learn how to configure bind . 
I will try the DNSMasq but I would appreciate it if you could help me figure out what is wrong with my settings.

---

### Post by Doug S on 2012-01-15
Hi umniah,
 
And welcome to ubuntu forums. I am not an expert with bind, but I do use it and I have tried to help on other forum threads before.
 
You need to be carfeful with the syntax and when a period is needed at the end of stuff and when it is not. Also, you can only have one reverse IP per name. I don't think it will give and error if there are multiple entries, but it would never use them.
 
My suggested db.test.com```
;
; BIND data file
;
$TTL 604800
@      IN      SOA      test.com. root.test.com. (
                        4; Serial
                        604800
                        86400
                        2419200
                        604800 )
                   IN     A     10.0.2.1
;
@                  IN     NS    ns.test.com.
ns                 IN     A     10.0.2.1
web                IN     A     10.0.2.3

```My suggested db.10```
;
; BIND reverse zone
;
$TTL 604800
@ IN SOA ns.test.com. admin.test.com. (
                        3      ; Serial
                        604800;
                        86400;
                        2419200;
                        604800
)
;
@       IN      NS      ns.test.com.
1       IN      PTR     ns.test.com.
3       IN      PTR     web.test.com.

```
I hope this helps and please post back if problems continue. Perhaps try to supply more information if you post back. For example what was the actual output for "dig test.com" above? Does bind give any error messages when it starts or re-starts?

---

### Post by umniah on 2012-01-15
Hi Doug S,
Thank you so much for replying.
I modified the files as you suggested and I get this output from dig:
```

root@ns:/home/server# dig test.com

; <<>> DiG 9.7.0-PI <<>> test.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 59103
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;test.com. IN A

;; Query time: 452 msec
;; SERVER: 10.0.2.1#53(10.0.2.1)
;; WHEN: Sun Jan 15 22:24:40 2012
;; MSG SIZE rcvd: 24


``` 

as for bind, I get no errors when starting it.

I also tried the following:
```

root@ns:/home/server# named-checkzone test.com /etc/bind/db.test.com
zone test.com IN: loaded serial 8
OK

```
however, it seems that there is a problem with the reverse zone file when I check it:
```

root@ns:/home/server# named-checkzone test.com /etc/bind/db.10
zone test.com IN: NS 'ns.test.com' has no address records (A or AAAA)
zone test.com IN: not loaded due to errors. 

```
and I'm not sure how to fix it!
Thanks again for helping me, really appreciate it :)

---

### Post by Doug S on 2012-01-15
I believe (unconfirmed) the reverse check instructions in the Ubuntu server guide are incorrect.
See: [http://ubuntuforums.org/showthread.php?t=1905525](http://ubuntuforums.org/showthread.php?t=1905525) 
and also: [https://bugs.launchpad.net/serverguide/+bug/864259](https://bugs.launchpad.net/serverguide/+bug/864259)
Summary, do this instead (which, by the way, I did before my first reply):```
named-checkzone 2.0.10.in-addr.arpa /etc/bind/db.10
```I'll reply later on your first issue.

---

### Post by umniah on 2012-01-15
Yes now it shows OK for both files.

---

### Post by Doug S on 2012-01-15
For your "dig test.com" issue, it is not clear to me what is wrong. The time is key:```
;; Query time: 452 msec
```As it seems way to long, meaning the request was probably forwaded. I don't know why. For example, here are the results for my system:```
doug@doug-64:~/config/bind/temp1$ dig smythies.com
; <<>> DiG 9.7.1-P2 <<>> smythies.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50591
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
;; QUESTION SECTION:
;smythies.com.                  IN      A
;; ANSWER SECTION:
smythies.com.           604800  IN      A       192.168.111.1
;; AUTHORITY SECTION:
smythies.com.           604800  IN      NS      ns1.smythies.com.
;; ADDITIONAL SECTION:
ns1.smythies.com.       604800  IN      A       192.168.111.1
;; Query time: [COLOR=red]0 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Jan 15 12:17:48 2012
;; MSG SIZE  rcvd: 80

```

---

### Post by umniah on 2012-01-15
one more thing...
I tried this :
```

root@ns:/home/server# dig -x 10.0.2.3

; <<>> DiG 9.7.0-PI <<>> -x 10.0.2.3
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 59103
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;3.2.0.10.in-addr.arpa.        IN PTR

;; ANSWER SECTION:
;3.2.0.10.in-addr.arpa. 604800 IN PTR web.test.com.

;; AUTHORITY SECTION:
;2.0.10.in-addr.arpa.   604800 IN NS  ns.test.com.

;; Query time: 1124 msec
;; SERVER: 10.0.2.1#53(10.0.2.1)
;; WHEN: Sun Jan 15 22:15:14 2012
;; MSG SIZE rcvd: 80

```

this worked the same of 10.0.2.1 and 127.0.0.1

---

### Post by Doug S on 2012-01-15
While your reverse lookups seem to be working, they take a long time and the status is SERVFAIL. I am out of ideas. The only other difference I notice between our systems is that I do not have a search line in my resolv.conf file.

---

### Post by umniah on 2012-01-16
Thank you so much for your help, I really appreciate it.
I will post back if figure out whats wrong.

---

### Post by SeijiSensei on 2012-01-16
> root@ns:/home/server# dig test.com

This asks the server to find the A record associated with "test.com".  Your zone file only declares A records for the hosts "ns.test.com" and "www.test.com".  Try running "dig ns.test.com" and see what you get.

I generally use the "host" command instead of dig. By default "host some.domain.name" returns the A record for that name, but you can add the -t parameter to search for a particular type of record like "host -t ns test.com".

---

### Post by Doug S on 2012-01-16
Hi Seiji,
 
I think the changes I suggested in post #4 should have fixed the no A record for "test.com" issue. (by the way, I learned that change from you and your posting [here]("http://ubuntuforums.org/showpost.php?p=10720499&postcount=6"). So a way overdue thanks, as it fixed an issue that had been on my "to do" list for several months.)
 
... Doug

---

### Post by umniah on 2012-01-17
Hi

so I tried the host command and this is what I get:
```

root@ns:/home/server# host test.com
Host test.com not found: 2(SERVERFAIL) 

```

---

### Post by Doug S on 2012-01-17
I still think the important information is the SERVFAIL and the long query times in the dig results. For your named.conf.local file, try changing this line:```
file "etc/bind/db.test.com";

```to this:```
file "/etc/bind/db.test.com";

```But also try using quotes around the zone names. I'm saying try this:```
zone "test.com" { type master; file "/etc/bind/db.test.com"; };
zone "2.0.10.in-addr.arpa" { type master; notify no; file "/etc/bind/db.10"; };
```
After you restart bind, look for "named" entries in /var/log/syslog to see if it doesn't like something.

---

