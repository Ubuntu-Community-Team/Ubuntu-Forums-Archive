---
title: "Web server"
date: 2013-08-26
forum: Server Platforms
---

### Post by fperez87 on 2013-08-26
Hello, this is my first time using Ubuntu Server and I've been setting up an old computer so I can host my website from there. I set up LAMP and a Firewall following every single step from a tutorial ([http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)). the server is working in my network, but I don't know what's next for making my website available through the internet. My router is an Airport Express and of course I have dynamic IP's. I read something about setting up the router for having a public static IP, but I don't find any setting menu for doing that.... so I would appreciate a lot some clear guidance on what I should do next.

thanks

Frank

(by the way, I installed ubuntu server 12.04)

---

### Post by Kevin_Arnold on 2013-08-26
You would have to purchase a static IP address from your ISP but it probably isn't worth it. You could probably just use a VPS like digitalocean.com for less than the price of a static IP. 

You can also look in to dynamic dns services, they run on your router or computer and update a service so your domain will always have the right IP even though it is dynamic.  

Just for testing, you can just use your current dynamic IP. They usually stay the same for quite awhile.

Go to whatismyip.com to get your current dynamic address. You can just type that in the address bar in a browser on a computer not on your network to see if you have everything set up right.  If it doesn't work, you'll need to make sure you have port 80 forwarding to your server in the router.

---

### Post by lisati on 2013-08-26
*Thread moved to **Server Platforms**.*

Organizing a public-facing static IP address is usually organized with the help of your ISP, and is likely to cost you some money each month. Running a website from a dynamic IP address takes a small amount of extra work in the setup stage, but depending on who your DNS provider is, you might be able to organize automatic updates to your DNS records to make sure that your domain name points to the correct IP address. no-ip.com and dyn.com both have update clients that you can run on your server; if you're in luck your router might be able to do this for you.

---

