---
title: "Problem with BIND9"
date: 2007-02-01
forum: Server Platforms
---

### Post by MAO on 2007-02-01
**/etc/hosts**

127.0.0.1       localhost       localhost
217.29.22.205   kadamjai.software.kg    kadamjai

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
_______________________________________________
**/etc/hostname**

kadamjai.software.kg
_______________________________________________
**/etc/bind/named.conf.options**

options {
        directory "/var/cache/bind";
forwarders {
        217.29.16.250;
        217.29.16.249;
};

        auth-nxdomain no;    # conform to RFC1035
        allow-recursion { localnets; };
______________________________________________
**/etc/bind/named.conf.local**

zone "software.kg" {
        type master;
        file "/etc/bind/zones/software.kg.db";
};

zone "22.29.217.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.22.29.217.in-addr.arpa";
};
_______________________________________________
**/etc/bind/zones/software.kg.db**

$ORIGIN software.kg.
$TTL    604800
@       IN      SOA     kadamjai.software.kg. admin.software.kg. (
        2007310111              ; Serial
        604800          ; Refresh
        86400           ; Retry
        2419200         ; Expire
        604800 )        ; Negative Cache TTL
;
software.kg.    IN      NS      software.kg.
software.kg.    IN      NS      kadamjai.software.kg.
software.kg.    IN      MX      10      mail.software.kg.

www     IN      A       217.29.22.205
mail    IN      A       217.29.22.205
kadamjai        IN      A       217.29.22.205
localhost       IN      A       127.0.0.1

@       IN      TXT     "SOFTWARE LTD."
_______________________________________________
**/etc/bind/zones/rev.22.29.217.in-addr.arpa**            

$ORIGIN 22.29.217.in-addr.arpa.
$TTL    604800
@       IN      SOA     kadamjai.software.kg.   admin.software.kg. (
        2007310111
        28800
        604800
        604800
        86400
)

        IN      NS      kadamjai.software.kg.
205     IN      PTR     software.kg.
206     IN      PTR     mail.software.kg.


This My Settings !!!

And I Have this:

root@kadamjai:/# **dig software.kg**

; <<>> DiG 9.3.2 <<>> software.kg
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63955
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;software.kg.                   IN      A

;; AUTHORITY SECTION:
software.kg.            604800  IN      SOA     kadamjai.software.kg. admin.software.kg. 2007310111 604800 86400 2419200 604800

;; Query time: 0 msec
;; SERVER: 217.29.22.205#53(217.29.22.205)
;; WHEN: Thu Feb  1 05:08:34 2007
;; MSG SIZE  rcvd: 80

root@kadamjai:/# 
____________________________________________________________________

root@kadamjai:/# **dig 217.29.22.205**

; <<>> DiG 9.3.2 <<>> 217.29.22.205
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: **[COLOR="Red"][SIZE="4"]NXDOMAIN[/SIZE][/COLOR]**, id: 10682
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;217.29.22.205.                 IN      A

;; AUTHORITY SECTION:
.                       9932    IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2007013101 1800 900 604800 86400

;; Query time: 0 msec
;; SERVER: 217.29.22.205#53(217.29.22.205)
;; WHEN: Thu Feb  1 05:09:02 2007
;; MSG SIZE  rcvd: 106

root@kadamjai:/# 

___________________________________________

ISP Config :
Domain SOFTWARE.KG  (INACTIVE)
Name servers in the listed order:

SOFTWARE.KG       217.29.22.205
NAME2.SAIMANET.KG 217.29.16.250
NAME.SAIMANET.KG  217.29.16.249
___________________________________________
[http://dnsreport.com/tools/dnsreport.ch?domain=software.kg]("http://dnsreport.com/tools/dnsreport.ch?domain=software.kg")
[ERROR: The parent servers say that the domain software.kg does not exist. Note that the DNS Report only works on domains, not hostnames.]

Please Show Me What is Wrong with my Settings ????

---

### Post by DaveArb on 2007-02-01
> ISP Config :
Domain SOFTWARE.KG (**INACTIVE)**

My guess is that the bolded part is an issue. Have you _just_ registered this name? If so, it may not have propagated yet.

From here, infotel.kg (who I assume is responsible for the .kg TLD) says software.kg doesn't exist. I'm not familiar with how .kg is organized, but for .com (roughly speaking) your registrar has to notify the TLD responsible servers to forward name requests to them for a given domain. Then, they can forward the request to where you've designated for actual resolution.

---

### Post by MAO on 2007-02-02
And HOW to corect resive in DNS 
root@kadamjai:/# dig 217.29.22.205

; <<>> DiG 9.3.2 <<>> 217.29.22.205
;; global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 10682
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;217.29.22.205. IN A

;; AUTHORITY SECTION:
. 9932 IN SOA a.root-servers.net. nstld.verisign-grs.com. 2007013101 1800 900 604800 86400

;; Query time: 0 msec
;; SERVER: 217.29.22.205#53(217.29.22.205)
;; WHEN: Thu Feb 1 05:09:02 2007
;; MSG SIZE rcvd: 106

root@kadamjai:/#

What NXDOMAIN means and where in my config i have mistake!?

---

### Post by MAO on 2007-02-05
Domain SOFTWARE.KG (INACTIVE) 

I fix the problem with ISP !!! no Domain ACTIVE, now I need help with some problems:

[http://dnsreport.com/tools/dnsreport.ch?domain=software.kg](http://dnsreport.com/tools/dnsreport.ch?domain=software.kg)

**Reverse DNS entries for MX records**
ERROR: The IP of one or more of your mail server(s) have no reverse DNS (PTR) entries/* (if you see "Timeout" below, it may mean that your DNS servers did not respond fast enough)*/. RFC1912 2.1 says you should have a reverse DNS for all your mail servers. It is strongly urged that you have them, as many mailservers will not accept mail from mailservers with no reverse DNS entry. You can double-check using the 'Reverse DNS Lookup' tool at the DNSstuff site if you recently changed your reverse DNS entry (it contacts your servers in real time; the reverse DNS lookups in the DNS report use our local caching DNS server). The problem MX records are:
205.22.29.217.in-addr.arpa [No reverse DNS entry (rcode: 3 ancount: 0) (check it)]

**Connect to mail servers**
ERROR: I could not complete a connection to any of your mailservers!

kadamjai.software.kg: Timed out [Last data sent: [Did not connect]]

If this is a timeout problem, note that the DNS report only waits about 40 seconds for responses, so your mail *may* work fine in this case but you will need to use testing tools specifically designed for such situations to be certain.

How to Correct IT!!!

---

