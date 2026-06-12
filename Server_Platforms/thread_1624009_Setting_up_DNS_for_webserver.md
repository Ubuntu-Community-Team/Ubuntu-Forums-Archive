---
title: "Setting up DNS for webserver"
date: 2010-11-17
forum: Server Platforms
---

### Post by syvil on 2010-11-17
Hey guys, I'm new here but would like to see if I can get some help. I'll explain what I'm trying to do.

I want to learn how to create an entire server from scratch using a   minimal install. I know Ubuntu Server 10.04.1 comes with packages that   can be included during install but for the sake of learning I only   installed SSH access.

I was able to get Apache2, MySQL, PHP5 installed and running fine. What   I'm trying to do next is setup DNS so I can point fragdata.com to my   Ubuntu server and have other people see my test site.

I have registered the nameserver ns1.fragdata.com with my IP and updated DNS in my registrar. I followed the tutorial but "dig fragdata.com" gives me the following:
```
root@linux-server:/home/syvil# dig fragdata.com

; <<>> DiG 9.7.0-P1 <<>> fragdata.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 34713
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;fragdata.com.                  IN      A

;; Query time: 0 msec
;; SERVER: 192.168.1.202#53(192.168.1.202)
;; WHEN: Wed Nov 17 10:07:16 2010
;; MSG SIZE  rcvd: 30
```I followed this guide [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)  but it doesn't seem to be working. I'll explain my setup a little more. I  used an old computer that was collecting dust.

Intel Celeron 1.8ghz
640mb RAM
40GB HDD
Ubuntu Server 10.04.1 LTS

Network Settings (Behind Router)
Static IP 192.168.1.202
Default Gateway 192.168.1.1
Subnet 255.255.255.0

Here's my server configs.

/etc/bind/named.conf.local:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "fragdata.com" {
        type master;
        file "/etc/bind/zones/fragdata.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with   your network address in reverse notation - e.g my network address is   192.168.0
zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};
```/etc/bind/named.conf.options (using OpenDNS):
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
    //     0.0.0.0;
    // };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };

    forwarders {
         # Replace the address below with the address of your provider's DNS server
        208.67.222.222;
        208.67.220.220;
    };
};
```/etc/bind/zones/fragdata.com.db:
```
// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
fragdata.com.      IN      SOA     ns1.fragdata.com. admin.fragdata.com. (
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
// example.com = domain name
fragdata.com.      IN      NS              ns1.fragdata.com.
fragdata.com.      IN      MX     10       mta.fragdata.com.

// Replace the IP address with the right IP addresses.
www              IN      A       192.168.1.202
mta              IN      A       192.168.1.202
ns1              IN      A       192.168.1.202
```/etc/bind/zones/rev.1.168.192.in-addr.arpa:
```
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the   DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA ns1.fragdata.com. admin.fragdata.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.fragdata.com.
202                    IN    PTR    fragdata.com
```/etc/resolv.conf:
```
// replace example.com with your domain name, and 192.168.0.1 with the address of your new DNS server.
search fragdata.com
nameserver 192.168.1.202
```

---

### Post by arrrghhh on 2010-11-17
All of your DNS work is only going to apply locally - so are these other people on your LAN?  Are they pointed to this box for DNS?

I'm assuming the people involved are across a WAN - in that case you need to use dyndns, or purchase a domain and a static IP from your provider :D

---

### Post by syvil on 2010-11-17
> **arrrghhh said:**
> All of your DNS work is only going to apply locally - so are these other people on your LAN?  Are they pointed to this box for DNS?

I'm assuming the people involved are across a WAN - in that case you need to use dyndns, or purchase a domain and a static IP from your provider :D

Thanks for your reply. Yes I want to people to be able to see my domain across the internet. I have a domain purchased and a static IP already by my provider.

I'm guessing something in my configs is setup wrong or I'm missing something? All ports needed have been forwarded to the Ubuntu box in DD-WRT.

The whole idea for me is to learn how to setup a web server from scratch with no third party help from services like DynDNS if possible.

---

### Post by arrrghhh on 2010-11-17
> **syvil said:**
> Thanks for your reply. Yes I want to people to be able to see my domain across the internet. I have a domain purchased and a static IP already by my provider.

I'm guessing something in my configs is setup wrong or I'm missing something? All ports needed have been forwarded to the Ubuntu box in DD-WRT.

The whole idea for me is to learn how to setup a web server from scratch with no third party help from services like DynDNS if possible.

Oh ok.  So you're setup then - you don't need to run a DNS server.  That would only be for local DNS lookup - inside your LAN.

Basically you just need to go to your provider who you paid for that domain - then point the domain to your static IP.  Simple :D

