---
title: "Bind dns resolving local servers"
date: 2018-05-23
forum: Server Platforms
---

### Post by brent1975 on 2018-05-23
Hello - I have had bind9 installed and running on my server for some time now. However, I have never been able to do a lookup on a specific server on my network to get the IP or vise verse. I have looked at multiple forums and seems that there are so many different configurations.  Thank you in advance for any guidance.

Here is my setup

server001.linux-network.home  - 192.168.1.105  (Bind DNS Server)  {Ubuntu 16.04 with latest updates}
server002.linux-network.home  - 192.168.1.110  (Virtual testing server) {Centos7 }
server003.linux-network.home  -  192.168.1.111 (Virtual testing server)  {Centos7}

All my devices on the network use server001 IP for DNS and able to access the internet without a problem. using dig to find name servers for google.com for example works great.

The issues I am having is when I do a lookup for server001,2 or 3 weather it is hostname or fqdn I am not getting an IP address. I am also not getting a host name when I lookup the IP address of one of the servers.

Here is what I get when I dig the ip of server002
[IMG]http://kc-linux.com/download/digip.PNG[/IMG]

Here is what I get when I dig the hostname or fqdn

[IMG]http://kc-linux.com/download/digfqdn.PNG[/IMG]

Here is what I get when I run nslookup from my windows box.

[IMG]http://kc-linux.com/download/nslookup.PNG[/IMG]

Here are my bind config files.

db.192

[IMG]http://kc-linux.com/download/db192.PNG[/IMG]

db.linux-network.home

[IMG]http://kc-linux.com/download/db.linux-network.home.PNG[/IMG]

named.conf.local

[IMG]http://kc-linux.com/download/named.conf.local.PNG[/IMG]

named.conf.options

[IMG]http://kc-linux.com/download/named.conf.options.PNG[/IMG]

---

### Post by Doug S on 2018-05-23
Any chance that you could fix the formatting of your listings?
Your db.192 file looks incorrect.

---

### Post by papibe on 2018-05-23
Hi brent1975.

A few thoughts:

I think you want to use zone "linux-network.home"  instead of "linux-master.com" in named.conf.local.

In order for client to resolve hostnames (no domain, like server002), they need to have the proper 'search' and/or 'domain'. These are passed by the DHCP server. Who is handling DHCP?

The zone "1.168.192.in-addr.arpa" (file /etc/bind/db.192) should resolve single digits, like 101 for server001. For example:
```
; PTR Records
105           IN      PTR      server001.linux-network.home.
```
Could you please paste again the files so spaces and newlines are respected? 

Regards.

---

### Post by darkod on 2018-05-23
It doesn't hurt reading little basic documentation too: [https://help.ubuntu.com/lts/serverguide/dns-configuration.html.en-GB](https://help.ubuntu.com/lts/serverguide/dns-configuration.html.en-GB)

In your forward zone file, in the IN SOA line, the domain and admin email address need to finish with a DOT. In your case they don't. This will prevent correct zone functioning.

And your CNAMEs are wrong. You can't make a CNAME saying server1 is alias to server1.domain.com. That is the point of the zone file, the domain.com part is automatically added.

Follow the instructions in my link, make a basic zone file first, fix the DOTs you are missing and delete the CNAME records. Restart bind and check if it worked.

---

### Post by brent1975 on 2018-05-23
> **papibe said:**
> Hi brent1975.

A few thoughts:

I think you want to use zone "linux-network.home"  instead of "linux-master.com" in named.conf.local.

In order for client to resolve hostnames (no domain, like server002), they need to have the proper 'search' and/or 'domain'. These are passed by the DHCP server. Who is handling DHCP?

The zone "1.168.192.in-addr.arpa" (file /etc/bind/db.192) should resolve single digits, like 101 for server001. For example:
```
; PTR Records
105           IN      PTR      server001.linux-network.home.
```
Could you please paste again the files so spaces and newlines are respected? 

Regards.

Thanks for the response. I corrected the zone. my understanding for the zone file db.192 "105" for example is supposed to be the last octet of the device IP. I don't use dhcp on my network.

---

### Post by darkod on 2018-05-25
I will try one more time because you don't seem to be reading all the replies. Your db.linux-network.home has major errors. Did you see my previous post and read the document?

You need to fix that. The reverse zone is the least of your problems, it is rarely used anyway. The nslookup you posted is for the forward zone. And that still needs fixing if it looks like your post #1.

---

### Post by brent1975 on 2018-05-25
> **darkod said:**
> I will try one more time because you don't seem to be reading all the replies. Your db.linux-network.home has major errors. Did you see my previous post and read the document?

You need to fix that. The reverse zone is the least of your problems, it is rarely used anyway. The nslookup you posted is for the forward zone. And that still needs fixing if it looks like your post #1.

I read your post. I created a new one and this what I have.

[IMG]http://kc-linux.com/download/db.linux-network2.PNG[/IMG]


When I do a dig on ns now I get:
[IMG]http://kc-linux.com/download/dig.ns.PNG[/IMG]

I am at least getting answers now. However, I was thinking it should have my server listed. not root-servers.net.

---

### Post by Doug S on 2018-05-25
"dig" does not auto append the dns-search stuff (the rest of the FQDN). nslookup does.
Example:

