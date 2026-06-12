---
title: "bind resolves non-existant hosts or ping weirdness"
date: 2006-10-03
forum: Server Platforms
---

### Post by darkpixel on 2006-10-03
My appologies if this has been answered before--but search on ubuntuforums is broken.  (searching for 'bind' throws an error page).

I have a server that I use to host several websites.  It handles DNS for a handfull of domains.

Here's a quick rundown of the setup.

resolv.conf contains "nameserver 127.0.0.1".
nsswitch.conf's hosts line is "hosts: files dns"

Bind appears to be setup correctly.  Here is one of the zone files.
$ttl 38400
@                       IN      SOA     ns.mydomain.com. dns.mydomain.com. (                                        2006100303
                                        10800
                                        3600
                                        604800
                                        38400 )
                        IN      NS      ns.mydomain.com.
                        IN      NS      ns2.mydomain.com.
                        IN      A       111.222.333.444
                        IN      MX      10 mail.mydomain.com.
www                     IN      CNAME   cust-domain.com.
mail                    IN      CNAME   mail.mydomain.com.



If I ping [www.cust-domain.com](www.cust-domain.com) or cust-domain.com it resolves correctly from any machine.  The server, my workstation, etc...

If I ping dork.cust-domain.com (which isn't in the zone file) FROM THE SERVER it resolves to a strange IP.

If I ping dork.cust-domain.com from my workstation I get the standard 'unknown host' response.

PING c17-ss-2-lb.cnet.com (216.239.113.148) 56(84) bytes of data.
64 bytes from c17-ss-2-lb.cnet.com (216.239.113.148): icmp_seq=1 ttl=240 time=76.1 ms

That IP is indeed a cnet.com domain--and it's not mine.

It gets even stranger.

If I do an nslookup or a dig from the server, they both return that dork.cust-domain.com wasn't found.  Same thing on the server.

The only thing that appears to be effected (affected?  I never remember which is which) is the ping command on the server.


If anyone wants to try tackling this problem, just let me know and I can attach whatever logs you need.]

---

### Post by homnay on 2006-11-06
Hi darkpixel,

I've the same problem with you, please help me how to resolve it.

I'm using: CentOS 4.4.

Thanks,
homnay

---

### Post by darkpixel on 2006-11-06
I have no clue why this is happening and no one has replied with a solution yet.

---

### Post by jbarchuk on 2007-02-09
Well, let's keep the thread going because it's the middle of February and I've still got the same problem and it is a *severe* and clearly technically faulty interference.

Further, pings [unknowndomains].org return responses from 9a.f6.ead8.static.theplanet.com

[unknown].us returns from s85265.centralnic.net

.info returns new.web5.info.com

Picking a few other TLDs at random...

.cz returns 63.251.92.195

.ru returns:

PING fdh4jhewkjnjksdkf8834d2skf.ru.com (213.146.149.161) 56(84) bytes of data.

--- fdh4jhewkjnjksdkf8834d2skf.ru.com ping statistics ---
28 packets transmitted, 0 received, 100% packet loss, time 27018ms

Buuut .net .ar and .tv correctly return 'unknown host.'

Using fedora 9 with all current updates, *but* using a handrolled Bind.

I called cnet but they're soooooo big it's almost impossible to find a tech type person who even understands the words I'm using such as 'ping.' LOL!

My intuitive guess is that it's got to be a DSN misconfiguration, something that tosses all unknowns towards this particular box, but I don't see anything obvious in dig responses.

I think I'm gonna post this all to a bind user group, maybe they know how to debug it, because I'm getting really tired of it.

Have a :) day!

jb

[email]jb@jbarchuk.com[/email]

---

### Post by darkpixel on 2007-02-09
I still have the retarded issue.
Even pinging dork.microsoft.com returns
# ping dork.microsoft.com
PING c17-ss-2-lb.cnet.com (216.239.113.148) 56(84) bytes of data.
64 bytes from c17-ss-2-lb.cnet.com (216.239.113.148): icmp_seq=1 ttl=241 time=75.8 ms

I think it's possibly a defect in dapper.  I have had several bind geeks look at my config and they say there's nothing wrong with it.

nslookup and traceroute returns values correctly--but ping or mtr.
Maybe something to do with the libraries they link to?  I don't know--it's out of my field.

---

### Post by MJN on 2007-02-10
Post the output of **dig dork.microsoft.com A +trace **(also run it without the +trace option)
 
