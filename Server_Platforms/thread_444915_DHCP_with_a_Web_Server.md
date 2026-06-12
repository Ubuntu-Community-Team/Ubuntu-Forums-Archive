---
title: "DHCP with a Web Server"
date: 2007-05-15
forum: Server Platforms
---

### Post by blmartin777 on 2007-05-15
I am building a web server for the first time. Do I have to have a static IP address to do that or can I have DHCP? I know I can use DynDNS or NoIP but are those reliable?

---

### Post by mssever on 2007-05-15
> **blmartin777 said:**
> I am building a web server for the first time. Do I have to have a static IP address to do that or can I have DHCP? I know I can use DynDNS or NoIP but are those reliable?

I haven't had any trouble with DynDNS, but if your IP changes, it could be a little bit (up to 48 hours in the most extreme cases) before the various DNS caches get updated. This means that your site could appear to go down for a while. This isn't too likely, but it all depends on what kind of reliability you're looking for. If you're trying to build the next Google, you need a static IP. If you're just setting up a small site that only a few people are likely to visit, than a dynamic IP is sufficient.

---

### Post by x64Jimbo on 2007-05-15
DynDNS is quite reliable - I've been using it exclusively for 4 years now without any problems. If you are behind a router in your house, you can usually even have the router do the talking to DynDNS and save yourself having to run their software on your PC. Now, you will probably need a static IP for the machine behind your router since you'll have to forward port 80 to that machine. You can usually set up what's called "Static DHCP" where the machine always requests a dynamic IP address, but the router always assigns it the same address, no matter what. That way, your port forwards will always stick.

---

### Post by mssever on 2007-05-15
> **x64Jimbo said:**
> DynDNS is quite reliable - I've been using it exclusively for 4 years now without any problems. If you are behind a router in your house, you can usually even have the router do the talking to DynDNS and save yourself having to run their software on your PC. Now, you will probably need a static IP for the machine behind your router since you'll have to forward port 80 to that machine. You can usually set up what's called "Static DHCP" where the machine always requests a dynamic IP address, but the router always assigns it the same address, no matter what. That way, your port forwards will always stick.

In my case, my router won't let me do static DHCP, so I've configured my server to use a static IP address and not DHCP. It works fine with my router (Linksys WRT54G). Your mileage may vary.

---

### Post by blmartin777 on 2007-05-15
Do you use the free dyndns service? Does it ever expire? Or should you pay the $9.95 to upgrade?

Thanks for the help

---

### Post by mssever on 2007-05-15
> **blmartin777 said:**
> Do you use the free dyndns service? Does it ever expire? Or should you pay the $9.95 to upgrade?

Thanks for the help

I use the free service. It expires if it goes 30 days without updating. You can probably configure your router to do the updating automatically, though. At any rate, they'll e-mail you before it expires; you can simply log on to their site and manually update. I've only had to do that once in the approximately six months I've been using DynDNS.

---

### Post by blmartin777 on 2007-05-15
Do you notice a speed issue? Mine seems slow. I am assuming it is the upload on my ISP though. What is good upload speed when hosting websites?

---

### Post by mssever on 2007-05-15
> **blmartin777 said:**
> Do you notice a speed issue? Mine seems slow. I am assuming it is the upload on my ISP though. What is good upload speed when hosting websites?

Residential ISPs usually provide poor upload speeds--and they're usually not too sympathetic towards server operators. I take what I can get. There's no way I'm going to pay a bunch of money for better upload speeds.

---

### Post by blmartin777 on 2007-05-15
I think I have 256k upload right now but I can get 1mb for $15 dollars a month more. Is 1 mb pretty good for upload?

---

### Post by mssever on 2007-05-15
> **blmartin777 said:**
> I think I have 256k upload right now but I can get 1mb for $15 dollars a month more. Is 1 mb pretty good for upload?

Depends on what you're doing. It's certainly a lot faster, but I don't know whether it'll suit your needs.

---

### Post by blmartin777 on 2007-05-15
How fast would a major web company be. Like say google for instance. I know I don't need that kind of speed but what would there speed be? I want websites that I host to come up fairly quickly.

---

### Post by x64Jimbo on 2007-05-15
> **mssever said:**
> In my case, my router won't let me do static DHCP, so I've configured my server to use a static IP address and not DHCP. It works fine with my router (Linksys WRT54G). Your mileage may vary.
YMMV indeed. My Linksys WRT54G **does** allow me to set such static DHCP addresses. Firmware upgrade?

---

### Post by mssever on 2007-05-15
> **x64Jimbo said:**
> YMMV indeed. My Linksys WRT54G **does** allow me to set such static DHCP addresses. Firmware upgrade?

My router is a WRT54G version 6 with firmware version 1.01.1. Are you using a later version, or have I missed something?

(I'm looking to see if there's newer firmware available now.)

---

### Post by x64Jimbo on 2007-05-16
#-oOops. I'm using the DD-WRT firmware. Forgot that I upgraded to that. I **highly** recommend it, though. It adds a TON of features like this and really makes your router more useful.

---

