---
title: "DHCP should send automatic DNS entry"
date: 2008-12-01
forum: Server Platforms
---

### Post by MaindotC on 2008-12-01
I'd like to know how to set DHCP or DNS so when a client joins a network and receives DNS information - DNS servers, default gateway, all that good stuff - the DNS records are automatically updated to create an entry for the client that joined the network.

For example, my campus has a domain name of morrisville.edu.  The network primarily consists of windows machines and is managed with active directory.  If I plug my non-domain Ubuntu machine into the network, I receive DHCP information and I can now type:
```

nslookup <my_hostname>

```
And it will reply with
```

<my_hostname>.morrisville.edu

```
and my current IP address.  I can also do an nslookup of my ip address and it will return my machines host name.

How do you do this in Ubuntu?  I've already installed dhcp3-server and bind and have them configured - they issue DHCP information correctly and resolve names correctly providing I have the proper entries in DNS.  But if I join a new client to the network, after receiving DHCP information I can't resolve that client's hostname or IP address unless I make a new entry in DNS.  So how do I enable that, if it's possible?  Is this a Windows only thing?  Thanks!

---

### Post by doas777 on 2008-12-01
according to [this]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html") you need to add a line like the following to /etc/dhcp3/dhcpd.conf
(replace the ns names with your bind servers IP address(es))
```

option domain-name-servers ns1.example.org, ns2.example.org;

```


also make sure you have bind forwarding to an ISP dns for NXs. you set that in bind.conf.options.

