---
title: "enable port 8080 for www"
date: 2012-01-23
forum: Server Platforms
---

### Post by hewe on 2012-01-23
I have a server installed for website testing behind a router in my LAN. My isp blocks port 80, so i have to use 8080.
In the LAN everything works perfect with port 80. However using 8080 the server dows not react with "It Works". I assume i will have to setup a few things to have 8080 listen and react on tcp traffic for apache.

How do I check this and
what do I have to do to get this running?
thanks in advance for 
Henk

---

### Post by Grenage on 2012-01-23
I believe that Apache2 listen ports can be configured here:

/etc/apache2/ports.conf

---

### Post by HugoSerrano on 2012-01-23
> **Grenage said:**
> I believe that Apache2 listen ports can be configured here:

/etc/apache2/ports.conf


Or you can configure you router to do a forward from port 8080 to port 80 in your server. 
In this case, you will access your page in port 8080 from outside (WAN) and port 80 from inside (LAN).


Regards!

---

### Post by hewe on 2012-01-23
Thanks for the tips. I will give both a try.

Thanks,
Henk

---

### Post by TFroehlich3 on 2012-01-23
I will also be trying this when I get back to my place!
I too thank you!

---

### Post by mario.niessner on 2012-01-23
You ***will*** have to configure port forwarding in your router, anyway (whether you do change the listening port in your web server configuration or not), as long as your router is not configured in bridge mode. That being the case, port forwarding is mandatory for every service you'd want to be seen from the WAN.

Choose any port your ISP is not blocking (e.g. 8080) as the incoming port at your router's config, and the webserver's ip:port as the destination. That's all.

---

### Post by spindler on 2012-01-23
sub

---

### Post by TFroehlich3 on 2012-01-23
> **HugoSerrano said:**
> Or you can configure you router to do a forward from port 8080 to port 80 in your server. 
In this case, you will access your page in port 8080 from outside (WAN) and port 80 from inside (LAN).


Regards!

Alright, so after I port forward from 8080, what do I do after that? From there am I just going to my domains site and putting that info in there to point the domain to my server? And would that be 192.168.X.X:8080?

---

### Post by hewe on 2012-01-24
No, when you server is behind the router it gets a 192.168.x.x address, because the router uses NAT. On the WAn site you have an IP address given by your ISP. When you have a dynamic ip provided visit no-ip.com and get a "static" domain name, such as <name>.servehttp.com to be used to get through to your server behind the router with NAT. You can use <name>.servehttp.com:8080 when you use port 8080

succes
Henk.

---

### Post by TFroehlich3 on 2012-01-24
> **hewe said:**
> No, when you server is behind the router it gets a 192.168.x.x address, because the router uses NAT. On the WAn site you have an IP address given by your ISP. When you have a dynamic ip provided visit no-ip.com and get a "static" domain name, such as <name>.servehttp.com to be used to get through to your server behind the router with NAT. You can use <name>.servehttp.com:8080 when you use port 8080
 
succes
Henk.
 
Okay,
   So what do I need to do in order to be able to access the website by entering the IP address of the server (over the internet / not local) just to test the site and its functions?

---

### Post by Grenage on 2012-01-24
All you need to do is forward the ports (from the router config) to the webserver.  As previously mentioned, you could just forward 8080 on the router, to 80 on the webserver - assuming the router has port translation.  If it does not, you'd simply forward 8080, and change apache to 8080.

Then it would be:

