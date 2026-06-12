---
title: "Multiple Dynamic DNS Providers"
date: 2010-09-11
forum: Server Platforms
---

### Post by megabuffen on 2010-09-11
I am currently using dyndns.org and ddclient to host a web server with dynamic IP address. To be able to host multiple websites for friends i would like to be able to use multiple dynamic DNS providers or possibly multiple user accounts within dyndns,´.org, although i have a feeling they may ban me for that, even if the account belongs to someone else.

I can easily create a list of as many domains as i want, but there is only one place where I can sspecify the server to update. It's the same with my username and password.

Is there any way to configure ddclient with multiple providers/accounts or perhaps a way around it?

---

### Post by Bachstelze on 2010-09-11
What I do personally is that I just set all domains as CNAME records on my "primary" one.

---

### Post by megabuffen on 2010-09-12
You're right. After reading a little bit about CNAME I agree with you. Will it still work if I'm using virtual domains on my apache server?

For example, if i have the domain example.com as a CNAME record pointing to example.dyndns.org, will the web browser request example.com or example.dyndns.org from my web server?

---

### Post by Bachstelze on 2010-09-12
> **megabuffen said:**
> You're right. After reading a little bit about CNAME I agree with you. Will it still work if I'm using virtual domains on my apache server?

For example, if i have the domain example.com as a CNAME record pointing to example.dyndns.org, will the web browser request example.com or example.dyndns.org from my web server?

It will request example.com. DNS is only used to match a name with an IP. Apache doesn't use it, it only looks at the header in the HTTP request, independently of DNS.

---

