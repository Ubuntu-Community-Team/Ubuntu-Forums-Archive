---
title: "Issue setting up reverse DNS with BIND9"
date: 2011-09-26
forum: Server Platforms
---

### Post by Kolusion on 2011-09-26
I setup a DNS server last month but didn't setup a reverse DNS server.  Now I need to do it and having trouble getting things up and running,  and hoping my Linux bros can help me out:

[B]named.conf.local:
[/B]> I'll keep it real simple for you guys, so here it is:
zone "78.456.123.in-addr.arpa" {
     type master;
     notify no;
     file "/etc/bind/db.78";
};

**db.78:**
> ;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns1.domain1.com. nik.domain1.com. (
                  1        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns1.
1.0.0    IN    PTR    ns1.domain1.com.

Where have I stuffed up?

---

### Post by Kelketek on 2011-09-27
Reverse DNS is handled by your ISP. Are you an ISP trying to set up PTR records?

The PTR records have to be done by the ISP because when people do a reverse lookup on an IP address, the the lookup queries the servers responsible for the IP address. That's not your servers. Your servers just use the IP addresses. They didn't assign them to you.

If you're not trying to start up your own ISP, you should call your ISP and tell them you need rDNS on your IP addresses and what you want the name for them to be.

---

### Post by Kolusion on 2011-09-27
> **Kelketek said:**
> Reverse DNS is handled by your ISP. Are you an ISP trying to set up PTR records?

Are you sure reverse DNS is handled by my ISP? I don't see how that makes sense, because when someone does a reverse DNS lookup, doesn't it connect to the IP address on port 53, where a DNS server is listening to serve information regarding which domains are associated with the IP?

Perhaps a PTR is not what I need. I don't know what PTR means. I am following ins
truction on setting up reverse DNS here:
**[https://help.ubuntu.com/community/BIND9ServerHowto#Reverse_Zone_File](https://help.ubuntu.com/community/BIND9ServerHowto#Reverse_Zone_File)**

---

### Post by cconstantine on 2011-09-27
Others have asked about the bigger logic of your needing to serve rev dns. And how you set that up etc. So setting that aside...

But there's a glaring error in your zone. If you config the zone as 78.456.123.in-addr.arpa and then have the record as 1.0.0, you're telling bind to serve a record as data for 1.0.0.78.456.123.in-addr.arpa -- if you have three octets represented in the name of the zone, you just want "1" in the record, so you have 1.78.456.123.in-addr.arpa .

---

### Post by Kelketek on 2011-09-27
Yes, I'm certain. If the reverse DNS lookup contacted the IP, you'd need BIND running on every IP address you wanted a PTR record for (or at least some running wrapper that queried it). Since the PTR record is typically used for a mail server's identification, it wouldn't make sense to have BIND running on the mail server.

The guide you're reading is trying to be complete. Setting PTR records in your zone file won't hurt anything, but if your name servers aren't authoritative for your /IP/ addresses, this won't work. Try this:

```
nslookup 34.23.98.23
```
Where 34.23.98.23 is your actual IP address. This will tell you the name servers assigned to your IP address. If those servers aren't yours, you need to call the people who manage them.

---

### Post by SeijiSensei on 2011-09-27
> **Kolusion said:**
> Are you sure reverse DNS is handled by my ISP? I don't see how that makes sense, because when someone does a reverse DNS lookup, doesn't it connect to the IP address on port 53, where a DNS server is listening to serve information regarding which domains are associated with the IP?

No, the resolver sends the query to an in-addr.arpa domain server (the server a.in-addr-servers.arpa, for example) to determine the specific nameserver that handles requests for xxx.yyy.zzz.in-addr.arpa.  ISPs maintain the reverse nameservers for the address blocks they've been assigned.  End-users rarely have control over their reverse lookups unless their providers offer [RFC2317 delegation]("http://www.ietf.org/rfc/rfc2317.txt").

You need to ask the ISP to set up reverse DNS for your address.

---

### Post by offCourse2007 on 2012-01-25
HI

I am trying to setup a bulk mail server using ubuntu and would like to properly setup the reverse dns's.

My situation is this: 

Website located in bluehost.com under the domain "example.com.pt"
Newsletter installed in our own server under the domain "newsletter.example.com.pt"

What should I ask the ISP to setup for my fixed IP?

Reverse DNS associated with "newsletter.example.com.pt" or "example.com.pt" is enough?

And do I need to setup bind for this

Thanks for your help.

Cheers

---

### Post by SeijiSensei on 2012-01-25
The canonical (no pun intended!) solution is to have a single name for the machine that is used for both inbound and outbound mail.  For instance:

```

@      IN SOA  example.com. support.example.com. { stuff }
       IN MX   0 mail.example.com.
               5 mail2.example.com.

       IN TXT  "v=spf1 a:mail.example.com a:mail2.example.com ~all"

mail   IN A    10.1.2.1
mail2  IN A    10.1.2.2

```

I'd give the primary server the hostname "mail.example.com" with IP 10.1.2.1 and have the ISP point that address to "mail.example.com" in the reverse domain, 2.1.10.in-addr.arpa.

I've also included a sample "[SPF]("http://www.openspf.net/")" record which tells remote SMTP servers the names of the servers allowed to send mail for your domain.  This helps you pass through spam filtering since most anti-spam scanners will look up the SPF record and, if the server names match, give your messages a lower likely-spam score.  (SpamAssassin, among others, does this.)

If you want to receive mail for a subdomain address like "newsletters.example.com" on a *different machine* than the one accepting mail for "example.com", you need additional MX records like this:

```

newsletters   IN  MX  0 mail.somewhere-else.com.

```

If you send mail out as @newsletters.example.com you'll need another SPF record unless the sending server for that subdomain is the same as the one for example.com.

---

