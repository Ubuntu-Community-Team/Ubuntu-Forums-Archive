---
title: "DNS Resolving Issues"
date: 2013-03-14
forum: Server Platforms
---

### Post by jlacroix on 2013-03-14
I have a DNS/DHCP server in my house running Ubuntu Server 12.04. It handles name resolution for all my internal computers. I know it's overkill, but I am studying for Linux certifications so it's important to me that I learn this stuff.

Anyway, it's been working perfectly fine up until about four days ago. Then, it started not resolving almost any outside web sites. I kept getting redirected to the OpenDNS "website unavailable" page. So, I got frustrated and removed OpenDNS from the forwarding and replaced it with Google's DNS servers. I thought that would fix it, but today it's acting up again, not resolving almost anything. This time, however, I'm getting Google's error page and not the OpenDNS error page. I think that two different DNS servers having trouble would be a strange coincidence. With the Google DNS error page, if I refresh my browser, the requested site will load fine.

No changes have been made to my DNS server recently other than removing OpenDNS, so maybe it is the outside DNS servers that are the problem.

Named.conf:
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
```

named.conf.options:
```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
		8.8.8.8; 8.8.4.4;
	};

	recursion yes;

	//========================================================================
	// If BIND logs error messages about the root key being expired,
	// you will need to update your keys.  See https://www.isc.org/bind-keys
	//========================================================================
	dnssec-validation auto;

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};
```

net.localnet:
```
;
; dns zone for for localnet
;

$TTL 1D

; any time you make a change to the domain, bump the
; "serial" setting below. the format is easy:
; YYYYMMDDI, with the I being an iterator in case you
; make more than one change during any one day

@ IN SOA localnet. hostmaster.localnet. (

201301281 ; serial

8H ; refresh
4H ; retry
4W ; expire
1D ) ; minimum
IN A 172.16.254.10
;
@ IN NS pluto.localnet.
ceres	        IN      A       172.16.254.11
daphne		IN	A	172.16.254.12
eris		IN	A	172.16.254.14
phoebe          IN      A       172.16.254.13
pluto		IN	A	172.16.254.10

