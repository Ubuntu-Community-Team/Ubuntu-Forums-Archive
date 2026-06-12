---
title: "Bind9"
date: 2012-10-05
forum: Server Platforms
---

### Post by jaynv0i on 2012-10-05
I have been banging my  head against the wall for the past couple of days, and have not been able to find an answer to this.

I have installed BIND on Ubuntu 12.04.  Since the install, I have made the following changes to the named.conf.options file.


forward only;
        forwarders {
                24.217.0.5;
                24.217.201.67;
         };
        listen-on-v6 { none; };

My ultimate goal is to have this server serve as a DNS host for our company as well as forwarding any requests it cannot answer to the forwarders.  I would also like to continue to use BIND since we will be working on a project with ISC-DHCP in the very near future.

Using dig @127.0.0.1 [www.perl.org](www.perl.org) +trace, I receive the following results.

; <<>> DiG 9.8.1-P1 <<>> @127.0.0.1 [www.perl.org](www.perl.org) +trace
; (1 server found)
;; global options: +cmd
.                       3600000 IN      NS      B.ROOT-SERVERS.NET.
.                       3600000 IN      NS      L.ROOT-SERVERS.NET.
.                       3600000 IN      NS      K.ROOT-SERVERS.NET.
.                       3600000 IN      NS      D.ROOT-SERVERS.NET.
.                       3600000 IN      NS      G.ROOT-SERVERS.NET.
.                       3600000 IN      NS      M.ROOT-SERVERS.NET.
.                       3600000 IN      NS      F.ROOT-SERVERS.NET.
.                       3600000 IN      NS      H.ROOT-SERVERS.NET.
.                       3600000 IN      NS      J.ROOT-SERVERS.NET.
.                       3600000 IN      NS      I.ROOT-SERVERS.NET.
.                       3600000 IN      NS      C.ROOT-SERVERS.NET.
.                       3600000 IN      NS      E.ROOT-SERVERS.NET.
.                       3600000 IN      NS      A.ROOT-SERVERS.NET.
;; Received 228 bytes from 127.0.0.1#53(127.0.0.1) in 86653 ms

org.                    172800  IN      NS      b0.org.afilias-nst.org.
org.                    172800  IN      NS      c0.org.afilias-nst.info.
org.                    172800  IN      NS      b2.org.afilias-nst.org.
org.                    172800  IN      NS      a0.org.afilias-nst.info.
org.                    172800  IN      NS      d0.org.afilias-nst.org.
org.                    172800  IN      NS      a2.org.afilias-nst.info.
;; Received 432 bytes from 192.203.230.10#53(192.203.230.10) in 17397 ms

perl.org.               86400   IN      NS      ns1.eu.bitnames.com.
perl.org.               86400   IN      NS      ns1.us.bitnames.com.
perl.org.               86400   IN      NS      ns1.p20.dynect.net.
perl.org.               86400   IN      NS      ns2.us.bitnames.com.
perl.org.               86400   IN      NS      ns2.p20.dynect.net.
perl.org.               86400   IN      NS      ns2.develooper.com.
;; Received 181 bytes from 199.249.120.1#53(199.249.120.1) in 23716 ms

[www.perl.org](www.perl.org).           300     IN      CNAME   varnish-lb.develooper.com.
;; Received 69 bytes from 208.78.70.20#53(208.78.70.20) in 29 ms

Doing a similar query by using an external DNS server, I see the following.

; <<>> DiG 9.8.1-P1 <<>> @24.217.0.5 [www.postfix.org](www.postfix.org) +trace
; (1 server found)
;; global options: +cmd
.                       384218  IN      NS      e.root-servers.net.
.                       384218  IN      NS      c.root-servers.net.
.                       384218  IN      NS      j.root-servers.net.
.                       384218  IN      NS      m.root-servers.net.
.                       384218  IN      NS      d.root-servers.net.
.                       384218  IN      NS      i.root-servers.net.
.                       384218  IN      NS      a.root-servers.net.
.                       384218  IN      NS      b.root-servers.net.
.                       384218  IN      NS      f.root-servers.net.
.                       384218  IN      NS      k.root-servers.net.
.                       384218  IN      NS      l.root-servers.net.
.                       384218  IN      NS      h.root-servers.net.
.                       384218  IN      NS      g.root-servers.net.
;; Received 512 bytes from 24.217.0.5#53(24.217.0.5) in 14 ms

org.                    172800  IN      NS      a2.org.afilias-nst.info.
org.                    172800  IN      NS      a0.org.afilias-nst.info.
org.                    172800  IN      NS      b0.org.afilias-nst.org.
org.                    172800  IN      NS      d0.org.afilias-nst.org.
org.                    172800  IN      NS      b2.org.afilias-nst.org.
org.                    172800  IN      NS      c0.org.afilias-nst.info.
;; Received 435 bytes from 192.33.4.12#53(192.33.4.12) in 39 ms

postfix.org.            86400   IN      NS      ns5.cloud9.net.
postfix.org.            86400   IN      NS      ns2.cloud9.net.
postfix.org.            86400   IN      NS      ns4.cloud9.net.
postfix.org.            86400   IN      NS      ns1.cloud9.net.
;; Received 115 bytes from 199.19.54.1#53(199.19.54.1) in 351 ms

[www.postfix.org](www.postfix.org).        86400   IN      A       131.211.84.186
[www.postfix.org](www.postfix.org).        86400   IN      A       168.100.10.85
postfix.org.            86400   IN      NS      ns1.cloud9.net.
postfix.org.            86400   IN      NS      ns2.cloud9.net.
postfix.org.            86400   IN      NS      ns4.cloud9.net.
postfix.org.            86400   IN      NS      ns5.cloud9.net.
;; Received 323 bytes from 82.130.104.214#53(82.130.104.214) in 146 ms

Any suggestions as to what I am missing would be greatly appreciated.

Thank you in advance for your help.



Jay

---

### Post by jaynv0i on 2012-10-05
After having lunch, and re-reading my post, I realize how horribly my question was written.  

When querying my internal DNS server, requests almost always time out before the name is resolved.  Resolution of internal names works correctly; lookups only fail for external namees.

Using dig, nslookup, etc. when querying an external DNS server resolution happens as expected.

Sorry for the lack of information.

Thanks,



Jay

---

### Post by Doug S on 2012-10-06
I run bind as the DNS for my internel network, and get normal times for lookups that need to be sent upstream to the forwarders. I don't know what the problem is with your system, but I did notice that our named.conf.options files are a little different. I'll post mine:```
options {
        directory "/var/cache/bind";
        recursion yes;
        allow-recursion {any;};
        allow-query {any;}; // this is needed to override the default
        allow-transfer {"none"; }; // transfer will be allowed per zone below.
        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113
        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.
        forwarders {
                75.153.176.9;
                75.153.176.1;
        };
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```Note: While I don't use ip-v6, I left that line.
I don't know if this reply will be any help, but since it has been a day and nobody else replied ...

---

### Post by confusedstingray on 2012-10-07
do you have dhcp issuing ip's and what dns server is being passed to your clients.
if you internal dns server is not in the list first the internal query wil time out because it is going pass the internal dns server  and directly to the external dns servers(your fowarders)
also if your clients are static ip what dns server is in there setup

---

### Post by jdthood on 2013-01-06
Anyone interested in having bind9's forwarders list get dynamically updated, please add your voice to the following (wishlist) bug report.

    [https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602)

---