Unless you post your real domain I won't attempt to debug your BIND config (too much potential for copy-and-paste errors etc and no scope for live testing) however we can look for hints from the dig output above (although I've just noticed you say it only affects pings).
 
Have you captured a packet trace with Ethereal (or other packet sniffer) when doing a ping to a previously-untried destination?
 
Mathew

---

### Post by darkpixel on 2007-02-10
> **MJN said:**
> Post the output of **dig dork.microsoft.com A +trace **(also run it without the +trace option)
 
Unless you post your real domain I won't attempt to debug your BIND config (too much potential for copy-and-paste errors etc and no scope for live testing) however we can look for hints from the dig output above (although I've just noticed you say it only affects pings).
 
Have you captured a packet trace with Ethereal (or other packet sniffer) when doing a ping to a previously-untried destination?
 
Mathew

It doesn't matter what domain I ping--if it's a non-existent host it returns bogus results.  However I would be more than happy to post my actual bind config--just give me a few minutes to get it together.


; <<>> DiG 9.3.2 <<>> dork.microsoft.com A +trace
;; global options:  printcmd
.                       253891  IN      NS      L.ROOT-SERVERS.NET.
.                       253891  IN      NS      M.ROOT-SERVERS.NET.
.                       253891  IN      NS      A.ROOT-SERVERS.NET.
.                       253891  IN      NS      B.ROOT-SERVERS.NET.
.                       253891  IN      NS      C.ROOT-SERVERS.NET.
.                       253891  IN      NS      D.ROOT-SERVERS.NET.
.                       253891  IN      NS      E.ROOT-SERVERS.NET.
.                       253891  IN      NS      F.ROOT-SERVERS.NET.
.                       253891  IN      NS      G.ROOT-SERVERS.NET.
.                       253891  IN      NS      H.ROOT-SERVERS.NET.
.                       253891  IN      NS      I.ROOT-SERVERS.NET.
.                       253891  IN      NS      J.ROOT-SERVERS.NET.
.                       253891  IN      NS      K.ROOT-SERVERS.NET.
;; Received 260 bytes from 38.113.64.122#53(38.113.64.122) in 1 ms

com.                    172800  IN      NS      a.gtld-servers.net.
com.                    172800  IN      NS      g.gtld-servers.net.
com.                    172800  IN      NS      h.gtld-servers.net.
com.                    172800  IN      NS      c.gtld-servers.net.
com.                    172800  IN      NS      i.gtld-servers.net.
com.                    172800  IN      NS      b.gtld-servers.net.
com.                    172800  IN      NS      d.gtld-servers.net.
com.                    172800  IN      NS      l.gtld-servers.net.
com.                    172800  IN      NS      f.gtld-servers.net.
com.                    172800  IN      NS      j.gtld-servers.net.
com.                    172800  IN      NS      k.gtld-servers.net.
com.                    172800  IN      NS      e.gtld-servers.net.
com.                    172800  IN      NS      m.gtld-servers.net.
;; Received 496 bytes from 198.32.64.12#53(L.ROOT-SERVERS.NET) in 73 ms

microsoft.com.          172800  IN      NS      ns1.msft.net.
microsoft.com.          172800  IN      NS      ns2.msft.net.
microsoft.com.          172800  IN      NS      ns3.msft.net.
microsoft.com.          172800  IN      NS      ns4.msft.net.
microsoft.com.          172800  IN      NS      ns5.msft.net.
;; Received 214 bytes from 192.5.6.30#53(a.gtld-servers.net) in 27 ms

microsoft.com.          3600    IN      SOA     dns.cp.msft.net. msnhst.microsoft.co
m. 2007020901 300 600 2419200 3600
;; Received 107 bytes from 207.68.160.190#53(ns1.msft.net) in 87 ms

---

### Post by darkpixel on 2007-02-10
Here's my bind config.  Everywhere there is an include line (file "/some/file") I have included the actual text of the file.



