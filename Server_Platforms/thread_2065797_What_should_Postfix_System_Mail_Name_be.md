---
title: "What should Postfix System Mail Name be?"
date: 2012-10-02
forum: Server Platforms
---

### Post by BandC on 2012-10-02
I have a virtual server with a static IP and a real FQDN. I set up Postfix on it and everything works. While setting up Postfix, the guide that I followed suggested that I enter the server's FQDN as Postfix system mail name which I did (My FQDN and reverse DNS given to me by my hosting company is something like virtualhost123.myhostingprovider.com).

Now I want to host two domains on this server: say domainA.com and domainB.com. When I send outgoing mail to Gmail from my server for example (let's say from e-mail address [email]support@domainA.com[/email]) everything works fine but in the e-mail received, Gmail says:

E-mail from [email]support@domainA.com[/email] via virtualhost123.myhostingprovider.com.

I am worried that e-mail providers could block me thinking I'm just relaying spam (I am not sending spam but since the sender e-mail domain and via domain don't match maybe it looks suspicious).

Should I be worried? What should Postfix system mail name be set to for a server that hosts multiple domains?

What are the best practices about this or stuff that I need to do so big e-mail providers like Gmail, Hotmail, etc. don't block my server?

Thanks.

---

### Post by SeijiSensei on 2012-10-03
If you control the DNS for the hosted domains, there are a couple of things you can do.

First, make sure that your virtual server is listed as the primary MX record for each domain.  That means it will be accepting inbound mail for the domain, which I presume is what you want to do.

Second, add an "SPF" record to the domain's DNS that looks like this:

```

@  IN TXT "v=spf1 a:virtualhost123.myhostingprovider.com ~all"

```

That tells remote mail servers that honor SPF records that your hosted server is the valid outbound SMTP sender for the domain. If other servers are valid as well, just add additional "a:hostname" entries separated by spaces.

It sounds like forward and reverse DNS are set properly which is the other common issue with sending mail.  I don't reject inbound mail from hosts whose reverse DNS doesn't match their claimed hostnames, but I give those machines extra points in SpamAssassin.

---

### Post by BandC on 2012-10-06
Thank you very much SeijiSensei.

I set a primary MX record with my server FQDN (virtualhost123.myhostingprovider.com) and created an SPF TXT record again with my FQDN (virtualhost123.myhostingprovider.com).

Hopefully that will do it. The e-mails I receive from my domain still say "via virtualhost123.myhostingprovider.com" but all seems to be well for now. Thanks again.

---

