---
title: "Need Someone to Explain DNS Entries for Subdomains"
date: 2013-03-30
forum: Server Platforms
---

### Post by Beacon11 on 2013-03-30
Hello all.

First, a bit of background:

I have my domain nam registered with 1&1, which limits the number of subdomains I can create to something like ten. I then have A2 Hosting as my webhost, with 1&1 using A2's nameservers. With this setup I can actually use A2's cpanel "Advanced DNS Zone Editor" to create an unlimited number of subdomains and direct them wherever I like. The subdomains I create have a name, a TTL of 14400, a class of IN, a type of A, and a record equal to the IP address to which they direct traffic.

Now, the problem:

As Ruby and Rails have advanced beyond what A2 is hosting, I have actually started hosting my own websites at my apartment (they're private anyway), but I'm still paying A2 Hosting simply because they have all my subdomains. I understand Apache2, Ruby on Rails, and rvm pretty well, but I've never dealt much with DNS or nameserver stuff other than registering them and pointing them to the right place.

My question is this: is there either A) a domain name registrar that will allow me to register an unlimited amount of subdomains, or B) a straightforward way for me to host my own nameserver so I can create my own subdomains like A2 does?

I would really appreciate some guidance and advice! Thank you all!

---

### Post by darkod on 2013-03-30
I'm not 100% clear on the term "subdomain", but I believe you don't need to create any subdomains. You only create hosts with A record poiting to the specific public IP. And that should be it.

For example, you have example.com as A record, and then you have www as CNAME (so that it works with or without www).

From there on, you can create a host (A record) like test1 and point it to a public IP. When someone looks for test1.example.com it should direct him to that IP.

As far as I know, most registrars should allow you many A records, not just 5 or 10.

At work we use GoDaddy for many domains and I believe they don't limit you to 10 only. But best check with them. Anyway, I don't think it's referred as subdomain, only as A record, but I might be wrong.

As for the second option, hosting your own ubuntu nameserver is not too complicated, if you want to try that.

PS. I just chacked the GoDaddy DNS Manager and for standard users there is a limit indeed, but rather high. It says you can make up to 100 records.

---

### Post by Maddjokerz on 2013-03-31
Beacon11 if you are running an apache server have you tried looking at virtural hosting? This tutorial should give you more to go on [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

---

### Post by Beacon11 on 2013-03-31
> **Maddjokerz said:**
> Beacon11 if you are running an apache server have you tried looking at virtural hosting? This tutorial should give you more to go on [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

I use virtual hosts, but that has nothing to do with creating domains/subdomains-- it's only regarding hosting multiple sites on the same server with different domain names (that are already registered and pointing to one's server).

---

### Post by Beacon11 on 2013-03-31
> **darkod said:**
> I'm not 100% clear on the term "subdomain", but I believe you don't need to create any subdomains. You only create hosts with A record poiting to the specific public IP. And that should be it.

For example, you have example.com as A record, and then you have www as CNAME (so that it works with or without www).

From there on, you can create a host (A record) like test1 and point it to a public IP. When someone looks for test1.example.com it should direct him to that IP.

As far as I know, most registrars should allow you many A records, not just 5 or 10.

At work we use GoDaddy for many domains and I believe they don't limit you to 10 only. But best check with them. Anyway, I don't think it's referred as subdomain, only as A record, but I might be wrong.

As for the second option, hosting your own ubuntu nameserver is not too complicated, if you want to try that.

PS. I just chacked the GoDaddy DNS Manager and for standard users there is a limit indeed, but rather high. It says you can make up to 100 records.

It looks like GoDaddy is probably my best option, thank you :) . However, just hypothetically, let's say I host my own nameserver. How does it propagate to others? What happens if I lose power and the nameserver goes down for an hour?

Thank you for your help!

---

### Post by darkod on 2013-03-31
If the server is down, it's down. It will continue propagating info when it starts working again. That's why the DNS rules say you have to have two nameservers minimum. Most people when using a home server make the same server as first and second nameserver, which in reality you shouldn't do. :)

When the server is working, bind takes care of talking to other servers and propagating the info. But if you decide to do this, make sure you investigate first whether your ISP is blocking port 53, or other ports you might need, since they often block ports for services to residential customers. To stop people having web servers, mail servers, etc at home.

But I still think only hosts are enough for you. Now, if the current registrar is limiting you with hosts, that's another matter.

---

### Post by SeijiSensei on 2013-03-31
Internet standards require you to have two DNS servers exactly to protect against outages like you describe.

That said, I don't know what you mean by a "subdomain" either.  Usually a name like "host.example.com" refers to a specific machine and is referenced by a A record, or aliased with a CNAME.  "Subdomains" usually mean another separate domain with its own nameserver.  For instance, a company might use example.com, but have another internal domain name server for its workstations with names like host.local.example.com, where local.example.com is a subdomain.  Subdomains usually have their own nameserver records (NS), although sometimes they can appear only as a mail exchanger (MX).  For instance, you can have email addresses like [email]someone@example.com[/email], or addresses that exist within a subdomain of example.com like [email]someone@mail.example.com[/email].  In those cases there is usually a different mail server handling mail for each set of addresses.

If you want to host everything yourself, and this is a commercial project, I recommend renting a virtual server at some place like [Linode]("http://www.linode.com/").  Trying to host production services on a residential connection is asking for trouble in the long run.

---

### Post by CharlesA on 2013-03-31
> **SeijiSensei said:**
> 
If you want to host everything yourself, and this is a commercial project, I recommend renting a virtual server at some place like [Linode]("http://www.linode.com/").  Trying to host production services on a residential connection is asking for trouble in the long run.

Just adding a +1 to this. I have a VPS at [Secure Dragon]("http://securedragon.net/") and so far I have been pleased with it.

---

