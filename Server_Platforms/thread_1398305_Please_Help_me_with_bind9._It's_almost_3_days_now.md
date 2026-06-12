---
title: "Please Help me with bind9. It's almost 3 days now"
date: 2010-02-04
forum: Server Platforms
---

### Post by salman4u on 2010-02-04
Hello,
I am begiiner in Linux and needless to say i am weak in networking fundamentals also. I just wanted to setup dns server using bind9. Read few tutorials and did exactly what it said but i am getting output from my public dns server means even if i type any junk address like dig kjkljkjlkjkljkljkl.com it gives NOERROR message. My domain name should be bapaji.com and I want my domain to be my localhost only means i just want that when i type bapaji.com in mozilla it should ping to my localhost. That's it. I have not hosted my website, it's in development stage.

When i did ifconfig i got this output

```

eth0      Link encap:Ethernet  HWaddr 00:13:a9:81:82:87  
          inet6 addr: fe80::213:a9ff:fe81:8287/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1356415 (1.3 MB)  TX bytes:388743 (388.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23537 (23.5 KB)  TX bytes:23537 (23.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:d5:0e:68  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fed5:e68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:391293 (391.2 KB)  TX bytes:150345 (150.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-D5-0E-68-64-35-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I am behind router and it's default gateway is 192.168.1.1.

Here is my named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "bapaji.com" {
        type master;
        file "/etc/bind/zones/bapaji.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - #e.g my network address is 192.168.0
zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```


Here is named.conf.options
```

options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    forwarders {
          # Replace the address below with the address of your provider's DNS server
          61.1.96.69;
    };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};

```

This is my bapaji.com.db

```

// replace blogger.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
bapaji.com.      IN      SOA     bapaji.com.(
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// blogger.com = domain name
bapaji.com.      IN      NS              bapaji.com.

// Replace the IP address with the right IP addresses.
localhost        IN      A       192.168.1.103
mta              IN      A       192.168.1.103
ns1              IN      A       192.168.1.103

```

Here it's asked to put dns server name in place of ns1. But i don't know what is my dns server name. How can i know it's name?

This is my rev.1.168.192.in-addr.arpa

```

//replace bapaji.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR blogger.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA bapaji.com. bapaji.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     bapaji.com.
103                    IN    PTR    bapaji.com

```

This is /etc/resolve.conf

```

# Generated by NetworkManager
domain PARAG
search PARAG
nameserver 208.67.220.222
nameserver 208.67.220.220

search bapaji.com
nameserver 192.168.1.103

```


Now when i do dig bapaji.com i get :-
```

administrator@ubuntu:~$ dig bapaji.com

; <<>> DiG 9.6.1-P2 <<>> bapaji.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48301
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;bapaji.com.            IN    A

;; ANSWER SECTION:
bapaji.com.        0    IN    A    208.67.219.132

;; Query time: 409 msec
;; SERVER: 208.67.220.222#53(208.67.220.222)
;; WHEN: Thu Feb  4 09:02:49 2010
;; MSG SIZE  rcvd: 44

```


I don't understand why do i get this number "208.67.219.132"? It's on localhost then it should be 127.0.0.1 but it always gives "208.67.219.132" and even when i do something rubbish like jkhjhkkkhkjhjkjk.com i get this output

```

administrator@ubuntu:~$ dig jkhjhkkkhkjhjkjk.com

; <<>> DiG 9.6.1-P2 <<>> jkhjhkkkhkjhjkjk.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26745
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;jkhjhkkkhkjhjkjk.com.        IN    A

;; ANSWER SECTION:
jkhjhkkkhkjhjkjk.com.    0    IN    A    208.67.219.132

;; Query time: 363 msec
;; SERVER: 208.67.220.222#53(208.67.220.222)
;; WHEN: Thu Feb  4 09:04:47 2010
;; MSG SIZE  rcvd: 54

```

Please help me geeks. I am at your mercy. Nobody in my college uses Ubuntu and those use don't know nicely. They are in the same category as me. So please!

---

### Post by cdenley on 2010-02-04
Your system is still configured to use opendns. The IP it returns for invalid domains is an OpenDNS web server which returns suggestions when you look up an invalid domain in a web browser.
```

# Generated by NetworkManager
domain PARAG
search PARAG
[B][COLOR="Red"]nameserver 208.67.220.222
nameserver 208.67.220.220[/COLOR][/B]

search bapaji.com
nameserver 192.168.1.103

```
It won't use your third one (192.168.1.103) until the first two you configured fail. If you only want to resolve the domain on your computer, why bother with DNS? Just add an entry to /etc/hosts:
```

192.168.1.103 bapaji.com

```

---

### Post by dnvikram on 2010-02-04
> **salman4u said:**
> Hello,
I am begiiner in Linux and needless to say i am weak in networking fundamentals also. I just wanted to setup dns server using bind9. Read few tutorials and did exactly what it said but i am getting output from my public dns server means even if i type any junk address like dig kjkljkjlkjkljkljkl.com it gives NOERROR message. My domain name should be bapaji.com and I want my domain to be my localhost only means i just want that when i type bapaji.com in mozilla it should ping to my localhost. That's it. I have not hosted my website, it's in development stage.

When i did ifconfig i got this output

