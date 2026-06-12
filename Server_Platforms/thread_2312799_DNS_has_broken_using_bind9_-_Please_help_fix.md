---
title: "DNS has broken using bind9 - Please help fix"
date: 2016-02-07
forum: Server Platforms
---

### Post by ashley.bye on 2016-02-07
I had a working local DNS using bind9.  However, I have recently purchased a domain name and have updated my DNS configuration to reflect this, but now it doesn't work.  Please can you help me fix the problem?

/etc/bind/named.conf.local
```

[COLOR=#839496][FONT=Menlo]//[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]// Do any local configuration here[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]//[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]// Forward zones (ns1)[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]zone "home.mydomain.uk" {[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]        type master;[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]        file "/etc/bind/zones/db.home.mydomain.uk";    # Zone file path[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]        # allow-transfer { secondary.server.ip.address }; # Secondary nameserver (ns2) ip address - private[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]};[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]// Reverse zones (ns1)[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]zone "1.168.192.in-addr.arpa" {[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]        type master;[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]        file "/etc/bind/zones/db.1.168.192";    # 192.168.1.0/24 subnet[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]        # allow-transfer { secondary.server.ip.address }; # Secondary nameserver (ns2) ip address - private[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]};[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]// Consider adding the 1918 zones here, if they are not used in your[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]// organization[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]//include "/etc/bind/zones.rfc1918";[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]// Blacklist[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]include "/etc/bind/named.blacklist.zones";[/FONT][/COLOR]
```

/etc/bind/zones/db.home.mydomain.uk
```

[COLOR=#839496][FONT=Menlo];[/FONT][/COLOR][COLOR=#839496][FONT=Menlo]; BIND data file for local home network[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo];[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]$TTL    604800[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]@       IN      SOA     home.mydomain.uk. admin.home.mydomain.uk. ([/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                     20160207142311     ; Serial - remember to change this after every edit![/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                             604800     ; Refresh[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                              86400     ; Retry[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                            2419200     ; Expire[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                             604800 )   ; Negative Cache TTL[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; nameservers - NS records[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]        IN      NS      internal.home.mydomain.uk.[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; nameservers - A records[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]internal.home.mydomain.uk.      IN      A       192.168.1.1[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; 192.168.1.0/24 - A records[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]internal.home.mydomain.uk.      IN      A       192.168.1.1[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]external.home.mydomain.uk.      IN      A       192.168.1.2[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]esxi.home.mydomain.uk.          IN      A       192.168.1.200[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]router.home.mydomain.uk.        IN      A       192.168.1.254[/FONT][/COLOR]
```

/etc/bind/zones/db.1.168.192
```

[COLOR=#839496][FONT=Menlo];[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; BIND reverse data file for home network [/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo];[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]$TTL    604800[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]@    IN    SOA    home.mydomain.uk. admin.home.mydomain.uk. ([/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]         20160207132014        ; Serial - remember to change this after every edit![/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                604800        ; Refresh[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                 86400        ; Retry[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]               2419200        ; Expire[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                604800 )      ; Negative Cache TTL[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; Nameservers[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]    IN    NS    internal.home.mydomain.uk.[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; PTR records[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]1      IN    PTR    internal.home.mydomain.uk.    ; 192.168.1.1[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]2      IN    PTR    external.home.mydomain.uk.    ; 192.168.1.2[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]200    IN    PTR    esxi.home.mydomain.uk.        ; 192.168.1.200[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]254    [/FONT][/COLOR][COLOR=#839496][FONT=Menlo]IN    [/FONT][/COLOR][COLOR=#839496][FONT=Menlo]PTR    [/FONT][/COLOR][COLOR=#839496][FONT=Menlo]router.home.mydomain.uk.      [/FONT][/COLOR][COLOR=#839496][FONT=Menlo]; 192.168.1.254[/FONT][/COLOR]
```

I can post /etc/bind/named.conf.options,/etc/bind/named.blacklist.zones and /etc/bind/named.blacklist.hosts files but I haven't made any changes to these.  Prior to the above, the domain was just 'home.com', with servers at internal.home.com, external.home.com, etc.  All I have done is replaced '.com' with 'my domain.uk', and this now no longer works.

sudo named-checkconfig returns no errors and I can sudo service service bind9 restart without error.  However, when I do an nslookup I get the following error:

