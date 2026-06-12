---
title: "DNS problem with bind9"
date: 2011-02-01
forum: Server Platforms
---

### Post by carachi on 2011-02-01
Hi, 
I try to install a dns server with bind9, 
I configure the forwarders in /etc/bind/named.conf.options and the zone  in /etc/bind/named.conf.local
but the clients can't resolve the URL... 
have you any ideas? 

Thank you
Bye

---

### Post by rudelgurke on 2011-02-01
Which clients can't resolve which URL ? And does Bind ouput any errors in the logfile(s) ?

---

### Post by carachi on 2011-02-01
> **rudelgurke said:**
> Which clients can't resolve which URL ? And does Bind ouput any errors in the logfile(s) ?

Hi rudelgurke,
the client how I have set the nameserver don't resolve any URL ... dig ubuntu.com reply error time connection.
I try to find logs file but I didn't find the query log file in /var/log/.
where can I search it?

Thank you 
Bye

---

### Post by rudelgurke on 2011-02-01
Well - a simple setup with forwarding would be:

```

options {
 ...
 listen-on { 127.0.0.1; };
 forwarders { ip_of_the_first_forwarder; ip_of_the_second_forwarder; ... };
 allow-recursion { 127.0.0.1; };
 allow-transfer { none; };
 allow-update { none; };
 version none;
 hostname none;
 server-id none;
 ...
};

```

Then following the zone definitions. Ensuring Bind runs:

netstat -tulpen | egrep '127.0.0.1:53'

And finally setting it in resolv.conf.

Then the setup should be fine so far.

In /var/log/messages Bind should output some messages. If not:

grep -ril 'bind' /var/log/*

will print the files where the info can be found.

---

### Post by carachi on 2011-02-02
Thank you rudelgurke !
Now the DNS works for the clients, but if I try to go on my FDQN don't find the web pages.
I set the files so:

```


  GNU nano 2.2.4             File: /etc/hosts                                   

127.0.0.1       localhost
127.0.1.1       router.mydomain.it       router
192.168.2.254   ns.mydomain.it           ns
192.168.2.254   smtp.mydomain.it         smtp
192.168.2.254   imap.mydomain.it         imap
192.168.2.254   mail.mydomain.it         mail


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters



/etc/resolv.conf

#nameserver 192.168.1.254
search mydomain.it
nameserver 127.0.0.1
nameserver 8.8.8.8
#nameserver 8.8.4.4
nameserver 208.67.222.222
domain mydomain.it


  GNU nano 2.2.4                     File: /etc/bind/named.conf.local                                                  

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "mydomain.it" {
        type master;
        file "/etc/bind/db.mydomain.it";
};

zone "2.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192.168.2";
};



GNU nano 2.2.4                      File: /etc/bind/db.mydomain.it                                                    

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.mydomain.it. root.mydomain.it. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      mydomain.it.
@       IN      A       127.0.0.1
@       IN      AAAA    ::1




 GNU nano 2.2.4                      File: /etc/bind/db.192.168.2                                                     

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.mydomain.it. root.mydomain.it. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
1.0.0   IN      PTR     ns.mydomain.it.



```

Where I wrong?

Thank you

Bye

---

### Post by rudelgurke on 2011-02-02
Your zone files are wrong, except you really want to use 127.0.0.1 as IP.

And note - 127.0.0.1 also resolves for all clients so even external ones would resolve mydomain.it to 127.0.0.1.

Correct these, then it should work as expected

---

### Post by James78 on 2011-02-02
This BIND security template will really help you out. It includes ways to secure down your BIND, but of course it has a full configuration that works. Enjoy!
[http://www.cymru.com/Documents/secure-bind-template.html](http://www.cymru.com/Documents/secure-bind-template.html)

---

