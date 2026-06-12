---
title: "Apache2 webserver"
date: 2012-06-17
forum: Server Platforms
---

### Post by Pemblem on 2012-06-17
So, I'm trying to set up a live webserver in Apache2. I've got a whole PC dedicated to hosting this one site. I've installed Apache2, I've made a start page for my website, and put some files in the right folders, I've opened up port 80 on the network, and I've pointed my domain name to the webstie on my server. I can access the website from any PC on our home network through the 192 url, but I can't access it from my domain name, or from any computer outside my network. So, basically, it seems to be working, but it's not live, What do I do? 

Please help? :(

---

### Post by lisati on 2012-06-17
Is your server connected through a dynamic public IP address? If so, you might need to arrange for your DNS records to be updated automatically [s]if[/s] when your IP address changes. Your router might be configurable to do this for you - I know mine can handle accounts with DynDns and no-ip. Failing an option in your router, you might be able to install a client. 

Another possibility is that your ISP is blocking incoming requests to port 80. This is something you might have to take up with your ISP.

---

### Post by Pemblem on 2012-06-17
It could be a problem with the isp, I dunno. 
I'm 99% sure though that our IP address is a static one.

---

### Post by N0oki3 on 2012-06-17
> **Pemblem said:**
> I'm 99% sure though that our IP address is a static one.
You can ask your internet provider to be 100% sure. 

> **Pemblem said:**
> 
I can access the website from any PC on our home network through the 192 url, but I can't access it from my domain name, **or from any computer outside my network.**


did you edit http conf to allow from all (connection)

---

### Post by Pemblem on 2012-06-17
> **N0oki3 said:**
> did you edit http conf to allow from all (connection)

I don't think so, I'll have to check (recovering from surgery, can't get on server atm ) that might be the problem. 

I love your avatar, btw.

---

### Post by lisati on 2012-06-17
> **Pemblem said:**
> I don't think so, I'll have to check (_recovering from surgery_, can't get on server atm ) that might be the problem. 

Here's to a speedy recovery! Hopefully the ideas that come your way will be of some help when you're in a better position to access the server.

One website that might be of help figuring out IP address stuff, including whether or not your on a static IP, is [www.whatismyipaddress.com](www.whatismyipaddress.com)

---

### Post by Pemblem on 2012-06-17
Thanks a lot! That should help.

---

