---
title: "Bind DNS help needed"
date: 2010-10-18
forum: Server Platforms
---

### Post by clegends on 2010-10-18
Hi folks, am having some real difficulties with my bind configuration for my DNS server. Situation is I have a main server located under my desk, which I'm trying to configure as my primary dns server. This is also setup as a cacheing nameserver, currently using Google's public DNS. My box is hosting my mail server (working perfectly, sans dkim keys, which I need dns working for first), as well as my website via apache (also working fine).

I'm using xname.org for my dns slaves, currently the only dns nameservers resolving for my domain. I'm quite new at this, and still don't understand how xname.org is resolving correctly if my primary nameserver is not... anyway.

Here is the error I keep getting from [www.checkdns.net](www.checkdns.net)
```

Error fetching SOA from ns.curiouslegends.com.au [124.254.118.5], request timed out. Probably DNS server is offline.

```

Can someone help me troubleshoot this? I really want bind working on my server. Thanks in advance.

---

### Post by robert_pectol on 2010-10-18
The nameserver at ns.curiouslegends.com.au is not reachable.  I tested it from here and got no response when I tried to resolve your domain with your nameserver.  Luckily your slaves are able to resolve it, which means they must be successfully, or have been successful recently, contacting ns.curiouslegends.com.au.  It would seem that you either have an ACL which denies external nonrecursive queries, or a firewall which is blocking external requests to your server.  What do your logfiles say about it (ex: grep named /var/log/syslog)?  If you have a firewall, have you allowed inbound UDP to port 53 of your nameserver?

---

### Post by clegends on 2010-10-19
Score! Thanks so much Rob, the firewall was the main issue... I think...lol. Still getting the hang of this. I thought I'd already opened up that port, but apparently not... Anyway, all 4 servers are now alive and active, though the xname servers are using an older serial number... my guess is that its probably from the last time they were able to contact my nameserver... likely before I reconfigured my iptables firewall. Anyway. 

Can I get you to take a look at the two files below? The first is the zone file for curiouslegends.com.au and the second is my reverse dns file for the same. Just want to double check I'm on the right track. In particular, do I need the TXT entries for xname.org? Thanks again for your help... onwards to configuring opendkims now...

/etc/bind/db.curiouslegends.com.au:
```

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.curiouslegends.com.au. curiouser.curiouslegends.com.au. (
                      2010101906        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.curiouslegends.com.au.
@       IN      A       124.254.118.5
@       IN      AAAA    ::1
ns      IN      A       124.254.118.5
www     IN      A       124.254.118.5 
@       IN      MX 1    mail.curiouslegends.com.au.
mail    IN      A       124.254.118.5
curiouslegends.com.au.  IN      NS      ns0.xname.org.
curiouslegends.com.au.  IN      NS      ns1.xname.org.
curiouslegends.com.au.  IN      NS      ns2.xname.org.
curiouslegends.com.au.  IN      TXT     ns0.xname.org.
curiouslegends.com.au.  IN      TXT     ns1.xname.org.
curiouslegends.com.au.  IN      TXT     ns2.xname.org.
curiouslegends.com.au.  IN      TXT     "v=spf1 a mx ~all"

```
/etc/bind/db.124
```


;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA ns.curiouslegends.com.au. curiouser@curiouslegends.com.au. (
                       2010101906       ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.curiouslegends.com.au.
ns      IN      A       124.254.118.5
1.0.0   IN      PTR     curiouslegends.com.au.
1.0.0   IN      PTR     www.curiouslegends.com.au.
1.0.0   IN      PTR     mail.curiouslegends.com.au.

```

---

### Post by SeijiSensei on 2010-10-19
The TXT entries that replicate the NS entries are superfluous.  However the last one specifies the location(s) from which legitimate outbound message may be sent using the [Sender Policy Framework]("http://www.openspf.org/") approach.  Read [this page](http://www.openspf.org/SPF_Record_Syntax) to make sure the rule you've specified is the policy you want to implement.

---

### Post by clegends on 2010-10-19
Thanks for that. Will have a read and see what I come up with. One more thing, I'm trying to get opendkims to work, and keep getting this error message:
```

curiouser@curioushost:/etc/mail$ named-checkzone curiouslegends.com.au /etc/bind/db.curiouslegends.com.au
dns_rdata_fromtext: /etc/bind/db.curiouslegends.com.au:26: unbalanced quotes
dns_master_load: /etc/bind/db.curiouslegends.com.au:27: label too long
dns_master_load: /etc/bind/db.curiouslegends.com.au:28: label too long
dns_master_load: /etc/bind/db.curiouslegends.com.au:29: syntax error
zone curiouslegends.com.au/IN: loading from master file /etc/bind/db.curiouslegends.com.au failed: unbalanced quotes
zone curiouslegends.com.au/IN: not loaded due to errors.

```
It only happens when I add this entry to my zone file:
```

2010._domainkey.curiouslegends.com.au. IN   TXT "k=rsa; t=y; p=(real key)"

```

Otherwise it's fine. So the error is with this entry. Any thoughts on this? Thanks.

---