options {
        directory "/var/cache/bind";
        auth-nxdomain no;    # conform to RFC1035
        listen-on { 127.0.0.1; 38.113.64.122; };
        recursion yes;
};
zone "." {
        type hint;
        file "/etc/bind/db.root";
;;;;/etc/bind/db.root
.                        3600000  IN  NS    A.ROOT-SERVERS.NET.
A.ROOT-SERVERS.NET.      3600000      A     198.41.0.4
.                        3600000      NS    B.ROOT-SERVERS.NET.
B.ROOT-SERVERS.NET.      3600000      A     192.228.79.201
.                        3600000      NS    C.ROOT-SERVERS.NET.
C.ROOT-SERVERS.NET.      3600000      A     192.33.4.12
.                        3600000      NS    D.ROOT-SERVERS.NET.
D.ROOT-SERVERS.NET.      3600000      A     128.8.10.90
.                        3600000      NS    E.ROOT-SERVERS.NET.
E.ROOT-SERVERS.NET.      3600000      A     192.203.230.10
.                        3600000      NS    F.ROOT-SERVERS.NET.
F.ROOT-SERVERS.NET.      3600000      A     192.5.5.241
.                        3600000      NS    G.ROOT-SERVERS.NET.
G.ROOT-SERVERS.NET.      3600000      A     192.112.36.4
.                        3600000      NS    H.ROOT-SERVERS.NET.
H.ROOT-SERVERS.NET.      3600000      A     128.63.2.53
.                        3600000      NS    I.ROOT-SERVERS.NET.
I.ROOT-SERVERS.NET.      3600000      A     192.36.148.17
.                        3600000      NS    J.ROOT-SERVERS.NET.
J.ROOT-SERVERS.NET.      3600000      A     192.58.128.30
.                        3600000      NS    K.ROOT-SERVERS.NET.
K.ROOT-SERVERS.NET.      3600000      A     193.0.14.129 
.                        3600000      NS    L.ROOT-SERVERS.NET.
L.ROOT-SERVERS.NET.      3600000      A     198.32.64.12
;;;;end /etc/bind/db.root
};

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
;;;;/etc/bind/db.local
$TTL    604800
@       IN      SOA     localhost. root.localhost. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      localhost.
@       IN      A       127.0.0.1
;;;;end /etc/bind/db.local
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
;;;;/etc/bind/db.127
$TTL    604800
@       IN      SOA     localhost. root.localhost. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      localhost.
1.0.0   IN      PTR     localhost.
;;;;end /etc/bind/db.127
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
;;;;/etc/bind/db.0
$TTL    604800
@       IN      SOA     localhost. root.localhost. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      localhost.
;;;;end /etc/bind/db.0
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
;;;;;/etc/bind/db.255
$TTL    604800
@       IN      SOA     localhost. root.localhost. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      localhost.
;;;;end /etc/bind/db.255
};

// root-delegation-only exclude { "DE"; "MUSEUM"; };


zone "ubertragen.com" {
        type master;
        file "/etc/bind/ubertragen.com.hosts";
;;;;/etc/bind/ubertragen.com.hosts
$ttl 38400
@                       IN      SOA     ns.ubertragen.com. dns.ubertragen.com. (
                        2005121503
                        10800
                        3600
                        604800
                        38400 )
                        IN      NS      ns.ubertragen.com.
                        IN      NS      ns2.ubertragen.com.
                        IN      TXT     "v=spf1 a mx ~all"
                        IN      MX      10 mail.ubertragen.com.
                        IN      A       38.113.64.122
ns                      IN      A       38.113.64.122
ns2                     IN      A       38.113.64.122
www                     IN      CNAME   ubertragen.com.
mail                    IN      A       38.113.64.122
tools                   IN      CNAME   ubertragen.com.
svn                     IN      CNAME   ubertragen.com.
irc                     IN      A       38.113.65.96
services                IN      A       38.113.65.97
cp                      IN      CNAME   ubertragen.com.
;;;;end /etc/bind/ubertragen.com.hosts

};

zone "64.113.38.in-addr.arpa" {
        type master;
        file "/etc/bind/pri.64.113.38.in-addr.arpa";
;;;;/etc/bind/pri.64.113.38.in-addr.arpa
$TTL        86400
@               IN      SOA     ns.ubertragen.com. hostmaster.ubertragen.com. (
                                2006101620       ; serial, todays date + todays seri
al #
                                28800   ; Refresh
                                7200    ; Retry
                                604800  ; Expire
                                86400)  ; Minimum TTL
                        NS      ns.ubertragen.com.
                        NS      ns2.ubertragen.com.
122     PTR     mail.ubertragen.com.
123     PTR     ubertragen.com.
124     PTR     ubertragen.com.
125     PTR     ubertragen.com.
;;;end /etc/bind/pri.64.113.38.in-addr.arpa
};

