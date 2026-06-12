---
title: "Trouble configuring DNS on my server."
date: 2009-02-01
forum: Server Platforms
---

### Post by Maheriano on 2009-02-01
I want to forward my domain name to my web server which (in all other aspects) is working fine. I'm following a guide [here]("http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml") on how to do this but it doesn't seem to be working.

The IP of my server on my network is 10.0.0.6 and for testing purposes, I'll post my router's IP here as 1.2.3.4. I just don't want anyone slamming my machine. But I can confirm my web pages are accessible outside my network by using my IP so it is correct.

First I edit /etc/bind/named.conf.local to this:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "deemarwebdesign.com" {
type master;
file "/etc/bind/zones/deemarwebdesign.com..db";
};

zone "0.10.10.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.0.10.10.in-addr.arpa";
};

```

Then I edit /etc/bind/named.conf.options:
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
                1.2.3.4;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

Then:
```
mkdir /etc/bind/zones
```

Then created  /etc/bind/zones/deemarwebdesign.com.db:
```
deemarwebdesign.com. IN SOA ns1.deemarwebdesign.com. ns2.deemarwebdesign.com. (

2006081401
28800
3600
604800
38400 )

deemarwebdesign.com. IN NS ns1.deemarwebdesign.com.
IN A 1.2.3.4
mail.deemarwebdesign.com. IN MX 10 mail.deemarwebdesign.com.
deemarwebdesign.com. IN MX 10 mail.deemarwebdesign.com.

www IN A 1.2.3.4
mail IN A 1.2.3.4
ns1 IN A 1.2.3.4


```

Then created  /etc/bind/zones/rev.rev.0.10.10.in-addr.arpa:
```
@ IN SOA deemarwebdesign.com. ns2.deemarwebdesign.com. (
2006081401;
28800;
604800;
604800;
86400 );

IN NS ns1.deemarwebdesign.com.
4 IN PTR deemarwebdesign.com.

```
In this one I put 4 there which is actually the final 3 digits in my IP. That's what I understood goes there from the tutorial, he uses 77. I'm not sure if that's because it's the last digits of his sample IP or if it should actually be 77.

Then restarted bind:
```
/etc/init.d/bind9 restart
```

But when I try Host and Dig, I don't get my expected results:
```
deemar@Jurassic:/etc/bind$ host deemarwebdesign.com 127.0.0.1
Using domain server:
Name: 127.0.0.1
Address: 127.0.0.1#53
Aliases: 

Host deemarwebdesign.com not found: 2(SERVFAIL)
deemar@Jurassic:/etc/bind$ dig deemarwebdesign.com

; <<>> DiG 9.5.0-P2 <<>> deemarwebdesign.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 41100
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;deemarwebdesign.com.		IN	A

;; Query time: 226 msec
;; SERVER: 10.0.0.1#53(10.0.0.1)
;; WHEN: Sun Feb  1 13:10:22 2009
;; MSG SIZE  rcvd: 37

```

---

### Post by inphektion on 2009-02-01
take a look at /var/log/daemon.log for errors from bind.

Hopefully this is just a typo in your post here
> file "/etc/bind/zones/deemarwebdesign.com..db";
otherwise that is a problem too.

---

### Post by Maheriano on 2009-02-01
Thanks, now I get this which is a little better. Is this right or wrong?

> deemar@Jurassic:/etc/bind$ host deemarwebdesign.com 127.0.0.1Using domain server:
Name: 127.0.0.1
Address: 127.0.0.1#53
Aliases: 

Host deemarwebdesign.com not found: 2(SERVFAIL)
deemar@Jurassic:/etc/bind$ sudo nano /etc/bind/named.conf.local
[sudo] password for deemar: 
deemar@Jurassic:/etc/bind$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                 [ OK ] 
 * Starting domain name service... bind9                                 [ OK ] 
deemar@Jurassic:/etc/bind$ host deemarwebdesign.com 127.0.0.1
Using domain server:
Name: 127.0.0.1
Address: 127.0.0.1#53
Aliases: 

deemarwebdesign.com mail is handled by 10 mail.deemarwebdesign.com.
deemar@Jurassic:/etc/bind$ dig deemarwebdesign.com

; <<>> DiG 9.5.0-P2 <<>> deemarwebdesign.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 48767
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;deemarwebdesign.com.		IN	A

;; Query time: 209 msec
;; SERVER: 10.0.0.1#53(10.0.0.1)
;; WHEN: Sun Feb  1 17:30:33 2009
;; MSG SIZE  rcvd: 37


---

### Post by Maheriano on 2009-02-02
???

---

### Post by Maheriano on 2009-02-02
I just followed [this]("http://ubuntuforums.org/showthread.php?t=236093") tutorial and noticed I had misunderstood a lot of things from the other tutorial which was very confusing. I believe I have everything set up correctly now and have created the new nameservers with my registrar and pointed my domain to them. How do I know for sure it's working? Wait 2 days and see if it resolves in Firefox? Can I check now?

---

### Post by Maheriano on 2009-02-04
Is anybody out there?

---

### Post by Maheriano on 2009-02-06
I don't know what else I need to do to get help around here, anybody who sets up a webserver on a domain has had to create this before. Is there honesty nobody here to help me? What more do I have to do?

---

### Post by mistypotato on 2009-02-21
Going through the same learning curve pains here.

I don't have the answer you're seeking but I have found Google to be a good ally in this fight. ;)

---

