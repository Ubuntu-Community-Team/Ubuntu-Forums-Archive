---
title: "Unable to Ping FQDN from another machine to Ubuntu machine"
date: 2017-01-13
forum: Server Platforms
---

### Post by amit.pal on 2017-01-13
Hello Everyone,

I have installed Ubuntu 14.04 LTS as one of the servers in our company domain. This server has been assigned a static IP and has successfully joined the domain. Ping from Ubuntu server works fine (whether through IP Address or network hostnames or external websites). Hostname returns the correct hostname and hostname -f returns the FQDN. 

From another machine (whether Windows or Ubuntu) IP Address ping works fine to 14.04 LTS Server however ping hostname or ping fqdn does not works at all. 

I have searched whatever I could on the internet and tried everything but could not resolve this. Would be deeply grateful for any suggestions here.

Regards,

---

### Post by wildmanne39 on 2017-01-13
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-01-13
Did you check the local DNS server whether the ubuntu record is created and correct?

When you do ping fqdn the machine sends the request to its DNS server. If the DNS servers does not know what to reply for that fqdn, the client machine doesn't know where to send the ping...

From the above it looks like your ubuntu server has no record in your domain / LAN DNS.

---

### Post by SeijiSensei on 2017-01-13
It sounds like you're using Active Directory to manage your domain.  You'll need to create a custom DNS record for the server in AD.

---

