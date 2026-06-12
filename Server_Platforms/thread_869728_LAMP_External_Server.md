---
title: "LAMP External Server"
date: 2008-07-25
forum: Server Platforms
---

### Post by rockstarrem on 2008-07-25
Hello all,

All I want to do is run a LAMP external server that I can use one of my domain names on. I have no idea how to do this and have followed the perfect server tutorial and the DNS server/LAMP server tutorial and I'm just not getting what I want. This is all I want:

1. Reach my LAMP server from outside of my network with one of my domain names.

Can someone help me out? I'm willing to reinstall Ubuntu Server Edition to do this, in fact I'd prefer it. Thanks!

Dom

---

### Post by windependence on 2008-07-25
You're going to have to be a little more specific than "I'm just not getting what I want". What is not happening that should be? Are you getting any error messages? What have you done so far? Have you pointed your domain at your server? Do you have a static IP address? Does your ISP block your port 80?

Reinstalling is not an option, that is Windoze land and not necessary. Probably won't fix anything anyway. Give me a bit more specific information and we'll try to get you going on this.

-Tim

---

### Post by rockstarrem on 2008-07-25
Hello,

Thanks for the reply. The only "problem" that I've ran into now really is the fact when I point my domain nameservers to the ones listed in the files they don't work. 1&1 says that the nameserver isn't verified or something. But those tutorials are way more then I need, all I want is the LAMP server that I can access elsewhere.

And yes, my ISP does block port 80.

---

### Post by windependence on 2008-07-25
First, you shouldn't need to run your own nameservers. Use your Domain registrar's nameservers and their control panel to point your domain at a redirection service such as no-ip or dyndns. Then set up your dynamic dns to point at your server, and you will have to install a client on your webserver to keep your IP updated with the dynamic service. If you set up a DNS server, you probably don't need it. I don't know why the tutorials even mention that. Use your ISP's DNS servers or any of the public ones out there. An internal DNS server won't help you here anyway.

BTW, how do you know your ISP blocks 80? What port is your webserver listening on? 

-Tim

---

### Post by basicxman on 2008-07-25
Isn't port 80 what almost every website uses?  I doubt your ISP blocks it.

Do you mean you followed the tutorial but you want to create an actual domain, like [www.example.com](www.example.com)

---

### Post by rockstarrem on 2008-07-25
> **windependence said:**
> First, you shouldn't need to run your own nameservers. Use your Domain registrar's nameservers and their control panel to point your domain at a redirection service such as no-ip or dyndns. Then set up your dynamic dns to point at your server, and you will have to install a client on your webserver to keep your IP updated with the dynamic service. If you set up a DNS server, you probably don't need it. I don't know why the tutorials even mention that. Use your ISP's DNS servers or any of the public ones out there. An internal DNS server won't help you here anyway.

BTW, how do you know your ISP blocks 80? What port is your webserver listening on? 

-Tim
I called my ISP and they block port 80. They don't want you running servers I guess, they allow it, they just don't like it. Kind of stupid.

Also, could you walk me through this redirection thing? I don't want my IP to show up in the address bar though, I want it to show [www.example.com/index.html](www.example.com/index.html) or whatever.


> **basicxman said:**
> Isn't port 80 what almost every website uses?  I doubt your ISP blocks it.

Do you mean you followed the tutorial but you want to create an actual domain, like [www.example.com](www.example.com)

No no, I have 17 domains that I use on my webhost (I have web space I use outside of my house, Dreamhost) and want to use one here.

---

