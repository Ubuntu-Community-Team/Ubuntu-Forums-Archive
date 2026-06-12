---
title: "bind9 for hosting website"
date: 2014-10-05
forum: Server Platforms
---

### Post by theluli2 on 2014-10-05
Dear All

Since a week , l am trying to find solution for a hosting website , and till now no results, l don't know if someone has a same topic here , but incase there are please forgive or delete my topic


The problem is that , l have purchased a website, and l have my server up and running with LAMP, but when it comes to bind/dns , really l don't know where to search for solution 


so please if anyone can advise me how to host a website with my own BIND


Thank you 
Theluli

---

### Post by nerdtron on 2014-10-05
Why do you want to use your own BIND? Isn't your domain provider (registrar) also a provider of DNS? Are your needing features that are not provided by your registrar?

And how far did you manage on the installation of BIND? Any specific problems you are having?
Is this what you are looking for? [https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-an-authoritative-only-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-an-authoritative-only-dns-server-on-ubuntu-14-04)

---

### Post by theluli2 on 2014-10-05
Also l forget to mention that , l have public IP , l can open any port so rest of the world can access the server

Well there is a DNS by domain provider, but l would like to make by my self configuration, to see more how things working
Thanks for the tutorial, l checked before the same but whene l try to access my website from internet l don't get any respond

l am more interested how things work in real world
an example :

Where tu put my public ip
where to put my internal ip 
where to put my  domain name

l hope you get my point ?

---

### Post by nerdtron on 2014-10-05
Where tu put my public ip - Depends on your network setup, how many do you have? If just one, assign it to the router.
where to put my internal ip - If you only have 1 public IP, assign private IP on your servers and setup port forwarding on the router.
where to put my  domain name - the domain will be in the zone files of the bind server. The zone file maps the domain name to the IP of the website.


BTW: Experiment you setup using all private IP addresses on your servers. The public internet is a dangerous place for experimental, unsecured servers with public IP addresses.

---

### Post by theluli2 on 2014-10-06
Hi Nerdtron

Thanks for fast respond 

l don't everything , from port forwarding and yes l have only one public IP that is attached to my router 

" where to put my  domain name - the domain will be in the zone files of the [COLOR=#417394]bind[/COLOR] server. The zone file maps the domain name to the IP of the website." -------> The problem is here ! , l can not map my domain name to the IP of the website , instead is pointed to Public IP of the router

---

### Post by nerdtron on 2014-10-06
> **theluli2 said:**
> Hi Nerdtron

  l can not map my domain name to the IP of the website , instead is pointed to Public IP of the router

You only have a single IP so port forwarding would involve port for DNS 53, and HTTP which is 80. Port 53 should be forwarded to the internal IP of your dns server, port 80 on the internal IP of the web server. You can test your DNS server by querying the domain name from the outside internet.

From the outside internet, try a dns query to your dns server:
```
nslookup mydomain.com IP.x.x.x.
```
IP you provide would be the Public IP address of your DNS server.

---

### Post by theluli2 on 2014-10-06
Here is what l am getting 

[EMAIL="ubuadmin@ns1:/etc/bind/zones$"]ubuadmin@ns1:/etc/bind/zones$[/EMAIL] nslookup net-kos.com
Server:         192.168.0.8
Address:        192.168.0.8#53
Name:   net-kos.com
Address: 173.193.105.241

---

### Post by nerdtron on 2014-10-06
Seems about right, your internal dns server answered the query.
Try nslookup from the outside internet.
```
nslookup net-kos.com 172.193.105.241
```

---

