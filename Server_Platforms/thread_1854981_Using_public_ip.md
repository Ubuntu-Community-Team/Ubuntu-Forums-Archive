---
title: "Using public ip"
date: 2011-10-05
forum: Server Platforms
---

### Post by Mattwilkinson on 2011-10-05
Hi,

I want to get my server up on the Internet for the public to view my website, but I don't know how to make it public.

The server works fine in my network with my local ip but how do I get it to run off a public ip? I have forwarded the port 80...

Thanks for your help.

---

### Post by [S|G] on 2011-10-05
There are a number of things you should check if you want to make your server public:

1 - Check that port 80 is reachable on your public address. If you're running the server from home it is possible that your ISP is blocking port 80. If that happens, you'd need to switch to an unblocked port

2 - If your port 80 is reachable, you'd need to forward it to your webserver (you did this from what you mentioned).

3 - Make sure the webserver can reply to internet (i.e. has the correct gateway)

4 - The website should be accessible from [http://[your](http://[your) public ip address here]. If you're not running from port 80, you'd need to use [http://[your](http://[your) public ip address here]:[port]

To make things simpler, you can also use a DDNS service to map your address to a name instead of using your IP address.

---

### Post by lcman on 2011-10-05
> **Mattwilkinson said:**
> Hi,

I want to get my server up on the Internet for the public to view my website, but I don't know how to make it public.

The server works fine in my network with my local ip but how do I get it to run off a public ip? I have forwarded the port 80...

Thanks for your help.

You need to purchase a public static IP address from your ISP to make that happen. You will also need to make your router accessible from outside by setting up a DNS server. DynDNS has a free service you can use.

---

### Post by matt_symes on 2011-10-05
Hi
> 
1 - Check that port 80 is reachable on your public address. If you're  running the server from home it is possible that your ISP is blocking  port 80. If that happens, you'd need to switch to an unblocked portIf you need to check this then try a service such as

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

and enter port 80 when your web server is running and the correct ports forwarded on your router.

EDIT: If they are blocking port 80 find an unblocked port and use dyndns with webhops specifying the ip address and port number in the web hop.

If have not tried this myself - my ISP is pretty good - but i believe it works.

Kind regards

---

### Post by [S|G] on 2011-10-05
> **lcman said:**
> You need to purchase a public static IP address from your ISP to make that happen. You will also need to make your router accessible from outside by setting up a DNS server.

Not really. For non-production purposes such as developing a website and/or sharing stuff with friends/coworkers a dynamic IP is fine. If he intends to make the website available to a greater audience then a static IP address would be desirable.

DNS too is optional and for a home web server a free DDNS service should suffice.

---

