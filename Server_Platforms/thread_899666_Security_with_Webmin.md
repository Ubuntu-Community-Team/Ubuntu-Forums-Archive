---
title: "Security with Webmin"
date: 2008-08-24
forum: Server Platforms
---

### Post by stringkarma on 2008-08-24
Hello all,
I have been learning to administer websites with ubuntu for just over 6 months now. I have done all of it with the command line and ssh so far, but as I get deeper and deeper I have been wishing for something to take some of the complexity out of it.

I have come across webmin and I like that it simplifies editing the config files and particularly should help me keep my syntax straight. Also it has sql control too so I can eliminate phpmyadmin.

I have two questions though:

1) how safe is webmin? Do I open myself up too much by using it?

2) can I include webmin in denyhosts to prevent the script attacks I know must be coming as soon as I have port 10000 open. (This is partly why I may prefer to use webmin vs phpmyadmin as I think denyhosts should see webmin.

2a) I know I can set BLOCK_SERVICES = ALL but could I just list sshd and webmin somehow?

Thanks guys

---

### Post by Dr Small on 2008-08-24
The first layer of security Webmin offers is SSL for encrypting the traffic. This means that anyone on your network who is packet sniffing won't be able to decrypt your login information or any settings your could be changing.

If you don't forward port 10000 to the web, you won't get any attempted logins to it anyhow.

---

### Post by stringkarma on 2008-08-25
> **Dr Small said:**
> The first layer of security Webmin offers is SSL for encrypting the traffic. This means that anyone on your network who is packet sniffing won't be able to decrypt your login information or any settings your could be changing.

If you don't forward port 10000 to the web, you won't get any attempted logins to it anyhow.

Unfortunately I believe that I have to forward 10000 as I am running a headless server.

For future reference, how would I prevent 10000 from being opened as Ubuntu opens the port when it is in use by default?

---

