---
title: "Forwarding domains from godaddy to home server?"
date: 2010-07-01
forum: Server Platforms
---

### Post by Lucky75 on 2010-07-01
Hey,

I recently purchased a GoDaddy domain with the intent of hosting a website myself at home on a box I have lying around, but I'm somewhat confused, and was wondering if anyone could help.

First of all, I don't have a static IP, so I set up dyndns with my router.

Do I want to just have GoDaddy forward traffic to my dyndns account? Or do I manually change the nameservers? To what? Also, this seems to work for http(s) traffic only. What happens if I want to use ssh/ftp/smtp?

And do I need to configure anything on my end aside from installing/configuring the appropriate server binaries? 

Is there a way to update GoDaddy when my ip changes?

Thanks for the help!

---

### Post by dlepiane on 2010-07-01
> **Lucky75 said:**
> Hey,

I recently purchased a GoDaddy domain with the intent of hosting a website myself at home on a box I have lying around, but I'm somewhat confused, and was wondering if anyone could help.

First of all, I don't have a static IP, so I set up dyndns with my router.

Do I want to just have GoDaddy forward traffic to my dyndns account? Or do I manually change the nameservers? To what? Also, this seems to work for http(s) traffic only. What happens if I want to use ssh/ftp/smtp?

And do I need to configure anything on my end aside from installing/configuring the appropriate server binaries? 

Is there a way to update GoDaddy when my ip changes?

Thanks for the help!

Hi Luck75,

Your questions seem unclear to me, maybe there's missing info, but I'll just give it a shot.

You have two problems.  One is how to update DNS so that visitors can find your site when your IP address changes. The second problem is hosting the website.

GoDaddy does not support dynamic DNS.  Period.  So the best thing to do is to register a dynamic host record with dyndns.  You didn't say what the domain is or the host name you registered, so let's assume you've got example.com and your dyndns host is example-server.dyndns.org.  

So now your website.  Again, I'm making an assumption here, but say you want example.com and [www.example.com](www.example.com) to be on your webserver at home.  Well, the easiest way is to use a DNS alias, called a CNAME.  So with GoDaddy, remove the existing example.com and [www.example.com](www.example.com) records and create two CNAME records (@, which is the domain, and www) which are aliases for example-server.dyndns.org.

In this configuration, GoDaddy isn't "forwarding" any traffic.  Users who navigate to [www.example.com](www.example.com) will get the current / correct IP address for your home server.

Look up who DNS works, in particular CNAMEs and I think you'll find this gives you the solution you want for your website and other services (SSH, FTP, etc).

---

### Post by Lucky75 on 2010-07-01
Hmm, I think that's indeed what I want. Thanks!

Im confused though,because I had already added forwarding, which added the subdomain and the @ domain to the A(Host) table. I removed the subdomain and then added it to the CNAME/aliases table, but I'm not sure what to do with the @. 

The A table only accepts IPs. Is there a way I can do that for a dyndns address? Or should I just remove everything from the A table and make even '@' an alias?

Thanks!

---

### Post by volkswagner on 2010-07-02
I am not sure the instructions dlepiane offered will work for the top level domain (since you cant have your A record point to a domain name).  If you want to use example.com you will want to set up a pay account with DynDns.com, noip.com or similar.

To use your vanity domain with a dynamic service, you should change the name servers at godaddy to the nameserver of your choice dynamic provider.

To use DynDNS you will have to subscribe to the [custom DNS]("https://www.dyndns.com/services/dns/custom/").

I have not found a free way to use a dynamic provider service with vanity domains.  If you start to accumulate domains as I did, getting a VPS soon becomes a more reliable, less expensive solution to hosting at home.

So if you want free, you may have to just forward you godaddy domain, to your free dynDns domain...obviously this will show in the URL unless you can use a mask or rewrite...beyond my pay scale...

---

### Post by dlepiane on 2010-07-02
> **Lucky75 said:**
> Im confused though,because I had already added forwarding, which added the subdomain and the @ domain to the A(Host) table. I removed the subdomain and then added it to the CNAME/aliases table, but I'm not sure what to do with the @. 

Yes, the A records take only IP addresses so you'll have to remove your A records to create corresponding CNAME records.

> **Lucky75 said:**
> The A table only accepts IPs. Is there a way I can do that for a dyndns address? Or should I just remove everything from the A table and make even '@' an alias?

> **volkswagner said:**
> I am not sure the instructions dlepiane offered will work for the top level domain (since you cant have your A record point to a domain name).  If you want to use example.com you will want to set up a pay account with DynDns.com, noip.com or similar.

Huh, good point.  I don't think there's any limitation in DNS that doesn't allow you to create your top-level record as a CNAME.  I just tested in GoDaddy myself and it was letting me do that though so it may just be a limitation of GoDaddy's setup?

The simplest solution would be to just remove the A record for the top-level and then just have your website referred to by "www.example.com".  Most web browsers, if "example.com" fails will automatically try "www.example.com". 

If you have no A record for your domain though, make sure you have your MX records setup properly for email.  But for that, the simplest thing to do is to use [Google Apps Standard]("http://www.google.com/apps/intl/en/group/index.html") which is free and doesn't require an A record for example.com.

---