; bla           IN      CNAME   pluto ; Example of a CNAME record, if necessary
; www           IN      A       172.16.254.10 ; Example of a www record
```

revp.172.16.254:
```
;
; reverse pointers for 172.16.254.0 subnet
;
$TTL 1D
@ IN SOA pluto.localnet. hostmaster.localnet. (
201301281 ; serial
28800 ; refresh (8 hours)
14400 ; retry (4 hours)
2419200 ; expire (4 weeks)
86400 ; minimum (1 day)
)
;
@ NS pluto.localnet.
10      PTR     pluto.localnet.
11      PTR     ceres.localnet.
12      PTR     daphne.localnet.
13      PTR     phoebe.localnet.
14	PTR	eris.localnet.
```

---

### Post by SeijiSensei on 2013-03-14
Don't use a forwarder.  There's no reason to do so if you have a fully-functioning BIND9 server already.  It will resolve names outside your domain just as well as Google does.

The only time I use forwarding is when I want to resolve names against my clients' internal DNS servers that I can see over a VPN tunnel.  In those cases I'll pass queries for those domains over the tunnel to the client's internal server.

---

### Post by jlacroix on 2013-03-14
> **SeijiSensei said:**
> Don't use a forwarder.  There's no reason to do so if you have a fully-functioning BIND9 server already.  It will resolve names outside your domain just as well as Google does.

The only time I use forwarding is when I want to resolve names against my clients' internal DNS servers that I can see over a VPN tunnel.  In those cases I'll pass queries for those domains over the tunnel to the client's internal server.
Doesn't disabling that disable caching? Also, if I disable forwarding, how does it know which outside DNS server to use?

---

### Post by SeijiSensei on 2013-03-14
No, it doesn't disable caching.  The server in my office here caches just fine.

As for your other question, we need to start with how DNS works.  Suppose I ask my server to resolve host.example.com.  The server first contacts one of the seventeen "root" nameservers that are authoritative for the com domain and asks what servers are authoritative for the example.com domain.  Every DNS installation includes a zone file for the root servers.  Since I use CentOS for servers, I can't tell you which file that is in Ubuntu, but you should find it in the same directory as the other zone files.

A root server will then return the IP addresses of the authoritative servers for example.com.  Then my server asks one of those for the address associated with host.example.com.  

In essence, the server in my office is no different than one of Google's or any other nameserver on the Internet.

---

### Post by Vegan on 2013-03-14
I have a bunch of forwards I use simply to speed up the browser on client machines.

Forwards are not strictly needed, BIND9 can act as a cache server and it will find what it needs automatically from hints etc that come with the default install.

I found Webmin to be expedient to managing BIND

---

### Post by jlacroix on 2013-03-14
Thank you for your assistance, I really appreciate it. I didn't know that forwarding wasn't necessary, that's good to know. I think this is solved, because even though I haven't gotten around to changing anything, the problem seems to have resolved itself. Maybe Google's DNS servers were having issues.

---

### Post by ac5jw on 2013-03-16
I have been studying up lately on this DNS topic because I wanted to speed up my Internet and also to look for an online place that filters out or blocks domains and host names.  One of the things I read was that there are events when a DNS service becomes degraded or unavailable.  If that happens, it may be good for you to have a ready backup to quickly take charge of DNS until things come back to normal at your preferred DNS service.  I am now learning about nslookup and iptables and related topics on my Ubuntu 12.04.2 LTS in support of blocking those pesky ad servers I get all the time.  I am also considering a firewall option but I do not know enough yet how to set up a blacklist.

---

### Post by jlacroix on 2013-03-16
> **ac5jw said:**
> I have been studying up lately on this DNS topic because I wanted to speed up my Internet and also to look for an online place that filters out or blocks domains and host names.  One of the things I read was that there are events when a DNS service becomes degraded or unavailable.  If that happens, it may be good for you to have a ready backup to quickly take charge of DNS until things come back to normal at your preferred DNS service.  I am now learning about nslookup and iptables and related topics on my Ubuntu 12.04.2 LTS in support of blocking those pesky ad servers I get all the time.  I am also considering a firewall option but I do not know enough yet how to set up a blacklist.
In my situation, I had OpenDNS set up in my DNS server, and then my fallback was my router which contained Google as the DNS. In theory, it should have used OpenDNS and then Google if there was a problem. However, my DNS server just wouldn't fall back. It would try OpenDNS and if it didn't find what it needed, it would fail out and never fall back. I still don't understand why it wouldn't fall back.

In the case of Google failing as well, I notice that it would also fail if I am running a backup via Crashplan. While a backup is in progress, DNS will rarely resolve and I'll get Google's 404 page. I'm perplexed why I would get Google's 404 page if my server itself was busy.

So I have more to learn.

---

### Post by ac5jw on 2013-03-16
So do I.  I am happy to report that I abandoned Linux Mint OS due to a bug where its Network Manager would not update my new DNS choices.  I gave up after trying for several hours, and then out of frustration I installed Ubuntu 12.04.2 LTS and wiped out the old data.  Apparently the Linux Mint was using a backup DNS file to restore the original setting and I did not know enough to fix it in terminal or in GUI Network Manager.  I learned to set the DNS preferences immediately upon loading the live DVD and I set a connection name to follow the data through the installation.  After setting DNS using the connection settings and verifying them in the Network Manager option, I then chose to Install from DVD.  After reboot, the data I had placed on the RAM actually made it into the permanent installation with the connection name and all!  It was great to resolve the issue because my newest choice for DNS had been showing good connection speeds within about a half a day of choosing it.

---

### Post by chrisguk on 2013-03-16
Hi also take a look at a long post I made about installing DHCP/DNS hope thats helps.

[http://ubuntuforums.org/showthread.php?t=2109373](http://ubuntuforums.org/showthread.php?t=2109373)

---

### Post by ac5jw on 2013-03-16
Thanks for the link to the tutorial.  I bookmarked it and I am already starting to read it !

---

### Post by chrisguk on 2013-03-16
No problem, though I have made a few changes along the way so if you have any issues just ask and I will clarify for you.

---

### Post by ac5jw on 2013-03-16
OK I may take you up on your offer to field questions.  I am still very new with Linux and networking !

---

