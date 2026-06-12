---
title: "Home server, whats next?"
date: 2008-11-23
forum: Server Platforms
---

### Post by santaslittlehelper on 2008-11-23
Yesterday I set up ubuntu as an home server on an old computer following this guide -
[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)
All I what to do is host a testing website, nothing serious, just fun. 
It all works fine, I can both access the website form the outside world and ssh into the server.

So here are my question.

1.Should I do anything else to harden the box?
2.How would I go about securing ssh beside having a good password?
3.Can I use port 81 instead of port 80 if I what to?
4.Where would you suggest I get a cheap domain name? And how would I configure the server to use the domain name?
5.Can I use myphpadmin remotely?

Know it's a lot to ask, hope it all makes sense if not please ask. :)

---

### Post by Thirtysixway on 2008-11-23
To harden the box you could install something like fail2ban to block IPs trying to break into your server using bruiteforcers.

Change the default port of ssh and anything else open to the world like ftp or webmin.  Also you could setup public/private keys so only those computers with the keys can access ssh.  You could even go as far as blocking all access to that port with iptables and only allowing a few trusted IPs through.

To change the port that apache listens on, simply edit /etc/apache2/ports.conf and restart apache using /etc/init.d/apache2 restart

You can get a cheap domain from name.com, or even a free one from somewhere like [www.co.cc](www.co.cc).  If you don't want to go through the trouble of setting up dns/static IPs and whatnot you can get a dynamic dns name ([www.no-ip.com](www.no-ip.com)) and point it to your IP address.

PHPmyadmin should be accessable remotely as long as you have web acces to the server.

---

### Post by ITAndrew on 2008-11-23
A great spot to look which is generally overlooked with plenty of information is located here:[https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)
This is probably the most up to date information of the server config for Ubuntu.

Most server packages have an enhanced security option, mostly involving SSL, also great to look into.

> 2.How would I go about securing ssh beside having a good password?

You may want to look into stronger cryto keys than the standard 2046 bits, but this is usally sufficent. Again, the docs have a great explanation of enhanced security.

(anyone remember [http://www.neowin.net/news/main/08/05/13/debian-and-ubuntu-flaw-leaves-private-sslssh-keys-guessable](http://www.neowin.net/news/main/08/05/13/debian-and-ubuntu-flaw-leaves-private-sslssh-keys-guessable) That was fun!)

> 3.Can I use port 81 instead of port 80 if I what to?

Most browsers like Firefox, and Galeaon I know for sure throw errors for nonstandard ports. A good alternate would be 8080 if you do not want to use the standard 80.

> 4.Where would you suggest I get a cheap domain name? And how would I configure the server to use the domain name?

Godaddy.com ~ Home of the 9.99 domain names (10.60 something after tax)
DynDNS.org ~ Most home users have a dynamic IP address this uses their nameservers to point to your dynamic IP address via an updater that can be run on your PC or router. This is free if you use their yourhost.dyndns.org subdomain addresses, otherwise the cost is 36 for your own FQDN.

> 5.Can I use myphpadmin remotely?

Absolutly. You would need to modify your apache config to specify the myphpadmin alias. I.e.. Alias /phpmyadmin "/usr/local/www/phpMyAdmin/"

Look into further docs for a wider explanation.

I have this setup and I love it, If you want to learn more of the sysadmin side of ubuntu this is the way I recommend. Also, add a mail server to your list of projects. There are also pleanty of books that are *freely* available with more explanations as well, if you cath my drift. Knowlege should be free!

---

### Post by Lars Noodén on 2008-11-23
You might look at using SSH keys.  The key has a password, you have the key.  Both the password and key are needed to log in.  That might be too much though.  

Be sure that remote root login is disabled, if it is not already.

You probably should look into limiting the rate at which SSH connections are allowed, to make bruteforce attacks harder:

[INDENT]]http://iptables-tutorial.frozentux.net/iptables-tutorial.html#LIMITMATCH[/INDENT

---

### Post by santaslittlehelper on 2008-11-23
Thank you all.

That's a lot of information I will be looking into as much as possible. 
So fare I have changed the default port for ssh, it is the only port that is forwarded with port 80 in my router.

I registered a free domain name at [www.co.cc](www.co.cc) but I am somewhat stock now.

I do have a static IP. 
I followed the these guides.
[https://help.ubuntu.com/8.10/serverguide/C/dns-installation.html](https://help.ubuntu.com/8.10/serverguide/C/dns-installation.html)
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

The server is still up and running and I can access the website though my IP.
 However I can't seem to point the server to domainName.co.cc?
When co.co asks for my name server I am unsure what to feet it?

Am I even on the right track here?

---

### Post by ITAndrew on 2008-11-23
You are again looking at a service like dyndns. I believe the exact service would be custom DNS.

This allows you to use DynDNS's nameservers for resolution to the Domain name.

---

### Post by santaslittlehelper on 2008-11-24
It's working now with DynDNS. Thank you all :)

---

### Post by tsucol11 on 2008-11-25
Thanks for the info. Just what I needed to start off.

Brian

---