```
doug@DOUG-64:~$ [COLOR="#FF0000"]dig s15[/COLOR]

; <<>> DiG 9.10.3-P4-Ubuntu <<>> s15
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 6290
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;s15.                           IN      A

;; AUTHORITY SECTION:
.                       10800   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2018052500 1800 900 604800 86400

;; Query time: 200 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri May 25 07:21:41 PDT 2018
;; MSG SIZE  rcvd: 107

doug@DOUG-64:~$ [COLOR="#FF0000"]nslookup s15[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53

Name:   s15.smythies.com
Address: 192.168.111.112

doug@DOUG-64:~$ [COLOR="#FF0000"]dig s15.smythies.com[/COLOR]

; <<>> DiG 9.10.3-P4-Ubuntu <<>> s15.smythies.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45975
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;s15.smythies.com.              IN      A

;; ANSWER SECTION:
s15.smythies.com.       604800  IN      A       192.168.111.112

;; AUTHORITY SECTION:
smythies.com.           604800  IN      NS      ns1.smythies.com.

;; ADDITIONAL SECTION:
ns1.smythies.com.       604800  IN      A       192.168.111.1

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri May 25 07:24:03 PDT 2018
;; MSG SIZE  rcvd: 95

doug@DOUG-64:~$

```

---

### Post by darkod on 2018-05-25
The IN SOA line is still wrong. It should contain the domain name, not the FQDN of the server. It should be:
```
@   IN   SOA   linux-network.home. root.linux-network.home. (
```

Then, the A record for server001 should be:
```
server001   IN   A   192.168.1.105
```

You don't need to have the ns A record you set up now if you don't need it. In the documentation they use ns because that is what they call the server. Yours is server001.

---

### Post by brent1975 on 2018-05-25
I changed the A record

[IMG]http://kc-linux.com/download/db.linux-network.home2.PNG[/IMG]


I restarted bind and ran nslookup 

[IMG]http://kc-linux.com/download/nslookup2.PNG[/IMG]

---

### Post by darkod on 2018-05-25
For each modification of the zone file you need to change the Serial value. Not sure if bind is insisting on that or not. I notice you have serial of 6 now and before, you didn't change it.

Best to use date format with couple of digits on the end (two digit XX would allow you up to 99 changes on the same day). Try putting the serial at 2018052501 and restart bind.

And the IN NS line is not correct, it needs dot at the end:
```
@   IN   NS   server001.linux-network.home.
```

Change that line and the serial, restart bind and try the nslookup again.

---

### Post by Doug S on 2018-05-25
> **darkod said:**
> For each modification of the zone file you need to change the Serial value. Not sure if bind is insisting on that or not.It depends. see [this]("https://ubuntuforums.org/showthread.php?t=2132979&p=12596074#post12596074").

> **darkod said:**
> 
And the IN NS line is not correct, it needs dot at the end:
```
@   IN   NS   server001.linux-network.home.
```Good catch. I've been looking and looking and didn't see it.

---

### Post by brent1975 on 2018-05-25
I am now able to do a nslookup and dig and get results using the fqdn. 

dig:

[IMG]http://kc-linux.com/download/dns1.PNG[/IMG]

nslookup:


[IMG]http://kc-linux.com/download/nslookup3.PNG[/IMG]

question, to add my other servers do I just create the two A records for each server?

@                          IN      A         192.168.1.110
server002              IN      A         192.168.1.110
@                          IN      A         192.168.1.111
server003               IN      A         192.168.1.111

---

### Post by Doug S on 2018-05-25
> **brent1975 said:**
> 

question, to add my other servers do I just create the two A records for each server?

@                          IN      A         192.168.1.110
server002              IN      A         192.168.1.110
@                          IN      A         192.168.1.111
server003               IN      A         192.168.1.111No. Leave out the @ lines. Do this:
```

server002              IN      A         192.168.1.110
server003              IN      A         192.168.1.111
``` Example```
;
; BIND data file for smythies.com
;
$TTL    604800
@       IN      SOA     smythies.com. doug.smythies.com. (
                        2016012601      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
                IN      A       192.168.111.1
;
@               IN      NS      ns1.smythies.com.
ns1             IN      A       192.168.111.1
www             IN      A       192.168.111.1

DOUG-64         IN      CNAME   ns1
mail            IN      CNAME   ns1
Wireless-R      IN      A       192.168.111.57
doug-xps        IN      A       192.168.111.100
doug-xps2       IN      A       192.168.111.101
s10             IN      A       192.168.111.102
cyd-hp          IN      A       192.168.111.103
cyd-hp2         IN      A       192.168.111.104
tv01            IN      A       192.168.111.105

```

---

### Post by brent1975 on 2018-05-26
Thank you! I am now able to do a dig and nslookup from my ns server001 and get responses. I seem to be having issues from other devices getting the answers though. Have any suggestions on that one?  

on server002 here is what I get.

here is my dig
[IMG]http://kc-linux.com/download/dig5.PNG[/IMG]

Here is my nslookup
[IMG]http://kc-linux.com/download/nslookup5.PNG[/IMG]

---

### Post by Doug S on 2018-05-26
well, you do not seem to have told server002 to use server001 as its DNS. How you do that depends on how server002 gets it IP address, and, I suppose, with 18.04 if you're using netplan or not. If you are using static IP addresses (and not netplan) you can specify in the /etc/network/interfaces file using the "dns-nameservers" stanza. If you are using DHCP and a DHCP server, then it can be specified with the lease response data using the "option domain-name-servers" stanza.

---

### Post by brent1975 on 2018-05-26
I use 16.04 and all my devices have static IP's. my test centos 7 box server002 was using dns 8.8.8.8. corrected dns and now they work. Thanks for stepping me through this.

---

