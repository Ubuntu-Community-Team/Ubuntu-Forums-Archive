---
title: "No www?"
date: 2011-05-23
forum: Server Platforms
---

### Post by d3fau1t on 2011-05-23
I set up multiple servers on my home pc, but I don't know how to make it work with "www". In other words, if my website was "thechamp.com", [http://thechamp.com](http://thechamp.com) would take you there, but [http://www.thechamp.com](http://www.thechamp.com) will take you to a "page not found" screen.

It's got to be something simple, right? What am I overlooking?

Thanks.

---

### Post by doas777 on 2011-05-23
www is a DNS A or CNAME record that points to your Web server in your domain. 

here is a sample zone for a domain called example.com
```
; zone file for example.com
$TTL 2d    ; 172800 secs default TTL for zone
$ORIGIN example.com.
@             IN      SOA   ns1.example.com. hostmaster.example.com. (
                        2003080800 ; se = serial number
                        12h        ; ref = refresh
                        15m        ; ret = update retry
                        3w         ; ex = expiry
                        3h         ; min = minimum
                        )
              IN      NS      ns1.example.com.
              IN      MX  10  mail.example.net.
joe           IN      A       192.168.254.3
www           IN      CNAME   joe
```in this case, [www.example.com]("http://www.example.com") is a CNAME (alias) for joe.example.com which points to 192.168.254.3.

here is an intro to Bind, the most common unix DNS server:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

since you have a home network, you would probably want to point your clients to your bind server, and configure "forwarders" to your ISP dns servers, so that when one of your hosts wants a page, it asks your DNS server. your server does not find the site in the local domain so it forwards on your request to the isp and relays back its response.

---

### Post by d3fau1t on 2011-05-24
The company I registered my domain names with has a dns service.

I go to set up a zone, and it says it is also creating the prefix www. 

I type the domain in the address bar, and it goes to my IP. But I add the www, and it doesn't. Are you sure I need to use dns software on my computer?

I think this has something to do with me using virtual hosts in apache.

Thanks for answering, btw.

---

### Post by Ryan Dwyer on 2011-05-24
In that case you might have the DNS set up correctly. If you run "dig www.thechamp.com" and see the IP then you know DNS is fine. To set up to vhost to listen on www as well, add "ServerAlias www.thechamp.com" to your vhost config file. Reload Apache and it should be working.

By the way, I assume you're using an internal DNS server because I can't resolve either [www.thechamp.com](www.thechamp.com) or thechamp.com.

---

### Post by d3fau1t on 2011-05-24
Thanks, Ryan.

Using that command in a terminal does show my ip.

I did try changing the vhost file to say www, but it didn't seem to fix it. I'll try it again.

("thechamp.com" was just an example lol.)

---

### Post by doas777 on 2011-05-24
> **d3fau1t said:**
> The company I registered my domain names with has a dns service.

I go to set up a zone, and it says it is also creating the prefix www. 

I type the domain in the address bar, and it goes to my IP. But I add the www, and it doesn't. Are you sure I need to use dns software on my computer?

I think this has something to do with me using virtual hosts in apache.

Thanks for answering, btw.
ahh, if you have purchased service from a registrar, then no, you don't need a DNS server on site. the principal for configuring your domain is the same however. if dig returns correctly, then your issue is likely not a naming resolution problem. 

you say your site comes up and displays correctly if you go to the domain root, but not to [www.thechamp.com](www.thechamp.com) ? and that 
```
nslookup thechamp.com
nslookup www.thechamp.com
``` both resolve correctly? if so your DNS is just fine. if the names resolve, but the page does not come up for either, have you configured your router to forward the server ports, and tested that configuration?

