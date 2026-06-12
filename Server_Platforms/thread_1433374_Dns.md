---
title: "Dns"
date: 2010-03-18
forum: Server Platforms
---

### Post by t.choi on 2010-03-18
Hi,

I m using ubuntu server 9.04 version and trying to configure a primary master DNS on my server as followed the ubuntu&#347; offical documentation 
[https://help.ubuntu.com/9.04/serverguide/C/dns-configuration.html#dns-primarymaster-configuration](https://help.ubuntu.com/9.04/serverguide/C/dns-configuration.html#dns-primarymaster-configuration)

the files named.conf.local, db.example.com & db.192 are almost same as the documentation.

and I can restart DNS

But when i followed the troublshooting page to ping example.com 

thomas@UServer:~$ ping -c 4 example.com
PING example.com (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.047 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.067 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.058 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.061 ms

--- example.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.047/0.058/0.067/0.009 ms
thomas@UServer:~$ 

it is not show my server &#347; IP. 

Is it correct on the configuration?

Thank you

---

### Post by cdenley on 2010-03-19
Entries in your /etc/hosts file will override any DNS records for pings.
```

host example.com
dig @mydnsserverip example.com

```

---

### Post by t.choi on 2010-03-21
> **cdenley said:**
> Entries in your /etc/hosts file will override any DNS records for pings.
```

host example.com
dig @mydnsserverip example.com

```

[B]Hello,

[/B]**Is it correct? Does my configuration is correct?**

thomas@UServer:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    UServer

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
thomas@UServer:~$ host example.com
example.com has address 127.0.0.1
example.com has IPv6 address ::1

**while **

thomas@UServer:~$ dig @192.168.1.33 example.com

; <<>> DiG 9.5.1-P2.1 <<>> @192.168.1.33 example.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5187
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;example.com.            IN    A

;; ANSWER SECTION:
example.com.        604800    IN    A    127.0.0.1

;; AUTHORITY SECTION:
example.com.        604800    IN    NS    ns.example.com.

;; ADDITIONAL SECTION:
ns.example.com.        604800    IN    A    192.168.1.33

;; Query time: 0 msec
;; SERVER: 192.168.1.33#53(192.168.1.33)
;; WHEN: Sun Mar 21 22:42:18 2010
;; MSG SIZE  rcvd: 78

[B]This is a correct response ? but if so why when I used PING it does show the 127.0.0.1 instead of 192.168.1.33 
[/B]
Thank  you

---

### Post by inphektion on 2010-03-21
can you post your db.example.com

127.0.0.1 is the localhost address of the box, so since you are running these cmds from that same server it makes sense it shows that in the ping.  you can add your fqdn to the hosts file if you want but won't effect the master dns anyway.

---

### Post by t.choi on 2010-03-22
Yes, thank you for helping


thomas@UServer:~$ cat /etc/bind/db.example.com
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns.example.com. root.example.com. (
              2010031902    ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.example.com.
ns    IN    A    192.168.1.33
@    IN    A    127.0.0.1
@    IN    AAAA    ::1
thomas@UServer:~$

---

### Post by cdenley on 2010-03-22
> **t.choi said:**
> Yes, thank you for helping


thomas@UServer:~$ cat /etc/bind/db.example.com
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns.example.com. root.example.com. (
              2010031902    ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.example.com.
[B]ns    IN    A    192.168.1.33
@    IN    A    127.0.0.1[/B]
@    IN    AAAA    ::1
thomas@UServer:~$

It is working properly. The A record for ns.example.com is 192.168.1.33. The A record for example.com is 127.0.0.1. That guide tells you to ping "example.com", then it gives you the results of pinging "ns.example.com", so I can see why you are confused. It is working as you configured it. I'm not sure why a DNS server would resolve anything to 127.0.0.1, though.

---

### Post by t.choi on 2010-03-22
Thank you cdenley

If I edited @ IN A 127.0.0.1 -> @ IN A 192.168.1.33

thomas@UServer:~$ cat /etc/bind/db.example.com
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns.example.com. root.example.com. (
              2010031903    ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.example.com.
ns    IN    A    192.168.1.33
@    IN    A    192.168.1.33
@    IN    AAAA    ::1
thomas@UServer:~$ 
 
 

then

when I ping example.com ( of course restart the bind9 first )

thomas@UServer:~$ ping -c 4 example.com
PING example.com (192.168.1.33) 56(84) bytes of data.
64 bytes from ns.example.com (192.168.1.33): icmp_seq=1 ttl=64 time=0.043 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=2 ttl=64 time=0.060 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=3 ttl=64 time=0.058 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=4 ttl=64 time=0.059 ms

--- example.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.043/0.055/0.060/0.007 ms

then I got 192.168.1.33 fm ping

But this change would make some error (@ IN A 127.0.0.1 -> @ IN A 192.168.1.33)?

---

### Post by cdenley on 2010-03-22
> **t.choi said:**
> 
But this change would make some error (@ IN A 127.0.0.1 -> @ IN A 192.168.1.33)?

What do you mean? Where do you want your records to point?

---

### Post by t.choi on 2010-03-22
i mean I added an A record, ¨@    IN    A    192.168.1.33¨ on before the line of the  A record ¨@    IN    A    127.0.0.1¨ in my db.example.com

then now my db.example.com is 
@    IN    NS    ns.example.com.
ns    IN    A    192.168.1.33
@    IN    A    192.168.1.33
@    IN    A    127.0.0.1
@    IN    AAAA    ::1

when I ping example.com 3 times I got different IPs

thomas@UServer:~$ ping -c 4 example.com
PING example.com (192.168.1.33) 56(84) bytes of data.
64 bytes from ns.example.com (192.168.1.33): icmp_seq=1 ttl=64 time=0.046 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=2 ttl=64 time=0.059 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=3 ttl=64 time=0.059 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=4 ttl=64 time=0.059 ms

--- example.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.046/0.055/0.059/0.010 ms
thomas@UServer:~$ ping -c 4 example.com
PING example.com (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.049 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.060 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.066 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.061 ms

--- example.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.049/0.059/0.066/0.006 ms
thomas@UServer:~$ ping -c 4 example.com
PING example.com (192.168.1.33) 56(84) bytes of data.
64 bytes from ns.example.com (192.168.1.33): icmp_seq=1 ttl=64 time=0.045 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=2 ttl=64 time=0.068 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=3 ttl=64 time=0.065 ms
64 bytes from ns.example.com (192.168.1.33): icmp_seq=4 ttl=64 time=0.060 ms

--- example.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.045/0.059/0.068/0.011 ms

---

### Post by cdenley on 2010-03-22
> **t.choi said:**
> i mean I added an A record, ¨@    IN    A    192.168.1.33¨ on before the line of the  A record ¨@    IN    A    127.0.0.1¨ in my db.example.com

then now my db.example.com is 
@    IN    NS    ns.example.com.
ns    IN    A    192.168.1.33
@    IN    A    192.168.1.33
@    IN    A    127.0.0.1
@    IN    AAAA    ::1

when I ping example.com 3 times I got different IPs


Well, yeah. Why would you add a new entry? Pick which address you want example.com to resolve to, then use that entry (not both).

---

### Post by inphektion on 2010-03-22
Basically there is no reason for this in a dns server.
@ IN A 127.0.0.1

just delete it.  it can only cause harm by being there.

---

### Post by t.choi on 2010-03-23
> **inphektion said:**
> Basically there is no reason for this in a dns server.
@ IN A 127.0.0.1

just delete it.  it can only cause harm by being there.

Thank you

@ IN A 127.0.0.1

this line is just copied fm the offical documentation of Ubuntu server 9.04

---

### Post by t.choi on 2010-03-23
How could I report this bug to the Documentation for 9.04?

---

### Post by inphektion on 2010-03-23
prob not a bug.  it's supposed to be in db.local which is maybe where you read it.  It is not supposed to be in db.example.com where you were putting it.  if you installed bind from repo's then I think db.local is already created for you with that defined.  you then need to create your actual domains and you don't point them to 127.0.0.1 as nothing outside of your box will use that address.

---

