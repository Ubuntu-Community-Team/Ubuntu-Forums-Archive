---
title: "Cannot access server content"
date: 2013-03-12
forum: Server Platforms
---

### Post by MadsRH on 2013-03-12
Hi

I just installed Ubuntu server 12.04.2 and found that I cannot access it via localhost or from Filezilla.

In Chrome, on my desktop, I can access the server using *192.168.1.51* and phpmyadmin with *192.168.1.51/phpmyadmin*, but if I write *[http://localhost](http://localhost)* or simply* localhost* I get an error message :confused:

In Filezilla with SFTP as protocol, I get this:

```
fzSftp started
Command:	open "madsrh@192.168.1.51" 8080
Error:	Network error: Connection refused
Error:	Could not connect
```

With FTP, I get:

```
Forbindelsesforsøg mislykkedes med "ECONNREFUSED - Connection refused by server".
```

Can anyone tell me what I'm missing?

---

### Post by solarghost on 2013-03-13
What happens when you try [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) ?

---

### Post by MadsRH on 2013-03-13
> **solarghost said:**
> What happens when you try [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) ?

Chrome says UPS! that the page is damaged.

---

### Post by ranger12 on 2013-03-13
If you are on your desktop, localhost would refer to your desktop not the server. You do not have name resolution setup to resolve a name to your server IP address. Do you have the firewall up and running on your server? Is port 8080 open for incoming traffic  on your server?

what are you running on your desktop? If it is ubuntu like mine, try using the hostname you gave your server + .local in the address bar and see what that does., other wards - *hostname*.local/phpmyadmin and see what happens.

---

### Post by MadsRH on 2013-03-13
> **ranger12 said:**
> If you are on your desktop, localhost would refer to your desktop not the server. You do not have name resolution setup to resolve a name to your server IP address. 

Aahh, that makes sense! There's no GUI on the server, so I assumed that localhost was for the desktop PC. So to access the server from my desktop, I will have to write the IP or set up some kind of DNS?

> **ranger12 said:**
>  Do you have the firewall up and running on your server? Is port 8080 open for incoming traffic  on your server? 

This is simply the default installation with a check in the checkbox for LAMP during the installation. I didn't install a firewall afterwards.

Do I need to setup FTP to be able to edit the **var/www/** files?

---

### Post by ranger12 on 2013-03-13
On your desktop pc, localhost does refer to your desktop but if you ping localhost at the server console than you would be pinging the loopback address of your server, unless you changed it which you shouldn't. You do not install the firewall in Ubuntu - it is built into the kernel. By default after you installed Ubuntu server the firewall is off. You can turn it on by typeing sudo ufw enable. UFW is just a commandline interface to netfilter. You can do *man ufw* at your server console and get more info about it.  You can also check the status of the firewall by the command *sudo ufw status* and it will tell you if it is running but it sounds like it is not running. Are you running Ubuntu Desktop on your desktop? What is the hostname that you gave your server? As far as editing the files in /var/www you can just use vim. If you setup ssh on your desktop you can just ssh over to the server and load those files in vim and edit them that way. That is what I do but you may not like using vim. You can setup DNS on your server; that is what I did to resolve it but avahi and multicast dns wuold allow you to do it as well.  I use the mDNS .local names to resolve things on my network but that is just me. That is what I meant by trying *hostname*.local/phpmyadmin. This is the way I have mine setup since last summer and I have never had any problems with but I also don't use php either but I do have vsftpd setup on mine. It all depends on what you are actually after.

---

### Post by MadsRH on 2013-03-14
Thanks I didn't know that about the firewall. I'm not going to tinker with the firewall before I know that everything work.

The desktop is currently not running Ubuntu - it has some kind of widespread proprietary OS :lolflag:

What I really want, is to use the server as a replacement for my current paid webhosting. That means I want to upload files via FTP and have a "real" URL (no just the IP) that I can access from outside my network.

These are the two items that I need to resolve! [SIZE=2]Sorry about the localhost confusion - not relevant.[/SIZE]

---

