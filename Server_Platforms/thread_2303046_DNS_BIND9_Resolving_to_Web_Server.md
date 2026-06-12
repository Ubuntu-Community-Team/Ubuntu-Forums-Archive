---
title: "DNS BIND9 Resolving to Web Server"
date: 2015-11-15
forum: Server Platforms
---

### Post by squall_leonhart2 on 2015-11-15
I am new to bind and DNS.  I have set up a BIND9 server in Ubuntu 14 and have build some local zone files that seem to work for host name resolution - after setting another host on the network to use my DNS server as its DNS, it can resolve host names to IP and ping other hosts by host name for example.  However my problem is that when I type in the hostname of my web server in a web browser on the same local network, it will not direct the web browser to the web server running on that host.

192.168.1.95 is my webserver, hostname: "www.----.tld"

ping "www.----.tld" and it resolves the IP and pings fine

however on that same host that can resolve and ping, "www.----.tld" or "http://www.----tld" in a web browser will not display the web server running on that host.  If you type in "192.168.1.95" in the address bar in the browser the web server pulls up the web page immediately and works just fine.  I have to be able to have the DNS server resolve this and point someone to the web server if they try to go to the URL/Hostname.

How can I configure my DNS server to point to the web server of this machine?  Or what I have done incorrectly?  I will attach a copy of my zone file that I created, the edited parts have my full domain.  Please help if you know how to do this.

---

### Post by CharlesA on 2015-11-16
Run dig and see if it is hitting the correct DNS server or not.

```
dig A www.example.com
```

---

### Post by darkod on 2015-11-16
Yes, try with dig or nslookup to check if it resolves the URL correctly. Although you say ping by hostname works so that part sounds good.

Also, in your zone file the main @ IN A record should point to the 192.168.1.95, not to the local loop 127.0.0.1. Is there any reason you left it as local loop? But this error should not prevent [www.domain.tld]("http://www.domain.tld") to work. It can however give you issues with domain.tld. Usually both domain.tld and [www.domain.tld]("http://www.domain.tld") would point to the same IP (of the web server).

If DNS is good it might be apache issue.

---

### Post by squall_leonhart2 on 2015-11-16
> **CharlesA said:**
> Run dig and see if it is hitting the correct DNS server or not.

```
dig A www.example.com
```

First note is that the IP should have been .95 not .96, however even after I corrected this in the zone file and restarted the DNS server, the same problem persists..  

Below is the output from the dig command, which seems to be talking to my DNS server "ns" .53 and resolves the hostname to the correct IP (in this case 95).  However when I type that hostname into the web browser (with or without http or https [which this server is not running https anyway]) it will not resolve it or go to the web server that is running on it..  See screen shot with dig.

Thanks.  I tried changing that from the loop back to the web server IP, but the same problem persisted.  I replied above to the request for the dig results as well - looks like dig resolves it correctly and is using my internal DNS server (.53). (note in my reply about the .95/.96 mistake)

This is what the browser displays when I try to enter the host name in the address box.

---

### Post by darkod on 2015-11-16
Hmmm, in that case it looks more like apache issue. It sounds silly, but have you restarted apache after any changes in the config that might have been done?

Is your site .conf file configured properly? It might help if you post the .conf file. And I assume you enabled it with a2ensite? I personally don't know apache in details but other people might help too after seeing the .conf file.

---

### Post by Habitual on 2015-11-16
Isn't www a cname? ;)

How about [http://domain.tld](http://domain.tld) what's that 'do'?

---

### Post by squall_leonhart2 on 2015-11-16
> **Habitual said:**
> Isn't www a cname? ;)

How about [http://domain.tld](http://domain.tld) what's that 'do'?


[COLOR=#000000]Thanks for you response!![/COLOR]

[COLOR=#000000]I'm Not sure (I'm new to BIND and DNS configuration). How would I enter the CNAME into my zone file? I tried to add a CNAME for this but when I did it, all resolution on the hostname/IP that was working (ping, nslookup, dig, etc.) stopped working.. Perhaps this is the key and I just did it incorrectly.. [/COLOR]

[COLOR=#000000]http:// prefixed to a number of combinations ([/COLOR][www.,]("http://www.%2C/")[www.domain.tld]("http://www.domain.tld/")[COLOR=#000000], domain.tld, etc.) would not yield any different results.[/COLOR]

---

### Post by Habitual on 2015-11-16
```
domain.tld.  IN    A    123.456.123.456
www.domain.tld.    IN    CNAME    domain.tld.
```

Notice the periods.
```
service bind9 restart && rndc reload
``` to restart and reload.

I'm not convinced this is the cause of the problem however.

Post the apache site.conf file as suggested...?

---

### Post by darkod on 2015-11-17
Also, going back to your first post and the zone file screenshot. Are you sure the file is correct? You have masked the domain so we can't know. You don't have to publish it in public if you don't feel comfortable, just make sure it's correct. Because it all starts there... The @ IN SOA line should be like:

```
@   IN   SOA   domain.tld.   admin.localhost.   {.....
```

I have seen cases where people don't use the domain.tld. correctly in the SOA line, and the dns resolving starts from there... Having the domain exactly correct.

PS. You say ping and dig return the correct IP so probably the domain in the zone is correct, but it's worth giving it another look. The bottom line is, if ping, dig and nslookup return the correct IP, then bind is working fine and you need to look more at apache than at bind.

---

