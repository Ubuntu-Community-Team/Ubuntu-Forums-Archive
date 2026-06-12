---
title: "Can not get Bind9 recursive to work"
date: 2011-04-11
forum: Server Platforms
---

### Post by Nattereri on 2011-04-11
I have googled for hours and can not find an answer to what this means.
 
dig @172.16.255.254 twitter.com.
; <<>> DiG 9.7.0-P1 <<>> @172.16.255.254 twitter.com.
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 53764
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;twitter.com.                   IN      A
;; Query time: 333 msec
;; SERVER: 172.16.255.254#53(172.16.255.254)
;; WHEN: Mon Apr 11 21:48:38 2011
;; MSG SIZE  rcvd: 29
 
dig @172.16.255.254 +trace ubuntu.com
; <<>> DiG 9.7.0-P1 <<>> @172.16.255.254 +trace ubuntu.com
; (1 server found)
;; global options: +cmd
.                       3600000 IN      NS      C.ROOT-SERVERS.NET.
.                       3600000 IN      NS      A.ROOT-SERVERS.NET.
.                       3600000 IN      NS      J.ROOT-SERVERS.NET.
.                       3600000 IN      NS      L.ROOT-SERVERS.NET.
.                       3600000 IN      NS      D.ROOT-SERVERS.NET.
.                       3600000 IN      NS      G.ROOT-SERVERS.NET.
.                       3600000 IN      NS      H.ROOT-SERVERS.NET.
.                       3600000 IN      NS      K.ROOT-SERVERS.NET.
.                       3600000 IN      NS      F.ROOT-SERVERS.NET.
.                       3600000 IN      NS      M.ROOT-SERVERS.NET.
.                       3600000 IN      NS      B.ROOT-SERVERS.NET.
.                       3600000 IN      NS      E.ROOT-SERVERS.NET.
.                       3600000 IN      NS      I.ROOT-SERVERS.NET.
;; Received 228 bytes from 172.16.255.254#53(172.16.255.254) in 2 ms
ubuntu.com.             86      IN      A       91.189.94.156
ubuntu.com.             102589  IN      NS      ns2.canonical.com.
ubuntu.com.             102589  IN      NS      ns3.canonical.com.
ubuntu.com.             102589  IN      NS      ns1.canonical.com.
;; Received 156 bytes from 199.7.83.42#53(L.ROOT-SERVERS.NET) in 180 ms


My named.conf.options file looks like this:
 
// Access control lists
acl localsubnets { 192.168.0.0/24; 172.16.0.0/16; localhost; };
options {
        directory "/var/cache/bind";
 
        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)
 
        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.
 
        // forwarders {
        //      0.0.0.0;
        // };
 
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
 
        // Custom Cobitis Options
        // This is a internet cahcing only server configuration.
        // Only the local subnets are allowed to query the server.
 
        // Version statement inhibitied for security reasons.
        version "The name is Bind, James Bind.";
 
        // Disable all zone transfer request.
        allow-transfer { "none"; };
 
        // Restrict queires to local subnets.
        allow-query { localsubnets; };
 
        // To make it work we must add the allow statements.
        allow-recursion-on { localsubnets; };
        allow-recursion { localsubnets; };
};
// Logging
logging {
        channel default_channel {
                file "/var/cache/bind/bind.log";
                severity debug 3;
                print-severity yes;
                print-time yes;
                print-category yes;
        };
        category default {
                default_channel;
        };
};

And I have a very long debuging log file I will not post unless requested.
 
I also have added a ufw allow from all to all rule for testing purposes only. Any advice on where to begin solving this problem would be appreciated.

---

### Post by Nattereri on 2011-04-15
Must not be bind according to this.
 
james@ITDGATEWAY001UL:~$ sudo tcpdump -i ppp0 port 53 > ~/tcpdump.dns &
[1] 4862
[EMAIL="james@ITDGATEWAY001UL:~$"]james@ITDGATEWAY001UL:~$[/EMAIL] tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ppp0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
 
james@ITDGATEWAY001UL:~$ dig apple.com
; <<>> DiG 9.7.0-P1 <<>> apple.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 18541
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;apple.com. IN A
;; Query time: 839 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Apr 15 14:08:44 2011
;; MSG SIZE rcvd: 27
 
james@ITDGATEWAY001UL:~$ jobs
[1]+ Running sudo tcpdump -i ppp0 port 53 > ~/tcpdump.dns &
james@ITDGATEWAY001UL:~$ fg
sudo tcpdump -i ppp0 port 53 > ~/tcpdump.dns
^C4 packets captured
112 packets received by filter
0 packets dropped by kernel
 
james@ITDGATEWAY001UL:~$ cat tcpdump.dns
14:08:44.094659 IP 72.59.234.251.4510 > 192.5.6.30.domain: 44853 [1au] A? apple.com. (38)
14:08:44.098999 IP 72.59.234.251.8303 > 192.26.92.31.domain: 50360 [1au] PTR? 30.6.5.192.in-addr.arpa. (52)
14:08:44.264299 IP 192.5.6.30.domain > 72.59.234.251.4510: 44853 2/6/7 A 17.172.224.27, (311)
14:08:44.267007 IP 72.59.234.251.icpv2 > 17.254.0.59.domain: 59645 [1au] A? apple.com. (38)

---