this thread looks like it may help with your automatic registration problem:
[http://ubuntuforums.org/showthread.php?t=267974](http://ubuntuforums.org/showthread.php?t=267974)

hope that helps

---

### Post by MaindotC on 2008-12-01
Thanks for replying.  I'm familiar with this article and I do have my dhcpd.conf file configured to send out the DNS servers to the clients.  The clients do show the name servers in /etc/resolv.conf.  They can resolve names and addresses just fine but ONLY if there are correlating entries in DNS.  The client can't resolve his or her hostname and/or ip address unless I got into DNS, add an entry, and then restart DNS.  It's not a HUGE hassle but I'm sure there's a way to automate it.

---

### Post by lswb on 2008-12-01
I believe you would need to set up some type of dns server on your local network. There are several available in the repositories, e.g dnsmasq and maradns. Search synaptic for "dns" to find more. The dnsmasq description says it can do both dhcp and dns for a local net which might make it a good choice. There are some that use ldap/active directory too.

Your campus net must have something like this running. I'm curious if your computer and another using the same hostname were both plugged in at the same time, what would happen?

---

### Post by bab1 on 2008-12-01
What you are attempting to do in BIND is doable.  See [**here**]("http://www.opensourcebrooklyn.com/?q=node/25") and [**here**]("http://jim.studt.net/depository/index.php/dynamic-dns-in-bind9").

As usual, YMMV.

---

### Post by MaindotC on 2008-12-01
lswb - I've thought of that as well and what happens is they both resolve to the same address.  I've done this - I installed Ubuntu on a virtual machine, bridged the VM to an interface, and plugged that into the campus network.  The host machine was using the wireless and the VM was using the wired.  They both had different ip addresses and the same hostname.  When I did an nslookup it just returned both addresses.  When I did an nslookup for the machine name for some reason it returned the first ip address listed in the previous step.

bab1 - thank you for your reply.  I'm familiar with this "send host-name" feature, but I was hoping there would be a way for clients to do that without going into their machines and configuring it.  I believe what you suggested is what I'm looking for.  Thank you for your help!

---

### Post by doas777 on 2008-12-02
whats your named.conf.local look like?

---

### Post by MaindotC on 2008-12-03
Sorry for the delay in replying - I have DHCP/DNS running on Fedora in a VM on VirtualBox and all I'm trying to do is copy those files to my USB drive and that is just unbelievably difficult.  The VM won't detect my USB drive, even after I enabled it, and creating a shared folder doesn't help because Fedora says it doesn't know vboxfs or vboxsf (when mounting) and I installed Guest Additions and still no luck.  I may have to manually re-type everything.

---

### Post by MaindotC on 2008-12-09
Ok, finally got named.conf.  I don't use ".local" as you specified - just my preferred naming scheme.  I couldn't get the shared folder to work with a fedora vm so I had to plug the ethernet cable into both NIC's and sftp into it :p  So 1.0 but hey it worked:
```

//
// named.caching-nameserver.conf
//
// Provided by Red Hat caching-nameserver package to configure the
// ISC BIND named(8) DNS server as a caching only nameserver 
// (as a localhost DNS resolver only).
//
// See /usr/share/doc/bind*/sample/ for example named configuration files.
//
// DO NOT EDIT THIS FILE - use system-config-bind or an editor
// to create named.conf - edits to this file will be lost on 
// caching-nameserver package upgrade.
//

options {
	listen-on port 53 { 10.2.1.3; };
	listen-on-v6 port 53 { ::1; };
	directory 	"/var/named";
	dump-file 	"/var/named/data/cache_dump.db";
        statistics-file "/var/named/data/named_stats.txt";
        memstatistics-file "/var/named/data/named_mem_stats.txt";
//	allow-query     { localhost; };
	recursion yes;
};

logging {
        channel default_debug {
                file "data/named.run";
                severity dynamic;
        };
};

zone "." IN {
	type hint;
	file "named.ca";
};

zone "galt.com" IN {
	type master;
	file "named.galt.com";
};

zone "1.2.10.in-addr.arpa" IN {
	type master;
	file "named.1.2.10";
	allow-update {none;};
};

include "/etc/named.rfc1912.zones";

```
named.galt.com:
```

$TTL 3h
@	IN	SOA	ns1.galt.com. none.none.com. (
		20080215; Serial
		28800 ; Refresh
		14400 ; Retry
		3600000; Expire
		86400 ); Minimum
	IN	NS	ns1
	IN	A	10.2.1.3

ham-rtr		IN	A	10.2.1.1
ham-sw		IN	A	10.2.1.2
ns1		IN	A	10.2.1.3
ns2		IN	A	10.1.1.10
www		IN	A	10.2.1.4
ids		IN	A	10.2.1.4
rt		IN	A	10.2.1.4
nsa-ptrt	IN	A	10.2.1.4
nsa-intranet	IN	A	10.2.1.5
nsa-ids		IN	A	10.2.1.6
nsa-printer	IN	A	10.2.1.7

```
and reverse lookup named.1.2.10:
```

$TTL 3h
@	IN	SOA	ns1.galt.com. none.none.com. (
				2002072100 ; Serial
				28800 ; Refresh
				14400 ; Retry
				3600000 ; Expire
				86400 ); Minimum
	IN	NS	ns1
1	IN	PTR	ham-rtr.galt.com
2	IN	PTR	ham-sw.galt.com
3	IN	PTR	ns1.galt.com
4	IN	PTR	nsa-ptrt.galt.com
4	IN	PTR	ids.galt.com
4	IN	PTR	rt.galt.com
5	IN	PTR	nsa-intranet.galt.com
6	IN	PTR	nsa-ids.galt.com
7	IN	PTR	nsa-printer.galt.com

```
And of course I had a named.1.1.10 but I doubt you'd need to see that.

---

### Post by koenn on 2008-12-09
> **bab1 said:**
> What you are attempting to do in BIND is doable.  See [**here**]("http://www.opensourcebrooklyn.com/?q=node/25") and [**here**]("http://jim.studt.net/depository/index.php/dynamic-dns-in-bind9").

As usual, YMMV.
unless you're already married to bind9 and dhcpd, you might want to have a look at dnsmasq. It's a simple dns+dhcp server in one, so it has no problem updating dns with address/hostname pairs.
You would still need to have the hosts send their hostname when requesting a dhcp lease (or let dhcp assign hostnames to dhcp clients ?) otherwise how would it be possible to match hostnames to addresses ?

The difficulty with bind and dhcp3 is that you expect one process (dhcp3) to write into the config files of another process (bind). Unix/Linux's security model aims at preventing that. There is a solution that involves sharing a secret between bind and dhcpd so that there's at least some form of control when dhcpd wants to add entries in bind's zone file. That's what makes it harder to set up, but it is doable.

The windows solution is that the dhcp server, or even any random workstation that has gotten an address lease, can write to the dns server's zone file, no questions asked. In light of the sort of spoofing and hijacking you can set up when you have this sort of access to a DNS server, this is not a very secure arrangement.

---

### Post by MaindotC on 2008-12-09
I'm just trying to replicate something I see happen in windows DNS/DHCP.  I'm not sure if it's some sort of add-on or if it's actually part of the dns/dhcp packages.  It just boggled my mind that this stuff automatically happened in windows but I couldn't figure how to get it working in *nix.  I'll try it out in vm's for practise and see how it goes.  Just been busy w/ finals right now.  Thanks for staying up on the thread.

---

### Post by netztier on 2008-12-12
> **koenn said:**
> 
The difficulty with bind and dhcp3 is that you expect one process (dhcp3) to write into the config files of another process (bind). 

There is no need to have the DHCP-server write into the config files of the DNS server (and subsequently restart it). That would be a Bad Thing [TM], I agree.

[COLOR="Red"]*Edit: this post is just noise. What I suggest here's already been suggested by bab1 in [http://ubuntuforums.org/showpost.php?p=6291763&postcount=5](http://ubuntuforums.org/showpost.php?p=6291763&postcount=5). Credits should go to him.*
[/COLOR]

Still, the DHCP server can issue a DDNS RR update (Dynamic DNS Ressource Record) to the DNS [1]. To do so, it will in general have to:

[LIST]
[*]learn the hostname or FQDN from the DHCP client - there's probably no way around this: the client will have to submit it in it's DHCP-DISCOVER or -REQUEST messages.
[*]look up the SOA record for the client's domain
[*]determine the client domain's NS records
[*]send DDNS updates to these NSs.
[/LIST]

In turn, these DNSs will of course have to be configured to accept DDNS updates for that particular domain. Update messages can be signed with a shared secret or key, so the DNS server has some means of verifying the trust relationship to the DHCP server.

This being said, it is of course also thinkable (but not necessarily recommended) that the client itself send a DDNS update to the nameserver of it's domain. Windoze used to have (still has?) a checkbox somewhere deep in it's TCP/IP config to do exactly that. I can't go through the depths of a dhcpclient.conf right now, but maybe there's something similar in there?

As for the server part: you might want to look here: This is for Debian allright, but what works there should work on ubuntu as well.

[http://www.debian-administration.org/articles/343](http://www.debian-administration.org/articles/343)

regards

Marc



[1] although similar in nature, do not confuse this with DynDNS.com and other services of that kind - they work quite differently.

---

### Post by koenn on 2008-12-12
> **netztier said:**
> There is no need to have the DHCP-server write into the config files of the DNS server (and subsequently restart it). That would be a Bad Thing [TM], I agree.

Still, the DHCP server can issue a DDNS RR update (Dynamic DNS Ressource Record) to the DNS [1]. To do so, it will in general have to:

In turn, these DNSs will of course have to be configured to accept DDNS updates for that particular domain. Update messages can be signed with a shared secret or key, so the DNS server has some means of verifying the trust relationship to the DHCP server.

This being said, it is of course also thinkable (but not necessarily recommended) that the client itself send a DDNS update to the nameserver of it's domain. Windoze used to have (still has?) a checkbox somewhere deep in it's TCP/IP config to do exactly that. I can't go through the depths of a dhcpclient.conf right now, but maybe there's something similar in there?

As for the server part: you might want to look here: This is for Debian allright, but what works there should work on ubuntu as well.

[http://www.debian-administration.org/articles/343](http://www.debian-administration.org/articles/343)

regards

Marc
That's what I meant, maybe my choice of words was a bit poor. 
The dhcp server needs to update the dns. The dns server will want some sort of verification; you don't want just anybody adding or modifying dns records. Hence the keys in the config files. 

The reason it seems to work automatically on Windows is that Windows allows dhcp servers and workstations to update DNS without any check (or maybe domain membership is used to allow or reject DDNS updates), while the linux approach is that a sysadmin has to explicitely enable such mechanisms.

---

### Post by MaindotC on 2008-12-14
I think the keyword I was looking for was Dynamic DNS.  I should have wiki'd it.  I'll read up on it more and thank you all for pointing this out to me!

---

### Post by bab1 on 2008-12-14
@netztier,

Thanks for noticing my post.  Sadly circular thought seems to the norm these days.

@koenn,

> The reason it seems to work automatically on Windows is that Windows allows dhcp servers and workstations to update DNS without any check (or maybe domain membership is used to allow or reject DDNS updates)...

The above behavior is allowed in Windows because the host and user have been issued a Kerbros ticket upon login to the system.  This portable system authorization has also been used by  Novell (SUSE) since the days of NDS.  Security is there.  It is supplied by Kerbros which indeed requires domain membership.

---

