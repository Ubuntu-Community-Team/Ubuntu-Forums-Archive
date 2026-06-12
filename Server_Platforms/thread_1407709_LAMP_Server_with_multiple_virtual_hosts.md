---
title: "LAMP Server with multiple virtual hosts"
date: 2010-02-15
forum: Server Platforms
---

### Post by Jonakoudijs on 2010-02-15
Dear UbuntuForums-members,

This is the first time in my life that I actually post something like this :p, but I am really desperate to find the answer.. I looked everywhere and I just can't find the answer.. So I really hope someone can help me with my problem.

_The situation is as follows:_
I have a Xubuntu Web Server (I choose Xubuntu because of the lightweight graphic interface that may come in handy because eventually someone else maby has to manage it). I want to host a couple of websites, they will all be simple html-php websites. The problem I am facing is that I just can't get the multiple virtual hosts setup to work. I've build LAMP servers in the past, but all for one website.

I eventually tried Webmin and used the Apache interface to add the virtual hosts but still no succes. I tried to do it with different ports and with different server names.. still no succes. I don´t really know what kind of information to give to you all, but if you need anything I´ll give anything I can as soon as possible.

I really hope someone can help me.

Thanks in advance!

---

### Post by cdenley on 2010-02-15
I never used webmin to configure apache, so I can't help you with that. The correct way to create a new vhost in ubuntu is to:

1. Create a copy of your default vhost to build your new one
```

cd /etc/apache2/sites-available
sudo cp default newvhost

```

2. Edit the new vhost file
```

sudo nano newvhost

```

3. Add a "ServerName" value within the "VirtualHost" tag. If there are additional hostnames for this vhost, use "ServerAlias" values. Change other paths/variables as needed.

4. If using ubuntu 8.04, I believe there will be a "NameVirtualHost" line at the top you need to remove.

5. Enable the new vhost.
```

sudo a2ensite newvhost

```

6. Reload apache configuration
```

sudo /etc/init.d/apache2 reload

```

---

### Post by Jonakoudijs on 2010-02-15
Thank you very much for the quick reply! I am going to try that at once! :D

---

### Post by Jonakoudijs on 2010-02-15
Ok.. now I'm resetting my test machine (my last try, was a try with brute forse.. :p)
So if a want to go to my new virtual host I have to typ in the name of the name I gave that virtual host right in my webbrowser, right?

---

### Post by cdenley on 2010-02-15
> **Jonakoudijs said:**
> Ok.. now I'm resetting my test machine (my last try, was a try with brute forse.. :p)
So if a want to go to my new virtual host I have to typ in the name of the name I gave that virtual host right in my webbrowser, right?

Yes (assuming the hostname is both configured in apache and resolves to your server's IP). When in your browser, you browse to [http://mydomain.com/](http://mydomain.com/), your browser sends an an http-header which indicates the "Host" you are requesting (mydomain.com). This is what apache uses to determine which vhost to serve. It serves the first vhost it finds with a matching ServerName or ServerAlias, starting with the default.

---

### Post by Jonakoudijs on 2010-02-15
> **cdenley said:**
> Yes (assuming the hostname is both configured in apache and resolves to your server's IP). When in your browser, you browse to [http://mydomain.com/](http://mydomain.com/), your browser sends an an http-header which indicates the "Host" you are requesting (mydomain.com). This is what apache uses to determine which vhost to serve. It serves the first vhost it finds with a matching ServerName or ServerAlias, starting with the default.
That was the missing puzzle-piece! I was not really sure about how Apache would decide which Vhost to get then! Thank you =D! And does this also work in the same LAN? I know I can reach my website with the domain name from inside the LAN (I do this every day with my own website)?

Thanks for the quick reply! :D

---

### Post by cdenley on 2010-02-15
It depends on your router. If your domain name resolves to your router's WAN address, then some router's will not port forward LAN connection attempts to that IP back to the server in your LAN. If that is the case, you can either configure an internal DNS server which resolves your domains to the appropriate LAN address, configure your domains in each client's hosts file, or use some other kind of name resolution with non-DNS hostnames (avahi, netbios, etc).

---

### Post by Jonakoudijs on 2010-02-15
> **cdenley said:**
> It depends on your router. If your domain name resolves to your router's WAN address, then some router's will not port forward LAN connection attempts to that IP back to the server in your LAN. If that is the case, you can either configure an internal DNS server which resolves your domains to the appropriate LAN address, configure your domains in each client's hosts file, or use some other kind of name resolution with non-DNS hostnames (avahi, netbios, etc).
Prais the lord, and prais Jezus! It works =D!!!

Well I did exactly what you said now it works :D (I jelled a few curse words, but later I realized that I didn't edited the index directory :p).

Thank you very much for you help!! I'll try to help other people with my bit of Linux knowledge I have in me :)

Thanks again ;)

---