Most providers have a control panel for configuring such things.

---

### Post by SeijiSensei on 2010-11-17
> I have registered the nameserver ns1.fragdata.com with my IP and updated DNS in my registrar.

I don't see any public records for fragdata.com:

$ host -t any fragdata.com
Host fragdata.com not found: 3(NXDOMAIN)
$ host ns1.fragdata.com
Host ns1.fragdata.com not found: 3(NXDOMAIN)
$ host -t ns fragdata.com
Host fragdata.com not found: 3(NXDOMAIN)

Whois reports that ns1.fragdata.com is the nameserver for this domain.

---

### Post by syvil on 2010-11-17
> **SeijiSensei said:**
> I don't see any public records for fragdata.com:

$ host -t any fragdata.com
Host fragdata.com not found: 3(NXDOMAIN)
$ host ns1.fragdata.com
Host ns1.fragdata.com not found: 3(NXDOMAIN)
$ host -t ns fragdata.com
Host fragdata.com not found: 3(NXDOMAIN)

Whois reports that ns1.fragdata.com is the nameserver for this domain.

Weird namecheap gives me this error when trying to register it again.

**There is some problem adding the NameServers**
• ns1.fragdata.com- Error: This nameserver is already registered.

I opened UDP port 53 in my router for this box in question.

---

### Post by SeijiSensei on 2010-11-17
It may be the registered nameserver, but it doesn't appear to have a zone file for your domain.  Registration simply tells the root nameservers where to look for information about your domain.  I take it the registration record includes an IP address that points to ns1.fragdata.com?  If not, that's the first step.  Then you'll still have to create the various NS, MX, and A records on that machine to populate the zone if you haven't done so already.

---

### Post by syvil on 2010-11-17
> **SeijiSensei said:**
> It may be the registered nameserver, but it doesn't appear to have a zone file for your domain.  Registration simply tells the root nameservers where to look for information about your domain.  I take it the registration record includes an IP address that points to ns1.fragdata.com?  If not, that's the first step.  Then you'll still have to create the various NS, MX, and A records on that machine to populate the zone if you haven't done so already.

Thanks making some progress.

I ran those commands after following  instead of the link I posted and I get this.

A remote server away from network responds with the same result.
```
root@linux-server:/home/syvil# host ns1.fragdata.com
ns1.fragdata.com has address 192.168.1.202
```

My question is do I need to change/ etc/bind/zones/fragdata.com.db to the following instead of using my local IP? "MY.IP" being my real IP of course.
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.fragdata.com. root.fragdata.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.fragdata.com.
ns1      IN      A       MY.IP
box     IN      A       MY.IP
```

---

### Post by arrrghhh on 2010-11-17
Oh you're setting 192.168.1.202 as your IP...?  You need to specify your WAN IP, not the LAN IP...

Do you have a static WAN IP?  That's what I meant with static IP in this case...

---

### Post by syvil on 2010-11-17
> **arrrghhh said:**
> Oh you're setting 192.168.1.202 as your IP...?  You need to specify your WAN IP, not the LAN IP...

Do you have a static WAN IP?  That's what I meant with static IP in this case...
Yes I have a static WAN IP, I have set this now and restarted BIND9

I'll give it some time to update. I'm at Starbucks on their Wifi but behind a VPN I use so may take some time on the VPN side :)

---

### Post by arrrghhh on 2010-11-17
> **syvil said:**
> Yes I have a static WAN IP, I have set this now and restarted BIND9

I'll give it some time to update. I'm at Starbucks on their Wifi but behind a VPN I use so may take some time on the VPN side :)

Ok, just make sure your provider has your WAN IP as well...  Seems like you have a grasp on it now tho.

---

### Post by syvil on 2010-11-17
> **arrrghhh said:**
> Ok, just make sure your provider has your WAN IP as well...  Seems like you have a grasp on it now tho.
Ok getting closer!

[http://ns1.fragdata.com/](http://ns1.fragdata.com/) works

However [http://fragdata.com](http://fragdata.com) doesn't

Do I need to setup a zone for my WAN IP? I think I'm missing a thing or two in my configs

I did the following:

/etc/bind/zones/fragdata.com.db:
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.fragdata.com. root.fragdata.com. (
                     1290023180         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.fragdata.com.
ns1      IN      A       70.124.125.15
box     IN      A       70.124.125.15
www     IN      A       70.124.125.15
```

/etc/bind/zones/rev.125.124.70.in-addr.arpa:
```
  GNU nano 2.2.2                            File: /etc/bind/zones/rev.125.124.70.in-addr.arpa                                                                

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.fragdata.com. root.fragdata.com. (
                     1290028428         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.
202      IN      PTR     ns1.fragdata.com.
202      IN      PTR     fragdata.com.
```

