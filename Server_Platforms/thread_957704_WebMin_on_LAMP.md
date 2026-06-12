---
title: "WebMin on LAMP"
date: 2008-10-24
forum: Server Platforms
---

### Post by craigp on 2008-10-24
What do you guys think of WebMin for a LAMP server? Lots of virtual hosting (a few hundred sites) and thought it might be good for controlling user accounts and other misc maintenance.. what do you guys think of it? Security is a neccesity.. Any alternatives you guys recommend?

Cheers

---

### Post by volkswagner on 2008-10-24
I like webmin.  I think you may want to look into ISPconfig if you want to act like a reseller for all the users.  They will get there own control panel.  ISPconfig seemed like more than I needed as a single admin for one user and a few sites.

[http://www.ispconfig.org/]("http://www.ispconfig.org/")

---

### Post by jamesrfla on 2008-10-24
I use webmin and it works great. I can manage almost everything on that server and the server physically.

---

### Post by Coreigh on 2008-10-24
The only bad thing I can say is that I occasionally have a problem with some of the more advanced operations, like installing new packages. I prefer to to the heavier maintenance with a terminal or at least ssh. But I do have the luxury of having the server on site so I can kick it if I have to.

---

### Post by linuxpenguin on 2008-10-24
I like Webmin.

The only thing I don't like is that it uses its own server.  The amount of extra resources that takes is negligible, but still - I'd rather not leave it running.  I use it so infrequently I still feel it's not worth it.

I do think it's a nice tool though.  It can come in handy on those very rare occasions when you can't use SSH for some reason, and sometimes I like to use it just so I can use the GUI rather than typing.

I can't speak for the security aspect though - the only servers I've ever managed are ones I set up for my own use, so security is/was not a huge concern (at least not to the degree that it would be if I were managing a server as part of a business, like it sounds like you're doing).  My guess is that Webmin is fairly secure, but I don't really know.

---

### Post by lykwydchykyn on 2008-10-25
Webmin can be configured for SSL encryption and limited access (only certain IP's or networks, e.g.).  I would recommend doing both if this is going to be accessible from the Internet.  

Another secure way to use webmin is to have it listen only on 127.0.0.1, then install a browser on the server and foward X11 over ssh to run the browser and bring up webmin from the server itself.  This way you only need ssh open, which you can secure using PK encryption.

---

### Post by rubenverweij on 2008-10-25
I read your replies to craigp, and I might want to use it myself, too. But I don't really like it because it has too much features, I only need: vsftpd management, mail server management.
Is there a similar web control panel which has this features but isn't so complicated as webmin? I need something simple my dad can manage :).
Thanks,
Ruben

---

### Post by lykwydchykyn on 2008-10-25
Webmin allows you to customize login accounts so that they see only selected modules, and you can set a default module for a user to see when they log in.  It also automatically disables services modules for services that are not installed.  I'm not aware of another web-based management tool for vsftpd.

---

### Post by Brazen on 2008-10-26
> **lykwydchykyn said:**
> Webmin can be configured for SSL encryption and limited access (only certain IP's or networks, e.g.).  I would recommend doing both if this is going to be accessible from the Internet.  

Another secure way to use webmin is to have it listen only on 127.0.0.1, then install a browser on the server and foward X11 over ssh to run the browser and bring up webmin from the server itself.  This way you only need ssh open, which you can secure using PK encryption.

Wouldn't it make more sense to just forward port 80 through ssh and use the browser on your workstation?

Yes.  Yes it would.

edit: oops, yeah I mean port 10000 or whatever custom port you change it to for smoke-and-mirrors security.

---

### Post by lykwydchykyn on 2008-10-26
Maybe, except webmin doesn't run on port 80.  But otherwise, definitely maybe.

---

