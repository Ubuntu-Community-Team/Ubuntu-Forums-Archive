---
title: "DNS for internal sub-domain from external domain?"
date: 2013-06-20
forum: Server Platforms
---

### Post by wlraider70 on 2013-06-20
I have a company website hosted by godaddy.

I also have an internal small business network. I have been making it a bit more corporate latterly. I've added a few intranet tools and even one that I would like to have accessibly from the Internet.


So Can I create a sub domain that is internal while using the godaddy DNS to point to my local server?
Will a bind9 and samba setup work for the sub domain?


Thanks?

---

### Post by SeijiSensei on 2013-06-20
> **wlraider70 said:**
> So Can I create a sub domain that is internal while using the godaddy DNS to point to my local server? Will a bind9 and samba setup work for the sub domain?

Yes and yes.

However I usually have two pairs of DNS servers, a public service that runs on my cloud-based servers at Linode, and a private one visible only within my local network.  Some of the address mappings in the local server point to addresses at Linode; the rest point to local servers and clients.  That eliminates the need for subdomain addressing like "hostname.local.example.com".  It also avoids having to advertise the subdomain on your publicly-visible server.

Just make sure local clients use the local nameserver for all queries against your domain.

---

### Post by wlraider70 on 2013-06-20
That makes sense.

I have an apache server and its serving one site/application.
Right now it's at <officeipaddress>/database.php. Is it possible to use an ip record to make that discoverable at mysite.org/whatever/addresses    ?

How would I configure that record?

---

### Post by SeijiSensei on 2013-06-20
You could point the DNS A record to the public server IP and use port forwarding with iptables to relay the traffic on ports 80 and/or 443 to your local machine.  I recommend setting up an [OpenVPN point-to-point tunnel with static keys]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for this task.

---

### Post by wlraider70 on 2013-06-20
Thanks

---