Id' suspect an apache config issue as well. this may help:
[http://www.cyberciti.biz/faq/apache-redirect-domaincom-to-wwwdomaincom/](http://www.cyberciti.biz/faq/apache-redirect-domaincom-to-wwwdomaincom/)

---

### Post by SeijiSensei on 2011-05-24
As Ryan said, you need a ServerAlias directive in the Apache configuration for this virtual host like this:

```

<VirtualHost *:80>
ServerName     thechamp.com
ServerAlias    www.thechamp.com

[etc.]

```

Now the server will respond equivalently for either requested hostname.

---

### Post by d3fau1t on 2011-05-24
Thanks guys.

I added the "ServerAlias www.thechamp.com" line and restarted, but unfortunately it still doesn't work for some reason.

:confused:

---

### Post by Ryan Dwyer on 2011-05-25
When you dig [www.thechamp.com](www.thechamp.com), do you get the correct IP?

When you browse to [www.thechamp.com](www.thechamp.com) in a browser, do you get a connection error, timeout, or does it load your default virtualhost?

What does your registrar's system say?

Can you tell us what the domain name really is?

---

### Post by d3fau1t on 2011-05-25
Actually, it doesn't give the right ip:

```
dig www.eliteos.ca

; <<>> DiG 9.7.3 <<>> www.eliteos.ca
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31176
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.eliteos.ca.			IN	A

;; ANSWER SECTION:
www.eliteos.ca.		0	IN	A	67.63.50.58

;; Query time: 28 msec
;; SERVER: 64.59.135.143#53(64.59.135.143)
;; WHEN: Wed May 25 18:00:51 2011
;; MSG SIZE  rcvd: 48
```

My ip is 96.51.30.151. "dig eliteos.ca" does give the right ip.

eliteos.ca is one of my domains

When I type 'eliteos.ca' into my browser, the page comes up. But when I type 'www.eliteos.ca' it goes to my ISP's 'dns help' google search page.

---

### Post by doas777 on 2011-05-25
> **d3fau1t said:**
> Actually, it doesn't give the right ip:

```
dig www.eliteos.ca

; <<>> DiG 9.7.3 <<>> www.eliteos.ca
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31176
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.eliteos.ca.            IN    A

;; ANSWER SECTION:
www.eliteos.ca.        0    IN    A    67.63.50.58

;; Query time: 28 msec
;; SERVER: 64.59.135.143#53(64.59.135.143)
;; WHEN: Wed May 25 18:00:51 2011
;; MSG SIZE  rcvd: 48
```My ip is 96.51.30.151. "dig eliteos.ca" does give the right ip.

eliteos.ca is one of my domains

When I type 'eliteos.ca' into my browser, the page comes up. But when I type 'www.eliteos.ca' it goes to my ISP's 'dns help' google search page.

ok, then the problem definitely appears to  be with the registrar's dns configuration for your site. have you contacted them for support?

---

### Post by d3fau1t on 2011-05-26
Kind of. :)

So the prefix thing is broke at their end, even tho the non-prefix address is ok?

---

### Post by Ryan Dwyer on 2011-05-26
Yeah. Look in their control panel to see if you can figure out how to fix it, otherwise contact them for help.

Note that when I dig [www.eliteos.ca](www.eliteos.ca) I get NXDOMAIN (no result) whereas you get your ISP's IP address. This is something your ISP is doing because you're using their DNS server. Everyone else would get the NXDOMAIN response.

---

### Post by doas777 on 2011-05-26
> **d3fau1t said:**
> Kind of. :)

So the prefix thing is broke at their end, even tho the non-prefix address is ok?
exactly. the dig queries for yoursite and [www.yoursite](www.yoursite) should return the same address. if they do not, then something is wrong on the registrar's end. 

I too get an NXDOMAIN for your www alias, but your site root resolves correctly for me.

---

### Post by d3fau1t on 2011-05-26
They wrote me back saying to go into my dns settings and click "add host" and then enter the www address. I thought I was ok there because it automatically generated a www alias when I created the main address.

So I did that, but alas, no change.

---

### Post by hawkmage on 2011-05-26
Why is your system resolving against 64.59.135.143?

```
hawkmage@ubuntu:~$ host 64.59.135.143
143.135.59.64.in-addr.arpa domain name pointer nsc3.so.cg.shawcable.net.
hawkmage@ubuntu:~$ host nsc3.so.cg.shawcable.net
nsc3.so.cg.shawcable.net has address 64.59.135.143
nsc3.so.cg.shawcable.net has IPv6 address 2001:4e8:0:4001::13
```