zone "65.113.38.in-addr.arpa" {
        type master;
        file "/etc/bind/pri.65.113.38.in-addr.arpa";
;;;;/etc/bind/pri.65.113.38.in-addr.arpa
$TTL        86400
@               IN      SOA     ns.ubertragen.com. hostmaster.ubertragen.com. (
                                2006101620       ; serial, todays date + todays seri
al #
                                28800   ; Refresh
                                7200    ; Retry
                                604800  ; Expire
                                86400)  ; Minimum TTL
                        NS      ns.ubertragen.com.
                        NS      ns2.ubertragen.com.
96      PTR     irc.ubertragen.com.
97      PTR     services.ubertragen.com.
98      PTR     ubertragen.com.
99      PTR     ubertragen.com.
100     PTR     ubertragen.com.
101     PTR     ubertragen.com.
102     PTR     ubertragen.com.
103     PTR     ubertragen.com.
;;;;end /etc/bind/pri.65.113.38.in-addr.arpa
};

---

### Post by darkpixel on 2007-02-10
> **MJN said:**
> Post the output of **dig dork.microsoft.com A +trace **(also run it without the +trace option)
 
Unless you post your real domain I won't attempt to debug your BIND config (too much potential for copy-and-paste errors etc and no scope for live testing) however we can look for hints from the dig output above (although I've just noticed you say it only affects pings).
 
Have you captured a packet trace with Ethereal (or other packet sniffer) when doing a ping to a previously-untried destination?
 
Mathew

The computer in question is a remote server on the opposite side of the US from me.  I'm in Washington, it's in Florida.  I don't have X installed on it, so I can't run ethereal, but I did capture the offending packets with tcpdump along with an strace of ping running.  I have attached both files.  (The syntax for tethereal's filtering confused the hell out of me.  If anyone wants a tethereal dump I can get it--it'll just take me a while to get the filter syntax figured out)

tcpdump -e -i eth0 -n -X -vvv port 53 > tcpdump-domain.txt
strace -o strace-ping.txt ping -c 1 not-a-valid-host42.not-a-valid-domain42.com

Surprisingly not-a-valid-domain.com actually exists. ;)

---

### Post by MJN on 2007-02-10
Thanks for that lot. I'm accessing this via a PDA so kind of limited with what I can do with it right now.

However, in the interim until I'm at my PC can you confirm your /etc/resolv.conf?

EDIT: You've already done so in your first post so scrap that request!

Mathew

---

### Post by MJN on 2007-02-10
Just thinking aloud, can you do a tracepath to a non-existant domain?

---

### Post by darkpixel on 2007-02-10
> **MJN said:**
> Just thinking aloud, can you do a tracepath to a non-existant domain?

Yup.  I can also traceroute and mtr.

darkpixel@ubertragen:~$ tracepath notahost.notadomain123124234.com
 1:  ubertragen.com (38.113.64.122)                         0.269ms pmtu 1500
 1:  192.168.0.100 (192.168.0.100)                          2.033ms 
 2:  g0-2-na21.b005947-0.jax01.atlas.cogentco.com (66.28.230.33)   1.140ms 
 3:  g0-1.core01.jax01.atlas.cogentco.com (38.112.38.89)    0.908ms 
 4:  p15-0.core01.mia01.atlas.cogentco.com (66.28.4.137)    9.046ms 
 5:  p8-0.core01.mia03.atlas.cogentco.com (154.54.6.178)    8.377ms 
 6:  xo.mia03.atlas.cogentco.com (154.54.11.154)            8.741ms 
 7:  p4-0-0.rar1.miami-fl.us.xo.net (71.5.168.21)         asymm  8   9.496ms 
 8:  p4-0-0.rar1.dallas-tx.us.xo.net (65.106.0.58)        asymm 11  35.834ms 
 9:  p6-0-0.rar2.la-ca.us.xo.net (65.106.0.14)            asymm 11  65.721ms 
10:  p0-0-0d0.rar1.la-ca.us.xo.net (65.106.1.49)          asymm 11  65.643ms 
11:  p6-0-0.rar2.sanjose-ca.us.xo.net (65.106.0.18)        75.932ms 
12:  p0-0-0.mar2.fremont-ca.us.xo.net (65.106.5.138)       75.952ms 
13:  p15-0.CHR1.Fremont-CA.us.xo.net (207.88.80.182)      asymm 12  75.593ms 
14:  67.104.60.210.ptr.us.xo.net (67.104.60.210)           76.153ms 
15:  ge3-8.365-sfo1-6506-2.cnet.com (216.239.127.49)      asymm 13  76.355ms 
16:  c17-ss-2-lb.cnet.com (216.239.113.148)               asymm 15  76.136ms reached
     Resume: pmtu 1500 hops 16 back 15 


