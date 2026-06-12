---
title: "How do I point my domain from my DNS provider to my VPS ubuntu server?"
date: 2019-09-08
forum: Server Platforms
---

### Post by pinkflow on 2019-09-08
Hello

I have been trying to point my domain to my server without any luck.

From the start, I was able to visit my website thru web browser by using my servers IP adress.
I added my domain to the domain provider under @, autoconfig and under www. All with type A.

this did not do the trick. 
I was recommended to run the dig command and this is is the result is gave when it came to status

dig mydomain.com [@ns1]("https://www.sweclockers.com/medlem/ns1").dns-provider.com
- NOERROR


dig mydomain.com
- SERVFAIL


dig soa mydomain.com
- SERVFAIL


dig +trace +all mydomain.com NS
- REFUSED


dnschekcer was red on every single country. 

After this I was told to add some hosts and a virtual host so thats what I did:

In Hosts I added this:
SERVERIP mydomain.com
SERVERIP [www.mydomain.com]("http://www.mydomain.com")

In virtual hosts I added this:
<VirtualHost *:80>
    ServerName [www.mydomain.com]("http://www.mydomain.com")
    ServerAlias mydomain.com
    DocumentRoot /opt/lampp/htdocs
    ErrorLog /opt/lampp/logs/error_log
</VirtualHost>

After this, the dig statuses changed to:

dig mydomain.com [@ns1]("https://www.sweclockers.com/medlem/ns1").dns-provider.com
- AUTHORITY

dig mydomain.com
- NOERROR

dnschekcer showed green on almost every country.

The bad thing now was that I could not connect to my website thru web browser with my servers IP. And the domain still didnt work. I dont know if the only thing needed to be fixed now is to make it possible to access my website with the servers IP thru a browser agian? Because to me - it looks like the domain is now configured correctly?

Could you guys please help me out?
[URL="http://WWW.LOOPIADOMÄN.SE"]
[/URL]

---

### Post by SeijiSensei on 2019-09-08
First, I take it you have a domain at a DNS provider?  If not, none of this will work.  

If so, you need to have an A record that points the name www to the IP address of the virtual machine.  I run my own DNS servers, but if you're using a domain provider you should be able to do this via the provider's dashboard.  What you need to start with is a record that looks like this:
```

www     IN     A     10.10.10.10

```
in the zone file for your domain.  You've already set the ServerName directive in Apache, so I'm guessing you just haven't set up the DNS records correctly.

If you install the whois client in Ubuntu with "sudo apt install whois" then the command "whois mydomain.com" should return records like this:

```

Domain Name: UBUNTUFORUMS.ORG
Registry Domain ID: D104981837-LROR
Registrar WHOIS Server: whois.markmonitor.com
Registrar URL: http://www.markmonitor.com
Updated Date: 2018-09-07T09:02:45Z
Creation Date: 2004-10-09T16:28:59Z
Registry Expiry Date: 2020-10-09T16:28:59Z
Registrar Registration Expiration Date:
Registrar: MarkMonitor Inc.
[etc.]
Name Server: NS2.CANONICAL.COM
Name Server: NS1.CANONICAL.COM

```

Once everything is set up correctly you should be able to use the host command like this:

```

$ host www.ubuntuforums.org
www.ubuntuforums.org has address 91.189.94.16
www.ubuntuforums.org has address 91.189.94.12

```

---

### Post by TheFu on 2019-09-08
Three things are required to have a public service on the internet.
[LIST=1]
[*]Domain Registrar with a record pointing to the authoratative DNS for the domain
[*]DNS Provider that points whatever DNS you need A/CNAME/MX/TXT to the server.
[*]Web/Mail/IMAP/whatever server accessible over the internet
[/LIST]

Registrar --> DNS --> Apache

If any of those are missing, it won't work.  These can be handled all-in-one, but I prefer to keep all three separate so that firing any single provider is much easier.  With all-in-one, it is common to find you can't easily move to a different provider. They will make up all sorts of excuses to delay the move.  I've heard of domain registrar transfers being prohibited less than 60 days before the end of service, so plan 6 months in advance if you intend to change the registrar.

I've been with 1 registrar almost 20 yrs now.  They charge way too much and is known to suck with terrible interfaces and up selling, but since I deal with them only once every 10 yrs, that 10 minutes of pain is less than the trouble to change.  I've changed DNS providers at least 4 times over the decades and can't count the number of times I've moved servers.

---

### Post by SeijiSensei on 2019-09-08
I've used [DirectNIC](https://directnic.com/) for years after I dumped Network Solutions. DirectNIC is based in New Orleans and managed to keep their servers up through hurricane [Katrina]("https://news.netcraft.com/archives/2005/08/31/directnic_stays_online_in_new_orleans_facility.html").  After that I vowed to stick with them. A year costs $15 with discounts for multi-year registrations.

---