nslookup external.home.mydomain.uk
> 
[COLOR=#839496][FONT=Menlo]Server:[/FONT][/COLOR][COLOR=#839496][FONT=Menlo]192.168.1.1
[/FONT][/COLOR][COLOR=#839496][FONT=Menlo]Address:    192.168.1.1#53[/FONT][/COLOR][COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]** server can't find external.home.mydomain.uk: SERVFAIL[/FONT][/COLOR]

How can I repair this?  Thanks.

---

### Post by darkod on 2016-02-07
1. Which domain you want to create the zone for? In your files you have home.domain.uk and that is not the same as domain.uk if that's what you want the zone for.

2. The A records are defined only with the record name, not the full FQDN (bind will get it from the zone itself). So your A record definitions should be like:
```
internal   IN   A   192.168.1.1
external   IN   A   192.168.1.2
etc
```

And no need to declare internal record twice, like you have.

Make those modifications and restart bind. Don't forget to change the serial too with any modification.

---

### Post by ashley.bye on 2016-02-07
Darko, Thanks.  Re point 1, I want to set up x.home.mydomain.uk and also x.domain.uk, i.e. www. How does the setup for this differ from just my domain.uk?

---

### Post by darkod on 2016-02-07
Then it is set up good for home.mydomain.uk. Basically the domain name you want to create the zone for is specified in named.conf.local and in the IN SOA line in db.home.mydomain.uk.

According to what you posted, the zone should be correct when you modify how you define the A records as I mentioned earlier. The zone file already knows the full domain. For the A records you only define the first part, the hostname (or record name) that you want to define.

Did you try the modification?

---

### Post by ashley.bye on 2016-02-07
Okay, so I now have /etc/bind/zones/db.home.mydomain.uk as follows:

```

[COLOR=#839496][FONT=Menlo];[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; BIND data file for local home network[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo];[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]$TTL    604800[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]@       IN      SOA     home.mydomain.uk. home.mydomain.uk. ([/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                     20160207160746     ; Serial - remember to change this after every edit![/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                             604800     ; Refresh[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                              86400     ; Retry[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                            2419200     ; Expire[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]                             604800 )   ; Negative Cache TTL[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; nameservers - NS records[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]        IN      NS      internal.home.mydomain.uk.[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; nameservers - A records[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]internal         IN      A       192.168.1.1[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]; 192.168.1.0/24 - A records[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]external         IN      A       192.168.1.2[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]esxi             IN      A       192.168.1.200[/FONT][/COLOR]
[COLOR=#839496][FONT=Menlo]router           IN      A       192.168.1.254[/FONT][/COLOR]
```

I want to get this working before I look at 'www.mydomain.uk', which I assume will require a separate zone file of 'db.mydomain.uk' but that the reverse zone can just go in db.1.168.192?  However, restarting bind this still generates the same error.

---

### Post by darkod on 2016-02-07
Is the 192.168.1.1 the IP of the bind server or that's your home router IP?

---

### Post by ashley.bye on 2016-02-07
That's the IP of the server, the router is .254

---

### Post by darkod on 2016-02-07
It all looks good in the config. And checkconfig or bind restart is not reporting any errors... I really don't see anything wrong.

It looks like your client is asking the correct dns server for the query because in post #1 it does say Server:192.168.1.1 and Address:192.168.1.1.#53. So that part looks good.

But out of whatever reason, it is not reporting back to the query request.

Did you look in /var/log/syslog if you can find something there? Or other log files?

---

### Post by ashley.bye on 2016-02-07
Okay, so the actual issue was with my serial numbers. The format YYYYMMDDHHMMSS is larger than bind's maximum, which is 32 bits.  I don't know why it wasn't causing this issue previously but I now have a working my domain.uk.  I'll re-attack home.mydomain.uk after a cup of coffee!  Thanks for your help.

---

### Post by darkod on 2016-02-07
Wow... In fact, I think the YYYYMMDD and two numbers for a version XX is enough. You will never change the config more than 99 times in one day. :) In fact even one digit X for version is enough. It gives you up to 9 changes in one day.

Once you have tested it and have things running I mean.

---

### Post by ashley.bye on 2016-02-07
[FONT=verdana]All sorted for home.mydomain.uk.  Reverse lookups were working fine but forward lookups still gave an error.  Running named-checkzone home.mydomain.uk /etc/bins/zones/db.home.mydomain.uk gave an "ignoring out-of-zone data (internal)" error.  Changing internal., external., etc back to internal.home.mydomain.uk etc fixed this.[/FONT]

---

### Post by SeijiSensei on 2016-02-08
Just a hint for building domain.uk along with home.domain.uk.  You'll need to create a separate zone file for domain.uk and include a record like this:
```
home     IN     NS     192.168.1.1
```
which tells it to look to the 192.168.1.1 server for the home subdomain.

---

### Post by darkod on 2016-02-08
Is that why a record of type:
```
external   IN   A   192.168.1.2
```

didn't work? The OP says he has to put the FQDN to resolve correctly. Usually you put only the host(name) and the domain part is taken from the zone itself.

But in this case it was a home subdomain so that might make a difference.

---

### Post by SeijiSensei on 2016-02-08
In the zone file as posted, "external" is the short name for "external.home.domain.uk".  How that is handled by the resolver on a client machine depends on how the "domain" and "search" fields are configured in /etc/resolv.conf.  If that has "search domain.uk" then "ping external" translates to "ping external.domain.uk" which is not defined.  If resolv.conf has "search home.domain.uk" then "ping external" should work.  Another option is to include search entries for both domain.uk and home.domain.uk in resolv.conf, or use "domain domain.uk" along with "search home.domain.uk".

---