I believe it's something odd with bind though.
I changed resolv.conf at one point to point to the IP of one of the root servers and everything resolved correctly.  Pointing it back at my server causes this weird error.

Although on the flip side, I've tried setting my laptop and storage server at my house to that nameserver and I do NOT have those issues.

So it appears to only affect the results when the local box connects to itself.

I suppose anyone could try pointing their nameserver to 38.113.64.122 to try it out...

---

### Post by MJN on 2007-02-11
Whilst I'm not entirely sure what's to blame I think I'm getting somewhere...

Looking at your tcpdump attachment we've basically the following:

38.113.64.122 > 192.5.6.30 (you > gtld nameserver) : Asks for A record for aninvaliddomain.com (your trace is truncated, possibly due to the filter, but not to worry)
192.5.6.30 > 38.113.64.122 (gtld ns > you) : Responds with no such domain

...so far so good...

however instead of giving up your machine then goes on to ask:

38.113.64.122 > 216.239.123.201 (you > who?) : A record for  aninvaliddomain.com? (again, truncated but not to worry)
216.239.123.201 > 38.113.64.122 (who? > you): An answer of 216.239.113.148!

What?!

This raises three questions: 1) Why is your machine going to 216.239.123.201 despite an already failed domain query? 2) Who is 216.239.123.201? and 3) Why is 216.239.123.201 giving you an answer for an known-invalid domain and why is it always the same address (within a similar netblock?)

Well the last question gave the game away that something fishy is going on ... and this is it:

216.239.123.201 is authoritive for the com.com domain! Furthermore, any DNS query for a domain within com.com results in an IP which, if connected to on port 80/HTTP, gives a 'search.com' page! Nice way to trap accidentaly double-.com suffixes (not advertising on the page so could be legit).

Working back through the questions the reason therefore that you're always getting an IP for a known-invalid domain is because your resolver is adding an additional .com suffix to your already-suffixed .com domain! Hence why you always end up at the nameservers of .com.com.

So why is your resolver adding a .com suffix? Can you confirm you don't have a 'search .com' entry in ./etc/resolv.conf? I thought it might also be the absence of a trailing dot somewhere in your BIND config but it looks okay...

Mathew

---

### Post by darkpixel on 2007-02-11
> **MJN said:**
> 
So why is your resolver adding a .com suffix? Can you confirm you don't have a 'search .com' entry in ./etc/resolv.conf? I thought it might also be the absence of a trailing dot somewhere in your BIND config but it looks okay...

Mathew

That's the point that stumped me.
/etc/resolv.conf contains only one line
"nameserver 38.113.64.122"
That's the address of my server.

My hosts file has nothing out of the ordinary, and nsswitch.com seems to be ok.
# /etc/nsswitch.conf
passwd:         compat mysql
group:          compat mysql
shadow:         compat mysql
hosts:          files dns mdns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

---

### Post by dcstar on 2007-02-12
> **darkpixel said:**
> That's the point that stumped me.
/etc/resolv.conf contains only one line
"nameserver 38.113.64.122"
That's the address of my server.
........

What are your Forwarders set to? (should be in a named.conf file somewhere).

---

### Post by darkpixel on 2007-02-12
> **dcstar said:**
> What are your Forwarders set to? (should be in a named.conf file somewhere).

I have none defined.

---

### Post by dcstar on 2007-02-12
> **darkpixel said:**
> I have none defined.

If you have no forwarders, how is your own DNS server going to query the rest of the Internet to get any information outside of your own domain?

---

### Post by darkpixel on 2007-02-13
> **dcstar said:**
> If you have no forwarders, how is your own DNS server going to query the rest of the Internet to get any information outside of your own domain?

The list of root servers...

---

### Post by dagnabbit on 2007-03-15
This one stumped me for a while until I found a simple fix.  At the top of your /etc/resolv.conf, make sure you put in a "search yourdomain.com".  Otherwise, whenever the resolver cannot find a domain, it automatically puts a .com on the end.  (E.g. asdfasdfsadfdsaf.google.com becomes asdfasdfsadfdsaf.google.com.com, which belongs to cnet.com and gets resolved to c17-ss-2-lb.cnet.com.

Dag

---

### Post by MJN on 2007-03-15
Mine doesn't....

```

$ ping asdfasdfsadfdsaf.google.com
ping: unknown host asdfasdfsadfdsaf.google.com

```

You're correct about the purpose of the search directive however the absence of such (i.e. the default) should not cause a .com suffix to be added (as discussed above).

Mathew

---

