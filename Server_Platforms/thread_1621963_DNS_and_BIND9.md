---
title: "DNS and BIND9"
date: 2010-11-14
forum: Server Platforms
---

### Post by deusexcalibur on 2010-11-14
I'm interested in learning exactly how to set up a DNS server using BIND9, but I am very confused over how everything works. I've only recently delved into making my own server. I'm about to purchase the book DNS & BIND by O'Reilly.

The server I'm building is a web and mail server in one machine behind a router. I currently use DynDns since my IP is dynamic. I could stick with the easy way but I'd like to do it the hard way as a learning experience. When I'm out of college I'd like to have this knowledge.

I have a basic understanding of DNS but when it comes to implementing a solution for my server I simply don't know jack. I know I need BIND9 and I need to register a DNS. (with network solutions?) Online research hasn't really cleared my confusion.

What hoops would I have to go through so I could create a domain name and have it work on the web? I only have one machine as the server so I wouldn't have a slave dns server. Would I 1) register a domain like example.net on network solutions and then 2) configure BIND9 accordingly? How would I work around having a dynamic ip? I've read that I may need something called DHCP-Server3, but I'm still very new to this and the tutorials aren't making too much sense at this point .

Would I be able to set it up in a way where my network behind the router can access the server via a different domain name? (ex server.net)

Thanks in advance!

---

### Post by James78 on 2010-11-14
This doesn't answer your question exactly how you wanted, but I wrote a crash course on this a little bit back. You may find it helpful.
[http://ubuntuforums.org/showthread.php?t=1598245](http://ubuntuforums.org/showthread.php?t=1598245)

---

### Post by KB1JWQ on 2010-11-14
Very short version is that you'll have a named.conf that sets up the server's configuration.  After that, you'll have zone files that spell out records for each domain you're handling DNS for.  The latter is what gets updated when you change DNS information, followed by a named reload.

That's a VERY high level view, glossing over a lot of important data; if you have specific questions please ask, and we'll do what we can to help you out. :-)

---

### Post by deusexcalibur on 2010-11-15
Ok, I thought I would start small and attempt to make a local intranet DNS before purchasing a domain. I feel like if I wanted to set up a local DNS my setup would need to be router->server->PCs. Right now it is Router->PCs+Server. I'd prefer to keep it that way. If not I may just get a super cheap web domain to experiment with.

The server has been up and running, working with apache2 and squirrelmail with my dyndns address, for a little while now. I had no problem setting all of those things up, for some reason BIND just makes me want to pull my hair out. Right now I simply type:

[http://my.dyndns.com](http://my.dyndns.com) for the main apache2 directory
[http://my.dyndns.com/forum](http://my.dyndns.com/forum) for the phpbb board
[email]user@my.dyndns.com[/email] to send emails to the server

My router's IP is 192.168.0.1 and the server is 192.168.0.100. Would there be a way to configure BIND so that my other PCs could locally connect to it via a DNS address?

If I am to understand correctly, the www in the zones config would redirect [www.mydomain.com](www.mydomain.com) to the apache2 server with the local machine host name www? Or simply direct www to the machine that has the IP 192.168.0.*? Is it the equivalent of 192.168.0.*.example.com?

ex www IN A 192.168.0.*
    mail IN A 192.168.0.*2
    ftp IN A 192.168.0.*3

What if www, ftp, and mail are on the same machine? Would I just enter localhost or not leave any entry in whatsoever? Would the machine that is the DNS server need to be named ns1 in the /etc/hosts file? I'm trying to get the most out of this one server. :)

Could I somehow experiment with my current dyndns address? (ex set up subdomains like forum.my.dyndns.com and edit the Server Alias in apache accordingly)

I know that's a lot of questions but I feel like I'm stumbling around in the dark here. For each answer there seems to be only 20 more questions! I'm pretty sure I'll think of 10 more right after I hit post. :D  I feel like I am slowly getting it though. I apologize for my lack of understanding, but I only made the server and started learning Linux for the first time a week and a half ago.

---

### Post by SeijiSensei on 2010-11-15
> I apologize for my lack of understanding, but I only made the server and started learning Linux for the first time a week and a half ago.

BIND is not something I'd recommend to a person just starting out.  It's substantially more complicated to set up than regular daemons.

Here are a few answers:
> What if www, ftp, and mail are on the same machine? Would I just enter localhost or not leave any entry in whatsoever? Would the machine that is the DNS server need to be named ns1 in the /etc/hosts file? I'm trying to get the most out of this one server. 

DNS is designed to handle this problem through the use of the CNAME aliasing record.  For instance:

```

www      IN  A      192.168.1.1
ftp      IN  CNAME  www

```

will point both [www.example.com](www.example.com) and ftp.example.com to the same address.  You can't use aliasing for NS or MX records, although the hosts to which they point can be aliased:

```

subdomain    IN   NS   ns1.example.com.
             IN   NS   ns2.example.com.

ns1          IN   A      192.168.1.1
ns2          IN   CNAME  backupns.somewhere.net.

```

BTW, you can't use wildcards like "*" in the data fields of a record as you have in the example above.

> My router's IP is 192.168.0.1 and the server is 192.168.0.100. Would there be a way to configure BIND so that my other PCs could locally connect to it via a DNS address?

Just set up the DHCP server on your router to give out 192.168.0.100 as the primary nameserver to the hosts on your local network.

Where things get tricky is if you want to support public DNS lookups that point to a publicly-visible address like your router's IP and a private DNS server with only privately-visible addresses behind the router.  I often maintain separate DNS zone files for clients with one set running on a public DNS server and another running on a machine inside the local network.  That way [www.example.com](www.example.com) can point to a public address outside but a private address inside if appropriate.

---

### Post by deusexcalibur on 2010-11-15
UPDATE: I got it working! Though if I don't configure each of my network PCs to forcibly use 192.168.0.100 as their DNS server, the router just assigns 192.168.0.1 and I can't see the local domain (or anything if no secondary DNS is on the router). Not sure what to do with that.

mydomain.net and [www.mydomain.net](www.mydomain.net) forward to the apache2 webserver and gw.mydomain.net forwards to the router. I can't use mydomain.net:10000 to access webmin. I have to add ns1 as the subdomain. (ex ns1.mydomain.net:10000) It seems to copy whatever the hosts are in /etc/hosts. If I remove 192.168.0.100 ns1.mydomain.net ns1 I have to type server.mydomain.net (the server's host name).

I guess my next step is to buy a domain and make the separate zones in the same fashion?
ex: *my internet IP* IN NS ns1.example.com ? 

OLD POST:

Ok, thanks for the input all. I'm slowly getting closer to figuring this out. A reverse lookup on 192.168.0.100 produces the result:

```
100.0.168.192.in-addr.arpa      name = mydomain.net.0.168.192.in-addr.arpa.
```I don't get anything when I try this on another machine. 

All forward lookups fail externally. The nslookup of mydomain.net on the server itself produces:

```
** server can't find mydomain.net.mydomain.net: SERVFAIL
```To reiterate: I want my one server to be the DNS, web, ftp, and mail server. My router has the Primary DNS server set to 192.168.0.100. If I don't provide a secondary on the router's configuration I can't access any websites. My named.conf.options is set to forward to my ISP's primary DNS server.

Here is my named.local.conf:

```
//
// Do any local configuration here
//
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "mydomain.net" {
type master;
file "/etc/bind/zones/mydomain.net.db";
};

zone "0.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};    

```Here is the mydomain.net.db:

```
$TTL 3D
@ IN SOA ns1.mydomain.net. admin.mydomain.net. (
2006081401
28800
3600
604800
38400
)
mydomain.net. IN NS ns1 ; This is where I'm not sure what I am doing. What exactly should "subdomain" be?

ns1    IN    A        192.168.0.100; should this be localhost instead?
www    IN    CNAME    ns1
gw     IN    A        192.168.0.1
                 TXT  "Network gateway"

```And the reverse lookup file:

```
$TTL 3D
@ IN SOA ns1.mydomain.net.  admin.mydomain.net. (
2006081401
28800
604800
604800
86400
)
;
@ IN NS ns1.mydomain.net.  ; again this is the line where I'm not sure what I'm doing


1 IN PTR gw.mydomain.net
100 IN PTR mydomain.net

```And lastly my resolv.conf

```
 
[FONT=&quot][FONT=Arial]search mydomain.net.
nameserver 192.168.0.100[/FONT][/FONT]

```Does the /etc/hosts config come into play at all? Or /etc/hostname? My hostname is just server.

EDIT: If I set my Windows ethernet adapter to use only 192.168.0.100 as the DNS the server forwards properly but mydomain.net still doesn't resolve.

---

### Post by deusexcalibur on 2010-11-18
Ok, I registered my domain but I cannot access it externally. My registrar gave me a secondary DNS and I pointed the primary toward my IP.

```
 
[FONT=&quot]$TTL 3D
example.com. IN SOA ns1.example.com. admin.example.com. (
2006081401
28800
3600
604800
38400
)
;
example.com. IN NS ns1.example.com. 
example.com. IN MX 10 mail.example.com.

ns1.example.com.   IN A (My internet IP)
mail.example.com.  IN A 192.168.0.100
www.example.com. IN A 192.168.0.100
[/FONT]
  
```Is this set up correctly? My router is set to forward ports 53 and 80 to the server. It was registered last night, do I need to wait another day or two?

EDIT: I changed the line [FONT=&quot]ns1.example.com.   IN A (My internet IP) [/FONT]to point to 192.168.0.100. If my router is forwarding the port it should just be the internal IP address, correct? Still doesn't work though.[FONT=&quot]

[/FONT]I did a dig from an off site location and got this:[FONT=&quot]

[/FONT]> example.com.    172800    IN    NS    ns2.myregistrar.org
 example.com.    172800    IN    NS    ns3.myregistrar.org
 example.com.    172800    IN    NS    ns4.myregistrar.org
 example.com.    172800    IN    NS    ns5.myregistrar.org
 ;; Received 118 bytes from 192.55.83.30#53(m.gtld-servers.net) in 140 ms
 
 example.com.    38400    IN    SOA    server.example.com. admin.example.com. 2006081401 28800 3600 604800 38400
 ;; Received 83 bytes from 204.13.249.76#53(ns2.myregistrar.org) in 112 ms
Any ideas? Does this just mean I have to wait for root DNS servers to update?

---

