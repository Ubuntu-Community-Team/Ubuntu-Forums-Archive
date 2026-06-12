---
title: "BIND Issues"
date: 2008-06-27
forum: Server Platforms
---

### Post by TArozzelle on 2008-06-27
So I've started renting a VPS from Virpus, switching from a server that I rented (which happened to be overkill). First order of business is to transfer my domain names over to my provider's nameservers and configure it all in their provided control panel, yea?

Well, not really. Apparently, these folks don't offer their nameservers for use, meaning I need to either seek out a separate service or do it myself. I chose to latter option, figuring that it is a process I should learn soon enough. I reloaded the VPS, via their HyperVM panel, from CentOS to Ubuntu and installed the bind9 and dnsutils packages.

Following are the relevant configuration files:

```
/etc/bind/named.conf.local

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "themodernardeo.com" {
				type master;
				file "etc/bind/db.themodernardeo.com";
};

zone "209.89.208.in-addr.arpa" {
		type master;
		notify no;
		file "/etc/bind/db.208";
};
```

Note: My named.conf includes named.conf.local.

```
/etc/bind/db.themodernardeo.com

;
; BIND data file for themodernardeo.com
;
$ORIGIN themodernardeo.com.
$TTL	604800
@	   IN	  SOA	 ns1.themodernardeo.com. admin.themodernardeo.com. (
							  4	; Serial
						 604800	; Refresh
						  86400	; Retry
						2419200	; Expire
						 604800 )	 ; Negative Cache TTL
;
@	   IN	  NS	  ns1.themodernardeo.com.
@	   IN	  A	   208.89.209.29
ns1	 IN	  A	   208.89.209.29
```

I realize that my zone file in incomplete. At this point, I just wanted to see if the server could be found. My registrar is Name.com and I have set up the name server for the domain name "TheModernArdeo.com" such that it directs to 208.89.209.29, my server.

Both my forward and reverse resolution files check out find using named-checkzones.

For ping, "Unkown host" is as verbose as it gets, even with the proper flag.

Here is the output from dig.
```
; <<>> DiG 9.4.2 <<>> themodernardeo.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 58796
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;themodernardeo.com.		IN	A

;; Query time: 585 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Thu Jun 26 22:48:28 2008
;; MSG SIZE  rcvd: 36
```

For posterity's sake, this is the output of dig on the actual server.

```
; <<>> DiG 9.4.2 <<>> themodernardeo.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 56335
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;themodernardeo.com.		IN	A

;; Query time: 51 msec
;; SERVER: 4.2.2.1#53(4.2.2.1)
;; WHEN: Fri Jun 27 02:48:40 2008
;; MSG SIZE  rcvd: 36
```


This is the output of dnstracer on my server:

```
Tracing to themodernardeo.com[a] via 4.2.2.1, maximum of 3 retries
4.2.2.1 (4.2.2.1) 
  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29)
```


This is the output on my home box.

```
Tracing to themodernardeo.com[a] via 192.168.2.1, maximum of 3 retries
192.168.2.1 (192.168.2.1) 
 |\___ k.gtld-servers.net [com] (192.52.178.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) 
 |\___ b.gtld-servers.net [com] (2001:0503:231d:0000:0000:0000:0002:0030) send_data/sendto: Network is unreachable
* send_data/sendto: Network is unreachable
* send_data/sendto: Network is unreachable
* 
 |\___ b.gtld-servers.net [com] (192.33.14.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ j.gtld-servers.net [com] (192.48.79.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ e.gtld-servers.net [com] (192.12.94.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ g.gtld-servers.net [com] (192.42.93.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ h.gtld-servers.net [com] (192.54.112.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ d.gtld-servers.net [com] (192.31.80.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ c.gtld-servers.net [com] (192.26.92.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ m.gtld-servers.net [com] (192.55.83.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ i.gtld-servers.net [com] (192.43.172.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ f.gtld-servers.net [com] (192.35.51.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
 |\___ l.gtld-servers.net [com] (192.41.162.30) 
 |	  \___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
  \___ a.gtld-servers.net [com] (192.5.6.30) 
		\___ ns1.themodernardeo.com [themodernardeo.com] (208.89.209.29) (cached)
```


Any suggestions?

---

### Post by HalPomeranz on 2008-06-27
Looks like a probable typo in your named.conf file.  Under the zone declaration for themodernardeo.com you have: 'file "etc/bind/db.themodernardeo.com";'.  Shouldn't there be a leading '/' on that path name?

In general it looks like something is causing your name server not to load properly.  The root name servers appear to be looking in the right place, which implies that your name server isn't answering queries for some reason.  The typo could be the cause.

Failing that, I'd check your logs and see if there are any error messages from named when it starts up.

---

### Post by TArozzelle on 2008-06-27
The file was actually fine. My TTL was too long and the updated weren't made until some time this morning. Everything is kosher now.

Thanks.

---

