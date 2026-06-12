---
title: "Dns"
date: 2011-05-01
forum: Server Platforms
---

### Post by sohe1l on 2011-05-01
Hello All,

I am a new member here.

I have question about setting up a home server using ubuntu.

I have already installed ubuntu server on my machine with apache and mysql.

Now my question is that how to make a domain connected to this machine?

On the domain setting page, it asks me to enter 4 Name servers...

Thanks :)

---

### Post by elico on 2011-05-01
well it depends but most of the domain registrars have their own dns servers so you better use them at first.
after a while use your own.

---

### Post by hawk2010 on 2011-05-02
Dear Sohe,

Below in point form are the things you should be doing : 

1. Register the domain name (which you may have done right now)
2. Get a static IP address from your ISP (or if you still want to use dynamic, use DynDNS)
3. On your DSL router , use port forwarding and port forward port 80 to your internal server's private IP address
4. Configure ufw (firewall UI) to allow port 80 traffic
5. Configure your apache2 to listen to port 80 on your interface that is connected to your router.
6. Include a A  on your DNS so that your [www.mydomain.com](www.mydomain.com) points to yourdslpublicstaicIP address.

Hope this helps

Good lucK!

---

