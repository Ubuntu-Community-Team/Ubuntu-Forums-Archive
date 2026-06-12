---
title: "mail server is sending mail in spam"
date: 2014-05-09
forum: Server Platforms
---

### Post by spider.netpln on 2014-05-09
I set the mail server in ubuntu 12.04 everything working fine it's sending mail to gmail also but it's goes in spam. why it's happen and my squirrelmail is not receiving mail it's sending but not receiving.

---

### Post by spider.netpln on 2014-05-09
need any configuration code of main.cf or dovecot then i past here. please help

---

### Post by lisati on 2014-05-09
> **spider.netpln said:**
> I set the mail server in ubuntu 12.04 everything working fine it's sending mail to gmail also but it's goes in spam. why it's happen and my squirrelmail is not receiving mail it's sending but not receiving.

A couple of things to check:
[LIST]
[*]Do you have a static public IP address or a dynamic public IP address? Having a dynamic IP address can make for more work on your part setting things up so that other mail servers can find your server and deliver mail to it.
[*]Do you have Reverse DNS set for your IP address? Some spam filters get a little bit fussy about how they perceive your email server.
[/LIST]
You can check if your server is receiving mail by inspecting your mail server's log.

---

### Post by spider.netpln on 2014-05-09
> **lisati said:**
> A couple of things to check:
[LIST]
[*]Do you have a static public IP address or a dynamic public IP address? Having a dynamic IP address can make for more work on your part setting things up so that other mail servers can find your server and deliver mail to it.
[*]Do you have Reverse DNS set for your IP address? Some spam filters get a little bit fussy about how they perceive your email server.
[/LIST]
You can check if your server is receiving mail by inspecting your mail server's log.

[LIST=1]
[*]I have static Live IP addresss
[*]PTR record is also set.
[*]don't know about spam filters? how to set it?
[/LIST]

---

### Post by spider.netpln on 2014-05-09
spamassassin is alredy installed on the server

---

### Post by lisati on 2014-05-09
How's your [Reverse DNS]("http://en.wikipedia.org/wiki/Reverse_DNS_lookup")? If gmail thinks there is a problem with it, then gmail's spam filters might put mail into the recipient's spam folder. More information can be found here: [http://en.wikipedia.org/wiki/Reverse_DNS_lookup](http://en.wikipedia.org/wiki/Reverse_DNS_lookup)

---

### Post by spider.netpln on 2014-05-09
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.xyz.com. root.xyz.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.xyz.com.
1       IN      PTR     ns1.xyz.com.
1       IN      PTR     mail.xyz.com.

After your LINK I FOLLOW AND CHANGES LIKE THIS

> 

; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.xyz.com. root.xyz.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.teslafilm.net.
X.X.X.X.in-addr.arpa       IN      PTR     ns1.XYZ.COM.
X.X.X.X.in-addr.arpa       IN      PTR     mail.xyz.com.






---

