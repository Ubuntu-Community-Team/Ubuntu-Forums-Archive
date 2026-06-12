---
title: "Help with BIND configuration file"
date: 2010-01-15
forum: Server Platforms
---

### Post by vamega on 2010-01-15
I'm trying to edit the following bind zone file for a domain called testing.lan. I'm running the bind server on localhost, and the only computer that will access the DNS server will be the machine I am running the DNS server on.

```

; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for testing.lan
; Note: The extra “.” at the end of addresses are important.

tesing.lan. IN SOA <what should I put here>.testing.lan. admin.testing.lan. (
    20100111 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; NS indicates that 127.0.0.1 is the name server on testing.lan
; MX indicates that 127.0.0.1 is (also) the mail server on testing.lan
testing.lan. IN NS 127.0.0.1
testing.lan. IN MX 10 127.0.0.1

; Set the address for localhost.testing.lan
localhost    IN A 127.0.0.1

```Does this code seem right? I tried to modify it from [here]("http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/") but I'm not sure if I screwed up something.

I'm sorry if this seems like a stupid question, but I've never had any experience working with DNS. I'm a programmer, with a fair amount of experience, I'm just unfamiliar with DNS in general, and BIND and its configuration files more specifically.

Thanks in advance for all the help.

---

### Post by vamega on 2010-01-15
Also as an aside, does anyone know why there is a 10 after the MX in the mail record?

---

### Post by noway2 on 2010-01-15
Off hand your configuration looks like it will work.  It is a little different format that I'm accustomed to, but that doesn't mean it is wrong. It may be a shortcut, but after the ) in the SOA record, I would list the NS (server name) and an A record for the address.  Below that, you would put the A records for other (static) devices.

In the <what should I put here> section you should put the name of the system that is hosting the DNS.  

The MX record is used if you are running an email server, such as sendmail or postfix.  The 10 is a priority number that comes into play if you have multiple MX records.  The MX (mail) server with the lowest number will get the highest priority.  If that server is down, traffic will be sent to the next highest priority (next lowest number) and so forth.

---

### Post by vamega on 2010-01-16
BIND now refuses to start. I've posted all the configuration files I've modified below, and I'd really appreciate any help identifying the problem.

named.conf.local
```

zone “testing.lan” IN {
    type master;
    file “/etc/bind/zones/testing.lan.db”;
};

zone “0.0.127.in-addr.arpa” {
    type master;
    file “/etc/bind/zones/rev.0.0.127.in-addr.arpa”;
};

```The only modification I did to named.conf.options was to change the forwarders to point to the DNS servers given to me by my ISP.

named.conf.options
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
         4.2.2.2;
        208.67.222.222;
     };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```The two files in the zones folder

rev.0.0.127.in-addr.arpa
```
; IP Address-to-Host DNS Pointers for 192.168.1.0 subnet
@ IN SOA localhost.mydomain.lan. hostmaster.mydomain.lan. (
    200709131 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; define the authoritative name server
IN NS localhost.mydomain.lan.
; our hosts, in numeric order
1        IN PTR localhost.mydomain.lan.
```testing.lan.db
```
; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for testing.lan
; Note: The extra “.” at the end of addresses are important.
; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDI where
; the I index is in case you make more that one change in the same day.
tesing.lan. IN SOA localhost.testing.lan. hostmaster.testing.lan. (
    201001151 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; NS indicates that john is the name server on testing.lan
; MX indicates that john is (also) the mail server on testing.lan
testing.lan. IN NS 127.0.0.1
testing.lan. IN MX 10 127.0.0.1
; Set the address for localhost.testing.lan
localhost    IN A 127.0.0.1
```

As I said before I simply tried to modify the instructions found [here]("http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/") to my setup

Thanks
Vamega

---

### Post by koenn on 2010-01-17
look in /var/log, bind will have reported why it failed to start in one of the logs

---

### Post by vamega on 2010-01-17
After a long time spent prodding those files, I finally found out that the issue was that the file had true quotation marks instead of double quotation marks (I don't know if that makes sense, but I'm trying to say it had different characters for the opening and closing quotation mark).

I fixed that and bind started fine. However I'm still unable to access my machine at the address localhost.testing.lan.

Does anyone have any idea why?

---

