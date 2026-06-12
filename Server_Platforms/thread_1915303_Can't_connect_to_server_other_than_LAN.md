---
title: "Can't connect to server other than LAN"
date: 2012-01-25
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-01-25
Hello Everyone,
  I was wondering if someone could run the setting configuration by me to get my server online so that I can access it over the internet and not just local (LAN). I have the server running on a static IP, I have the ports opened on the router, what am I missing?

---

### Post by volkswagner on 2012-01-26
What happens when you go to canyouseeme.org and check ports 8080 and 22?

How are you trying to access the server (external ip or domain name?

Are you trying this from inside your LAN, if so try via a proxy such as hidemyass.com?

What happens when you try to access the server, what error do you get?

---

### Post by TFroehlich3 on 2012-01-26
> **volkswagner said:**
> What happens when you go to canyouseeme.org and check ports 8080 and 22?

How are you trying to access the server (external ip or domain name?

Are you trying this from inside your LAN, if so try via a proxy such as hidemyass.com?

What happens when you try to access the server, what error do you get?

I am trying to access it via IP address to access it with SFTP, or my WebMin. Neither of those work outside my Local Area Network. When I try to access it the connection just times out or doesn't respond. 

When I open the ports on my router should it be the IP address of the machine that I put in, or the IP address that is assigned to me by my ISP?

---

### Post by TFroehlich3 on 2012-01-27
Any idea's, anyone?

---

### Post by volkswagner on 2012-01-28
> **TFroehlich3 said:**
> Any idea's, anyone?


You did not answer or respond to all my inquiries.

Have you verified your external ip.  Did you check the open ports at canyouseeme.org?

From inside your LAN navigate to hidemyass.com and enter your external ip with port 8080 like
[http://123.123.123.123:8080](http://123.123.123.123:8080)   what do you get?

Your port forward looks correct on your router... yes you use your servers internal ip address to forward.

---

### Post by volkswagner on 2012-01-28
I just noticed your server is behind two routers?   Perhaps you should define your network setup.

If your server is behind two routers you will either want to set the second router in a DMZ from the first router, or you will need to forward all the individual ports to the second router.

---

