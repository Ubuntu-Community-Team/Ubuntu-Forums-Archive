---
title: "Home Server: DNS Clarification"
date: 2007-06-10
forum: Server Platforms
---

### Post by lightnb on 2007-06-10
I've got a server setup at my house and I can access it using a DynDNS Domain Name.

I've bought a 'real' domain name now and I want that domain name to point to my home server.

So [www.myname.com](www.myname.com) points to 67.209.5.76

This is where I get confused... I know my domain name and I know my static IP address, but I'm not so sure about this DNS thing.

I think my server is (also) a DNS... It's running BIND and ISPconfig... so do I use my server's public IP as the nameserver?? But my domain name control panel wants two nameservers...

---

### Post by MJN on 2007-06-10
They often do, and is indeed considered best practice (if not a standard itself).

You could try putting the same address in for both - this often works for many such automated control panels. Of course, you'll then have a single point of failure as far as DNS resolution is concerned but that's probably not an issue for most (non-critical) situations.

Mathew

---

### Post by elst on 2007-06-10
You need to have two DNS servers that actually hold records that list the systems on your domain ("zones"). Once these are registered any system will be able to look up hosts in that domain via DNS - the queries go to the registered servers. Buying a domain name doesn't mean that any DNS server has records for that domain - it just means that no one else can use that domain name.

Sometimes the organization that registers your ownership of a domain name can add records for your domain to their DNS servers, or you can pay for the service separately. Larger organizations often run multiple DNS servers themselves.

Be aware that a DNS server can run without holding any zones itself - you have to add the zones yourself if you want your own DNS server to maintain records for a particular domain, rather than asking other DNS servers.

---

### Post by Mr. C. on 2007-06-10
lightnb,

You need to configure an A record in your DNS provider's / registrar's system.  Most offer some control panel or web access to do this.  The A record will map your hostname to your static IP.  This A record will provide the Internet with a means to trasnlate your hostname into an IP address.

You can run and use your own DNS server internally as well.  Yours is likely configured as a caching-only server.  In that case, you can use it as your DNS server... it will do the rest of the work.  There is no requirement to have two DNS servers; one is sufficient, esp. when it is your own server.  Configuring the resolver to use a secondary and tertiary DNS server is only for redundancy.  If you use your own DNS server, you do not need to configure your ISPs DNS servers, but you could add them as 2nd or 3rd servers.

You will have to workout how you translate your internal NAT'd IP address for your hosts.  Your attempts to connect to your own hosts from the LAN will result in name lookups that return public IP (WAN) addresses.  Your router may not support NAT-loopback, so your attempts to contect to your LAN servers using a WAN address may fail.  The solution is to either setup your internal DNS to provide internal LAN addresses for your hosts, or configure /etc/hosts with your LAN server's hostname/IP pairs.

MrC

---

### Post by chris.zeman on 2007-06-10
I run a server at work and a server at home, and each server has its own domain name. I use a free DNS service from DNS Park, [http://dnspark.com](http://dnspark.com). I haven't had any problems with it. There are third-party updating programs available that will allow your server to update its IP address with DNS Park when it changes, just as it did with DynDNS.

*EDIT
I thought you were able to have 2 domains with DNS Park for free, but that may have changed since I signed up. I'm not really sure. DNS Park is just one of many services you can use, though. There are other freebies out there.

Good luck!
Chris

---

### Post by lightnb on 2007-06-10
Thanks everyone!

I've created A-records for both of my domain names and pointed them to my router's static IP. The .com name is stable and working great.

The .net equivalent though is still unstable. By that I mean sometimes it points where it's supposed to, and sometime it shows the registrants "this name is parked" page.

I think it's a configuration problem within ISP config on my server. I have a site created for the .com (presumably why it works) and I have the .net set as a 'co-domain' of the .com. The idea is that they both refer to exactly the same site.

I could probably create a site for the .net that immediately links to the .com, but is there a better way?

Thanks again for your assistance.

---

### Post by Mr. C. on 2007-06-10
You didn't mention when you created the A records.  They can take some time before all the DNS servers have up to date records.

Use the dig command to lookup the A records for your domain.  Eg: 

$ dig A [www.yourdomain.com](www.yourdomain.com)

This will give you an answer from the name server you are currently configured to use.  Look at the Answer section, and at the Authority section.  Do the same command, but this time, use a name server listed in the authority section (change DNSERVERNAME to the result of what you found).

$ dig A @DNSSERVERNAME [www.yourdomain.com](www.yourdomain.com)

You can do this for each of the authoritative name servers.  They should all come back as the same, but may not until your updates have occurred.   And do the same for each of the DNS servers your system is configured to use (eg. your ISP's name servers).

MrC

---

### Post by juantao on 2007-06-11
You can have one of several free services provide seconday DNS for you, such as everydns.net

---

### Post by MJN on 2007-06-11
If you tell us your domain name(s) it will be much easier for us to diagnose the current configuration and, if necessary, suggest an alternative to achieve your goal.
 
PM it to someone if for some reason you wish to keep it 'private' (although putting it in the public DNS obviously negates this to a certain extent).
 
Mathew

---

