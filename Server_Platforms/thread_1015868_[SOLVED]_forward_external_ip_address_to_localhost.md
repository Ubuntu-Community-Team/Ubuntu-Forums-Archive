---
title: "[SOLVED] forward external ip address to localhost?"
date: 2008-12-19
forum: Server Platforms
---

### Post by amac777 on 2008-12-19
My computer is behind NAT so it uses 192.168.1.6 as its IP address.

I have apache2 installed and working.

While sitting at my computer, I can browse my local website by going to [http://192.168.1.6](http://192.168.1.6).

I also have port forwarding setup and working on my router. So my friends can browse my website by going to my external IP address [http://219.x.x.x](http://219.x.x.x) (for example).

So we each need to use different IP addresses to browse the website. This is OK, however it makes it difficult to test functions like RSS feeds for example where I need to specify the full URL of the website, which is different for me and the external people.

What I would like to do is be able to browse my local website while sitting at my computer by using the external IP address.

Currently, if I try to browse using my external IP address [http://219.x.x.x](http://219.x.x.x), I end up at my router's login page. It seems the router redirects the external IP to it's login page when it's accessed from inside the network. 

I tried adding a forward from the external IP to the internal IP in /etc/hosts but that didn't work. (I guess because /etc/hosts only maps domain names to IP addresses - not IP addresses to other IP addresses)

Is there a way to forward/redirect/map an external IP address to localhost? Instead of actually sending traffic to the external IP address, I'd like to just redirect it to my localhost.

---

### Post by cdenley on 2008-12-19
I don't think you can tell your own computer to redirect outgoing traffic. Most routers will forward traffic sent to it's external IP from inside the LAN. Is there a setting in your router's configuration such as "local loopback". Maybe you can update your router's firmware.

A much simpler solution would be to access your site with a domain name.

---

### Post by cariboo on 2008-12-19
I would suggest using something like [noip free]("http://www.no-ip.com/"), that way you don't have to worry if your external ip address changes.

Jim

---

### Post by amac777 on 2008-12-19
For some reason I thought it would be easy to redirect outgoing traffic, but, you're right, it is easy to do this with a domain name so I that's what I just did. 

Also thanks for the noip free recommendation. I signed up on it and now external / internal can both access the site using the same domain name. much better for testing consistency purposes.

---

### Post by MJN on 2008-12-20
You've missed a step out. Regardless of whether you're using the external address direct or as a result of resolving the domain name you still have the issue of your router responding with its configuration page on port 80. That's where your problem lay - disable it and you're sorted.

Mathew

---

### Post by amac777 on 2008-12-20
You're right, using a domain name, the missing step is just to make a quick modification of /etc/hosts to resolve the domain name to my localhost (local IP) directly instead of going out via DNS and getting the external IP address. 

I did check through the settings of the router and found nothing in there about loopback or how to disable that weird "function" of giving me the config when I use the external address of the router.

---

### Post by MJN on 2008-12-20
You may find that if you can't disable the external config page (which you would want to do from a security perspective) then if you change the port it listens on you'd also be sorted.

Mathew

---

