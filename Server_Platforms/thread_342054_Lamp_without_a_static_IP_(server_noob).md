---
title: "Lamp without a static IP? (server noob)"
date: 2007-01-19
forum: Server Platforms
---

### Post by amoore on 2007-01-19
Ok, I know you should use a static IP when setting up a server...but I want to know If its possible for me set up a LAMP server without a static IP. I have high speed Internet connection at home about (1500kbs) and I use a dlink di-524 router which is always on holding the same IP address from my ISP . I have never set up a LAMP server before, is this possible? 

If possible how do it do it. All the guides I read use a static IP. 

This Lamp server would just be used as a toy and not for mission critical use. I want to expand my Linux knowledge with servers. I have used Ubuntu for a little over two years and I feel comfortable with it as a desktop but, would like to start learning about LAMP servers. :)

---

### Post by jtc on 2007-01-19
It is very doable to run a LAMP on a dynamic ip-address. In fact, it's something a lot of hobby-users do. Thought, it's nothing I'd recommend for a production-server.

I'll start by giving you the basic principles. Then you can ask more detailed questions as needed.

As long as you only use one ip-address Apache don't need to know it. Just tell it to listen on any ip-address. When it comes to MySQLd you can simply always connect to it as localhost.

The tricky part, well at least slightly so, is to make sure the rest of the world can continue to find your server when its ip-address changes. This is solved by a service such as [DynDNS]("http://www.dyndns.com/services/dns/dyndns/") or similar.

---

### Post by amoore on 2007-01-19
Thats great!!!! Can you point me to some documentation for using a dynamic ip-address with LAMP. Also can you tell me more about DynDNS?

---

### Post by jtc on 2007-01-20
Actually, the default apache-setup in Ubuntu is to listen to any ip-address, so it should pretty much work by default. But if you want a tutorial you ought to look at the one among the Ubuntu community docs.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

About DynDNS, did you follow the link to it in my first post? I thought it explained things pretty well.

---

### Post by chrisfay on 2007-01-20
> which is always on holding the same IP address from my ISP 

Unless you incorrectly stated this, you most likely DO have a static IP. If that's the case, you won't need any dynamic dns services. 

In either case, since you're behind a router you would need to supply your server on your LAN with a static IP rather than pulling one from your router's DHCP server and port forward port 80 to that ip/server. Even if your ISP designates your connection with a static ip, your internal LAN is most likely configured DHCP from your router which would need to be change before anything. 

This article shows the steps for both gui and shell methods. (for debian but works the same) 
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html) 

> Thats great!!!! Can you point me to some documentation for using a dynamic ip-address with LAMP

....Again, that's only necessary if your connection is in fact dynamic. If your router holds the same IP 'always', you may have a static connection. Or it may be dynamic, but rarely changing. If you're not sure, call your ISP. Its definately something you want to make sure on to eleviate extra uncecessary steps.

Another word of caution, I just had my cable connection suspended for hosting web sites on my home connection. It is agains almost every residential ISP's TOS to host public sites on their lines and they 'will' disconnect your services.

---

### Post by amoore on 2007-01-20
Thanks for everyones help, I got my lamp server up and going great!!! It was very fast including the Ubuntu install it wasup in just under one hour. Now its time to learn about PHP.

---

### Post by az on 2007-01-20
Here is a general page for running a server from home like you are doing:

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

