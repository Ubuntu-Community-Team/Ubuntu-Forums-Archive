---
title: "Is my DNS set up right?"
date: 2010-07-30
forum: Server Platforms
---

### Post by melat0nin on 2010-07-30
Hi all

I've been migrating my organisation's website to Ubuntu Server and we're almost at the stage where the domain can be transferred. I just need to make sure DNS is set up properly to accept the domain transfer (and to avoid any outages in access to the site or email redirecting).

I've got Webmin installed, and have used that to create the relevant config files, but I'm quite new to this aspect of web server admin so I'd like to check with more experienced folk before going ahead with the transfer.

My named.conf.local looks like this:

```

root@server:/etc/bind# cat named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "domainname.gov.uk" {
	type master;
	file "/var/lib/bind/domainname.gov.uk.hosts";
	};

```

and /var/lib/bind/domainname.gov.uk.hosts looks like this:

```

root@r33769:/etc/bind# cat /var/lib/bind/domainname.gov.uk.hosts
$ttl 38400
domainname.gov.uk.	IN	SOA	r33769.myisp.net. myemail\.address.gmail.com. (
			1280525265
			10800
			3600
			604800
			38400 )
domainname.gov.uk.	IN	NS	r33769.myisp.net.
domainname.gov.uk.	IN	A	123.45.123.45
www.domainname.gov.uk.	IN	A	123.45.123.45
domainname.gov.uk.	IN	NS	sdns1.myisp.net.
domainname.gov.uk.	IN	MX	5 emailserver.gov.uk.

```

..if there's any info I've left out please let me know and I'll post it. The config looks alright to me, but as I said I'm far from expert in this part of server admin.

Any help or tips would be much appreciated :)

---

### Post by HermanAB on 2010-07-31
Hard to say. 

Test it with 'dig'.  Read the man page.

$ dig @dnsserver domainname

Also check the A, MX and PTR records.

---

### Post by Bachstelze on 2010-07-31
You might want to change your serial.  Traditionally, they're of the form YYYYMMDDNN to reflect the date of the latest change (NN is a number you increment if you're modifying your zone files several time on the same day).

---

### Post by melat0nin on 2010-08-01
> **HermanAB said:**
> Hard to say. 

Test it with 'dig'.  Read the man page.

$ dig @dnsserver domainname

Also check the A, MX and PTR records.

Thanks for the tip, when I put enter 'dig @r33769.ovh.net scotlawcom.gov.uk' (r33769.ovh.net is the dedicated server the site is hosted on) I don't get any output. When I put in the host's secondary DNS server instead, I get this:

```

; <<>> DiG 9.5.1-P2.1 <<>> @sdns1.ovh.net scotlawcom.gov.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 58927
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;scotlawcom.gov.uk.		IN	A

;; Query time: 7 msec
;; SERVER: 213.251.188.140#53(213.251.188.140)
;; WHEN: Sat Jul 31 14:26:10 2010
;; MSG SIZE  rcvd: 35

```

..which looks more promising. Not sure why the hosting server isn't giving any feedback. I tried restarting bind but that didn't help.

Thanks for your help!

Laurence

---

### Post by Bachstelze on 2010-08-01
Are you sure BIND is running on your system?  I can't reach it from here:

```
firas@iori ~ % dig @r33769.ovh.net scotlawcom.gov.uk                 

; <<>> DiG 9.7.0-P1 <<>> @r33769.ovh.net scotlawcom.gov.uk
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached

```

---

### Post by melat0nin on 2010-08-01
> **Bachstelze said:**
> Are you sure BIND is running on your system?  I can't reach it from here:

```
firas@iori ~ % dig @r33769.ovh.net scotlawcom.gov.uk                 

; <<>> DiG 9.7.0-P1 <<>> @r33769.ovh.net scotlawcom.gov.uk
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached

```


Hmm I think so, I did both '/etc/init.d/bind9 start' and restart, and it seems to be running as a process :/

---

### Post by Bachstelze on 2010-08-01
The defaults settings probably make it listen only on 127.0.0.1.  What's your named.conf.options?

---

### Post by melat0nin on 2010-08-01
> **Bachstelze said:**
> The defaults settings probably make it listen only on 127.0.0.1.  What's your named.conf.options?

I think you're right:

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

        // forwarders {
        //      0.0.0.0;
        // };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { ::1; };
        listen-on { 127.0.0.1; };
        allow-recursion { 127.0.0.1; };
};

```

..I changed it to the server's IP and now I get some output from dig! Do you think that's it sorted then?

---

### Post by Bachstelze on 2010-08-01
Yeah, it seems good now.

---

### Post by melat0nin on 2010-08-01
> **Bachstelze said:**
> Yeah, it seems good now.

Nice once, thanks... will transfer the domain and keep my fingers crossed now!

---

