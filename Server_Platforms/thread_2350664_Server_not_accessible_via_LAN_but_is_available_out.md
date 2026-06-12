---
title: "Server not accessible via LAN but is available outside network"
date: 2017-01-26
forum: Server Platforms
---

### Post by sushiboxdev on 2017-01-26
Hello, this is my second thread as I try to set up an iRedMail server on Ubuntu.

I have iRedMail installed on my Ubuntu Server and it is running webmail and an admin portal interface through Apache. I want to be able to access webmail and everything through my domain name so I set up an A record pointing to my IP address.

If I attempt to view the webmail portal inside of my local network, the request times out. If I try to view it outside of my network, such as on my phone over LTE, it works. I opened 80 and 443 for that machine in my router config panel and since I am able to reach it outside of my network using both the IP address and my domain, everything seems to be working fine there. On my local network, I am able to ping to the server just fine. It seems like I am only unable to access it on port 80 and 443.

I am using Comcast Business as my ISP and they do not have any NAT loopback functionality supported.

---

### Post by wildmanne39 on 2017-01-26
*Thread moved to **{forum for better support}**.*

---

### Post by darkod on 2017-01-26
Sounds like NAT loopback is the issue. And if the ISP router does not have it supported, then it can't work with public IP from the local LAN.

One option would be to use local DNS on the local LAN which will point the domain name to the private IP, not the public one.

Or simply use the hosts file on all local clients to set up the record pointing to the private IP.

---