---

### Post by syvil on 2010-11-17
I think I got it. I made a dumb mistake and forgot add an alias. [www.fragdata.com](www.fragdata.com) was working but now fragdata.com oops :-x

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.fragdata.com. root.fragdata.com. (
                     1290031238         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.fragdata.com.
ns1      IN      A       70.124.125.15
box     IN      A       70.124.125.15
fragdata.com.           IN      A       70.124.125.15
www                     IN      CNAME   fragdata.com.
```

:)

---

### Post by SeijiSensei on 2010-11-17
You can consolidate the records like this:

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.fragdata.com. root.fragdata.com. (
                     1290031238         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

        IN      NS      ns1.fragdata.com.
        IN      A       70.124.125.15

ns1     IN      A       70.124.125.15
box     IN      CNAME   fragdata.com.
www     IN      CNAME   fragdata.com.

```

All the records with no entry in the first column share the same definition, so the SOA, NS and initial A records all relate to fragdata.com.  

Just for reference, you'll always need an IP address and an A record to define the nameserver, though.  I don't think you can use a CNAME to define ns1 since it's referenced in the NS record.  I think the same holds true for hosts referenced in MX records, though don't hold me to that.

I generally prefer to use the YYYYMMDDNN method to create serial numbers.  They're easier to read when you want to know when you last updated a zone file.  If you need to make changes and re-HUP the server, just increment NN.  (E.g, the first effort today would be 2010111701.  If that doesn't work correctly, use 2010111702, etc.)

You also have unreasonably long expirations.  The values you're using make sense when applied to the loopback interface, but not for zones that are publicly visible.  These values influence how long DNS servers will cache your records.  The larger they are the longer it takes for any changes you make to propagate across the Internet.  See [this document](http://www.ripe.net/docs/dns-soa.html) for some recommended values.  Make sure the $TTL entry is identical to the "negative cache" value.

---

