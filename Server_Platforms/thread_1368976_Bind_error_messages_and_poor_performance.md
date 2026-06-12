---
title: "Bind error messages and poor performance"
date: 2009-12-31
forum: Server Platforms
---

### Post by BalleClorin on 2009-12-31
I'm getting the following errors in /var/log/daemon.log

Dec 31 15:15:25 demigod named[12914]: success resolving 'youtube-global.blogspot.com/AAAA' (in 'blogspot.com'?) after reducing the advertised EDNS UDP packet size to 512 octets

and sometimes:

Dec 31 14:43:23 demigod named[12478]: success resolving 'www.vg.no/A' (in 'vg.no'?) after disabling EDNS

I've disabled everything related to intrusion detection and firewall in the ADSL-router but still get these errors. Tried adding edns-udp-size 512; to /etc/bind/named.conf.options but it doesn't seem to have any effect. Any ideas? I also tried adding the adsl-router as a forwarder, this reduced the number of error messages slightly...

Any ideas???

---

### Post by beadrifle on 2010-08-13
Bump. I have similar errors and extremely poor performance. disable ipv4 through /etc/defaults/bind9 stopped the EDNS error messages but bind9 is still performing extremely poorly. Any suggestions would help thank you.

---

### Post by menchi on 2010-12-17
Bump. Has somebody figured it out?

What I have tried is:
disabling ipv6 with "-4" in /etc/default/bind9 and
inserting "max-cache-size 0" and "edns-udp-size 512" in /etc/bind/named.conf.options with no effect.

PS: I'm running BIND9.7.x - latest from the repo.

---

### Post by g4m3c4ck on 2011-02-09
FYI, I found this googling around.

>     The better solution is to work out if it is a local problem 
        that is causing the messages and fix it. 
        The usual causes is a broken or misconfigure firewall / NAT. 
        * A Firewall that doesn't allow through DNS packets > 512 bytes. 
        * A Firewall/NAT that doesn't allow IP fragments through. 
        To workaround either of these set edns-udp-size to a 
        appropriate value but only do it if you can't fix the 
        underlying problem. 
        e.g. 
                I've got a NAT that can't handle out-of-order IP 
                fragments so I use "edns-udp-size 1460;" which is 
                small enough so that a UDP packet will fit in a 
                Ethernet packet without fragmentation provided no 
                IP options are set. 
        "dig +norec +dnssec example.com @a.root-servers.net" 
        Can be used to test if you firewall supports packets > 512. 
        "dig +dnssec +norec +ignore dnskey se @A.NS.se" 
        Can be used to test if IP fragments can get though at all. 
        I don't have a out-of-order IP fragmentation test. 
        These messages are rare events with a EDNS clear path. 

However, my firewall seems to process these fine too.

> Solution: 
add the following lines in /etc/named.conf or /var/named/chroot/etc/ 
named.conf: 
logging { 
category lame-servers {null; }; 
category edns-disabled { null; }; 
}; 

Hope to help ... 
Antonio Carlos de Lima 

Note that the location of named.conf differs in ubuntu and it is split into multiple files. named.conf.options is where I put it. Make sure you restart the bind daemon.

This will supress the error in your logs but doesn't solve the issue causing it.

I only assume the error is present due the dns server it is communicating with does not support edns.

---

### Post by g4m3c4ck on 2011-02-09
I found this command will test if a server supports EDNS

dig @127.0.0.1 +noall +comments +bufsize=1 query

I get the following output which shows a 4K udp packet size


;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 35828
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096

---

### Post by weaccept on 2011-03-23
EDNS: [http://en.wikipedia.org/wiki/Extension_mechanisms_for_DNS](http://en.wikipedia.org/wiki/Extension_mechanisms_for_DNS)

EDNS increases the DNS message length above 512 bytes.

> In practice, difficulties can arise when using EDNS traversing firewalls, since some firewalls assume a maximum DNS message length of 512 bytes and block longer DNS packets.

So the root cause is a firewall between your bind server and the Internet that is dropping DNS messages > 512 bytes.

Solutions:
  1) The best solution is to upgrade the firewall so that it is EDNS compatible and allows DNS messages > 512 bytes.

  2) If that isn't possible, you can globally disable EDNS within bind:

```

Edit /etc/bind/named.conf.options

Add this at the bottom (outside of the options clause):

server ::/0 {
       edns no;
};

server 0.0.0.0/0 {
       edns no;
};

```

---

