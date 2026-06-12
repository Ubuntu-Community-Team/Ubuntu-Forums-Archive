---
title: "My ISP added custom rDNS (PTR) record for my IP address - now what to do?"
date: 2017-06-27
forum: Server Platforms
---

### Post by Grigoriy on 2017-06-27
Hello!
                          
                          I run my own HTTP, SMTP and DNS server on a  local box. I have LAMP, Postfix and BIND9 on Ubuntu to be exact.  Everything was great, except that the e-mail which was sent from my mail  server often got rejected by the remote SMTP servers due to lack of  correct rDNS (PTR) record (basically, I never bothered to ask my ISP to  update it for me, so it was a generic one). So finally I did it. My ISP  updated rDNS record for an IP address that I use for all the servers  (they all are together on one physical computer). So an IP resolves to  the hostname of my mail server, which is:
                          
                          [mail.mysite.com]("http://mail.mysite.com")
                          
                          When I do reverse DNS lookup with "nslookup"  command, by FIRST choosing Google's DNS server (8.8.8.8), then I get the  correct hostname. But when I use my own DNS server, I get servfail  error. Right now every server of mine seems to be working correctly. I  haven't seen anything unusual or some problem with anything. So should I  just wait for the DNS propagation (my ISP updated an IP about 6 hrs.  ago) OR is there anything I personally should update either in my DNS  server's settings or something else maybe?

---

### Post by darkod on 2017-06-27
Your internal dns server can't own the reverse zone because you don't own it. You can try configuring a reverse zone but I'm not sureit will work because you don't own the public ip range.
Important is that the public dns is working, don't bother about your private one.

---

### Post by Grigoriy on 2017-06-27
So should I just wait? Logically, my own DNS server at some point has to show the correct setting?

---

### Post by darkod on 2017-06-27
I'm not 100% sure but I think rDNS does not work like standard (forward) DNS. If I'm right, you can wait as long as you want, it will not resolve the PTR record.

Standard DNS server looks at itself for the reply of the query. If it does not manage the zone, and if it is set up to use forwarder, it asks the forwarder for the reply. That is how your private DNS server can resolve other public records.

But for rDNS I don't think it forwards and it will not ask any other server. So because it does not manage the zone itself, it will never have the reply. Try searching that on internet, whether rDNS queries are forwarded in the same way or not...

---

### Post by Grigoriy on 2017-06-27
So because it does not manage the zone itself...

What do you mean by that? My DNS server does manage the zone (my domain). It is an authoritative DNS server for my domain.

OK, maybe I'll just leave it alone for now... As long as everything seems to be working OK.

---

### Post by darkod on 2017-06-27
Reverse zone is not the same as forward zone.

[https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)

---

### Post by Grigoriy on 2017-06-27
Okay, so I solved this like so:
              
              Let's say that my IP address would be 46.249.xx.yy
              In file named.conf.local I wrote this, regarding reverse DNS zone:

```
zone "xx.249.46.in-addr.arpa" {
type master;
file "/etc/bind/zones/db.46.249.xx";
};
```

In file db.46.249.xx, which is in "zones" directory I did this:

```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns1.xxxxxxxx.com. director.xxxxxxxx.com. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;

@      IN      NS     ns1.
yy     IN     PTR     ns1.xxxxxxxxxx.com.
yy     IN     PTR     mail.xxxxxxxxx.com.
```

Now when I restart BIND, I don't get any errors anymore in debug.log file and when I run this:
              
              nslookup 46.249.xx.yy 
              
              then I get 2 answers back:

ns1.xxxxxxxxx.com
              
              and
              
              mail.xxxxxxxx.com

And when I run the check:
              
              named-checkzone xxxxxxxxx.com /etc/bind/zones/db.46.249.xx
              
              I get OK.
              
              P.S. In short, my reverse DNS zone file was all messed up  and it really had nothing to do with my ISP updating my PTR record for  my static IP that they own.

---

### Post by darkod on 2017-06-28
Great that it worked. I wasn't sure it will but now I understand why... You can make the reverse zone for public IP subnet on your DNS server but it will be only "local". No public servers will consult it because on the internet the ISP owns the zone (the public IPs).

But for your internal clients, they will still consult this zone and your DNS server will reply to them, so from their point of view it is working.

Now you have it working both ways, the ISP has set the public PTR that all other machines on the internet will consult, and you have your internal zone for the internal clients on the LAN.

If you have it working as you wish please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