When I resolve you [www.eliteos.ca](www.eliteos.ca) against the authoritative DNS for your domain which should be your hosting providers DNS I get the correct address.
```
hawkmage@ubuntu:~$ nslookup -type=ANY www.eliteos.ca ns1.domain-dns.ca
Server:        ns1.domain-dns.ca
Address:    209.17.165.111#53

Name:    www.eliteos.ca
Address: 96.51.30.151

hawkmage@ubuntu:~$ nslookup -type=ANY www.eliteos.ca ns2.domain-dns.ca
Server:        ns2.domain-dns.ca
Address:    64.69.88.81#53

Name:    www.eliteos.ca
Address: 96.51.30.151

hawkmage@ubuntu:~$ nslookup -type=ANY www.eliteos.ca ns3.domain-dns.ca
Server:        ns3.domain-dns.ca
Address:    209.139.194.1#53

Name:    www.eliteos.ca
Address: 96.51.30.151
```

```
hawkmage@ubuntu:~$ nslookup -type=ANY eliteos.ca 
Server:        192.168.100.10
Address:    192.168.100.10#53

Non-authoritative answer:
eliteos.ca    nameserver = ns3.domain-dns.ca.
eliteos.ca    nameserver = ns1.domain-dns.ca.
eliteos.ca    nameserver = ns2.domain-dns.ca.

Authoritative answers can be found from:
eliteos.ca    nameserver = ns1.domain-dns.ca.
eliteos.ca    nameserver = ns2.domain-dns.ca.
eliteos.ca    nameserver = ns3.domain-dns.ca.

hawkmage@ubuntu:~$ nslookup eliteos.ca 
Server:        192.168.100.10
Address:    192.168.100.10#53

Non-authoritative answer:
Name:    eliteos.ca
Address: 96.51.30.151

hawkmage@ubuntu:~$ nslookup -type=ANY eliteos.ca ns1.domain-dns.ca
Server:        ns1.domain-dns.ca
Address:    209.17.165.111#53

eliteos.ca
    origin = ns1.domain-dns.com
    mail addr = hostmaster.baremetal.com
    serial = 1306463613
    refresh = 601
    retry = 300
    expire = 1048576
    minimum = 3600
eliteos.ca    nameserver = ns1.domain-dns.com.
eliteos.ca    nameserver = ns2.domain-dns.com.
eliteos.ca    nameserver = ns3.domain-dns.com.
eliteos.ca    nameserver = ns1.domain-dns.ca.
eliteos.ca    nameserver = ns2.domain-dns.ca.
eliteos.ca    nameserver = ns3.domain-dns.ca.
Name:    eliteos.ca
Address: 96.51.30.151

hawkmage@ubuntu:~$ nslookup -type=ANY www.eliteos.ca ns1.domain-dns.ca
Server:        ns1.domain-dns.ca
Address:    209.17.165.111#53

Name:    www.eliteos.ca
Address: 96.51.30.151

hawkmage@ubuntu:~$ host ns1.domain-dns.ca
ns1.domain-dns.ca has address 209.17.165.111
hawkmage@ubuntu:~$ host ns2.domain-dns.ca
ns2.domain-dns.ca has address 64.69.88.81
hawkmage@ubuntu:~$ host ns3.domain-dns.ca
ns3.domain-dns.ca has address 209.139.194.1
hawkmage@ubuntu:~$ host ns1.domain-dns.com
ns1.domain-dns.com has address 209.17.165.111
hawkmage@ubuntu:~$ host ns2.domain-dns.com
ns2.domain-dns.com has address 64.69.88.81
hawkmage@ubuntu:~$ host ns3.domain-dns.com
ns3.domain-dns.com has address 209.139.194.1
hawkmage@ubuntu:~$ 

```

---

### Post by d3fau1t on 2011-05-26
Yay, everything works now!

Thank you everyone.

---

### Post by hawkmage on 2011-05-26
What was the solution?

---

### Post by d3fau1t on 2011-05-26
Adding the ServerAlias line to each entry in my virtual hosts file, and adding the www record via my dns service.

---