### Post by syvil on 2010-11-18
> **SeijiSensei said:**
> You can consolidate the records like this:

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.fragdata.com. root.fragdata.com. (
                     1290031238         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

        IN      NS      ns1.fragdata.com.
        IN      A       70.124.125.15

ns1     IN      A       70.124.125.15
box     IN      CNAME   fragdata.com.
www     IN      CNAME   fragdata.com.

```All the records with no entry in the first column share the same definition, so the SOA, NS and initial A records all relate to fragdata.com.  

Just for reference, you'll always need an IP address and an A record to define the nameserver, though.  I don't think you can use a CNAME to define ns1 since it's referenced in the NS record.  I think the same holds true for hosts referenced in MX records, though don't hold me to that.

I generally prefer to use the YYYYMMDDNN method to create serial numbers.  They're easier to read when you want to know when you last updated a zone file.  If you need to make changes and re-HUP the server, just increment NN.  (E.g, the first effort today would be 2010111701.  If that doesn't work correctly, use 2010111702, etc.)

You also have unreasonably long expirations.  The values you're using make sense when applied to the loopback interface, but not for zones that are publicly visible.  These values influence how long DNS servers will cache your records.  The larger they are the longer it takes for any changes you make to propagate across the Internet.  See [this document]("http://www.ripe.net/docs/dns-soa.html") for some recommended values.  Make sure the $TTL entry is identical to the "negative cache" value.

Thanks for your help! I decided to switch the domain to [http://syvil.me](http://syvil.me) however I can't get it to work. [http://ns.syvil.me](http://ns.syvil.me) works and I set the nameserver to it in Namecheap.

Here's my new configs.

/etc/bind/named.conf.local
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "syvil.me" {
    type master;
    file "/etc/bind/zones/syvil.me.db";
};

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "1.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

zone "125.124.70.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/rev.125.124.70.in-addr.arpa";
};
```

/etc/bind/zones/rev.1.168.192.in-addr.arpa
```
;
; BIND reverse data file for local loopback interface
;
$TTL    38400
@       IN      SOA     ns.syvil.me. root.syvil.me. (
                     2010111802         ; Serial
                          28800         ; Refresh
                           3600         ; Retry
                         604800         ; Expire
                          38400 )       ; Negative Cache TTL
;
@        IN      NS      ns.
202      IN      PTR     ns.syvil.me.
202      IN      PTR     syvil.me.
```

/etc/bind/zones/rev.125.124.70.in-addr.arpa
```
;
; BIND reverse data file for local loopback interface
;
$TTL    38400
@       IN      SOA     ns.syvil.me. root.syvil.me. (
                     2010111802         ; Serial
                          28800         ; Refresh
                           3600         ; Retry
                         604800         ; Expire
                          38400 )       ; Negative Cache TTL
;
@        IN      NS      ns.
202      IN      PTR     ns.syvil.me.
202      IN      PTR     syvil.me.
```

/etc/bind/zones/syvil.me.db
```
;
; BIND data file for local loopback interface
;
$TTL    38400
@       IN      SOA     ns.syvil.me. root.syvil.me. (
                     2010111802         ; Serial
                          28800         ; Refresh
                           3600         ; Retry
                         604800         ; Expire
                          38400 )       ; Negative Cache TTL

        IN      NS      ns.syvil.me.
        IN      A       70.124.125.15

ns      IN      A       70.124.125.15
box     IN      CNAME   syvil.me.
www     IN      CNAME   syvil.me.
```

---

### Post by syvil on 2010-11-18
I tried running "dig syvil.me" on a few different servers I work with and all get the same result. Could this be an issue with the DNS just no propagating yet?

```
syvil@syvil.net [~]# dig syvil.me

; <<>> DiG 9.3.6-P1-RedHat-9.3.6-4.P1.el5_4.2 <<>> syvil.me
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 40088
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;syvil.me.                      IN      A

;; AUTHORITY SECTION:
me.                     646     IN      SOA     ns.nic.me. noc.afilias-nst.info. 2008508666 3600 3600 3600000 8400

;; Query time: 0 msec
;; SERVER: 208.116.46.74#53(208.116.46.74)
;; WHEN: Thu Nov 18 17:22:22 2010
;; MSG SIZE  rcvd: 89
```

---

### Post by syvil on 2010-11-22
So I've been tearing my hair out trying to figure this out. Even if I replicated EXACTLY what I did with fragdata.com and simply change fragdata.com to syvil.me it will not work. I've even tried using another domain I have, fogatomic.com and this too will not work no matter what I do. Any help is appreciated, it doesn't make sense to me that only one domain will work and others wont even though I'm using the same exact settings just different domains

---

### Post by arrrghhh on 2010-11-22
So you've purchased the domain?  Have you looked at the provider's control panel page for your domain?

---

### Post by syvil on 2010-11-22
> **arrrghhh said:**
> So you've purchased the domain?  Have you looked at the provider's control panel page for your domain?

Yes and I registered the name server the same way I did with fragdata.com, still the only one that seems to want to work is fragdata.com even if I change fragdata.com with syvil.me in all the settings, update the serial and restart the bind.

---

### Post by syvil on 2010-11-22
```
  **Nameserver trace for fogatomic.com:**

 
[LIST]
[*]Looking for who is responsible for root zone and followed e.root-servers.net.
[*]Looking for who is responsible for com and followed a.gtld-servers.net.
[*]Looking for who is responsible for fogatomic.com and followed ns1.fragdata.com.
[/LIST]
    **Nameservers for fogatomic.com:**

 
[LIST]
[*]         [COLOR=#ff0000]             **ns1.fragdata.com**                              returned (NORECORDS)                     [/COLOR]
[/LIST]
  

``````
  **Nameserver trace for syvil.me:**

 
[LIST]
[*]Looking for who is responsible for root zone and followed i.root-servers.net.
[*]Looking for who is responsible for me and followed ns.nic.me.
[/LIST]
    **Nameservers for syvil.me:**

 
[LIST]
[*]         [COLOR=#ff0000]             **c0.cctld.afilias-nst.info**                              returned (NORECORDS)                     [/COLOR]
[*]         [COLOR=#ff0000]             **d0.cctld.afilias-nst.org**                              returned (NORECORDS)                     [/COLOR]
[*]         [COLOR=#ff0000]             **ns.nic.me**                              returned (NORECORDS)                     [/COLOR]
[*]         [COLOR=#ff0000]             **b2.me.afilias-nst.org**                              returned (NORECORDS)                     [/COLOR]
[*]         [COLOR=#ff0000]             **a2.me.afilias-nst.info**                              returned (NORECORDS)                     [/COLOR]
[*]         [COLOR=#ff0000]             **b0.cctld.afilias-nst.org**                              returned (NORECORDS)                     [/COLOR]
[*]         [COLOR=#ff0000]             **a0.cctld.afilias-nst.info**                              returned (NORECORDS)                     [/COLOR]
[*]         [COLOR=#ff0000]             **ns2.nic.me**                              returned (NORECORDS)                     [/COLOR]
[/LIST]
  

```

Not sure why syvil.me isn't finding the correct nameservers, those were set almost a week ago.

---

