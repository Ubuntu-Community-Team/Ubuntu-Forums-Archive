---
title: "DNS zone delegation"
date: 2011-04-28
forum: Server Platforms
---

### Post by Barry Cent on 2011-04-28
Hi,

I'll try and make this as easy to understand as possible. Apologies in advance if it's unclear!

I have an existing bind setup, which serves a local DNS zone: merlin.local.

I would like to setup a subzone, below merlin.local, (preferably ad.merlin.local) to be used by an M$ AD domain, and thus M$ DNS servers. I would like to then be able to lookup addresses in both of the zones mentioned from any machine on my network.

I thought that this would be as simple as creating a zone delegation in bind, however when I have done this, and setup an M$ domain using ad.merlin.local as it's DNS name. Whilst this hasn't presented me with any errors, as such, I have been unable to come up with a setup which allows me to lookup addresses in both the merlin.local domain and the ad.merlin domain. To be perfectly honest, I'm not sure what configuration I need to perform to allow this to happen, I stupidly assumed it would just work!

Please advise what information you need from my setup, and I will provide it (I'm not sure what information would help best, sorry). It may be worth mentioning that I am using Webmin to configure my bind DNS server.

Thank you,

Joe

---

### Post by SeijiSensei on 2011-04-28
Do you want the AD server to respond to queries in the ad.merlin.local domain?  I think all you need to do is add a line to merlin.local's zone file that reads:

```

ad     IN     NS    adserver.merlin.local.
       IN     NS    adbackup.merlin.local.

```

adserver.merlin.local needs to have an A record in this same zone file.  If you have a secondary server, you can add that as I did above.  Otherwise you'll just have one line.

Now requests for host.ad.merlin.local should be answered by adserver, while requests for just merlin.local should be answered by the current DNS server.

---

### Post by Barry Cent on 2011-04-28
Hi,

Thanks four your reply.

Ok, I'll try what you suggested later on.

> Do you want the AD server to respond to queries in the ad.merlin.local domain?
Yes, that's fine.

As far as the M$ DNS setup is concerned, am I correct in saying that I would just setup a primary/master zone in DNS there for ad.merlin.local?

Could you explain how requests from AD clients in ad.merlin.local would resolve addresses in merlin.local please? Would I need anything else setup for this?

Thanks,

Joe

---

### Post by SeijiSensei on 2011-04-28
> **Barry Cent said:**
> As far as the M$ DNS setup is concerned, am I correct in saying that I would just setup a primary/master zone in DNS there for ad.merlin.local?

I think so.  I've not set up an Active Directory server, though I've run Linux DNS servers in organizations with AD as well.

It's often easier to make the AD server be the primary for the whole domain, especially if it's the network-wide DHCP server.  That's how we have things set up with my largest client using AD.  We just add static DNS records to the AD server for the Linux machines and external hosts that aren't governed by the AD server.

> Could you explain how requests from AD clients in ad.merlin.local would resolve addresses in merlin.local please? Would I need anything else setup for this?

When you say "resolve addresses" do you mean looking up the PTR record for an IP address to determine its hostname?  If so, making the AD server the primary for the entire merlin.local domain would again solve this problem.  Otherwise you can use a forwarder entry in a zone definition on your bind9 host for the network's reverse domain in /etc/named.conf like this:

```

zone "2.1.10.in-addr.arpa" {
     type forward;
     forward-only;
     forwarders { ip.of.ad.server; ip.of.ad.backup; };
};

```

That sends requests for resolution of addresses in 10.1.2.0/24 to the AD server or its backup.  Replace 2.1.10 with the IP address block the AD's DHCP server is using in reverse order.

However if by "resolving addresses" you actually meant resolving hostnames to IP addresses, I think you're asking how to get the AD clients to use the merlin.local DNS server rather than the AD server.  You just need to configure DHCP to give out the merlin.local server's IP as the primary resolver.  Its nameserver should have zone definitions for merlin.local and for all reverse domains like the 2.1.10.in-addr.arpa example I used above.  Use an NS record to point subdomains of merlin.local like I suggested above, and use forwarders to handle requests for reverse lookups.

---

### Post by koenn on 2011-04-28
> **Barry Cent said:**
> 
Could you explain how requests from AD clients in ad.merlin.local would resolve addresses in merlin.local please? Would I need anything else setup for this?
DNS zones like the ones you've set up resolve _names_, not addresses. Addresses are the result. 
a hostname such as  green.ad.merlin.local will be resolved from the ad.merlin.local zone, a hostname such as blue.merlin.local will be resolved from the merlin.local zone. Simple

If you want reverse lookups (addresses -> names), you need to set up reverse lookup zones (with PTR records)

In any case, all of that is probably irrelevant : if you want DNS that supports Microsoft AD, you'll need to create the specific zones and records that an MS AD requires : 
[http://technet.microsoft.com/en-us/library/dd316373.aspx](http://technet.microsoft.com/en-us/library/dd316373.aspx)
that article will give you an idea of what 's going on, but I suggest you find more recent documentation if this is what you're trying to do.

---

### Post by Barry Cent on 2011-04-28
SeijiSensei, koenn: Thank you so much for the information you have provided.

I apologize, I should have been more thoughtful about the terminology I was using in my previous post as it was incorrect.

What I ultimately want to do is be able to resolve hostnames to IP addresses from client machines in both zones - whether a computer is in merlin.local or ad.merlin.local, they should be able to look up hostnames in both zones.

With my current setup, my Bind9 server is my primary DNS server for the network, and that controls DHCP too. I then wanted the M$ DNS servers to just handle records for Windows machines on the network that are part of the AD domain.

I have had this working previously with two separate DNS namespaces setup locally on my network, and then setup stub zones in each DNS server to allow hostnames to be resolved in the other domain. Would you say that this is probably the best way to do acheive what I'm after, or I am I better to stick with zone delegation for the AD DNS zone which we've talked about previously?

Thank you for your time and patience!

Joe

---

### Post by Barry Cent on 2011-04-28
> **SeijiSensei said:**
> Do you want the AD server to respond to queries in the ad.merlin.local domain?  I think all you need to do is add a line to merlin.local's zone file that reads:

```

ad     IN     NS    adserver.merlin.local.
       IN     NS    adbackup.merlin.local.

```

adserver.merlin.local needs to have an A record in this same zone file.  If you have a secondary server, you can add that as I did above.  Otherwise you'll just have one line.

Now requests for host.ad.merlin.local should be answered by adserver, while requests for just merlin.local should be answered by the current DNS server.

I've added:
```
TESTWINDC1		A	192.168.1.25
ad              IN      NS      TESTWINDC1.merlin.local.
```
to my records file for merlin.local but when queried for the IP address for TEMPWINDC1.ad.merlin.local dig returns nxdomain :-( 

(TESTWINDC1 is my test M$ domain controller and DNS server that I'm using to test this setup.)

Any thoughts on why this may happen?

Thanks,

Joe

---

### Post by koenn on 2011-04-28
> **Barry Cent said:**
> 
I have had this working previously with two separate DNS namespaces setup locally on my network, and then setup stub zones in each DNS server to allow hostnames to be resolved in the other domain. Would you say that this is probably the best way to do acheive what I'm after, or I am I better to stick with zone delegation for the AD DNS zone which we've talked about previously?


I think what Sensei says sounds like a resonable approach:
> **SeijiSensei said:**
>  I think you're asking how to get the AD clients to use the merlin.local DNS server rather than the AD server.  You just need to configure DHCP to give out the merlin.local server's IP as the primary resolver.  Its nameserver should have zone definitions for merlin.local and for all reverse domains like the 2.1.10.in-addr.arpa example I used above.  Use an NS record to point subdomains of merlin.local like I suggested above, and use forwarders to handle requests for reverse lookups.


disclaimer : all my DNS setups are the result of an endless trial-error-debug-reconsider loop.

---

### Post by koenn on 2011-04-28
guess:

TEMPWINDC1_.ad._merlin.local  doesn't exist ?

All you're showing is records for TEMPWINDC1.merlin.local

---

### Post by Barry Cent on 2011-04-28
> **koenn said:**
> guess:

TEMPWINDC1_.ad._merlin.local  doesn't exist ?

All you're showing is records for TEMPWINDC1.merlin.local
Yes, I've got an A record for TEMPWINDC1.ad.merlin.local, however this is in the M$ DNS server. Have I misinterpreted where that should be?

My understanding from SeijiSensei's posts was that queries for **ad**.merlin.local which arrived at the Bind9 DNS server would match up to the NS record for **ad**(.merlin.local) would be passed to TESTWINDC1.merlin.local, which is then resolved to it's IP using the A record in the merlin.local zone. I bet thats wrong though! Sorry.

---

### Post by koenn on 2011-04-28
that sounds about right, yes.
as long as the name you're trying to resolve indeed has a record in the ad.merlin.local zone on the MS DNS server. (that wasn't obvious from your posts, but I'll take your word for it)

but it seems weird to, in that case, have testwindc01 both in merlin.local and ad.merlin.be. I'd expect something like
```

ad.merlin.local.              IN      NS      TESTWINDC1.ad.merlin.local.
TESTWINDC1.ad.merlin.local.   IN      A       192.168.1.25

```
i.e. you put the name server in the zone it rules, and point to it from the parent zone ("glue" record)
[http://www.zytrax.com/books/dns/ch9/delegate.html](http://www.zytrax.com/books/dns/ch9/delegate.html) appears to agree. 

technically, this is not different from what Sensei suggested, except that I prefer to have those things explicit, with FQDN. 
The short forms depend on how bind interpretes them, and bind config is error prone, so being explicit sometimes helps to get things right.  


then again, my disclaimer still stands. I'm by no means an expert on bind.


also, you do make sure bind reloads its config and zone files when you add or modify something, right ?

---

### Post by SeijiSensei on 2011-04-28
> **Barry Cent said:**
> I've added:
```
TESTWINDC1		A	192.168.1.25
ad              IN      NS      TESTWINDC1.merlin.local.
```
to my records file for merlin.local but when queried for the IP address for TEMPWINDC1.ad.merlin.local dig returns nxdomain :-( 

There shoulnd't be an IP address for testwindc1.ad.merlin.local unless you added a record for that host to the AD server's DNS.

You should be able to resolve testwindc1.merlin.local, and get 192.168.1.25 in response.

Now just to make sure we understand what's going on, you have a DHCP server on the machine running BIND9.  Does that provide addresses to machines in the AD domain?  Do your zone files [update automatically]("http://www.debianadmin.com/howto-setup-dhcp-server-and-dynamic-dns-with-bind-in-debian.html") when a machine obtains an address?

Or does the AD server also have a DHCP server that handles requests from machines in its subnet?  If it does, then the method I suggested originally should work.  However if you're using only the Linux server to handle DHCP, then I don't see how the AD machine will know the hostnames and IPs of the hosts in ad.merlin.local.

What if you set up the AD server with a plain-vanilla configuration, let it assign some addresses, then run queries against it?  Ask it to resolve a host in the ad.merlin.local domain, and ask it to return the PTR record for that host's IP address.  If you can determine that the AD server is authoritative for ad.merlin.local, then you can work out how to integrate that with the Linux server.

---

### Post by Barry Cent on 2011-04-29
koenn: I have tried your suggestion of adding FQNs for TESTWINDC1.ad.merlin.local. but it still returns nxdomain :-(.

SeijiSensei:

> There shoulnd't be an IP address for testwindc1.ad.merlin.local unless you added a record for that host to the AD server's DNS.
I have added an A record to my M$ DNS server for TESTWINDC1.ad.merlin.local., yes.

> You should be able to resolve testwindc1.merlin.local, and get 192.168.1.25 in response.
With an A record in place on the Bind9 server for merlin.local, this returns the correct IP, yes.

> Now just to make sure we understand what's going on, you have a DHCP server on the machine running BIND9. Does that provide addresses to machines in the AD domain? Do your zone files update automatically when a machine obtains an address?
That is correct, yes. My DHCPd server updates address via DDNS to the bind9 server. This DHCP server also provides address for all clients on the network, regardless of the domain they're in.

> What if you set up the AD server with a plain-vanilla configuration, let it assign some addresses, then run queries against it? Ask it to resolve a host in the ad.merlin.local domain
This side of things is working fine up to now. From my M$ DNS server I am able to resolve A records in ad.merlin.local correctly.

> ask it to return the PTR record for that host's IP address. If you can determine that the AD server is authoritative for ad.merlin.local, then you can work out how to integrate that with the Linux server. 
Looking up the PTR using dig from Windows returned NOERROR and correctly reported testwindc1.ad.merlin.local as the SOA for ad.merlin.local. Which sounds correct to me?

Thanks!

Joe

---

### Post by Barry Cent on 2011-05-01
Sorry to bump the thread, but has any one got any more input on this please?

Thanks,

Joe

---

### Post by SeijiSensei on 2011-05-01
> **Barry Cent said:**
> Sorry to bump the thread, but has any one got any more input on this please?

I read your last post as saying things were working properly.  Can you restate the problem you're having?  I'm now very unclear on what hosts and addresses the AD server is supposed to be resolving.  You say all the hosts get their addresses from the central DHCP server, and all their information is stored in that server's DNS via DDNS.  So what is the AD server supposed to be resolving?  What hosts are in ad.merlin.local that aren't in merlin.local?

Did delegation via the NS record not work?

---

### Post by Barry Cent on 2011-05-02
> **SeijiSensei said:**
> I read your last post as saying things were working properly.  Can you restate the problem you're having?  I'm now very unclear on what hosts and addresses the AD server is supposed to be resolving.  You say all the hosts get their addresses from the central DHCP server, and all their information is stored in that server's DNS via DDNS.  So what is the AD server supposed to be resolving?  What hosts are in ad.merlin.local that aren't in merlin.local?

Did delegation via the NS record not work?
Sorry my post wasn't clear and thank you for your continued effort and time.

The problem I am facing is that I am unable to resolve the IP for testwindc1.ad.merlin.local from machine which is on the merlin.local domain. When I try this, I receive an NXDOMAIN reply from dig. (This also applies for resolving other A records that are stored on the M$ DNS server _from_ machines which are on the merlin.local domain, so it's not just testwindc1.ad.merlin.local's A record that's affected, it's the whole subzone.)

As I said above, the AD server doesn't seem to have any problems resolving A records to address within the ad.merlin.local subzone, neither does the Bind9 server have any issues resolving hosts to addresses in the main merlin.local zone. Both servers are reporting that they are authoritative for the correct zones:
Bind9 server - authoritative and resolving addresses for merlin.local
M$ DNS  - authoritative and resolving addresses for ad.merlin.local

I hoped that DHCP from my Ubuntu server would be able assign addresses to client PC's in ad.merlin.local, and then update their own A records in the M$ DNS server's DB for that zone, which they are a part of and are assigned the .ad.merlin.local primary DNS suffix by default from AD. This theory seemed to work well when I previously had a system setup with two separate names spaces for Unix clients and domain joined Windows clients, so I am lead to believe this approach should work, even though it may not be the norm.

It may be clearer if I say what I ultimately want to achieve:
Ubuntu DHCPd server, providing addresses to all client machines (M$ & Linux).
Ubuntu Bind9 server hosting the merlin.local zone (for Linux machines).
M$ DNS server hosting the ad.merlin.local zone (for domain joined M$ clients).

Thank you,

Joe

---

### Post by Barry Cent on 2011-05-05
Hi,

Apologies for another bump, but I don't want this thread to get lost, as I've still not managed to suss out what's the problem with my setup unfortunately.

Has anyone got any ideas on the issue described above. Please let me know if you need any information from my config files/logs, etc.

Cheers,

Joe

---

### Post by koenn on 2011-05-05
that delegation + glue *should* work so i think it's time to go step- by step debugging until you find out where it fails. 

first, tell us how your delegation is set up - i.e are you now using this
```

TESTWINDC1		A	192.168.1.25
ad              IN      NS      TESTWINDC1.merlin.local.

```
```
or this 
ad.merlin.local.              IN      NS      TESTWINDC1.ad.merlin.local.
TESTWINDC1.ad.merlin.local.   IN      A       192.168.1.25
```

also, give us a name for the bind9 server, so we can say "on <name>, do <command;command;command>"


step 0 is check your bind conf. punctuation marks have meaning (eg  . ) and it's easy to get them wrong. There are tools to check this with - something like named-checkconf  and named-checkzone

step 1: see if each DNS server can resolve the other server's name, and see if you can get the relevant records (NS, in this case) from each server. (I can't phrase this question more clearly unless I know how your delegation is currently set up, re first question).

For this (and future) trouble shooting steps, it would be good if you post the exact commands you used, and the output you get. verbatim. 
like this```

~$ dig google.com NS

; <<>> DiG 9.7.0-P1 <<>> google.com NS
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52906
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	NS

;; ANSWER SECTION:
google.com.		30829	IN	NS	ns3.google.com.
google.com.		30829	IN	NS	ns4.google.com.
google.com.		30829	IN	NS	ns1.google.com.
google.com.		30829	IN	NS	ns2.google.com.

```

---

### Post by Barry Cent on 2011-06-05
Hi Koenn,

I have been trying to find the time to get the info you asked for. I hope I've included all the relevant info:

> 
first, tell us how your delegation is set up - i.e are you now using this
```

TESTWINDC1		A	192.168.1.25
ad              IN      NS      TESTWINDC1.merlin.local.
```

or this 
```

ad.merlin.local.              IN      NS      TESTWINDC1.ad.merlin.local.
TESTWINDC1.ad.merlin.local.   IN      A       192.168.1.25
```



I'm using this at the moment:
```
TESTWINDC1		A	192.168.1.25
ad              IN      NS      TESTWINDC1.merlin.local.

```

> also, give us a name for the bind9 server, so we can say "on <name>, do <command;command;command>"

Some information on my network that I believe to be useful:
_server.merlin.local_ is my Ubuntu Bind9 server. The IP of this server is _192.168.1.2_
_TestWinDC1.ad.merlin.local_ is a M$ AD DC, which runs an M$ DNS server that I have setup for this. The IP address of this server is [U]192.168.1.40
[/U]

> step 0 is check your bind conf. punctuation marks have meaning (eg . ) and it's easy to get them wrong. There are tools to check this with - something like named-checkconf and named-checkzone

```
joe@Server:~$ named-checkconf /etc/bind/named.conf
joe@Server:~$ 
```
```
joe@Server:~$ named-checkzone merlin.local /var/lib/bind/merlin.local.hosts
zone merlin.local/IN: loaded serial 1289878378
OK
joe@Server:~$
```

> 
step 1: see if each DNS server can resolve the other server's name, and see if you can get the relevant records (NS, in this case) from each server. (I can't phrase this question more clearly unless I know how your delegation is currently set up, re first question).

From my _Ubuntu_ server:

```
joe@Server:~$ dig merlin.local NS

; <<>> DiG 9.6.1-P2 <<>> merlin.local NS
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 36836
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;merlin.local.			IN	NS

;; ANSWER SECTION:
merlin.local.		300	IN	NS	server.merlin.local.

;; ADDITIONAL SECTION:
server.merlin.local.	38400	IN	A	192.168.1.2

;; Query time: 1 msec
;; SERVER: 192.168.1.2#53(192.168.1.2)
;; WHEN: Sun Jun  5 11:34:17 2011
;; MSG SIZE  rcvd: 67

```
```

joe@Server:~$ dig ad.merlin.local NS

; <<>> DiG 9.6.1-P2 <<>> ad.merlin.local NS
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51965
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 2

;; QUESTION SECTION:
;ad.merlin.local.		IN	NS

;; ANSWER SECTION:
ad.merlin.local.	2089	IN	NS	server.merlin.local.
ad.merlin.local.	2089	IN	NS	testwindc1.ad.merlin.local.

;; ADDITIONAL SECTION:
server.merlin.local.	38400	IN	A	192.168.1.2
testwindc1.ad.merlin.local. 2089 IN	A	192.168.1.40

;; Query time: 36 msec
;; SERVER: 192.168.1.2#53(192.168.1.2)
;; WHEN: Sun Jun  5 11:34:30 2011
;; MSG SIZE  rcvd: 111

```

From my M$ AD/DNS server:

```
PS C:\Users\Administrator\Downloads\BIND9.8.0> .\dig.exe merlin.local NS

; <<>> DiG 9.8.0 <<>> merlin.local NS
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22632
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;merlin.local.                  IN      NS

;; ANSWER SECTION:
merlin.local.           268     IN      NS      server.merlin.local.

;; ADDITIONAL SECTION:
server.merlin.local.    38368   IN      A       192.168.1.2

;; Query time: 31 msec
;; SERVER: 192.168.1.40#53(192.168.1.40)
;; WHEN: Sun Jun 05 11:10:40 2011
;; MSG SIZE  rcvd: 67
```

```
PS C:\Users\Administrator\Downloads\BIND9.8.0> .\dig.exe ad.merlin.local NS

; <<>> DiG 9.8.0 <<>> ad.merlin.local NS
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58443
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;ad.merlin.local.               IN      NS

;; ANSWER SECTION:
ad.merlin.local.        3600    IN      NS      testwindc1.ad.merlin.local.

;; ADDITIONAL SECTION:
testwindc1.ad.merlin.local. 3600 IN     A       192.168.1.40

;; Query time: 15 msec
;; SERVER: 192.168.1.40#53(192.168.1.40)
;; WHEN: Sun Jun 05 11:12:07 2011
;; MSG SIZE  rcvd: 74
```

Thank you for your continued help.

Cheers,

Joe

---

### Post by Barry Cent on 2011-06-05
Not sure if this highlights an issue somewhere, but I just ran
```
dig testwindc1.ad.merlin.local @192.168.1.2
```
from my client PC and I got the following in my syslog on server.merlin.local:
```
Jun  5 11:44:19 Server named[25390]: lame server resolving 'testwindc1.ad.merlin.local' (in 'ad.merlin.local'?): 192.168.1.2#53
Jun  5 11:44:19 Server named[25390]: enforced delegation-only for 'ad.merlin.local' (testwindc1.ad.merlin.local/AAAA/IN) from 192.168.1.40#53
Jun  5 11:44:20 Server named[25390]: enforced delegation-only for 'ad.merlin.local' (testwindc1.ad.merlin.local/A/IN) from 192.168.1.40#53
Jun  5 11:44:20 Server named[25390]: success resolving 'testwindc1.ad.merlin.local/A' (in 'ad.merlin.local'?) after reducing the advertised EDNS UDP packet size to 512 octets

```
However, the client PC wasn't given the IP address:
```
Joes-iMac:~ Joe$ dig testwindc1.ad.merlin.local @192.168.1.2

; <<>> DiG 9.6.0-APPLE-P2 <<>> testwindc1.ad.merlin.local @192.168.1.2
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 14928
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;testwindc1.ad.merlin.local.	IN	A

;; Query time: 809 msec
;; SERVER: 192.168.1.2#53(192.168.1.2)
;; WHEN: Sun Jun  5 11:53:22 2011
;; MSG SIZE  rcvd: 44

```

---

### Post by koenn on 2011-06-05
correct me if I'm wrong, but from your most recent posts I gather you now have 3 DNS servers : 

```

192.168.1.25  	TESTWINDC1.merlin.local. 		Windows DNS, NS for ad.merlin.local

192.168.1.40	TestWinDC1.ad.merlin.local 		M$ AD DC, which runs an M$ DNS 

192.168.1.2	server.merlin.local 	  		Ubuntu Bind9 server.   

```

If that's correct, I'm not supprized you're having problems
If it's not correct, maybe give the correct info so we can get this sorted out ?

---

### Post by Barry Cent on 2011-06-05
Hi Koenn,

TestWinDC1.ad.merlin.local used to have the IP ending .25 up to this week, but I had to change it to .40.

To confirm, there are only the two servers that I mentioned in my most recent post that are involved with this issue:

> server.merlin.local is my Ubuntu Bind9 server. The IP of this server is 192.168.1.2
TestWinDC1.ad.merlin.local is a M$ AD DC, which runs an M$ DNS server that I have setup for this. The IP address of this server is 192.168.1.40

Thanks,

Joe

---

### Post by koenn on 2011-06-12
on server, you've listed both server.merlin.local and testwindc1.ad.merlin.local as name servers for ad.merlin.local.

```
ad.merlin.local.	2089	IN	NS	server.merlin.local.
ad.merlin.local.	2089	IN	NS	testwindc1.ad.merlin.local.
```

so if you query server for names or addresses in ad.merlin.local, it will attempt to resolve them, and fail (because only testwindc1.ad.merlin.local) can resolve them. 

remove the line
ad.merlin.local.	2089	IN	NS	server.merlin.local.
restart the DNS server, then go through the troubleshooting steps again.

---

### Post by Barry Cent on 2011-06-12
I must admit, I'm not 100% sure why I was getting the output of 'dig ad.merlin.local NS' that you quoted in you last message.

So, I've checked through my records file for the existing merlin.local zone that server.merlin.local serves, and there is no mention of server.merlin.local being a name server for ad.merlin.local. Further more, I ran 'dig ad.merlin.local NS' again, and I'm now getting the expected output:

```
joe@Server:~$ dig ad.merlin.local NS

; <<>> DiG 9.6.1-P2 <<>> ad.merlin.local NS
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19021
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;ad.merlin.local.		IN	NS

;; ANSWER SECTION:
ad.merlin.local.	3559	IN	NS	testwindc1.ad.merlin.local.

;; ADDITIONAL SECTION:
testwindc1.ad.merlin.local. 3559 IN	A	192.168.1.40

;; Query time: 1 msec
;; SERVER: 192.168.1.2#53(192.168.1.2)
;; WHEN: Sun Jun 12 20:46:14 2011
;; MSG SIZE  rcvd: 74

joe@Server:~$ 
```

But I'm still not able to resolve hostnames to IP's in ad.merlin.local from a client that uses server.merlin.local as it's DNS server:
```
joe@Server:~$ dig testwindc1.ad.merlin.local

; <<>> DiG 9.6.1-P2 <<>> testwindc1.ad.merlin.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 35679
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;testwindc1.ad.merlin.local.	IN	A

;; Query time: 6 msec
;; SERVER: 192.168.1.2#53(192.168.1.2)
;; WHEN: Sun Jun 12 21:12:51 2011
;; MSG SIZE  rcvd: 44

joe@Server:~$

```

Just to confirm DNS is running ok on the M$ server I ran:
```
joe@Server:~$ dig testwindc1.ad.merlin.local @192.168.1.40

; <<>> DiG 9.6.1-P2 <<>> testwindc1.ad.merlin.local @192.168.1.40
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26600
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;testwindc1.ad.merlin.local.	IN	A

;; ANSWER SECTION:
testwindc1.ad.merlin.local. 3600 IN	A	192.168.1.40

;; Query time: 2 msec
;; SERVER: 192.168.1.40#53(192.168.1.40)
;; WHEN: Sun Jun 12 21:14:12 2011
;; MSG SIZE  rcvd: 60

joe@Server:~$
```

```
joe@Server:~$ dig test123.ad.merlin.local @192.168.1.40

; <<>> DiG 9.6.1-P2 <<>> test123.ad.merlin.local @192.168.1.40
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5020
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;test123.ad.merlin.local.	IN	A

;; ANSWER SECTION:
test123.ad.merlin.local. 3600	IN	A	192.168.1.222

;; Query time: 2 msec
;; SERVER: 192.168.1.40#53(192.168.1.40)
;; WHEN: Sun Jun 12 21:15:43 2011
;; MSG SIZE  rcvd: 57

joe@Server:~$
```

So that all seems ok...

Would it help at all if I were to provide some of my bind config files?

Thanks,

Joe

---

