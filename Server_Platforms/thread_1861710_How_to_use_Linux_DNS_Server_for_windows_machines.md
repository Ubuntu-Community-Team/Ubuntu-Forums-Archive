---
title: "How to use Linux DNS Server for windows machines"
date: 2011-10-15
forum: Server Platforms
---

### Post by trongbang on 2011-10-15
Hi guys,
My situation is like this:
I'm using Windows XP
I installed VMBox and a Virtual Machine which is an Ubuntu Server
On Ubuntu Server, I installed Apache and Bind9. I also changed /etc/resolv.conf to use the DNS installed.

Testing:
On Ubuntu Server, I can ping 192.168.56.102(ubuntu server)
On my windows XP, I can open web browser at [http://192.168.56.102](http://192.168.56.102)

But I can't use [http://example.com](http://example.com) (which was configured in Bind 9 to point to 192.168.56.102)

Can someone help me please?

Kind Regards,

---

### Post by VirtualFido on 2011-10-16
Have you set up the Ubuntu Server as the primary DNS for the Windows installation? Also, have you tried to clear the Windows DNS cache? Try this in CMD:
```
ipconfig /flushdns
```You can also try to do a nslookup in Windows CMD:
```
nslookup example.com
```The response should be like:
```
nslookup google.com
Server:   1337-SERVER (Your servers hostname or unknown)
Address:  10.0.0.1 (Your servers IP)

Response:
Navn:    google.com
Addresses:  74.125.39.103
          74.125.39.106
          74.125.39.105
          74.125.39.104
          74.125.39.147
          74.125.39.99
```

I am not familiar with BIND9, but you might want to post your config - it would make it easier for the DNS gurus on this forum :)

---

### Post by trongbang on 2011-10-17
> **VirtualFido said:**
> Have you set up the Ubuntu Server as the primary DNS for the Windows installation? Also, have you tried to clear the Windows DNS cache? Try this in CMD:
```
ipconfig /flushdns
```You can also try to do a nslookup in Windows CMD:
```
nslookup example.com
```The response should be like:
```
nslookup google.com
Server:   1337-SERVER (Your servers hostname or unknown)
Address:  10.0.0.1 (Your servers IP)

Response:
Navn:    google.com
Addresses:  74.125.39.103
          74.125.39.106
          74.125.39.105
          74.125.39.104
          74.125.39.147
          74.125.39.99
```

I am not familiar with BIND9, but you might want to post your config - it would make it easier for the DNS gurus on this forum :)
Thanks,

I did changed the dns config of my windows machine to point to 192.168.56.102. But when I used nslookup in cmd, it showed that it couldn't use it. Any ideas???

---

### Post by VirtualFido on 2011-10-17
The DNS server must allow access for your windows machine, are you listening on 0.0.0.0? or simply localhost? If you listen on localhost, other machines will not be able to access it - so try to listen on all interfaces (0.0.0.0) or 192.168.62.102 (which will allow clients on the local network to access it).

Again, I am not an expert on BIND9, the only DNS experience I have is with pdnsd for local dns caching.

This might help:
[http://www.cyberciti.biz/faq/unix-linux-bsd-bind-dns-listenon-configuration/](http://www.cyberciti.biz/faq/unix-linux-bsd-bind-dns-listenon-configuration/)

More specifically:
```
listen-on { any; };
```

or

```
listen-on { 192.168.56.102; };
```

in named.conf

---

### Post by smurphy_it on 2011-10-17
Login to your Ubuntu Server machine, and then check to ensure that DNS is listening on port 53.

```
netstat -ant | grep LISTEN
```

If you are unsure, you can always post the output of that command back here.
Cheers

---

### Post by collisionystm on 2011-10-17
> **trongbang said:**
> Hi guys,
My situation is like this:
I'm using Windows XP
I installed VMBox and a Virtual Machine which is an Ubuntu Server
On Ubuntu Server, I installed Apache and Bind9. I also changed /etc/resolv.conf to use the DNS installed.

Testing:
On Ubuntu Server, I can ping 192.168.56.102(ubuntu server)
On my windows XP, I can open web browser at [http://192.168.56.102](http://192.168.56.102)

But I can't use [http://example.com](http://example.com) (which was configured in Bind 9 to point to 192.168.56.102)

Can someone help me please?



Kind Regards,


Did you make sure to create a reverse dns file?

db.example.com <---forward
db.0.0.168.192 <--- reverse

if you have no idea what I am talking about, go back to the bind9 instructions.

---

### Post by trongbang on 2011-10-18
Thanks all for your help!

I tried but it still didn't work for me. This is what was executed on my windows machine:
> 
F:\Documents and Settings\Bang Nguyen>nslookup 41864603.com
*** Can't find server name for address 192.168.56.102: Server failed
Server:  vnsc-pri.sys.gtei.net
Address:  4.2.2.1

DNS request timed out.
    timeout was 2 seconds.
*** vnsc-pri.sys.gtei.net can't find 41864603.com: Non-existent domain


And this is what I did on my Ubuntu Server:

> 
netstat -ant | grep LISTEN
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 10.1.1.16:53            0.0.0.0:*               LISTEN
tcp        0      0 192.168.56.102:53       0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 192.168.56.102:631      0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::389                  :::*                    LISTEN
tcp6       0      0 :::53                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:631                 :::*                    LISTEN
tcp6       0      0 :::25                   :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN


This is my Bind9 Configuration:
> 
nano /etc/bind/named.conf.local
zone "41864603.com" {
        type master;
        file "/etc/bind/zones/41864603.com.db";
};

zone "56.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.56.168.192.in-addr.arpa";
};



> 
nano /etc/bind/zones/41864603.com.db
$TTL    604800
@       IN      SOA     ns.41864603.com. admin.41864603.com. (
                     2011101715         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.41864603.com.
@       IN      A       192.168.56.102
ns      IN      A       192.168.56.102
ubuntu-server   IN      A       192.168.56.102
ubunut-client   IN      A       192.168.56.101



> 
nano /etc/bind/zones/rev.56.168.192.in-addr.arpa
$TTL    604800
@       IN      SOA     ns.41864603.com. admin.41864603.com. (
                     2011101522         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
@       PTR     A       41864603.com.
41864603.com    IN      A       192.168.56.102
102     IN      PTR     ns.41864603.com


@VirtualFido: I think because I tested the port listening above, so I don't need to run this right: listen-on { 192.168.56.102; };

Thanks so much guys!

---

### Post by trongbang on 2011-11-04
I know the reason.

I have 2 internet connection: 1 is Virtual box , 1 is real Ethernet.

I configured the DNS server for the real Ethernet card. That's why.

I should have configured for the Virtual Box card.

---

