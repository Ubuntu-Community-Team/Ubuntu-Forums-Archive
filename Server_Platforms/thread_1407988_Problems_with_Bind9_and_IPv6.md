---
title: "Problems with Bind9 and IPv6"
date: 2010-02-15
forum: Server Platforms
---

### Post by rukiaEnix on 2010-02-15
hello I'm having a problem setting up a DNS using BInd9 in Debian.
I already have IPv6 module loaded and I have a static IPv6 address in my Debian computer and it works, also Apache2 works great with IPv6.
The only problem is Bind9, but it is weird because if I give a nslookup with the address:
```
nslookup 2002:a09:807::204:acff:fe66:7d47
```
it resolves the IPv6 address returning the domain name but If y give a nslookup with the domain name:
```
nslookup ipv6.mypc.com
```
and that's when I have an error because it says that such domain doesn't exist I don't know what I'm doing wrong because the reverse zone is obviously working but it just doesn't get the domain name.

My domain zone configuration file is:

```

;
; BIND data file for local loopback interface.
;
$TTL    604800
@    IN    SOA    ipv6.mycomputer.com. root.ipv6.mycomputer.com. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS        ipv6.mycomputer.com.
@    IN    AAAA    2002:a09:807::204:acff:fe66:7d47

```

I don't attach the reverse zone file because it's working fine the problem is with the domain name. And here is the section in named.conf that concerns to the domain:

```

zone "ipv6.mycomputer.com" {
    type master;
    file "/etc/bind/db.domain";
};

```

I hope someone can tell me what is wrong because it's a really weird problem.
Thanks.

---

### Post by yogesh.girikumar on 2010-02-19
Hi,


       Your configuration file seems ok. You can try specifying the type of record to look for when doing an nslookup:


   Try this
```
nslookup -type=AAAA ipv6.mypc.com
```This (non-interactive) command returns quad-A records that correspond to IPv6.If you want to execute the command in an interactive mode, do this:

```
# nslookup
> set type=AAAA
> ipv6.mypc.com
```Hope this helps.

---

### Post by rukiaEnix on 2010-02-19
Thanks for your help but I have already try that :frown:, I have been looking in other threads and it seems it has something to do with DHCP and I think it might be that because I'm using 2 interfaces, the first one has DHCP and the second one has the static IPV6 address.
I will try configuration with the DHCP and see what happens.
Thanks for your help!

---

### Post by yogesh.girikumar on 2010-02-23
Hi,[INDENT]      > I have been looking in other threads and it seems it has something to do with DHCP   [/INDENT]I still have a strong feeling that the DHCP server is not in the picture. Can you post the output of the following commands **while you are logged into the DNS server** itself so that it'll be easier to zero in on the cause of your issue?
   ```
$ nslookup -type=PTR 2002:a09:807::204:acff:fe66:7d47 localhost
```  ```
$ nslookup -type=AAAA ipv6.mypc.com localhost
```  ```
$ nslookup -type=A ipv6.mypc.com localhost
```      The result of these lookups might give an idea as to what the problem could be.

---

### Post by rukiaEnix on 2010-03-04
hello thanks for your help and sorry for answering so late, I've been really busy with my IPv6 investigations (thesis).
I did the 3 nslookups you told me and the 3 of them gave me this answer:
```

nslookup: couldn't get address for 'localhost': not found

```

Here is my syslog entry from named:

```

Mar  4 02:49:57 localhost named[2637]: starting BIND 9.5.1-P3 -u bind
Mar  4 02:49:57 localhost named[2637]: found 1 CPU, using 1 worker thread
Mar  4 02:49:57 localhost named[2637]: using up to 4096 sockets
Mar  4 02:49:57 localhost named[2637]: loading configuration from '/etc/bind/named.conf'
Mar  4 02:49:57 localhost named[2637]: max open files (1024) is smaller than max sockets (4096)
Mar  4 02:49:57 localhost named[2637]: using default UDP/IPv4 port range: [1024, 65535]
Mar  4 02:49:57 localhost named[2637]: using default UDP/IPv6 port range: [1024, 65535]
Mar  4 02:49:57 localhost named[2637]: listening on IPv6 interfaces, port 53
Mar  4 02:49:57 localhost named[2637]: listening on IPv4 interface lo, 127.0.0.1#53
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: 127.IN-ADDR.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: 254.169.IN-ADDR.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: D.F.IP6.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: 8.E.F.IP6.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: 9.E.F.IP6.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: A.E.F.IP6.ARPA
Mar  4 02:49:57 localhost named[2637]: automatic empty zone: B.E.F.IP6.ARPA
Mar  4 02:49:57 localhost named[2637]: command channel listening on 127.0.0.1#953
Mar  4 02:49:57 localhost named[2637]: command channel listening on ::1#953
Mar  4 02:49:57 localhost named[2637]: the working directory is not writable
Mar  4 02:49:57 localhost named[2637]: zone 0.in-addr.arpa/IN: loaded serial 1
Mar  4 02:49:57 localhost named[2637]: zone 255.in-addr.arpa/IN: loaded serial 1
Mar  4 02:49:57 localhost named[2637]: zone 0.0.0.0.7.0.8.0.9.0.a.0.2.0.0.2.ip6.arpa/IN: loaded serial 1
Mar  4 02:49:57 localhost named[2637]: zone ipv6.laboratorio.edu/IN: loaded serial 2
Mar  4 02:49:57 localhost named[2637]: running

```

I really don't know what is the error, this is driving me crazy now

---

### Post by yogesh.girikumar on 2010-03-05
Hi,

It looks like your localhost is not set up to point to 127.0.0.1

