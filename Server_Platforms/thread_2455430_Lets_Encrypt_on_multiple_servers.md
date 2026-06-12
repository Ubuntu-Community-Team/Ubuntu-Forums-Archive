---
title: "Lets Encrypt on multiple servers"
date: 2020-12-19
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2020-12-19
I'm setting up a new Ubuntu Apache server and intend to use Lets Encrypt certbot but I've run across an issue I don't understand.

I already have a server in a different location with a different IP Address. Each site has a separate IP address range because they use different ISPs. It already has a Lets Encrypt certificate.
All of the instructions I've seen require an A record for the domain and an A record for the server to point to the IP address of the server that is
[LIST]
[*]A  mydomain.com 10.10.10.10
[*]A  ww2.mydomain.com 10.10.10.10
[/LIST]

But I already have an a record for mydomain.com that points to a different IP address and an existing webserver.
[LIST]
[*]A mydomain.com 10.0.0.10
[*]A [www.mydomain.com](www.mydomain.com) 10.0.0.10
[/LIST]

How do you set something like this up?

Also is there any reason not to install Lets Encrypt from the Ubuntu repositories? That would seem to make sure all of the dependencies are installed.

```
apt install --install-suggests letsencrypt
```

---

### Post by LHammonds on 2020-12-19
I've had a dozen different domains / sites all pointing to the exact same IP and did not have an issue with Let's Encrypt.

Apache directs incoming traffic to a specific web site via the incoming domain name...which is the same process Let's Encrypt uses to access/test your website.

You are not required to have a different IP for every website.

LHammonds

---

### Post by rsteinmetz70112 on 2020-12-19
> **LHammonds said:**
> I've had a dozen different domains / sites all pointing to the exact same IP and did not have an issue with Let's Encrypt.

Apache directs incoming traffic to a specific web site via the incoming domain name...which is the same process Let's Encrypt uses to access/test your website.

You are not required to have a different IP for every website.

LHammonds

The issue is that I need to have two separate servers in two different locations for different purposes and the IP addresses must be different due to having two ISPs.

---

### Post by darkod on 2020-12-19
Sorry, but I don't get your question.

So you have the identical website files and databases (if applicable) on two servers? And all data is constantly synced?

From public DNS perspective you can have as many A records as you wish. For example:
mydomain.com A 12.23.34.45
mydomain.com A 98.87.76.65

I think the DNS would work as round-robin by default but that depends on the DNS setup too.

And of course, unless you have identical web/DB data on both servers, users directed to one or another server will not see the same content.

---

### Post by kevdog on 2020-12-20
You know if you just used Let's Encrypt with DNS validation you wouldn't have to worry about the mess you describe.

---

### Post by rsteinmetz70112 on 2020-12-20
darkod 

Unfortunately the servers are not identical and they provide different information, so the multiple A records won't work.

kevdog

I wasn't aware that was possible - Can you point me to some information on how to set that up?

---

### Post by darkod on 2020-12-21
Whether the servers are identical is not really relevant. I just wondered because you used mydomain.com both times in your first post. For me it didn't make much sense to have different web data on different servers but same public domain. Anyway...

Since the servers are independent (and even if they weren't), there should be no problem to use separate independent certificates. Did you try that?

Basically the cert doesn't even care about the server or your data. All it needs is the cert to be valid and to cover all the common names (URLs) that you want to use.

So just try to create LE cert on server A that will cover the URLs of server A, and another LE cert for server B covering the URLs of server B. That should be it.

---

### Post by kevdog on 2020-12-21
You need a dns provider that is supported by dns validation within acme.  I believe there is a list of about 15-16 DNS providers in which the acme protocol supports DNS validation using these providers.  I personally use Cloudflare -- I'm not sure if its better than other providers however it's also no cost to use and it's pretty simple. The hardest part was transferring my DNS records from my old provider to the new one.  Once you are setup with a provider which is supported by acme, you configure a few parameters when certbot/acme or whatever client you are using which specify your DNS provider and you usually pass one or two authentication tokens which you obtain from the DNS provider.  In comparison to the case when using HTTP validation and Let's encrypt needs to write a small file to your webserver to "prove" ownership, Let's Encrypt in this case writes a temporary record within your DNS records to "prove ownership".  I prefer this method for sure and find it very convenient.

---

### Post by rsteinmetz70112 on 2020-12-22
Thanks for the information.

I'm checking to see if my DNS provider - Network Solutions - supports ACME, so far they aren't on any list I can find. I've asked them directly so I'll see what happens. If necessary I'll move my DNS someplace. I just use them because it's included in the Domain Registration.

---

