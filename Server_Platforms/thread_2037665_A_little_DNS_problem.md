---
title: "A little DNS problem"
date: 2012-08-05
forum: Server Platforms
---

### Post by goldtrinitron on 2012-08-05
I have just install the 

The Perfect Server - Ubuntu 12.04 LTS (Apache2, BIND, Dovecot, ISPConfig 3)

everything work perfect 
I have only one small problem. When I what to see a webpage inside my network my router an Cisco RV220W route the me to it's management page.

If I go to another internet connection the page works fine it is only when I'm inside the same network. 
What is the easy way to see the pages local.

Kind Regards
Kasper

---

### Post by darkod on 2012-08-05
I don't know about that Cisco, but most home routers will not be able to return you to your webserver inside once you go out.

For this purpose, showing up a local website on your own server, you do it slightly differently.

I guess in your bind setup you do have A records for your website pointing to the local server private IP right?

In that case, you only need to tell the dhcp server on the Cisco to use your local server (bind is on it) as primary dns. When it sends network config to the clients on the network, it will send them your own server as primary dns. So when you type your domain in a browser, your bind will resolve that domain to the IP address of the local server.

Alternatively, you can edit the hosts file on each internal machine and making an entry for your domain with the server private IP.

Depending what's easier for you, both methods will work. The second method will work even if your bind is not set up correctly.

---

### Post by SeijiSensei on 2012-08-05
> **goldtrinitron said:**
> What is the easy way to see the pages local.

Use the server's local address, not its public IP.  If you are using name-based virtual hosting, you'll need to create an entry in the client's [hosts]("http://en.wikipedia.org/wiki/Hosts_(file)") file that associates the server name that you use in the URL with the server's internal-facing IP address.

---

