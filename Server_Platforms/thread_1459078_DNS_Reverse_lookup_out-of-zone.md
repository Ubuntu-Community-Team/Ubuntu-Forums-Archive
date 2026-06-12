---
title: "DNS Reverse lookup: out-of-zone"
date: 2010-04-20
forum: Server Platforms
---

### Post by Speakstofei on 2010-04-20
Hey there,
I have followed the [Ubuntu Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/dns-configuration.html") (Chapter 7) pretty thoroughly while setting up my local domain.  I have the forward lookup setup properly.  The dig/named-checkzone utilities are giving me the results I want.

Two things seem to be giving me an error at this point is the "named-checkconf -z" command, and "ping casuallee.local" I am getting an out-of-zone error from named-checkconf -z and I'd like to assume that ping doesn't work as intended because the reverse lookup isn't working properly; thereby, I think, ping seems to target IP address rather than host names.

Since I'm setup as private: Here is the error I'm getting:
```
root@hoosier:/etc/bind# named-checkconf -z
zone casuallee.local/IN: loaded serial 7
/etc/bind/db.192:5: ignoring out-of-zone data (casuallee.local)
zone 1.168.192.in-addr.arpa/IN: has 0 SOA records
_default/1.168.192.in-addr.arpa/IN: bad zone
zone localhost/IN: loaded serial 2
zone 127.in-addr.arpa/IN: loaded serial 1
zone 0.in-addr.arpa/IN: loaded serial 1
zone 255.in-addr.arpa/IN: loaded serial 1

```Here is the db.192 file:
```
;
; BIND reverse data file for casuallee.local
;
$TTL    604800
casuallee.local.    IN    SOA    hoosier.casuallee.local. root (
                  8        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
@    IN    NS    hoosier.
3    IN    PTR    hoosier.casuallee.local.

```And here is the referencing file (named.conf.local):
```
//
// Do any local configuration here
//
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
//These acknowledge this computer as the master for the domain.

zone "casuallee.local" {
     type master;
    file "/etc/bind/db.casuallee.local";
};

zone "1.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.192";
};

```My successful commands are here:
```
root@hoosier:/etc/bind# dig casuallee.local

; <<>> DiG 9.6.1-P2 <<>> casuallee.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3758
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;casuallee.local.        IN    A

;; AUTHORITY SECTION:
casuallee.local.    604800    IN    SOA    hoosier.casuallee.local. root.casuallee.local. 7 604800 86400 2419200 604800

;; Query time: 0 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Apr 20 21:51:59 2010
;; MSG SIZE  rcvd: 82

root@hoosier:/etc/bind# named-checkzone casuallee.local /etc/bind/db.192
zone casuallee.local/IN: loaded serial 8
OK
```How is it the 2 utilities are completely contradicting each other? 
Merely for the sake of posterity to show my hosts are setup properly.:
```
;
; BIND data file for local loopback interface
;
; This file is referred to by... named.conf.local
;
$TTL    604800
casuallee.local.    IN    SOA    hoosier.casuallee.local. root (
                  7        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
@    IN    NS    hoosier.casuallee.local.
hoosier    IN    A    192.168.1.3
```I'm probably missing something trivial, however, any help in regards to this matter would be appreciated.  Thanks in advance.

---

### Post by Speakstofei on 2010-04-20
heh, I found good news & bad.  I found my error in db.192. I had to change the beginning of my SOA line from casuallee.local. to @ so it answers to the network address, not the domain itself.  I found that fix [here]("http://tldp.org/HOWTO/DNS-HOWTO-5.html#ss5.2") 

My only problem is now, I still can't ping hoosier.casuallee.local or even casuallee.local. :( So my "reverse lookup failing prevents pinging" theory is wrong.

---

### Post by terazen on 2010-04-21
In the line in db.192:
@    IN    NS    hoosier.

I think it should say:
@    IN    NS    hoosier.casuallee.local.

Try to change those and then do a `sudo rndc reload` and check /var/log/syslog for errors.  The "." at the end of hoosier means that is the complete name, but it's not complete.  Also, the dig command wasn't successful.

---

### Post by Speakstofei on 2010-04-22
I got it.  I had to change the TLD from .local to .home.  I don't understand why I wasn't allowed to, but it must be some restriction within BIND.  Maybe its too close to localhost or something.  But I found a similar error [here]("http://www.linuxquestions.org/questions/linux-networking-3/bind9-host-does-reslove-a-dns-name-but-ping-says-unknown-host-619628/").  When I found an [RFC]("http://tools.ietf.org/html/rfc2606") and then [this article under Pseudo-Domains]("http://www.answers.com/topic/top-level-domain") I made the modification & my configuration worked fine. 

And yes, I changed that line to its full address of hoosier.casuallee.home.  Realizing now I could have just left it as "hoosier" w/o the "." and it would resolve the same way.

Edit:
> **terazen said:**
> Also, the dig command wasn't successful.
wait what?  I just ran dig again and got the same results: 1 query, 1 authoritative, NOERROR.  I realize I'm missing the "Answer" & "Additional" sections.  But now you have me second guessing this working config.

---

### Post by terazen on 2010-04-22
Do you get an answer section when you run `dig hoosier.casuallee.home`?  I think the reason it failed earlier was you didn't have an A record for casuallee.local.```
@                               IN      A       192.168.1.3
```

If you don't need an A record then you don't need to add it.  If you can resolve hoosier then you're set. :-)

---

