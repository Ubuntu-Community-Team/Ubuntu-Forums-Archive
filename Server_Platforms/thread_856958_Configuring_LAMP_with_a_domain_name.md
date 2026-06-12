---
title: "Configuring LAMP with a domain name"
date: 2008-07-12
forum: Server Platforms
---

### Post by applefat on 2008-07-12
Hello all! I realize there are bits and pieces of guides all over the place but I simply have not been able to get them all working together. I'm using Ubuntu 7.04 on an older macintosh and there are 2 other Windows XP machines on the same LAN (all can share files with each other via Samba).

So I've registered a free account at DynDNS.com, let's call it my new hostname:

*myprojects.dyndns.org*

and I've set the ip address to the external address for my home lan. If I use *dig myprojects.dyndns.org* on the server, I can see that it is indeed tied to my external network IP address.

I have Apache working, and I know it because the server's local address is 192.168.2.4, and if I go to:

*[http://192.168.2.4](http://192.168.2.4)*

I see the default apache website. I can see this from other computers on the LAN as well. 

Now, I know my ISP blocks incoming connections from port 80, but I've heard that you can use port 443 in the same way, by using
"https" rather than "http". In anticipation of this I've set up my router to send incoming connections on this port to the server's same port. My Belkan router config looks like this:
[http://myweb.unomaha.edu/~amills/temp.jpg](http://myweb.unomaha.edu/~amills/temp.jpg)

What do I do now? I read all this stuff about editing this or that config, but maybe someone can help me with my particular example?

---

### Post by windependence on 2008-07-12
I would not use 443. Use something like 8080 or another high port. You will have to point your dynamic ip at that port. I don't know how to do that with  dyndns since the only redirect I ever used was no-ip, but I know it's possible.

You may be better off in the end getting a static IP from your ISP. Some, like mine only cost a small amount. I pay an extra $4.95 per month.

-Tim

---

### Post by applefat on 2008-07-12
> **windependence said:**
> I would not use 443. Use something like 8080 or another high port. You will have to point your dynamic ip at that port. I don't know how to do that with  dyndns since the only redirect I ever used was no-ip, but I know it's possible.

You may be better off in the end getting a static IP from your ISP. Some, like mine only cost a small amount. I pay an extra $4.95 per month.

-Tim
Ah yes, I looked through no-ip and see that they have a nice port-redirect feature.

But, where/what would I need to set up on the server end to make that "connection"? I mean, surely I have to somehow associate the apache server config with whatever nameserver I end up using, and so on? Or to at least listen to port 8080 rather than whatever is default?

---

### Post by cdtech on 2008-07-12
Apache will listen on any port you want it to by setting the port number within the /etc/apache2/ports.conf. If your ISP blocked port 80 you would not be able to access the internet. How is that possible?

---

### Post by applefat on 2008-07-12
> **cdtech said:**
> Apache will listen on any port you want it to by setting the port number within the /etc/apache2/ports.conf. If your ISP blocked port 80 you would not be able to access the internet. How is that possible?

Well I've read that my ISP blocks /incoming/ requests from port 80, though perhaps I misread?

But anyway, I just changed the listening port and now I can connect with my no-ip address =)

---

### Post by cdtech on 2008-07-12
cool, good luck.....

---

### Post by windependence on 2008-07-12
> **cdtech said:**
> Apache will listen on any port you want it to by setting the port number within the /etc/apache2/ports.conf. If your ISP blocked port 80 you would not be able to access the internet. How is that possible?

Trust me they can and do block traffic on 80 that looks like it is server generated. I am not sure how this is done but it is done somehow at their routers.

-Tim

---

### Post by chris.zeman on 2008-07-12
> **cdtech said:**
> Apache will listen on any port you want it to by setting the port number within the /etc/apache2/ports.conf. If your ISP blocked port 80 you would not be able to access the internet. How is that possible?

Think of ISPs as firewalls. They'll allow anything to leave, but any connections not initiated by the customer can be blocked.

Chris

---

