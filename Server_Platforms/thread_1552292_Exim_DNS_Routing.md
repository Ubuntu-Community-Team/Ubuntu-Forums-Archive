---
title: "Exim DNS Routing"
date: 2010-08-13
forum: Server Platforms
---

### Post by kgeekworking on 2010-08-13
I am trying to configure exim to act as a forwarder to relay mail for my internal clients.  Exim's has no local domains and its host and domain settings are set to localhost.

I can successfully relay through to outside domains, but I am having trouble routing to an internal exchange server.

Exim's log reports: "all relevant MX records point to non-existent hosts"

I used Dig on the server machine to query the MX for the domain using the server's default DNS server. The answer section correctly shows the MX with the FQDN (not IP) and the additional section shows the matching A record with the correct IP address. I can successfully use telnet to connect to port 25 using both the FQDN and IP.

I am really not sure of the problem.  My best guess is that Exim is using a different way to lookup or there is some sort of conflict with the server's hostname is within the target domain.

Does anybody know if Exim is using a non-standard way to do DNS lookups?

---

### Post by kgeekworking on 2010-08-13
I have found the answer to my own question.

Exim will ignore any MX lookups that resolve to any of the Private IP address ranges.  This is done to filter out bogus DNS replies from the internet. Since these IPs are Ignored, the error says that the host is "non-existent". 

The solution is to add the domain as a domain that you will relay mail for.  The IP address check is bypassed for these domains, so the message will route without error.

I added this setting by using the config script (sudo dpkg-reconfigure exim4-config) and entering the domain under the "Domains To Relay Mail For" setting.

---