[http://xxx.xxx.xxx.xxx:8080](http://xxx.xxx.xxx.xxx:8080)

---

### Post by TFroehlich3 on 2012-01-24
> **hewe said:**
> No, when you server is behind the router it gets a 192.168.x.x address, because the router uses NAT. On the WAn site you have an IP address given by your ISP. When you have a dynamic ip provided visit no-ip.com and get a "static" domain name, such as <name>.servehttp.com to be used to get through to your server behind the router with NAT. You can use <name>.servehttp.com:8080 when you use port 8080

succes
Henk.

Okay, so tell me again why I need to get "static" domain name from "no-ip." Because I have a domain name from GoDaddy....

---

### Post by hewe on 2012-01-25
When you have static ip address from your isp it's okay. However when you get a dynamic ip address It will change once in a while. The dyndns domain checks regulary your real ip and adapts it when somebody enters your dyndns domain name.
In case you have a domain recognised by the dns servers, you are okay and do not need any other action, because it wiil be taken care of by the dns server.

Hope this helps.
Henk

---

### Post by HugoSerrano on 2012-01-25
So, if you get your dynamic dns service, you can do solve your dynamic dns name (no-ip, dyndns, whatever...) to your non-static IP and keep it updated. Then in your godaddy account, you create a CNAME record to point [www.example.com](www.example.com) to dynamicdnsname.no-ip.biz.

Then you can access you web page by your domain!

But, like hewe said, if you got static IP, you don't need the dynamic dns thing.

Regards!

---

### Post by TFroehlich3 on 2012-01-25
> **hewe said:**
> When you have static ip address from your isp it's okay. However when you get a dynamic ip address It will change once in a while. The dyndns domain checks regulary your real ip and adapts it when somebody enters your dyndns domain name.
In case you have a domain recognised by the dns servers, you are okay and do not need any other action, because it wiil be taken care of by the dns server.

Hope this helps.
Henk

Alright, so how can I tell if I have a dynamic ip or static ip from my isp? Because I am doing this from my apartment complex which has free internet via wired connection to every room.

---

### Post by Grenage on 2012-01-25
> **TFroehlich3 said:**
> Alright, so how can I tell if I have a dynamic ip or static ip from my isp? Because I am doing this from my apartment complex which has free internet via wired connection to every room.

Unless the provider says "you have a static IP", you can't really tell.  Most of the time it's an optional extra, but it depends where you are and who you use.

---

### Post by TFroehlich3 on 2012-01-25
> **Grenage said:**
> Unless the provider says "you have a static IP", you can't really tell.  Most of the time it's an optional extra, but it depends where you are and who you use.

Alright, so I will just give Charter Communications a call and see if they can give me that information.... If they can't give me that information because I'm not the account holder what can I do from there? Just find another location for my server?

---

### Post by Grenage on 2012-01-25
> **TFroehlich3 said:**
> Alright, so I will just give Charter Communications a call and see if they can give me that information.... If they can't give me that information because I'm not the account holder what can I do from there? Just find another location for my server?

I imagine there's a good chance that if you give them the IP and ask if it's static, they'll help; you aren't trying to alter the service.

If it's dynamic, you could either relocate the server, or opt for the Dynamic DNS option that was mentioned by previous posters.

---

### Post by codmate on 2012-01-25
Assume it's dynamic. The vast majority are.

---

### Post by TFroehlich3 on 2012-01-25
> **Grenage said:**
> I imagine there's a good chance that if you give them the IP and ask if it's static, they'll help; you aren't trying to alter the service.

If it's dynamic, you could either relocate the server, or opt for the Dynamic DNS option that was mentioned by previous posters.

I'm pretty sure that it is dynamic because I looked up my IP at whatsmyip.org and it said it was xx.xx.xxx.162 and I just now checked it and it said it was xx.xx.xxx.171. That does mean it's dynamic, right?

---

### Post by TFroehlich3 on 2012-01-25
> **HugoSerrano said:**
> So, if you get your dynamic dns service, you can do solve your dynamic dns name (no-ip, dyndns, whatever...) to your non-static IP and keep it updated. Then in your godaddy account, you create a CNAME record to point [www.example.com](www.example.com) to dynamicdnsname.no-ip.biz.

Then you can access you web page by your domain!

But, like hewe said, if you got static IP, you don't need the dynamic dns thing.

Regards!

How much are these services? :/

---

### Post by HugoSerrano on 2012-01-25
> **TFroehlich3 said:**
> How much are these services? :/

Free :-) maybe not to comercial use.

---

### Post by TFroehlich3 on 2012-01-25
> **HugoSerrano said:**
> Free :-) maybe not to comercial use.

Nice! Can't beat that!

---

### Post by TFroehlich3 on 2012-01-25
> **hewe said:**
> No, when you server is behind the router it gets a 192.168.x.x address, because the router uses NAT. On the WAn site you have an IP address given by your ISP. When you have a dynamic ip provided visit no-ip.com and get a "static" domain name, such as <name>.servehttp.com to be used to get through to your server behind the router with NAT. You can use <name>.servehttp.com:8080 when you use port 8080

succes
Henk.

Alright, so I'm on "no-ip" so now what do I do? Do I go to "hosts/redirects" ==> "Add Host" or no? Can someone help walk me through this? :)

---

### Post by TFroehlich3 on 2012-01-27
?

---

