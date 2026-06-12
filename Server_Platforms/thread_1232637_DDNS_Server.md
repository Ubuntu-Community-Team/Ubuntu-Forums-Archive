---
title: "DDNS Server"
date: 2009-08-05
forum: Server Platforms
---

### Post by scroo.loose on 2009-08-05
Has anyone set up a server using DDNS? I am trying to hold off on getting a dedicated IP for my server untill I have a reason for need all of the bandwidth.  Is there anything special i need to do when configuring server for ddns? Even if they seem like obvious suggestions pass them on. Sometimes frustration can make the obvious answers not so obvious.

---

### Post by cariboo on 2009-08-06
You can use any of several providers, the only one I've tried is no-ip. You choose your domain name when you register, and then you run the script that phones home with your ip address. Then port forward the service you want to access remotely to your router and your done.

---

### Post by trundlenut on 2009-08-06
check to see if your router can update the DDNS with your IP address, that will save you having to run any scripts or suchlike on the server.

---

### Post by Brazen on 2009-08-06
> **trundlenut said:**
> check to see if your router can update the DDNS with your IP address, that will save you having to run any scripts or suchlike on the server.

I set up my ddns configuration on my router.  However, my little brother is still in college so his computer moves around between our parent's house and student housing, so I set up ddclient on his computer.  That way, the dns name follows his computer instead of staying with the router.

---

### Post by scroo.loose on 2009-08-06
A buddy of mine told me about dyndns.com is anyone familiar with this site? They do free dns hosting. Are sites like this secure? Granted material that i am going to be posting is not sensitive i just dont want to deal with the hassel of poor functionality.

---

### Post by jdakhayman on 2009-08-07
I personally use no-ip.com and host several websites for local churches as well as provide email services for them. All of this using no-ip.com. They have been extremely reliable and the up date client is easy enough to install. They also support port 80 forwarding for free, which is usually one of the reasons people go looking for one of these services to get around there isp's blocking port 80 inbound requests.

Setting up a server for what ever reason is as easy as following one of the many guides that are around on the web. Personally I use how-to forge. Then making sure that all your dns entries point to the proper places.

jdakhayman

---

### Post by doomsayer97 on 2009-08-07
I used DynDNS for my server. It works great. You can use their IP updater client to have your IP get updated so that the address is up to date. But use DDClient instead of the one that DynDNS has. I think it's a lot better.


Also, some routers allow you to reserve IP addresses for devices that connect to the Internet through it. I did that for my server, because it was a lot easier.
I found this setting in the DHCP menu, if it helps. My router is a DLink VWR 11.4.

Also, as long as you keep the server turned on, the IP address will remain constant.

---

### Post by scroo.loose on 2009-08-07
i appreciate the responses. right now i am leaning towards dyndns.com. as far as no-ip goes do you need to purchase a domain name with them? or is it free of charge? i am tryin to go as low budget as possible without having to compromise funtionality. eventually once i have enough material put together i will be hosting a tutorial site as well as an ftp server for small files. eventually i may get into servering larger files and this will be when i purchase a seperate ip address from my isp. :D

---

### Post by doomsayer97 on 2009-08-08
Both DynDNS and No-IP are free services which offer paid services.

So with the free services, you'd get an appendage like:
.homelinux.com
And with the paid services, you'd get your own domain.

---

