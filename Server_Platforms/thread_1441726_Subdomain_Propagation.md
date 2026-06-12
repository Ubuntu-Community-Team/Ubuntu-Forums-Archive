---
title: "Subdomain Propagation"
date: 2010-03-29
forum: Server Platforms
---

### Post by dgohn on 2010-03-29
I am not quite sure what is going on so I will say what is happening and hopefully someone can clue me in.  I have a few ideas but not sure.

I set up Bind9 and Apache2 for web and dns servers.  The DNS server works and is handling my domain and I have set my name servers to point to my dns on GoDaddy my registrar and all seems to be working.  However when I went to setup sub domains.. user.mydomain.com everything seems to work from the server machine side but outside of that it doesn't seem to work.  If I set one of my computers on my network to use my DNS server along with my upline isp's dns server it works perfectly but the second I remove my dns address from the settings on that computer the subdomain no longer works.  Is this simply due to propagation and I have to wait for my DNS zones to propagate through the internet?  Also, How does it work that the zones on my server machine will propagate throughout the internet?  Thanks for any info.

---

### Post by Ryan Dwyer on 2010-03-29
You didn't explain your setup very well. Is GoDaddy hosting your DNS records or are you? (or both?) When you "setup sub domains" are you doing that on GoDaddy or your own server?

---

### Post by dgohn on 2010-03-29
I am hosting my own domain.  In GoDaddy I changed from their Nameservers to mine that I setup with Bind9.  Also I am setting up the subdomains in Bind9 by creating an A record user.mydomain.com and then setting up a virtual host in apache2 to handle the web portion of where to direct it to.

---

### Post by Ryan Dwyer on 2010-03-29
In that case you probably need to port forward the DNS port (I think it's 53 on both TCP and UDP). The GoDaddy server can't contact yours and therefore can't resolve the request.

---

### Post by cdenley on 2010-03-29
What TTL are you using. It can take the entire TTL before your changes propogate to any DNS server which may have cached your domain. Domains get cached for as long as your DNS server allows it to be valid.
```

dig user.mydomain.com

```

---

### Post by dgohn on 2010-03-30
Thanks... that is exactly what it was.  My TTL was set very very high.  Everything is working now :)

---