### Post by Nattereri on 2011-04-18
I have read about Sprint doing a 'transparent proxy' for DNS request to their own DNS servers. My problem seems to be the same one as in this post [https://lists.isc.org/pipermail/bind-users/2010-April/079602.html](https://lists.isc.org/pipermail/bind-users/2010-April/079602.html)
 
I get the same kind of errors in my bind log.
 
Bind log:
18-Apr-2011 08:16:20.457 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): query
18-Apr-2011 08:16:20.457 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): send
18-Apr-2011 08:16:20.458 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): sent
18-Apr-2011 08:16:20.458 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): udpconnected
18-Apr-2011 08:16:20.458 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): senddone
18-Apr-2011 08:16:20.569 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): response
18-Apr-2011 08:16:20.569 lame server resolving 'E.ROOT-SERVERS.NET' (in 'ROOT-SERVERS.net'?): 192.33.4.12#53
18-Apr-2011 08:16:20.569 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): cancelquery
18-Apr-2011 08:16:20.569 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): add_bad
18-Apr-2011 08:16:20.569 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): try
18-Apr-2011 08:16:20.569 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): cancelqueries
18-Apr-2011 08:16:20.569 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): getaddresses
18-Apr-2011 08:16:20.570 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): query
18-Apr-2011 08:16:20.570 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): send
18-Apr-2011 08:16:20.570 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): sent
18-Apr-2011 08:16:20.570 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): udpconnected
18-Apr-2011 08:16:20.570 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): senddone
18-Apr-2011 08:16:20.673 resquery 0xb5a25008 (fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA)): response
18-Apr-2011 08:16:20.673 lame server resolving 'E.ROOT-SERVERS.NET' (in 'ROOT-SERVERS.net'?): 128.8.10.90#53
18-Apr-2011 08:16:20.673 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): cancelquery
18-Apr-2011 08:16:20.673 fctx 0xb5a1e008(E.ROOT-SERVERS.NET/AAAA'): add_bad
 
Dig output (shortened):
Sprint's DNS:
; <<>> DiG 9.7.0-P1 <<>> @68.28.122.93 ibm.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60943
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4
 
Root DNS:
; <<>> DiG 9.7.0-P1 <<>> @192.228.79.201 ibm.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13672
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4

---

### Post by elico on 2011-04-18
im waiting for your reply on the firewall rule-set that i gave you to try.
by the way did you notice the IPV6 reply?
you should try:
> dig @198.41.0.4 google.com
or
> nslookup - 198.41.0.4
on the command prompt enter
[COLOR=#000000][FONT=tahoma]set type=ns
.
as like:
[/FONT][/COLOR]> > set type=ns
> .

if you dont understand try to look at this page:
[http://www.fir3net.com/General-Info/General-Info/dns-nslookup-how-to-find-the-root-servers.html](http://www.fir3net.com/General-Info/General-Info/dns-nslookup-how-to-find-the-root-servers.html)

---

### Post by Vegan on 2011-04-18
I have BIND9 installed but I have it setup for forwards to my ISP and only use BIND9 for subdomains that are under my registered domains.

I suggest this as the best setup as this assures safe operation.

---

### Post by Nattereri on 2011-04-19
I get two diffferent outputs from nslookup when executed on two different ISP networks. Could this be because my ISP is redirecting DNS request to their caching servers? Or to put it another way which one is the proper response for the query?
 
nslookup output when executed on the local host:
 
nslookup ibm.com 198.41.0.4
Server:         198.41.0.4
Address:        198.41.0.4#53
Non-authoritative answer:
Name:   ibm.com
Address: 129.42.38.1
 
nslookup output when executed on vps host on hosting providers network:
 
nslookup ibm.com 198.41.0.4

in-addr.arpa    nameserver = a.in-addr-servers.arpa
in-addr.arpa    nameserver = b.in-addr-servers.arpa
in-addr.arpa    nameserver = c.in-addr-servers.arpa
in-addr.arpa    nameserver = d.in-addr-servers.arpa
in-addr.arpa    nameserver = e.in-addr-servers.arpa
in-addr.arpa    nameserver = f.in-addr-servers.arpa
a.in-addr-servers.arpa  AAAA IPv6 address = 2001:500:13::73
a.in-addr-servers.arpa  internet address = 199.212.0.73
b.in-addr-servers.arpa  AAAA IPv6 address = 2001:500:87::87
b.in-addr-servers.arpa  internet address = 199.253.183.183
c.in-addr-servers.arpa  AAAA IPv6 address = 2001:43f8:110::10
c.in-addr-servers.arpa  internet address = 196.216.169.10
d.in-addr-servers.arpa  AAAA IPv6 address = 2001:13c7:7010::53
d.in-addr-servers.arpa  internet address = 200.10.60.53
e.in-addr-servers.arpa  AAAA IPv6 address = 2001:dd8:6::101
e.in-addr-servers.arpa  internet address = 203.119.86.101
f.in-addr-servers.arpa  AAAA IPv6 address = 2001:67c:e0::1
f.in-addr-servers.arpa  internet address = 193.0.9.1
*** Can't find server name for address 198.41.0.4: No information
Server:  UnKnown
Address:  198.41.0.4
Name:    ibm.com
Served by:
- a.gtld-servers.net
          192.5.6.30
          com
- b.gtld-servers.net
          192.33.14.30
          com
- c.gtld-servers.net
          192.26.92.30
          com
- d.gtld-servers.net
          192.31.80.30
          com
- e.gtld-servers.net
          192.12.94.30
          com
- f.gtld-servers.net
          192.35.51.30
          com
- g.gtld-servers.net
          192.42.93.30
          com
- h.gtld-servers.net
          192.54.112.30
          com
- i.gtld-servers.net
          192.43.172.30
          com
- j.gtld-servers.net
          192.48.79.30
          com

---

### Post by Nattereri on 2011-04-20
After more testing and some reading on how to trace recursive lookups, I have come to the conclusion that my ISP is redirecting DNS request. I can not get any authoritative responses from the actual servers that host the domains I traced. I will have to go with Vegan's strategy seeing as we have only one ISP here. At least I learned how the whole root server system works.

---

