---
title: "LAN DNS requests not relayed to tun0"
date: 2012-02-11
forum: Server Platforms
---

### Post by theclem35 on 2012-02-11
Hello!

I've a problem with my hotspot.
I use Chillispot as Captive Portal and Bind9 as DNS on the same server, behind a Wifi router. My WLAN is 192.168.14.0/24 and my router is wired to my eth0 interface.

When I start Chillispot, it creates a tun0 interface (192.168.14.1) and keep my eth0 without IP (it's normal). Chillispot gives correct IP config to my client (by DHCP):
Suffix : wifi.univ-nantes.fr
IP : 192.168.14.2
Gateway : 192.168.14.1
DNS : 192.168.14.1

I restart bind9 to make it listen on new tun0 IP (192.168.14.1).
When I try a dig, all is right :
```
root@TutWifi:~# dig portail1.wifi.univ-nantes.fr @192.168.14.1

; <<>> DiG 9.7.0-P1 <<>> portail1.wifi.univ-nantes.fr @192.168.14.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63708
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;portail1.wifi.univ-nantes.fr.    IN    A

;; ANSWER SECTION:
portail1.wifi.univ-nantes.fr. 604800 IN    A    192.168.14.1

;; AUTHORITY SECTION:
wifi.univ-nantes.fr.    604800    IN    NS    ns.wifi.univ-nantes.fr.

;; ADDITIONAL SECTION:
ns.wifi.univ-nantes.fr.    604800    IN    A    192.168.14.1

;; Query time: 0 msec
;; SERVER: 192.168.15.1#53(192.168.15.1)
;; WHEN: Sat Feb 11 11:47:47 2012
;; MSG SIZE  rcvd: 95
```

Client can successfully ping the DNS (which is the gateway).
**But when he tries to do a nslookup, he have a timeout error.**


_Some issues :_
I config a public DNS2 in chillispot config file.
Client have my 192.168.14.1 as primary and public as secondary.
When I launch Wireshark on tun0 interface, and try a nslookup on my client :
- No request at all for my 192.168.14.1 (but I can see it on eth0)
- I have all requests and responses for my secondary public DNS !! (on tun0 and eth0 for sure)

- If I try to ping my 192.168.14.1, I can see it on tun0, so it seems to be DNS request not relayed.

I've found a temporary solution :
- Create a virtual interface : ifconfig eth0:0 192.168.15.1 netmask 255.255.255.0 up
- Restart bind9 to listen on this new interface
- Add 192.168.15.1 as primary DNS into chilli config file
And now I can see DNS requests on my tun0 interface...

I think this is not a good solution, so I will be very happy if someone can tell me which is the problem !!!

Thank you so much,
Clement

---

### Post by SeijiSensei on 2012-02-12
Do you have the correct IPs specified in the "listen-on" directive in named.conf?

---

### Post by theclem35 on 2012-02-12
Yes, my named.conf.local contains :
```
zone "wifi.univ-nantes.fr" {
 type master;
 file "/etc/bind/db.wifi.univ-nantes.fr";
};
zone "14.168.192.in-addr.arpa" {
 type master;
 notify no;
 file "/etc/bind/db.14.168.192";
};
```

---

### Post by SeijiSensei on 2012-02-12
I'm talking about the "listen-on" directive that is usually in the options{} section at the top of named.conf.  On my DNS server it looks like this:

```
options {
        directory "/var/named";
        listen-on { 127.0.0.1; 192.168.100.100; 10.1.1.20; };
        pid-file "/var/run/named/named.pid";

        [other stuff]
};

```

I have two interfaces on this server besides localhost (127.0.0.1).  One is the 192.168.100.100 address assigned to eth0 on the local machine; the other, 10.1.1.20, is  this machine's end of an OpenVPN tunnel.  All these interfaces, or the keyword "any;" (with the semicolon), must appear in the listen-on directive; BIND will ignore requests sent to any other interfaces.

---

### Post by theclem35 on 2012-02-29
Hello,
 
Sorry for my late answer.
 
Bind9 listen on ANY interfaces.
Problem isn't already solved, I must send an IP of a virtual adapter to my clients which isn't very nice.. :(

---