```

eth0      Link encap:Ethernet  HWaddr 00:13:a9:81:82:87  
          inet6 addr: fe80::213:a9ff:fe81:8287/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1356415 (1.3 MB)  TX bytes:388743 (388.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23537 (23.5 KB)  TX bytes:23537 (23.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:d5:0e:68  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fed5:e68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:391293 (391.2 KB)  TX bytes:150345 (150.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-D5-0E-68-64-35-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I am behind router and it's default gateway is 192.168.1.1.

Here is my named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "bapaji.com" {
        type master;
        file "/etc/bind/zones/bapaji.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - #e.g my network address is 192.168.0
zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```


Here is named.conf.options
```

options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    forwarders {
          # Replace the address below with the address of your provider's DNS server
          61.1.96.69;
    };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};

```

This is my bapaji.com.db

```

// replace blogger.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
bapaji.com.      IN      SOA     bapaji.com.(
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// blogger.com = domain name
bapaji.com.      IN      NS              bapaji.com.

// Replace the IP address with the right IP addresses.
localhost        IN      A       192.168.1.103
mta              IN      A       192.168.1.103
ns1              IN      A       192.168.1.103

```

Here it's asked to put dns server name in place of ns1. But i don't know what is my dns server name. How can i know it's name?

This is my rev.1.168.192.in-addr.arpa

```

//replace bapaji.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR blogger.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA bapaji.com. bapaji.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     bapaji.com.
103                    IN    PTR    bapaji.com

```

This is /etc/resolve.conf

```

# Generated by NetworkManager
domain PARAG
search PARAG
nameserver 208.67.220.222
nameserver 208.67.220.220

search bapaji.com
nameserver 192.168.1.103

```


Now when i do dig bapaji.com i get :-
```

administrator@ubuntu:~$ dig bapaji.com

; <<>> DiG 9.6.1-P2 <<>> bapaji.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48301
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;bapaji.com.            IN    A

;; ANSWER SECTION:
bapaji.com.        0    IN    A    208.67.219.132

;; Query time: 409 msec
;; SERVER: 208.67.220.222#53(208.67.220.222)
;; WHEN: Thu Feb  4 09:02:49 2010
;; MSG SIZE  rcvd: 44

```


I don't understand why do i get this number "208.67.219.132"? It's on localhost then it should be 127.0.0.1 but it always gives "208.67.219.132" and even when i do something rubbish like jkhjhkkkhkjhjkjk.com i get this output

```

administrator@ubuntu:~$ dig jkhjhkkkhkjhjkjk.com

; <<>> DiG 9.6.1-P2 <<>> jkhjhkkkhkjhjkjk.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26745
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;jkhjhkkkhkjhjkjk.com.        IN    A

;; ANSWER SECTION:
jkhjhkkkhkjhjkjk.com.    0    IN    A    208.67.219.132

;; Query time: 363 msec
;; SERVER: 208.67.220.222#53(208.67.220.222)
;; WHEN: Thu Feb  4 09:04:47 2010
;; MSG SIZE  rcvd: 54

```

Please help me geeks. I am at your mercy. Nobody in my college uses Ubuntu and those use don't know nicely. They are in the same category as me. So please!

As the other poster suggested,try changing the nameserverdirective in /etc/resolv.conf to your actual configured dns server (or) use /etc/hosts if its just couple of hosts.I am attaching a setup doc for dns server on ubuntu.Hope you find it useful.Unfortunately its a MS Word document.As much I hate to send it in Word format,I am sending this from a windows machine which has ONLY MSOFFICE and not allowed to install any other software.You should be able to open it in OOo3.x without issues,barring any MS specific formatting will be a bit messed up.

---

### Post by terazen on 2010-02-04
If your server does a lookup, it uses it's resolv.conf.  Remove opendns servers from resolv.conf and your server will attempt to do the lookup itself.

In bind, where you set your forwarder, you can set that to opendns server ip address.

If the resolv.conf is set to localhost then any lookup that your server can't answer locally it will use the forwarder(opendns).  If the forwarder (opendns) doesn't know how to find bapaji.com it will return one of it's OWN ip addresses and send you to an opendns webpage.  This is how opendns makes it's money, similar to google and yahoo.

---

### Post by salman4u on 2010-02-05
Thank you folks,
And thanks friend for the MS word doc. I will read it.

@cdenley,
Actually i am trying to create a blogging application in Java (which i won't be hosting it. It's just for project submission). And i want whenever some user registers to website like T then he should be able to browse the site using T.xyz.com where xyz is my virtual server and i don't think adding dynamic subdomains such as *.xyz.com is allowed in hosts.

---

### Post by cdenley on 2010-02-08
> **salman4u said:**
> 
@cdenley,
Actually i am trying to create a blogging application in Java (which i won't be hosting it. It's just for project submission). And i want whenever some user registers to website like T then he should be able to browse the site using T.xyz.com where xyz is my virtual server and i don't think adding dynamic subdomains such as *.xyz.com is allowed in hosts.

You can use subdomains in a hosts file, but not wildcards. Users won't be able to resolve hostnames for xyz.com unless they are either configured to use your DNS, or your DNS server is the registered nameserver for that domain so your records will be propagated across the net. (or they create an entry in /etc/hosts as well)

---

### Post by terazen on 2010-02-08
That should be doable in bind.

```
something                               IN      A       1.2.3.4
*.something                             IN      CNAME   something.xyz.com.
```

---

