---
title: "dhcp + dns server: unkown host with ping"
date: 2007-09-12
forum: Server Platforms
---

### Post by twistedtwig on 2007-09-12
Hi all.

I have been fighting with setting up a dhcp and dns server tonight.... think I have it working.. well at least it is creating the jnl files and can resolve one of the ubuntu boxes and a windows xp box (for some reason my laptop is not updating but I am leaving that till the morning)...

Anyway.  if I am on a my main ubuntu desktop box and type ping betty (that is the server) it resolves. (the /etc/resolv.conf file has:

search ponywars.local
nameserver 192.168.10.1


which I believe is correct.  anyway the local dns is ponywars.local and the ip is the static internal network card on the server.

But if i try and ping ubuntuwiggly from the server I get unknown host. (Ubuntuwiggly is the ubuntu box I just did the ping from) 

is this because it is looking on the internet for the answer?  its resolv.conf is:

search ponywars.local
nameserver 194.74.65.69

I have tried changing the nameserver to the local IP also adding another line to it but with no luck.

Thank you for any and all help

---

### Post by netlogic on 2007-09-13
I am little confused by your question. It could be it is really late here. It could be a common mistake of one machine resolving names through netbios and other one through DNS.

In Linux, you have use nmblookup to resolve name by Netbios and use nslookup to  resolve name by DNS and host file. 2000/xp/2003 will resolve name through both.
When you use ping in Windows, it could have resolved through broadcast, wins, or DNS. Look into nbtstat in windows to see how you are resolving your name. Look at your netbios cache by "nbtstat -c" If you want to see if your netbios name is registered to wins, "nbtstat -n" In a hybrid LAN environment, you will have two name schemes to deal with, but there is a way to totally turn off Netbios scheme, but some apps will break.

---

### Post by twistedtwig on 2007-09-13
Sorry I think I may have been a bit confusing (was 2am ish when I wrote it).

server = Ubuntu lamp server.  name= "betty"

Betty = Fiesty- the server (dhcp, dns, lamp)

ubuntuwiggly = desktop computer = Fiesty

Felix = ubuntu 6.06

bobby = windows 2003 server (does not do the dhcp or dns, default install)

ubuntuwiggly can ping betty and it now resolves (didn't before playing with bind and dhcp last night). but it can not ping felix or bobby.

betty can not ping anyone though. 

My issue (at the moment) is trying to get betty to be able to use her own dns info to resolve names on her network.

I hope this is a bit clearer

---

### Post by primski on 2007-09-13
You say you got static ip configured on server box? and outter dns is in that /etc/resolv.conf?

well, here's your problem....either put your internal DNS in that resolv.conf or have it ip assigned dynamicly. you can even set your dhcp to give it fixed address so server will always have the same ip.

---

### Post by twistedtwig on 2007-09-13
Sorry I think I understand but not 100%.

the server has two nic cards:

eth0 is the external card and gets its IP dynamically from the ISP.

eth1 is the internal card and set to 192.168.10.1 statically.

I tried to add 

nameserver 192.168.10.1

into resolv.conf but it was removed almost instantely.

I don't get how having eth1 dynamic (but using the mac to keep it static) would solve it... OH.. does it mean that it would add it self to the dhcp and dns list because it makes a call to get its IP?

Thank you for your help

---

### Post by twistedtwig on 2007-09-13
can I just confirm, 99/9% sure this is right:

to give a sudo static IP when using dhcp I would put:

host betty {
  hardware ethernet 12:34:56:78:12:34;
  fixed-address 192.168.10.1;
}

into dhcp3/dhcpd.conf

where betty is the name of the computer and the IP address is what I want it to have and the other bit is the mac address.

naturally this IP needs to be out of the range of the dhcp.

Thanks

---

### Post by primski on 2007-09-13
yes, that is correct dhcp entry, tho you need a dns entry to successfully ping 'betty'. just an entry in dhcp does not resolve to the corresponding ip.

but, hold for one second,

you got dhcp server on betty, which is the same machine u run dns on...so basicly you are trying to assign ip to the server itself and then ping it localy? remind me again, what is the purpose of this?

i'd do it this way, unless u want to run a router and a firewall on your server, you don't need two NIC's... just create an eth alias and give it another ip manualy.

then install tinydns and dnscache and have it serve its dns entries only to local networks' requests.

and this is pretty much it, in theory it should work but in practice....its been a long time since i've done it so i cant give u step-by-step procedures but im here to help any theoretical questions tho ;)

best of luck

---

### Post by twistedtwig on 2007-09-13
betty connects directly to the internet.  it has the modem going directly into her to give her the external IP.

on her I have dhcp dns and apache running (web site is accessable to the rest of the world).

The reason I have two nics (didn't fully get your thing, will re read that in a mo).... is as follows.

the first (eth0) deals with external IP the second goes to the internal wireless router to dis out the LAN to my various computers and network DVD player etc.

The original reason for this post was because the server (betty) could not ping anyone "else" on the lan.  ubuntuwiggly can resolv names on the lan but betty can not even resolv ubuntuwiggly.

(Hope that made sense)

---

### Post by primski on 2007-09-13
aha, so you got another router behind betty, missed that part sorry.

do you have another private network configure under router? if thats the case, this could be the problem, because betty cannot resolve to that network, you would need to set your router the way it would let these packets thru.

if you ping from ubuntuwiggly, he first goes to betty to get the ip of the comp ur pinging, he gets it and can successfully ping it, becaue the target computer is on the same network as ubuntuwiggly, but not the other way around, betty does get ip which to ping but cannot actually ping it, cause router probably blocks it.

what dns servers do you have configured on router ?

---

### Post by NIT006.5 on 2007-09-13
First off, I would suggest using Webmin ([http://www.webmin.com](http://www.webmin.com)) as this made life much easier for me when setting up DHCP/DNS. 

I know some of these questions might seem irrelevant if things seem to be working for other hosts, but I can't think of any logical reasons for the problem you seem to be having, so maybe it's better to start at the bottom?

Have you configured a static IP for the server in the zone's host file? If you've done this you shouldn't need to worry about using the mac address and DHCP to keep it static - you could go with your current static IP and just add the A and PTR records to the zone files. Well it's an option anyway. Also, are the SOA and NS records set up in the zone's hosts file? Of course if you manually edit the dynamic zone files you'll probably have to delete the jnl files and possibly restart named or reload the zone (if I remember correctly?).

Even if the server doesn't have it's own DNS record though, I'm sure it should still be able to resolve other host names in the zone as long it's pointing to itself for dns. As a matter of interest, have you checked the log files to be sure that dhcp is actually succeeding when it tries to create the journal entries? Have you set up reverse lookups as well, and if so are those also not working from the server?

The server will have to have its own IP in /etc/resolve.conf - otherwise it definitely won't be able to resolve internal addresses. When you say you tried this with no luck, what exactly happened? As far as I know, you would ONLY have the internal dns server's address listed in resolve.conf, and then you would configure named to either do internet lookups directly to the root dns servers OR to forward internet lookups to your ISP's dns server. i.e. ALL hosts on your network (including the server itself) would look to your internal DNS server to resolve all addresses... any that don't belong to your network it would forward and then return the response when it gets one. 

Not sure if I've understood the problem correctly though - let me know if any of that is useful.

---

### Post by twistedtwig on 2007-09-13
firstly thank you for all your help! :)

I am at work at the moment so can not access my files to show you their content but will tonight.

primski

the router is a netgear router than does NOT do the DHCP as far as I can tell it just passes all the information through it to the server.  There are actually 3 routers in total.  betty passes the connection from eth1 (internal static 192.168.10.1) to the netgear wireless router which has two wired connections coming off of it.  These run to a router each in different rooms for things like my main comp area and ps2 and dvd player area.

NIT006.5

I tried webmin a long time ago and buggered it up a bit and since the new install had not tried it. but may give it ago.

"Have you configured a static IP for the server in the zone's host file? "

Not sure what you mean by this.  in the /etc/network/interfaces file eth1 is static, but do you mean in /etc/bind/ "some file in here"  Reading further I presume you mean bind... I can not recall the EXACT config without seeing it so will have to wait till I get home but I do remember having a PTR record for sure but don't want to mislead with almost acurate info

the two jnl files are being created.  (this took a while had silly errors and syslog, messages and daemon.log helped me figure them out).  as far as I can tell forward and reverse map is being done.  Again will do some dumps of those logs tonight.

When I tried to edit the /etc/reslv.conf file on betty (server) I would change the name-server to 192.168.10.1 I also tried adding an extra line so leaving the external IP there... Let me explain that better.

normally it has soething like:

search ponywars.local
name-server 194.75.bleh.bleh

I change the name-server to local IP.  I save it.. go back into it and see it is saved.  Leave it for a few mins then go into it and it has reverted back to the external IP (which I think is BT's name server).

---

### Post by NIT006.5 on 2007-09-13
Ya we've obviously got some differences in our setups. e.g. my files are
/var/named/chroot//etc/named.conf
/var/named/chroot/var/named/"all hosts files here"

But yes, bind/named, I mean the same thing. Also my DHCP/DNS is currently running on Fedora Core 6, not Ubuntu - not sure if that makes a difference?

The only issue I've had with Webmin is that it does seem to screw things up a little when you use it to manually add records to DYNAMIC zone files. Then it causes the whole zone to crash. But for the actual setup and config, webmin should be cool. If I need to manually edit any of my static dns records, I do it manually via text editor, but you should have no problems doing most other things through webmin.

To explain what I meant about a static record for the server:

I have all machines on the network obtaining their addresses from DHCP except for the two servers, my PC, a networked copier, a diskstation and the router. For all of these, I have static IPs. To make sure that I can still use friendly names for them (.e.g. ping ds, or ping router, etc.) I have manually created static records for them in the zone files. So, my hosts file starts something like this:

$ORIGIN .
$TTL 38400      ; 10 hours 40 minutes
exampledomain.co.zw IN SOA  ns.exampledomain.co.zw. root.exampledomain.co.zw. (
                                1165231639 ; serial
                                10800      ; refresh (3 hours)
                                3600       ; retry (1 hour)
                                604800     ; expire (1 week)
                                38400      ; minimum (10 hours 40 minutes)
                                )
                        NS      srv1.exampledomain.co.zw.
                        NS      srv2.exampledomain.co.zw.
$ORIGIN exampledomain.co.zw.
$TTL 38400      ; 10 hours 40 minutes
srv1                A       192.168.205.1
srv2                A       192.168.205.2
ns                   A        192.168.205.1
                       A        192.168.205.2
ds                   A        192.168.205.3
copier             A         192.168.205.7
router             A         192.168.205.8

(The ns A record just means that if anyone does a "nslookup ns.exampledomain.co.zw" it will return both addresses, or if they ping ns they will get a response from one of the servers - named alternates between the two servers for this. You don't need the ns record obviously. You just need the "actual" address records for the servers, in this case srv1 and srv2)

These static addresses are outside the dhcp pool obviously. So basically, you would just keep your current setup of static IP for the server (and any other hosts) and manually add A records to the host file (something like those above). The dynamic records are added to the same hosts file when dhcp issues a lease, but the static records remain untouched because named can tell that they weren't created dynamically. 

Of course, the same sort of thing applies in the reverse lookup hosts file (and you would have to manually create the PTR records):

$ORIGIN .
$TTL 38400      ; 10 hours 40 minutes
205.168.192.in-addr.arpa IN SOA ns.exampledomain.co.zw. root.205.168.1
92.in-addr.arpa. (
                                1165225793 ; serial
                                10800      ; refresh (3 hours)
                                3600       ; retry (1 hour)
                                604800     ; expire (1 week)
                                38400      ; minimum (10 hours 40 minutes)
                                )
                        NS      srv1.exampledomain.co.zw.
                        NS      srv2.exampledomain.co.zw.
$ORIGIN 205.168.192.in-addr.arpa.
1                       PTR     srv1.exampledomain.co.zw.
2                       PTR     srv2.exampledomain.co.zw.
3                       PTR     ds.exampledomain.co.zw.
7                       PTR     copier.exampledomain.co.zw.
8                       PTR     router.exampledomain.co.zw.

As I said before though, the server should still be able to resolve other addresses even if it doesn't have it's own A/PTR record. This would only be useful for the other hosts to be able to resolve the server's name. So if the server can't do lookups, I'm pretty sure that's to do with your resolv.conf issue. Personally I've never experienced what you describe i.e. resolv.conf being modified automatically after you've changed it. Are you running any software that could be doing that? I'm afraid I have no idea what could be causing that. Will think about it though. Unfortunately, I'm not expert on this either - I can only offer suggestions based on my own limited experience.

In summary: all this stuff about A records was just to explain what I meant, and to demonstrate an alternative to setting fixed addresses in DHCP using mac addresses. However, I don't think this is related to your current problem, which from what I can see MUST be because of the resolv.conf "ghost in the machine".

---

### Post by twistedtwig on 2007-09-13
Ok so to start with I am going to give my full bind setup:

```

jon@betty:/etc/bind$ ls -l
total 56
-rwxrwxr-x 1 root bind  237 2007-02-20 13:40 db.0
-rwxrwxr-x 1 root bind  271 2007-02-20 13:40 db.127
-rwxrwxr-x 1 root bind  237 2007-02-20 13:40 db.255
-rwxrwxr-x 1 root bind  353 2007-02-20 13:40 db.empty
-rwxrwxr-x 1 root bind  256 2007-02-20 13:40 db.local
-rwxrwxr-x 1 root bind 1507 2007-02-20 13:40 db.root
-rwxrwxr-x 1 root bind 1699 2007-09-12 22:14 named.conf
-rwxrwxr-x 1 root bind  799 2007-09-12 22:40 named.conf.local
-rwxrwxr-x 1 root bind  165 2007-07-26 22:31 named.conf.local_original
-rwxrwxr-x 1 root bind 1457 2007-07-26 22:34 named.conf.options
-rwxrwxr-x 1 root bind 1458 2007-07-26 22:32 named.conf.options_original
-rwxrwxr-x 1 bind bind   77 2007-07-26 19:41 rndc.key
drwxrwxr-x 2 root bind 4096 2007-09-13 20:03 zones
-rwxrwxr-x 1 root bind 1317 2007-02-20 13:40 zones.rfc1918

```

```
jon@betty:/etc/bind$ cd zones/
jon@betty:/etc/bind/zones$ ls -l
total 20
-rw-r--r-- 1 bind bind  586 2007-09-13 20:03 ponywars.local.db
-rw-r--r-- 1 bind bind 4530 2007-09-13 19:49 ponywars.local.db.jnl
-rw-r--r-- 1 bind bind  442 2007-09-13 20:02 rev.10.168.192.in-addr.arpa
-rw-r--r-- 1 bind bind 3396 2007-09-13 19:49 rev.10.168.192.in-addr.arpa.jnl
jon@betty:/etc/bind/zones$ 

```

named.conf:

```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

// zone "com" { type delegation-only; };
// zone "net" { type delegation-only; };

// From the release notes:
//  Because many of our users are uncomfortable receiving undelegated answers
//  from root or top level domains, other than a few for whom that behaviour
//  has been trusted and expected for quite some length of time, we have now
//  introduced the "root-delegations-only" feature which applies delegation-only
//  logic to all top level domains, and to the root domain.  An exception list
//  should be specified, including "MUSEUM" and "DE", and any other top level
//  domains from whom undelegated responses are expected and trusted.
// root-delegation-only exclude { "DE"; "MUSEUM"; };

include "/etc/bind/named.conf.local";

controls {
	inet 127.0.0.1 allow {127.0.0.1; 192.168.10.1; } keys { "rndc-key"; } ;
};
```

named.conf.local:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
include "/etc/bind/rndc.key";

# This is the zone definition. replace example.com with your domain name
zone "ponywars.local" {
        type master;
        file "/etc/bind/zones/ponywars.local.db";
	allow-update { key "rndc-key"; };
        allow-transfer { 192.168.10.0/24; }; 
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "10.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.10.168.192.in-addr.arpa";
     allow-update { key "rndc-key"; };
     allow-transfer { 192.168.10.0/24; }; 
};

```

named.conf.options
```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	// query-source address * port 53;

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	 forwarders {
	 	194.74.65.69;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };

	// By default, name servers should only perform recursive domain
	// lookups for their direct clients.  If recursion is left open
	// to the entire Internet, your name server could be used to
	// perform distributed denial of service attacks against other
	// innocent computers.  For more information on DDoS recursion:
	// http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987

	allow-recursion { localnets; };

	// If you have DNS clients on other subnets outside of your
	// server's "localnets", you can explicitly add their networks
	// without opening up your server to the Internet at large:
	// allow-recursion { localnets; 192.168.0.0/24; };

	// If your name server is only listening on 127.0.0.1, consider:
	// allow-recursion { 127.0.0.1; };
};

```

zones/ponywars.local.db
```
$ORIGIN .
$TTL 86400	; 1 day
ponywars.local		IN SOA	betty.ponywars.local. admin.ponywars.local. (
				77         ; serial
				604800     ; refresh (1 week)
				86400      ; retry (1 day)
				2419200    ; expire (4 weeks)
				86400      ; minimum (1 day)
				)
			NS	betty.ponywars.local.
$ORIGIN ponywars.local.
$TTL 300	; 5 minutes
awmgnlbjakq0		A	192.168.10.197
			TXT	"3179482bb4d21a0f2e835585da4cf655ca"
$TTL 86400	; 1 day
betty			A	192.168.10.1
$TTL 300	; 5 minutes
UbuntuWiggly		A	192.168.10.200
			TXT	"00c6897fa17801724b3fe979ac398a4924"
$TTL 86400	; 1 day
www			A	192.168.10.1
```

rev.10.168.192.in-addr.arpa
```
$ORIGIN .
$TTL 86400	; 1 day
10.168.192.in-addr.arpa	IN SOA	betty.ponywars.local. admin.ponywars.local. (
				11         ; serial
				604800     ; refresh (1 week)
				86400      ; retry (1 day)
				2419200    ; expire (4 weeks)
				86400      ; minimum (1 day)
				)
			NS	betty.ponywars.local.
$ORIGIN 10.168.192.in-addr.arpa.
1			PTR	betty
$TTL 300	; 5 minutes
197			PTR	awmgnlbjakq0.ponywars.local.
200			PTR	UbuntuWiggly.ponywars.local.
```

---

### Post by twistedtwig on 2007-09-13
For some reason beyond me I can not ping ubuntuwiggly from betty.  

I also have a normal xp box called "home" which uses the wireless which I can ping and a vm xp inside ubuntuwiggly which I can also ping (once I removed the firewalll in xp).

But I also have a laptop with ubuntu 6.06 on and that is getting its IP dynamically through the wire (lan) and it for some reason is not being added to the dns records as I can not ping it from anywhere.  

I also have a windows 2003 server inside the network that I can not ping. (not sure if its windows servery stuff getting in the way there as it does not have the same DNS suffice search list (it has its own) where as the other xp machines have ponywars.local.

I am not worried about the 2003 box but the laptop is very odd and confusing.  I feel very close but still cant touch that moment of complete dns' "nuss"

---

### Post by twistedtwig on 2007-09-13
when I do a release renew on the vmwiggly I get the following in daemon.log

```
Sep 13 22:50:30 betty named[3949]: client 192.168.10.1#32770: updating zone 'ponywars.local/IN': deleting an RR
Sep 13 22:50:30 betty named[3949]: client 192.168.10.1#32770: updating zone 'ponywars.local/IN': deleting an RR
Sep 13 22:50:30 betty named[3949]: client 192.168.10.1#32770: updating zone '10.168.192.in-addr.arpa/IN': deleting rrset at '173.10.168.192.in-addr.arpa' PTR
Sep 13 22:50:34 betty named[3949]: client 192.168.10.1#32770: updating zone 'ponywars.local/IN': adding an RR at 'vmwiggly.ponywars.local' A
Sep 13 22:50:34 betty named[3949]: client 192.168.10.1#32770: updating zone 'ponywars.local/IN': adding an RR at 'vmwiggly.ponywars.local' TXT
Sep 13 22:50:34 betty named[3949]: client 192.168.10.1#32770: updating zone '10.168.192.in-addr.arpa/IN': deleting rrset at '173.10.168.192.in-addr.arpa' PTR
Sep 13 22:50:34 betty named[3949]: client 192.168.10.1#32770: updating zone '10.168.192.in-addr.arpa/IN': adding an RR at '173.10.168.192.in-addr.arpa' PTR

```

in messages:

```
Sep 13 22:50:30 betty dhcpd: if vmwiggly.ponywars.local IN TXT "31ee19af10eb67224c79d91f87d1bd0033" rrset exists and vmwiggly.ponywars.local IN A 192.168.10.173 rrset exists delete vmwiggly.ponywars.local IN A 192.168.10.173: success.
Sep 13 22:50:30 betty dhcpd: if vmwiggly.ponywars.local IN A rrset doesn't exist delete vmwiggly.ponywars.local IN TXT "31ee19af10eb67224c79d91f87d1bd0033": success.
Sep 13 22:50:30 betty dhcpd: removed reverse map on 173.10.168.192.in-addr.arpa.
Sep 13 22:50:30 betty dhcpd: DHCPRELEASE of 192.168.10.173 from 00:0c:29:08:62:61 (vmwiggly) via eth1 (found)
Sep 13 22:50:33 betty dhcpd: DHCPDISCOVER from 00:0c:29:08:62:61 via eth1
Sep 13 22:50:34 betty dhcpd: DHCPOFFER on 192.168.10.173 to 00:0c:29:08:62:61 (vmwiggly) via eth1
Sep 13 22:50:34 betty dhcpd: Added new forward map from vmwiggly.ponywars.local to 192.168.10.173
Sep 13 22:50:34 betty dhcpd: added reverse map from 173.10.168.192.in-addr.arpa. to vmwiggly.ponywars.local
Sep 13 22:50:34 betty dhcpd: DHCPREQUEST for 192.168.10.173 (192.168.10.1) from 00:0c:29:08:62:61 (vmwiggly) via eth1
Sep 13 22:50:34 betty dhcpd: DHCPACK on 192.168.10.173 to 00:0c:29:08:62:61 (vmwiggly) via eth1

```

but when I do a /etc/init.d/networking restart   in the laptop i only get:

syslog:
```
Sep 13 22:53:27 betty dhcpd: DHCPRELEASE of 192.168.10.198 from 00:d0:59:34:17:7c via eth1 (found)
Sep 13 22:53:28 betty dhcpd: DHCPDISCOVER from 00:d0:59:34:17:7c via eth1
Sep 13 22:53:28 betty dhcpd: DHCPOFFER on 192.168.10.198 to 00:d0:59:34:17:7c via eth1
Sep 13 22:53:28 betty dhcpd: DHCPREQUEST for 192.168.10.198 (192.168.10.1) from 00:d0:59:34:17:7c via eth1
Sep 13 22:53:28 betty dhcpd: DHCPACK on 192.168.10.198 to 00:d0:59:34:17:7c via eth1

```

is there a release renew type thing in linux?  am I completely mad?

the resolv.conf does have (on laptop)

search ponywars.local
nameserver 192.168.10.1

---

### Post by NIT006.5 on 2007-09-14
> **twistedtwig said:**
> For some reason beyond me I can not ping ubuntuwiggly from betty.  

I also have a normal xp box called "home" which uses the wireless which I can ping and a vm xp inside ubuntuwiggly which I can also ping (once I removed the firewalll in xp).

But I also have a laptop with ubuntu 6.06 on and that is getting its IP dynamically through the wire (lan) and it for some reason is not being added to the dns records as I can not ping it from anywhere.  

I also have a windows 2003 server inside the network that I can not ping. (not sure if its windows servery stuff getting in the way there as it does not have the same DNS suffice search list (it has its own) where as the other xp machines have ponywars.local.

I am not worried about the 2003 box but the laptop is very odd and confusing.  I feel very close but still cant touch that moment of complete dns' "nuss"

When you say you can't ping, does that only apply to the host name? Can you ping the IP? For the one that's not being added to dns, what do the logs on the server say?

---

### Post by NIT006.5 on 2007-09-14
Sorry, posted the previous message before I had seen your logs.

Are there no entries at all in the messages log for the laptop? Surely if it's failing it should tell you there....

---

### Post by twistedtwig on 2007-09-14
Sorry that was misleading of me.. yes when I say ping i mean it does not resolve the name. I can ping the IP.

I can not see anything in syslog, messages or daemon.log about it failing just the HDCP part.  Makes no sense to me

---

### Post by NIT006.5 on 2007-09-14
Ok, this is just a shot in the dark because I'm also pretty baffled, but is there any chance that dhcp has any "special" options set for this client that is maybe causing it to NOT create a DNS entry? Did you define each host in dhcp, or does it accept requests from all clients whether they're known or unkown? If you've defined each, then it might be an option set for that client alone.

If it was attempting to create the journal entry and failing, it should definitely show that in the logs, so if there's nothing there, then all I can think is that it's not actually attempting to add the dns record for some reason - and as far as I know, that would have to be tied to the dhcp config. Of course, I could be completely off track though. Just a thought.

---

### Post by twistedtwig on 2007-09-14
I didn't change much of the DHCP at all.. I have not set anything for the laptop or anything else to behave differently.

I will have to compare the two ubuntu desktop boxes doing /etc/init.d/networking restart and see what the differences are.



(heheh.. I keep pressing TAB when I type those commands in here and surprise surprise it doesn't work!!!!!)

---

### Post by twistedtwig on 2007-09-16
WE HAVE LIFT OFF!!!!

on felix (laptop that would not update dns) had send host-name commented out where as the desktop didn't.  When I uncommented it and put its host name in there it seemed to work.

Not 100% sure why it worked but it DID!!!!

Thank you for all your help.  I am very pleased now :)

---