Can you try the same commands with '127.0.0.1' instead of 'localhost'?
$```
 nslookup -type=PTR 2002:a09:807::204:acff:fe66:7d47 127.0.0.1
$ nslookup -type=AAAA ipv6.mypc.com 127.0.0.1
$ nslookup -type=A ipv6.mypc.com 127.0.0.1
```
Also check your /etc/hosts file. It should have the following line in it somewhere. This maps the name 'localhost' with the loop back IP address ( i.e. 127.0.0.1 ). The error you are seeing could be because the mapping has not been done in the /etc/hosts file.
```
127.0.0.1        localhost
```
Check if your /etc/nsswitch.conf is set to look into files first. There should be a line that starts with hosts. The hosts defines the order of lookup of hostnames:
```
hosts:        files dns
```
Check if your /etc/resolv.conf has the proper nameservers set in them. Add the localhost as a nameserver too. This will also query the local DNS server for address lookups.
```
nameserver localhost
nameserver x.x.x.x
nameserver y.y.y.y

```
Where x.x.x.x and y.y.y.y could be the ip addresses of name servers. Usually these are the address of the dns servers of your ISP.

HTH

---

### Post by rukiaEnix on 2010-03-08
hello again, I still can't resolve the domain :-( but now I think it has something to do with localhost, here are the answers of what you told me to do:

The answer of:
```

$ nslookup -type=PTR 2002:a09:807::204:acff:fe66:7d47 127.0.0.1

```
is:
```

Server:        127.0.0.1
Address:    127.0.0.1#53

7.4.d.7.6.6.e.f.f.f.c.a.4.0.2.0.0.0.0.0.7.0.8.0.9.0.a.0.2.0.0.2.ip6.arpa    name = ipv6.laboratorio.edu.

```

The answer of:
```

$ nslookup -type=AAAA ipv6.mypc.com 127.0.0.1

```
is:
```

Server:        127.0.0.1
Address:    127.0.0.1#53

ipv6.laboratorio.edu    has AAAA address 2002:a09:807:0:204:acff:fe66:7d47

```

And the last one:
```

$ nslookup -type=A ipv6.mypc.com 127.0.0.1

```
gives me an error:
```

nslookup: couldn't get address for '127.0.0.1': not found

```

my hosts and nsswitch.conf files have the lines you told me.
This is my resolv.conf file:
```

search ipv6.laboratorio.edu  //my domain
nameserver 2002:a09:807::204:acff:fe66:7d47

```

I add nameserver 127.0.0.1 but it still gives me the couldn't be found message.
I think that the mistake is that in my named.conf I delete the zone for localhost, I did this because I have done it before and my DNS works fine with this configuration but now I don't know why it doesn't work even using IPv4 when it has work great before.
Should I add again my localhost zone to named.conf?

---

### Post by rukiaEnix on 2010-04-28
My Bind9 and Apache2 finally works with my IPv6 configuration :P what I finally did was add this lines to my /etc/protocols file:


[LIST]
[*] ipv6       41 IPv6       # IPv6
[*] ipv6-route 43 IPv6-Route # Routing Header for IPv6
[*] ipv6-frag  44 IPv6-Frag  # Fragment Header for IPv6
[*] ipv6-crypt 50 IPv6-Crypt # Encryption Header for IPv6
[*] ipv6-auth  51 IPv6-Auth  # Authentication Header for IPv6
[*] ipv6-icmp  58 IPv6-ICMP  icmpv6 icmp6   # ICMP for IPv6
[*] ipv6-nonxt 59 IPv6-NoNxt # No Next Header for IPv6
[*] ipv6-opts  60 IPv6-Opts  # Destination Options for IPv6
[/LIST]
I already had some of them but this are all the lines it should have for a good IPv6 support.
I find this solution at: [http://www.bieringer.de/linux/IPv6/IPv6-HOWTO/IPv6-HOWTO-6.html](http://www.bieringer.de/linux/IPv6/IPv6-HOWTO/IPv6-HOWTO-6.html)

and this is my zones configuration file:

```

zone "ipv6.laboratorio.edu" {
    type master;
    file "/etc/bind/db.laboratorio";
};

zone "0.0.0.0.7.0.8.0.9.0.a.0.2.0.0.2.ip6.arpa" {
    type master;
    file "/etc/bind/db.10";
};

```My domain zone file:

```

;
; BIND data file for local loopback interface
;
$TTL    604800
$ORIGIN ipv6.laboratorio.edu.
@    IN    SOA           ipv6.laboratorio.edu. root.ipv6.laboratorio.edu. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;

@       IN         NS      ipv6.laboratorio.edu.
@       IN      AAAA    2002:0a09:0807:0000:0204:acff:fe66:7d47
debian  IN      CNAME   ipv6.laboratorio.edu.

```

My reverse zone file:

```

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ipv6.laboratorio.edu. root.ipv6.laboratorio.edu. (
                  1        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@                                IN  NS    ipv6.laboratorio.edu.
7.4.d.7.6.6.e.f.f.f.c.a.4.0.2.0    IN  PTR    ipv6.laboratorio.edu.

```And finally my Apache2 configuration:

for /etc/apache2/ports.conf for listening only IPv6:

```

Listen [::]:80

```basic configuration for /etc/apache2/sites-available/default:

```

NameVirtualHost ipv6.laboratorio.edu
<VirtualHost *>
        ServerAdmin webmaster@localhost
    #ServerName ipv6.laboratorio.edu
        #ServerAlias ipv6.laboratorio.edu
    DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
        # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
    </Directory>
    .............more

```and obviously my resolv.conf:

```

search ipv6.laboratorio.edu
nameserver 2002:a09:807::204:acff:fe66:7d47

```well with this configuration for Bind9 and Apache2 IPv6 works great :P

---