### Post by efflandt on 2014-10-07
In order for your domain to work for the public, once you get your DNS working locally and from another computer on the internet specifying your nameserver (like nertron's nslookup example) you need to tell your registrar your nameserver(s).

Currently part of the output of **whois net-kos.com** is:
Name Server: No nameserver
No NameServers Defined.DNSSEC:Unsigned

Normally when you get web hosting, the hosting company does DNS for you and all you have to do is tell your registrar your hosting company's nameservers. If the hosts DNS includes a wildcard A record for *.net-kos.com, then any subdomain like [www.net-kos.com](www.net-kos.com) or even some.long.name.net-kos.com will all resolve to your IP address. Then if you are able to properly configure your own nameserver for name based virtual web hosting, you can use different subdomain names to serve different content. I played around with apache with name based virtual web hosting at home using multiple noip.com subdomains (since I have dynamic IP) about 10 years ago. I only used bind as a caching nameserver and to learn out how to configure local zones for my LAN.

---

### Post by theluli2 on 2014-10-07
Hi Nerdtron

Check the output please

Checked from windows machine
```
C:\>nslookup net-kos.com 172.193.105.241
DNS request timed out.
    timeout was 2 seconds.
Server:  UnKnown
Address:  172.193.105.241
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
*** Request to UnKnown timed-out
```

Hi efflandt

With ' whois net-kos.com ' - l got the same result as you mentioned here 

l don't really know what kind of record use my provider " myorderbox.com " , and with * l don't see, also is not allow me to add as a server starting with ns1

With apache2 a done everything based on ip , based on name , and when l try to access apache site l can accessit in two ways ( one with private ip and second with my public ip ) l don't know why apache is pointed to my public ip ?

Hi nerdtron
This is what l am getting

```
C:\Users\Orik>nslookup net-kos.com 172.193.105.241
DNS request timed out.
    timeout was 2 seconds.
Server:  UnKnown
Address:  172.193.105.241
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
*** Request to UnKnown timed-out
```

Hi Efflandt

l am getting the same output like you mentioned

```
 No NameServers Defined.DNSSEC:Unsigned
URL of the ICANN WHOIS Data Problem Reporting System: 
[http://wdprs.internic.net/](http://wdprs.internic.net/)
```

Question is how to add a DNS include wildcard or A record, because l don't have idea

Here is my output of Bind and apache

Bind

```
[EMAIL="ubuadmin@ns1:~$"]ubuadmin@ns1:~$[/EMAIL] dig @localhost [www.net-kos.com]("http://www.net-kos.com")
; <<>> DiG 9.9.5-3-Ubuntu <<>> @localhost [www.net-kos.com]("http://www.net-kos.com")
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41472
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;[www.net-kos.com](www.net-kos.com).               IN      A
;; ANSWER SECTION:
[www.net-kos.com]("http://www.net-kos.com").        604800  IN      A       173.193.105.241
;; AUTHORITY SECTION:
net-kos.com.            604800  IN      NS      ns1.net-kos.com.
;; ADDITIONAL SECTION:
ns1.net-kos.com.        604800  IN      A       192.168.0.8
;; Query time: 4 msec
;; SERVER: ::1#53(::1)
;; WHEN: Tue Oct 07 15:27:09 CEST 2014
;; MSG SIZE  rcvd: 94

[EMAIL="ubuadmin@ns1:~$"]ubuadmin@ns1:~$[/EMAIL] dig @192.168.0.8 [www.net-kos.com]("http://www.net-kos.com")
; <<>> DiG 9.9.5-3-Ubuntu <<>> @192.168.0.8 [www.net-kos.com]("http://www.net-kos.com")
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 8755
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;[www.net-kos.com](www.net-kos.com).               IN      A
;; ANSWER SECTION:
[www.net-kos.com]("http://www.net-kos.com").        604800  IN      A       173.193.105.241
;; AUTHORITY SECTION:
net-kos.com.            604800  IN      NS      ns1.net-kos.com.
;; ADDITIONAL SECTION:
ns1.net-kos.com.        604800  IN      A       192.168.0.8
;; Query time: 4 msec
;; SERVER: 192.168.0.8#53(192.168.0.8)
;; WHEN: Tue Oct 07 15:27:41 CEST 2014
;; MSG SIZE  rcvd: 94


[EMAIL="ubuadmin@ns1:~$"]ubuadmin@ns1:~$[/EMAIL] dig @localhost ns1.net-kos.com
; <<>> DiG 9.9.5-3-Ubuntu <<>> @localhost ns1.net-kos.com
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52401
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;ns1.net-kos.com.               IN      A
;; ANSWER SECTION:
ns1.net-kos.com.        604800  IN      A       192.168.0.8
;; AUTHORITY SECTION:
net-kos.com.            604800  IN      NS      ns1.net-kos.com.
;; Query time: 3 msec
;; SERVER: ::1#53(::1)
;; WHEN: Tue Oct 07 15:28:27 CEST 2014
;; MSG SIZE  rcvd: 74

Forward Zone


[EMAIL="root@ns1:/etc/bind/zones"]root@ns1:/etc/bind/zones[/EMAIL]# cat fwd.db.net-kos.com
; BIND data file for net-kos.com
;
$TTL 604800
@       IN         SOA      ns1.net-kos.com.      admin.net-kos.com. (
                                 2        ; Serial
                            604800        ; Refresh
                             86400        ; Retry
                            2419200       ; Expire
                            604800 )      ; Negative Cache TTL

;
; Name servers
net-kos.com.         IN     NS      ns1.net-kos.com.
; A record for name servers
ns1                  IN     A       192.168.0.8
; Other A records
@                    IN     A       173.193.105.241
www                  IN     A       173.193.105.241
[www.net-kos.com]("http://www.net-kos.com")      IN     CNAME   net-kos.com

Reverse Zone


[EMAIL="root@ns1:/etc/bind/zones"]root@ns1:/etc/bind/zones[/EMAIL]# cat rev.db.net-kos.com
; BIND reverse data file for local loopback interface
;
$TTL    604800
@      IN       SOA    ns1.net-kos.com. admin.net-kos.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@      IN     NS       ns1.net-kos.com.
8      IN     PTR      ns1.net-kos.com.
1      IN     PTR      ns1.net-kos.com.


 
apache

[EMAIL="root@ns1:/etc/apache2/sites-enabled"]root@ns1:/etc/apache2/sites-enabled[/EMAIL]# cat 001-www.net-kos.com 
<VirtualHost 192.168.0.8:80>
        ServerAdmin [EMAIL="admin@net-kos.com"]admin@net-kos.com[/EMAIL]
        ServerName ns1.net-kos.com
        ServerAlias [www.net-kos.com]("http://www.net-kos.com")
        <Directory />
              Options FollowSymLinks
              AllowOverride None
        </Directory>
        <Directory /home/www.net-kos.com/www/>
               Options Indexes FollowSymLinks MultiViews
               AllowOverride None
               Order allow,deny
               Allow from all
         </Directory>
        ErrorLog ${APACHE_LOG_DIR}/home/www.net-kos.com/www/logs/error.log
        CustomLog ${APACHE_LOG_DIR}/home/www.net-kos.com/www/logs/access.log combined
</VirtualHost>
# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

---

### Post by lisati on 2014-10-07
*Thread moved to **Server Platforms**.*

---

### Post by Michael_McKenney on 2014-10-07
nslookup net-kos.com 172.193.105.241

172 address range is class B internal.  Are you trying to access this web site from the internet?  Where is the server and where are you attempting to access it from?  

If on the internet and its an internal NAT address, you need to port forward your router or firewall and use the WAN address.

---

### Post by nerdtron on 2014-10-07
> 172 address range is class B internal
172.16.x.x is the internal class B address. His IP  172.193.105.241 is a public IP.

Two things we need to correct here first before the website forwarding etc.

1. You should have port forwarding on your router for port 53 (DNS) pointing to your internal DNS IP.
2. You're Registrar (for example Godaddy) should be aware that you are going to use your own DNS server instead of theirs. So on your domain configuration (on the registrar) you should declare the Name Server pointing to your public IP address.

---

### Post by theluli2 on 2014-10-08
sorry l meant to write 173.193.105.241 - and this IP belongs to my domain
Internal IP is 192.168.0.8 ( LAN )
My external IP is 91.187.x.x

l have forward port 53 to my LAN IP 192.168.0.8 and is showing that is open 

2. You're Registrar (for example Godaddy) should be aware that you are going to use your own DNS server instead of theirs. So on your domain configuration (on the registrar) you should declare the Name Server pointing to your public IP address.

l will check with my Registrar , when you that declare the Name Server pointing to your my public IP add ? ----> did you mean to 91.187.x.x ?

---

### Post by nerdtron on 2014-10-08
Yes, put your public IP to the Name Servers of your domain in the registrar's record.

---

### Post by theluli2 on 2014-10-09
Hi nerdtron

l just talk with domain registrat , and the told me that l can put under child name servers, l just put it ns1.net-kos.com ip 91.187 and ns2.net-kos.com the same ip , and nothing happen 

can you advise me how to add A and CNAME record please ?

and see if l am missing something on apache please ?!

---

### Post by nerdtron on 2014-10-09
> can you advise me how to add A and CNAME record please ?

and see if l am missing something on apache please ?!

First task here, even without your website, is to make your domain and dns server resolve on the public internet.

You shouldn't add (or rather you won't be able to add) A and CNAME records on the registrar if you use you own dns server (because your own dns server will handle the A and CNAME records). 
If your domain name is net-kos.com, then you public IP 91.187.x.x should show up as a DNS server on my dig command. Right now I think you are still using the registrars DNS servers.

```
[kenneth@nerdtron ~]$ dig ns net-kos.com

; <<>> DiG 9.8.2rc1-RedHat-9.8.2-0.10.rc1.el6 <<>> ns net-kos.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26528
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 16

;; QUESTION SECTION:
;net-kos.com.            IN    NS

;; ANSWER SECTION:
net-kos.com.        172793    IN    NS    info288009.venus.orderbox-dns.com.
net-kos.com.        172793    IN    NS    info288009.mercury.orderbox-dns.com.
net-kos.com.        172793    IN    NS    info288009.mars.orderbox-dns.com.
net-kos.com.        172793    IN    NS    info288009.earth.orderbox-dns.com.

;; ADDITIONAL SECTION:
info288009.venus.orderbox-dns.com. 172793 IN A    50.23.75.44
info288009.venus.orderbox-dns.com. 172793 IN A    50.23.75.45
info288009.venus.orderbox-dns.com. 172793 IN A    50.23.75.96
info288009.venus.orderbox-dns.com. 172793 IN A    50.23.75.97
info288009.mercury.orderbox-dns.com. 172793 IN A 50.23.136.173
info288009.mercury.orderbox-dns.com. 172793 IN A 50.23.136.174
info288009.mercury.orderbox-dns.com. 172793 IN A 50.23.136.229
info288009.mercury.orderbox-dns.com. 172793 IN A 50.23.136.230
info288009.mars.orderbox-dns.com. 172793 IN A    184.173.149.221
info288009.mars.orderbox-dns.com. 172793 IN A    184.173.149.222
info288009.mars.orderbox-dns.com. 172793 IN A    184.173.150.57
info288009.mars.orderbox-dns.com. 172793 IN A    184.173.150.58
info288009.earth.orderbox-dns.com. 172793 IN A    67.15.253.219
info288009.earth.orderbox-dns.com. 172793 IN A    67.15.253.220
info288009.earth.orderbox-dns.com. 172793 IN A    67.15.47.188
info288009.earth.orderbox-dns.com. 172793 IN A    67.15.47.189

;; Query time: 2 msec
;; SERVER: 10.10.210.10#53(10.10.210.10)
;; WHEN: Thu Oct  9 09:01:53 2014
;; MSG SIZE  rcvd: 423


```

I don't see your own DNS server on the WHOIS record either.
```
whois net-kos.com
...
...
Tech State/Province: Kosova
Tech Postal Code: 60000
Tech Country: AL
Tech Phone: +355.44603471
Tech Phone Ext: 
Tech Fax: 
Tech Fax Ext: 
Tech Email: lulzimveliu@gmail.com
[B]Name Server: info288009.earth.orderbox-dns.com
Name Server: info288009.mars.orderbox-dns.com
Name Server: info288009.mercury.orderbox-dns.com
Name Server: info288009.venus.orderbox-dns.com[/B]
DNSSEC:Unsigned
URL of the ICANN WHOIS Data Problem Reporting System: 
http://wdprs.internic.net/
>>>Last update of WHOIS database: 2014-10-09T16:07:48+0000Z<<<


```

---

### Post by theluli2 on 2014-10-09
Hi Nerdtron

Check now with whois 

l changed from ns1 to ns, because registers does not except ns1

but with dig ns net-kos.com stile getting the same

---

### Post by Doug S on 2014-10-09
For me, it will be another ~8 hours before the master reference is re-checked.```
doug@doug-64:~$ [COLOR=#ff0000]dig net-kos.com[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> net-kos.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48072
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 0

;; QUESTION SECTION:
;net-kos.com.                   IN      A

;; ANSWER SECTION:
net-kos.com.            [COLOR=#ff0000]28473[/COLOR]   IN      A       173.193.105.241

;; AUTHORITY SECTION:
net-kos.com.            162860  IN      NS      info288009.mercury.orderbox-dns.com.
net-kos.com.            162860  IN      NS      info288009.venus.orderbox-dns.com.
net-kos.com.            162860  IN      NS      info288009.mars.orderbox-dns.com.
net-kos.com.            162860  IN      NS      info288009.earth.orderbox-dns.com.

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Thu Oct  9 11:27:29 2014
;; MSG SIZE  rcvd: 183
```

---

### Post by theluli2 on 2014-10-10
Thanks Doug S
Now l got this :

~$ dig net-kos.com
; <<>> DiG 9.8.4-rpz2+rl005.12-P1 <<>> net-kos.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33390
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
;; QUESTION SECTION:
;net-kos.com.                   IN      A
;; ANSWER SECTION:
net-kos.com.            598887  IN      A       173.193.105.241
;; AUTHORITY SECTION:
net-kos.com.            166832  IN      NS      ns.net-kos.com.
;; ADDITIONAL SECTION:
ns.net-kos.com.         166832  IN      A       91.187.124.35
;; Query time: 230 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Fri Oct 10 11:57:18 2014
;; MSG SIZE  rcvd: 78



~$ dig ns net-kos.com
; <<>> DiG 9.8.4-rpz2+rl005.12-P1 <<>> ns net-kos.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2288
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
;; QUESTION SECTION:
;net-kos.com.                   IN      NS
;; ANSWER SECTION:
net-kos.com.            166763  IN      NS      ns.net-kos.com.
;; ADDITIONAL SECTION:
ns.net-kos.com.         166763  IN      A       91.187.124.35
;; Query time: 225 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Fri Oct 10 11:58:26 2014
;; MSG SIZE  rcvd: 62

Does this mean that now bind is working ?

l don't see that anything is coming to my site , stile the same error
Thanks to all for support

---

### Post by Doug S on 2014-10-10
From the outside world, nothing has changed.```
doug@doug-64:~$ [COLOR=#ff0000]dig net-kos.com[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> net-kos.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24885
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 0

;; QUESTION SECTION:
;net-kos.com.                   IN      A

;; ANSWER SECTION:
[COLOR=#ff0000]net-kos.com.            38260   IN      A       173.193.105.241[/COLOR]

;; AUTHORITY SECTION:
net-kos.com.            38330   IN      NS      info288009.mercury.orderbox-dns.com.
net-kos.com.            38330   IN      NS      info288009.mars.orderbox-dns.com.
net-kos.com.            38330   IN      NS      info288009.earth.orderbox-dns.com.
net-kos.com.            38330   IN      NS      info288009.venus.orderbox-dns.com.

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Oct 10 08:08:40 2014
;; MSG SIZE  rcvd: 183

doug@doug-64:~$ [COLOR=#ff0000]nslookup net-kos.com[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
[COLOR=#ff0000]Name:   net-kos.com
Address: 173.193.105.241[/COLOR]
```also, if I try to force your server it doesn't work.```
doug@doug-64:~$ [COLOR=#ff0000]nslookup net-kos.com  91.187.124.35[/COLOR]
;; [COLOR=#ff0000]connection timed out; no servers could be reached[/COLOR]

doug@doug-64:~$ [COLOR=#ff0000]nslookup[/COLOR]
> server 91.187.124.35
Default server: 91.187.124.35
Address: 91.187.124.35#53
> [COLOR=#ff0000]net-kos.com[/COLOR]
;; [COLOR=#ff0000]connection timed out; no servers could be reached[/COLOR]
> exit
```

---

### Post by Michael_McKenney on 2014-10-10
On GoDaddy, I have SCSIraidGURU.com and MichaelMcKenney.com setup as my domain names.  Under them, www has the IP address of my Dlink Router at home.   

```

V:\>nslookup mars.orderbox-dns.com
Server:  dc6.americorpusa.loc
Address:  192.168.20.203Non-authoritative answer:
Name:    mars.orderbox-dns.com
Addresses:  184.173.150.58
          184.173.150.57
          184.173.149.221
          184.173.149.222

V:\>nslookup earth.orderbox-dns.com
Server:  dc6.americorpusa.loc
Address:  192.168.20.203
Non-authoritative answer:
Name:    earth.orderbox-dns.com
Addresses:  67.15.253.220
          67.15.253.219
          67.15.47.189
          67.15.47.188

V:\>nslookup venus.orderbox-dns.com
Server:  dc6.americorpusa.loc
Address:  192.168.20.203
Non-authoritative answer:
Name:    venus.orderbox-dns.com
Addresses:  50.23.75.96
          50.23.75.45
          50.23.75.44
          50.23.75.97

V:\>nslookup mercury.orderbox-dns.com
Server:  dc6.americorpusa.loc
Address:  192.168.20.203
Non-authoritative answer:
Name:    mercury.orderbox-dns.com
Addresses:  50.23.136.230
          50.23.136.174
          50.23.136.173
          50.23.136.229

V:\>

```

Why do you have four separate servers for each FDQN name?   You need a unique registered IP address for each web site.

---

### Post by theluli2 on 2014-10-10
hi guys


Well l will attach my forward and revers zone that's all l can do , because really l don't understand any more whats wrong


fwd zone


 $TTL 604800
@       IN         SOA      ns.net-kos.com.      admin.net-kos.com. (
                            2014100901    ; Serial
                            604800        ; Refresh
                             86400        ; Retry
                            2419200       ; Expire
                            604800 )      ; Negative Cache TTL

;
net-kos.com.        IN     NS      ns.net-kos.com.
ns                  IN     A       192.168.0.8
@                   IN     A       173.193.105.241
www                 IN     A       173.193.105.241
ftp                 IN     CNAME   ns.net-kos.com.

rev zone
$TTL    604800
@      IN       SOA    ns.net-kos.com. admin.net-kos.com. (
                          2014100901    ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;

       IN      NS      ns.net-kos.com.
1      IN      PTR     ns.net-kos.com.
2      IN      PTR     [www.net-kos.com]("http://www.net-kos.com").

why l do have four separate server for each FDQN , this is from registrar, l deleted them , and put my ns , but stile appearing

---

### Post by Michael_McKenney on 2014-10-10
What are the four IP addresses for your four sites?   Do you have four A records with FDQN names that match on your registrar's DNS servers?  Do those four IP addresses match the IP of the each Apache servers?

---

### Post by theluli2 on 2014-10-10
l don't know l guess those are dns provided by registrar, l deleted them from registrar, and l have put my dns ns.net-kos.com and l have only IP that belongs to my domain and that is 173.193.105.241

---

### Post by Doug S on 2014-10-10
> **theluli2 said:**
> l deleted them from registrar, and l have put my dns ns.net-kos.com and l have only IP that belongs to my domain and that is 173.193.105.241I am confused. I thought you said your external IP address was 91.187.124.35, so I assumed you now wanted net-kos.com to resolve to that address.

Going back to your earlier posts, you can learn about and play with bind, but you don't have to do it for the WAN. My bind DNS is for internal use only, and I left my external DNS as it was.

Edit 1:
By the way, there seems to be a web site at 91.187.124.35 with the 14.04 default web page.
However, 173.193.105.241 access is forbidden due to being on [some block list]("http://www.spamhaus.org/dbl/") (something I have never seen before).

Edit 2:
I am not following or understanding the 4 FQDNs discussion.

---

### Post by Michael_McKenney on 2014-10-10
Doug, I agree.  He went from 16 IP addresses on registrar records to one address.   I run a corporate data center with 30+ web sites and web applications.  It requires registered IP subnets.  You can't use NAT on the servers.   My ISP assigned us several IP blocks that are registered to them provided to us.

/30 blocks for WAN side and our side of the router going to T1 and Metro Ethernet connections
/27 block for web sites in DMZ etc. (30 addresses)
/26 block for web sites, Exchange etc.  (62 addresses)

I don't count the network and broadcast addresses on subnets.  

I use layer 3 routing switches and Cisco router and firewall to manage and route my addresses.  

You have one IP address on your WAN?  Is this at home or a business?   What do these four web sites do?  Why do you need four web sites?  What are you trying to accomplish?  Are these web sites public (accessible on the internet) or private (only on your network).  Do you have four boxes running these web servers?

---

### Post by theluli2 on 2014-10-10
Ok

After configuring BIND, l have setup also apache, when l try base-name on apache, the only apache default site is going to my WAN IP , as doug S noticed , l can not get default webpage of apache to point to my domain name net-kos.com, in this case if dns resolv ip to names , than l am assuming that there is something wrong with bind ?
And to be honest l don't know where my site should be pointed to my WAN IP which is 91.187.124.35 or to the IP of the domain itself 173.193.105.241 ?

Hi Michael

l have one IP addres of WAN, l am using for personal use only, l wane learn more about hosting a site , and l have purchased only one domain name [www.net-kos.com]("http://www.net-kos.com"), and l have only one server. And yes wane have this site to be accessible on the internet, like normal webpage 

l called the guy and asked him, how l can put my dns-servername on cpanel , he told ,e that need to add at the child name server, l added my nameserver which is ns.net-kos.com
the other dns server that hosting company provided me, l have remove them, that's why l don't know why there are stile there , when we ping my site

---

### Post by Michael_McKenney on 2014-10-10
WAN IP which is 91.187.124.35 or to the IP of the domain itself 173.193.105.241 ?  WAN would be on your router.  What is the 173 address from?

I have an Ubuntu web site at home.   I have two Godaddy domains.   SCSIraidGURU.com and MichaelMcKenney.com.   The child is *.domain.com.  www is the child like ftp would be.   www points to my router WAN address that is assigned by the ISP.   Godaddy does registrat and dns for me.  

```


V:\>nslookup [www.scsiraidguru.com]("http://www.scsiraidguru.com")
Server:  dc6.americorpusa.loc
Address:  192.168.20.203
Non-authoritative answer:
Name:    [www.scsiraidguru.com]("http://www.scsiraidguru.com")
Address:  67.149.165.164

In Godaddy, my www address is 67.149.165.164.   

It is the same under the separate domain name MichaelMcKenney.com

my www address is 67.149.165.164.  


```

The DNS A record is [www.scsiraidguru.com]("http://www.scsiraidguru.com") 67.149.165.164
The DNS A record is [www.michaelmckenney.com]("http://www.michaelmckenney.com") 67.149.165.164

DNS takes up to 96 hours to change across the internet due to TTL (time to live) rules.  Change your hosts file in /etc to the new WAN address for testing.   

sudo gedit /etc/hosts  will access it.  no dot after hosts in Linux.  Windows has a hosts.

My hosts file would look like this.  

67.149.165.164    [www.scsiraidguru.com]("http://www.scsiraidguru.com")
67.149.165.164    [www.michaelmckenney.com]("http://www.michaelmckenney.com/")

You can also add the internal addresses for all your boxes to hosts of each computer.  

This will test your routing and port forwarding rules along with is your firewall open for port 80 and 443 traffic.  

If I paid $10 a month, I could get a registered WAN address that never changes.   Since I don't, when WOW! changes my WAN address, I have to update it on GoDaddy.com and in the DNS page also.  About every 5 years or so.  Not often.  

Next step on your router is port forward 80 and 443 to the NAT (LAN address) address of your web box.  

WAN is external, on home routers you have one.  WAN IP which is 91.187.124.35 
LAN addresses are internal and NAT network address translation.   

UFW or GUFW make sure port 80 and 443 are open for traffic.  This is the Ubuntu firewall.   When you install a web server, check your firewall for the inbound ports.  These are the firewalls I use.  I also have rules to allow the other two workstations to fully access each other in the firewalls. 

I would have to look up how I did Apache for my web sites.  I don't remember it took about 2 hours in Ubuntu to configure the first time.  I did a bunch of conf files.   I found a few google pages on Ubuntu Apache setup.  First time took longer because I just started with Ubuntu.  

I would not use planet names for your first web site.  Just www.  

You purchased domain net-kos.com.  So your first web site should be [www.net-kos.com]("http://www.net-kos.com").   www would be 91.187.124.35, the WAN address of your router.   Your A record would be under net-kos.com,  www 91.187.124.35.  Your reverse DNS record would be 35.124.187.in-appr.arpa with a pointer record 91.187.124.35 and name [www.net-kos.com]("http://www.net-kos.com").   At least on my Windows AD DNS servers.  I have not looked at my Godaddy DNS in years.

---

### Post by Doug S on 2014-10-10
> **theluli2 said:**
> And to be honest l don't know where my site should be pointed to my WAN IP which is 91.187.124.35 or to the IP of the domain itself 173.193.105.241 ?As far as I can tell 173.193.105.241 has nothing to do with you or your domain name or this thread. You should delete any reference to it from everywhere.
As far as I can tell you want the IP of the domain itself to be 91.187.124.35, and so that is it what you should be using everywhere.> **theluli2 said:**
> l called the guy and asked him, how l can put my dns-servername on cpanel , he told ,e that need to add at the child name server, l added my nameserver which is ns.net-kos.comHow would that place know where "ns.net-kos.com" is? You have to point the registrar entry somehow to 91.187.124.35.

Oh, and by the way, 91.187.124.35 does not appear to accessible from the WAN as a DNS.

---

### Post by Michael_McKenney on 2014-10-10
Doug, you are right the ns.net-kos.com does not exist for him.  He needs to use the registrar's DNS for entries like I do with Godaddy.  Your internal DNS is only for your computers to use like the hosts file.  You don't want to try to setup your own name server.   NS servers should be either your ISP or registrar.   

At work, my ISP Shutternet handles NS and DNS.  At home, Godaddy handles my NS and DNS.

---

### Post by Doug S on 2014-10-10
> **Michael_McKenney said:**
> I would not use planet names for your first web site.  Just www.Michael, I am just trying to understand here. I also haven't understood the references to 4 FQDNs. Those planet related domain names are just name servers, and not related at all to the original poster (theluli2) (well other than they are currently the SOA) aren't they? Example:```
doug@doug-64:~/tcpdump/072$ [COLOR=#ff0000]dig @info288009.mercury.orderbox-dns.com -t any net-kos.com[/COLOR]

; <<>> DiG 9.8.1-P1 <<>> @info288009.mercury.orderbox-dns.com -t any net-kos.com
; (4 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53253
;; flags: qr aa rd; QUERY: 1, ANSWER: 10, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;net-kos.com.                   IN      ANY

;; ANSWER SECTION:
net-kos.com.            38400   IN      NS      info288009.earth.orderbox-dns.com.
net-kos.com.            38400   IN      NS      info288009.mercury.orderbox-dns.com.
net-kos.com.            38400   IN      NS      info288009.venus.orderbox-dns.com.
net-kos.com.            38400   IN      TXT     "v=spf1 redirect=_spf.mailhostbox.com"
net-kos.com.            38400   IN      NS      info288009.mars.orderbox-dns.com.
net-kos.com.            38400   IN      MX      100 us2.mx1.mailhostbox.com.
net-kos.com.            38400   IN      MX      100 us2.mx3.mailhostbox.com.
net-kos.com.            38400   IN      MX      100 us2.mx2.mailhostbox.com.
[COLOR=#ff0000]net-kos.com.            7200    IN      SOA     info288009.mercury.orderbox-dns.com. lulzimveliu.gmail.com. 2014101001 7200 7200 172800 38400[/COLOR]
net-kos.com.            38400   IN      A       173.193.105.241

;; Query time: 36 msec
;; SERVER: 50.23.136.173#53(50.23.136.173)
;; WHEN: Fri Oct 10 14:46:04 2014
;; MSG SIZE  rcvd: 370
```

---

### Post by Michael_McKenney on 2014-10-10
He is trying to understand how to do a web site.  I think having four web sites at home will be confusing to start.  So make it simple and just do the standard www.  You can't have four web sites tied to one IP address on public A records.   You are allowed one web site per IP address or you run into issue.  He is trying to learn how to setup Apache web services.

---

### Post by Doug S on 2014-10-11
> **Michael_McKenney said:**
> He is trying to understand how to do a web site.Yes, but this thread is about name lookups. > **Michael_McKenney said:**
>  I think having four web sites at home will be confusing to start.  So make it simple and just do the standard www.???? There hasn't been anything about 4 web sites in this thread. > **Michael_McKenney said:**
> You can't have four web sites tied to one IP address on public A records.Yes, you can.

---

### Post by theluli2 on 2014-10-11
Hi guys the issue was here how to handle BIND/DNS by my own server , and than normally to learn more about dns not only locally also externally
Than creating website with wordpress with apache , and have fun !

Since l am new to BIND/DNS , l thought that the problem exist on DNS , but a guest that the problem exist on registrar 

Yesterday l spoke with one of my friend , and l  we cam up with the solution of the problem, l can not host dns and website from this domain provider unless they change something that l request , knowing that they are very lazy 

l can not setup Glue Record on my cpanel, l have to find some other domain providers !

Glue records are required when you wish to set the name servers of a
> domain name to a hostname under the domain name itself.
>
> For example if you wished to set the name servers of example.com to
> ns1.example.com and ns2.example.com you would need to also provide the
> glue records (i.e. the IP addresses) for ns1.example.com and
> ns2.example.com.
>
> If you did not provide the glue records for these name servers then
> your domain name would not work as anyone requiring DNS information
> for it would get stuck in a loop:
>
> What is the name server for example.com? -> ns1.example.com
> What is the IP address of ns1.example.com? -> don't know, try looking
> at name server for example.com
> What is the name server for example.com? -> ns1.example.com
>
> ...and so on.
>
> With the glue record in place the registry will hold the IP address
> and the loop will not occur:

At list l think this is the problem that why l can not host dns on my own server 

One last question , for transferring my domain name to other domain providers, do they charge me ?

---

### Post by Michael_McKenney on 2014-10-12
You are better off letting the registrar of your domain handle DNS.   Use their name servers for your web sites.   You can cause problem if you screw up on your name server.  You don't need to recreate the wheel.  I let Godaddy do it for me.  I can add my entries on my domain page.  In my data center, my ISP handles the external name servers.

---

