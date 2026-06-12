---
title: "Need some help with Bind"
date: 2010-11-25
forum: Server Platforms
---

### Post by themonkeh on 2010-11-25
I setup my dns server following [this guide]("http://ubuntuforums.org/showthread.php?t=236093"), however I dont get all the info I should when I dig my domain and it seems to work sometimes when I visit the url and not others, even though visiting the IP works fine. 

Any and all help is greatly appreciated!

```

; <<>> DiG 9.7.0-P1 <<>> learninghowtogarden.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 35745
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;learninghowtogarden.com.    IN    A

;; Query time: 0 msec
;; SERVER: 174.138.164.173#53(174.138.164.173)
;; WHEN: Thu Nov 25 13:54:31 2010
;; MSG SIZE  rcvd: 41

```These are my settings, I read somewhere that the problem was I needed to add an a record but no further explantion on how to do that was given.

/etc/bind/named.conf.local
```

zone "learninghowtogarden.com" {
        type master;
        file "/etc/bind/zones/learninghowtogarden.com.db";
};
zone "138.164.173.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/zones/rev.138.164.173.in-addr.arpa";
};
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```/etc/bind/named.conf.options
(I didn't edit this file because I have no idea what to put for forwarders, dont think its needed though please tell me if its important)
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

        // forwarders {
        //      0.0.0.0;
        // };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```/etc/bind/zones/learninghowtogarden.com.db
```

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
learninghowtogarden.com.      IN      SOA     ns1.learninghowtogarden.com. admin.learninghowtogarden.com. (
// Do not modify the following lines!
                                                        2010112501
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
learninghowtogarden.com.      IN      NS              ns1.learninghowtogarden.com.
learninghowtogarden.com.      IN      MX     10       mta.learninghowtogarden.com.

// Replace the IP address with the right IP addresses.
www              IN      A       174.138.164.173
mta              IN      A       174.138.164.173
ns1              IN      A       174.138.164.173


```/etc/bind/zones/rev.138.164.173.in-addr.arpa
```

//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA ns1.example.com. admin.example.com. (
                        2010112501;
                        28800; 
                        604800;
                        604800;
                        86400
)

                     IN    NS     ns1.learninghowtogarden.com.
174                    IN    PTR    learninghowtogarden.com

```/etc/resolv.conf
```

search learninghowtogarden.com
nameserver 174.138.164.173

```Thanks in advance to anyone who can help!

---

### Post by James78 on 2010-11-25
See if these work for you.

/etc/bind/zones/learninghowtogarden.com.db
```
// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
learninghowtogarden.com.      IN      SOA     ns1.learninghowtogarden.com. admin.learninghowtogarden.com. (
// Do not modify the following lines!
                                                        2010112501
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
learninghowtogarden.com.      IN      NS              ns1.learninghowtogarden.com.
learninghowtogarden.com.      IN      MX     10       mta.learninghowtogarden.com.

// Replace the IP address with the right IP addresses.
learninghowtogarden.com.                  IN      A       174.138.164.173
www.learninghowtogarden.com.              IN      A       174.138.164.173
mta.learninghowtogarden.com.              IN      A       174.138.164.173
ns1.learninghowtogarden.com.              IN      A       174.138.164.173
```

/etc/resolv.conf
```
search learninghowtogarden.com
nameserver 127.0.0.1
```

You should also make some empty zones for your router address, 192.168.0.1, otherwise DNS queries are likely getting leaked. You can do so via:

/etc/bind/named.conf.local
```
zone "learninghowtogarden.com" {
        type master;
        file "/etc/bind/zones/learninghowtogarden.com.db";
};
zone "138.164.173.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/zones/rev.138.164.173.in-addr.arpa";
};
// Consider adding the 1918 zones here, if they are not used in your
// organization
include "/etc/bind/zones.rfc1918";
```

[http://ubuntuforums.org/showthread.php?t=1598245](http://ubuntuforums.org/showthread.php?t=1598245)

---

### Post by themonkeh on 2010-11-25
You're a lifesaver, thanks so much!

```

; <<>> DiG 9.7.0-P1 <<>> learninghowtogarden.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11388
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;learninghowtogarden.com.    IN    A

;; ANSWER SECTION:
learninghowtogarden.com. 900    IN    A    174.138.164.173

;; AUTHORITY SECTION:
learninghowtogarden.com. 900    IN    NS    ns1.learninghowtogarden.

;; Query time: 11 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Thu Nov 25 03:29:19 2010
;; MSG SIZE  rcvd: 94

```

---

