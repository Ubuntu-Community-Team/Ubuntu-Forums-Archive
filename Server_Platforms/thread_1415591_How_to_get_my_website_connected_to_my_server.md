---
title: "How to get my website connected to my server?"
date: 2010-02-25
forum: Server Platforms
---

### Post by waloshin on 2010-02-25
So I gave up on the mail server Idea as that was too much of a headache. 

So I was wondering as I have registered waloshin.com with godaddy.com how can I get an apache hosted website to appear on that domain from my server?

Do I have to configure BIND9 to do so? 

While going to [http://whatismyipaddress.com/](http://whatismyipaddress.com/) it does say that my ip address is static:  Assignment:	Static IP

---

### Post by booshire on 2010-02-25
> **waloshin said:**
> So I gave up on the mail server Idea as that was too much of a headache. 

So I was wondering as I have registered waloshin.com with godaddy.com how can I get an apache hosted website to appear on that domain from my server?

Do I have to configure BIND9 to do so? 

While going to [http://whatismyipaddress.com/](http://whatismyipaddress.com/) it does say that my ip address is static:  Assignment:	Static IP

So, first part, make sure your ISP does not block a mail server, mine did and it took me a while to figure out why it just "stopped working".

Second. Installing apache2 from the repo will automatically set up your computer to output a website on port 80. Make sure you port forward if using a router (port forwarding on router itself, point the port to your private IP). The default location is /var/www/. You can move it in /etc/apache2/sites-available/default or with virtualhost (check apache2 docs or just search it). On godaddy, you have to point the domain to an IP, so just point it to yours. If internal there are sites like "myipaddress.com" to see your external address. Create CNAMES in the DNS part under advances settings to point at subdomains.

Third, godaddy controls the DNS so pointing to BIND would be overkill, but I assume someone else can help with that...

---

### Post by stlsaint on 2010-02-25
all you have to do is install apache2, point godaddy to your public ip(the one you get from the whatsmyip website), port forward in router, port 80 to your private ipaddress of server(192.168.x.xxx)
on server put all website files in: /var/www
(you might need to take ownership of it:
```
chown -R www-data:www-data /var/www/
```

---

### Post by waloshin on 2010-02-25
> **stlsaint said:**
> all you have to do is install apache2, point godaddy to your public ip(the one you get from the whatsmyip website), port forward in router, port 80 to your private ipaddress of server(192.168.x.xxx)
on server put all website files in: /var/www
(you might need to take ownership of it:
```
chown -R www-data:www-data /var/www/
```

So lets pretend my ip address is 11.11.111.111

So I would go to godaddy.com and enter 11.11.111.111 as my A host? And as long as my servers ip is port forwarded to port 80 It should work?

---

### Post by stlsaint on 2010-02-25
> **waloshin said:**
> So lets pretend my ip address is 11.11.111.111

So I would go to godaddy.com and enter 11.11.111.111 as my A host? And as long as my servers ip is port forwarded to port 80 It should work?

are you saying 11.11.111.111 is your private or public ip address? 
you give godaddy your public...so just go to whatsmyip.com or something and get the public ip...that is what you give to godaddy.
and yes you will set your public ip as the @host or (@Ahost) in your total dns manager in godaddy panel!

---

### Post by Kiwi76 on 2010-02-25
So long as the server itself is setup correctly, yes.

---

### Post by lisati on 2010-02-25
> **waloshin said:**
> So I gave up on the mail server Idea as that was too much of a headache. 


For setting up a mail server, you need to check that your ISP is not blocking port 25. A static IP (which you already have) is probably a good idea too.

---

### Post by waloshin on 2010-02-25
> **Kiwi76 said:**
> So long as the server itself is setup correctly, yes.

so as long as i have an lamp install? is there anything else that needs to be configured?

---

### Post by Kiwi76 on 2010-02-25
Well, there may be alot of stuff that may or may not need to be done. There's security stuff and little details, but, for the most part, the general answer is, yes, with those major pieces correct, it will "work".

Here's a good guide. Even if you've already started, you can skim it to see what steps may be needed.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

---

### Post by waloshin on 2010-02-25
> **Kiwi76 said:**
> Well, there may be alot of stuff that may or may not need to be done. There's security stuff and little details, but, for the most part, the general answer is, yes, with those major pieces correct, it will "work".

Here's a good guide. Even if you've already started, you can skim it to see what steps may be needed.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

Thanks. anybody else have any suggestions to securing it?

---

### Post by nullvariable on 2010-02-25
> **waloshin said:**
> Thanks. anybody else have any suggestions to securing it?

[LIST]
[*]Disable every service you can. 
[*]Uninstall any packages that you're not using. (the fewer programs someone can attack the better)
[*]Disable SSH access or limit it to local IP addresses.
[/LIST]

You may also run into two issues not mentioned in the above posts,
1, your isp probably blocks traffic to port 80, most major ISPs do.
2, your IP address may be fairly static but it still might change. You might consider using NameCheap's Dynamic DNS (no idea if godaddy offers a similar service) or DynDNS to ensure that your domain is always pointing at the right IP address.

---

### Post by waloshin on 2010-02-25
> **nullvariable said:**
> [LIST]
[*]Disable every service you can. 
[*]Uninstall any packages that you're not using. (the fewer programs someone can attack the better)
[*]Disable SSH access or limit it to local IP addresses.
[/LIST]

You may also run into two issues not mentioned in the above posts,
1, your isp probably blocks traffic to port 80, most major ISPs do.
2, your IP address may be fairly static but it still might change. You might consider using NameCheap's Dynamic DNS (no idea if godaddy offers a similar service) or DynDNS to ensure that your domain is always pointing at the right IP address.

port 80 is open and my ip address has never changed over the years.

---

### Post by waloshin on 2010-02-25
> **Kiwi76 said:**
> Well, there may be alot of stuff that may or may not need to be done. There's security stuff and little details, but, for the most part, the general answer is, yes, with those major pieces correct, it will "work".

Here's a good guide. Even if you've already started, you can skim it to see what steps may be needed.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

Cant find: sudo nano /etc/apache2/apache2.conf
Scroll down (down arrow) to where it says "ServerTokens Full" and change it to read "ServerTokens Prod"

The servertokens prod

And can I run shorewall with fail2ban?

Shorewall error: invalid action (ACCEPT) in macro : /usr/shore/shorewall/macro.SSH (Line 11)

---

