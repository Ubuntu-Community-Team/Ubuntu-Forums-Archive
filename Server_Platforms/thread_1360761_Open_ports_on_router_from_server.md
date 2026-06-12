---
title: "Open ports on router from server"
date: 2009-12-21
forum: Server Platforms
---

### Post by blsmit on 2009-12-21
I have a challenge for you amazing computer people.

Can I open a port on my Linksys router from a headless server, If I'm ssh'ing in from somewhere else.  

I have this server working off dyndns, so I can access without the ip address. 

If you need any other information please ask.

Thanks in advance for the responses, blsmit

---

### Post by BkkBonanza on 2009-12-21
Your question is a bit confusing so I'll answer what I think you are asking.

If you login into your server using ssh then you can run programs on the server that could use UPnp to update the ports forwarded on the router, as long as your router does have UPnp support and it's enabled.

UPnp (Universal Plug and Play) is a protocol for dynamically changing port forwarding. Often programs will have support for it (eg. uTorrent, Deluge etc) so they can manage dynamic port assignments.

How you actually configure this depends on what software you're using and how you intend to use it.

---

### Post by blsmit on 2009-12-21
Yes I figured it would be confusing. 

So what your saying is if UPnp is enabled on the router, I can use another program Like uTorrent, to open up ports that I need to be open on the Router. 

See, I don't have any issue opening ports on the server, but since it is the only computer connected to the router, I think it is the only way for me to open ports on the router.

Is there a howto somewhere for me to follow to use UPnp?

Thanks for the response and more are welcome.
Blsmit

---

### Post by gobbledigook on 2009-12-21
if i understand you right, you want to change the port configuration of your router via ssh'ing through to your server?

why not just enable remote management on the router?

another option could be to use VNCserver to create a remote desktop on the server and then pop open a browser to access the routers config... assuming you need to use the gui.

If you wanted to do it totally by command line then you would need to install open source firmware on the router like dd-wrt or tomato... this would allow you to remotely connect to the router via ssh and execute commands make configuration changes. mines set up using dd-wrt and optware as well, which allows for a better command shell and to load and run a variety of linux packages

---

### Post by blsmit on 2009-12-21
As much as I would love to do everything you mentioned, there are a few issues.  1. The router is currently 200 miles away from me, and there is no one close to change it (College student over christmas break). and the second issue is that the router is my girlfriends and if I broke it and she didn't have internet for weeks, well there would never be a server ever again.  So although I like your solutions, are there any others that you have?

Also the server is headless, so as much as I would like a gui, there isn't one to be had.

Thanks Blsmit.

---

### Post by bartos on 2009-12-21
Maybe try installing Lynx web browser on server to locally set router. Activate remote management.
That way you have a basic web interface to make adjustments.

---

### Post by gobbledigook on 2009-12-21
good call bartos :) i love lynx!

---

### Post by blsmit on 2009-12-21
lynx, sounds like the best thing ever and would work perfectly for what I need to do. However, while screwing around with the ports, I seem to have activated the ufw and can't get back in. any solution?  I used to log with ssh on a different port I set up.  

Thanks

---

### Post by HighCommander540 on 2009-12-21
> **gobbledigook said:**
> good call bartos :) i love lynx!

Better idea. I found it out myself. Use this command:

```
ssh -D port user@domain
```

To create a SOCKS proxy then set your browser to use the SOCKS proxy. Then just enter your router's IP address. And it will be a secure encrypted connection to your router.

Enabling remote management is insecure. Or if you already have Lynx installed. Why would you not just connect with SSH, and use Lynx to control it. Otherwise you are just using a connection that anyone can listen onto or connect to.

---

### Post by hessiess on 2009-12-22
> 
why not just enable remote management on the router?


This is a *EXTREMELY* bad idea, while it would let you edit the configuration, it would also give everyone else on the internet a chance to edit your configuration. If you do, make sure you have an extremely good password, like 64 characters of random junk;)

---

### Post by HighCommander540 on 2009-12-22
> **hessiess said:**
> This is a *EXTREMELY* bad idea, while it would let you edit the configuration, it would also give everyone else on the internet a chance to edit your configuration. If you do, make sure you have an extremely good password, like 64 characters of random junk;)

Yeah, thanks for backing me up on that one.

---

