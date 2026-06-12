---
title: "external ip problem"
date: 2010-08-26
forum: Server Platforms
---

### Post by timothyw on 2010-08-26
hello,
i have an ubuntu server in my network it has apache and ftp.
inside my network i can access it with it's internal ip.
but when i  go to whatismyip.org i get 91.177.91.232 .
when i go to whatismyip.org from annother pc in my network i get the same.
when i go to that ip from inside my network i get my router(b-box2) config page.
on the page stands that 91.177.91.232 is the pppoe adress.
any idea how to set up my server.
(sorry for my english).

---

### Post by craigp84 on 2010-08-26
Hi,

You need to configure port forwarding on your router config page to forward TCP ports 80, 21 & 20 to your server's internal IP.

---

### Post by timothyw on 2010-08-26
i've done tath still the same.

---

### Post by amsterdamharu on 2010-08-26
You have to forward ports to your server in your router settings.

But if the router forwards port 80 to your server then request to the router will be forwarded to your server and you will be unable to access the router settings so make sure you can chage the router settings to listen to another port.

For example you type in your browser:
[http://yourip](http://yourip) (same as http;//yourip:80)
you get the router settings if you type
[http://yourip:1234](http://yourip:1234) 
you get nothing because at the moment your router is not listening on port 1234 to display it's settings page.

I was unable to find any settings for this on my router and am reluctant to try forwarding port 80 (I will be unable to access the settings of my router). Your Internet provider might give you another ip address every so often so that ip address might not work very well anyway.

---

### Post by byStanderone on 2010-08-26
...a basic whois check shows that the ip ad you mentioned belongs to belgacom...tho pinging the said ip brings no result from where i am...are you sure that that ip ad is exclusively yours or perhaps it is a natted ip ad of your service provider?

---

### Post by timothyw on 2010-08-26
the ip belongs to belgacom.
but when i go to what is my ip its tath ip.
Any other way to check my ip?

---

### Post by cdenley on 2010-08-26
> **timothyw said:**
> the ip belongs to belgacom.
but when i go to what is my ip its tath ip.
Any other way to check my ip?

That IS the IP you are using, then. However, the question is whether that IP is used exclusively by your router. If so, then all you need is to configure your router to forward unsolicited traffic it receives on a specific port to your server. If not, then the router (not yours) which that IP actually belongs to will have no way of knowing which device the traffic was intended for. If your router says its WAN IP matches the IP you posted, then it should be used exclusively for that router, outside users should be able to reach it, and you should be able to configure it to forward traffic to your server. I can't say how to determine the WAN IP of your specific router, since they are all different.

---

### Post by BkkBonanza on 2010-08-26
You have to disable outside (external) access to the config page on your router. As long as that is enabled it will answer port 80 itself for config rather than forward it to your server. It should still be accessible using the gateway (private, internal) IP.

Also, some routers are dumb in that they won't route the public IP from inside the LAN. Your request goes out but rather than being routed back inside it goes dumb and just gives you the config page. If that is the case then it likely works from outside but you can't check from inside. Then you need to map the name->IP manually in your hosts file or setup some name resolution inside the LAN.

To check how it really works from outside try using a free public web proxy site and enter your IP there and see if it gives you back your page or the router config page.

---

