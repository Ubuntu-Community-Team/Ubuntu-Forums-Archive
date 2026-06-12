---
title: "Help needed with setting up a home web server please"
date: 2008-04-06
forum: Server Platforms
---

### Post by ianb72 on 2008-04-06
Hi,

I am trying to set up a web server to host my own web site(s) from home and I am confused about a few things.

Do I have to set up a static IP address or leave it set to DCHP and because my Broadband ISP is an Dynamic DNS how do I go about setting that up?

I have installed PHPMyAdmin but I am not sure how to start it, can someone tell me how as when I type:
[HTML]http://localhost [/HTML]

I just get 
apache2-default/
phpmyadmin/

Then when I click on myphpadmin it asks if I want to Save the file etc.


When trying to find out if PHP or MySQL are running by typing
[HTML]ps -ax[/HTML]
Neither PHP nor MySQL are running so how would I start them and how do I change the password in MySQL??

Is there a newbies guide to getting a web server up and running, I have looked through [The Pefect Ubuntu set up]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")
But yet again it is talking about a static IP address and I thought with having a Dynamic DNS I needed to keeps DCHP.

Please can anyone help me out??

Many Thanks
Ian

---

### Post by pseudo-random on 2008-04-06
Search for LAMP setup. There's loads of good tuts.
That'll run you through installing Apache,PHP,MySQL.

Please be careful with PHPmyadmin if you don't know what you're doing!
It's dangerous if configured badly or just left in the dafult configuration.
Leave your IP as Dynamic/DHCP but you'll need to get a dyndns.com account or similair and install a no-ip type update client which will make sure that mypc.home.example.com will always point to your IP.

---

### Post by tgalati4 on 2008-04-06
Servers are easier to maintain when you have a fixed IP address--both internal and external.  Although not required internally, you need an accurate /etc/hosts file with a fixed IP so that services that translate your hostname will have a clue.

Fixed external IP's are generally more expensive from internet providers.  They assume you are a business and will charge more.  For a personal server you can set up a fixed web name using dyndns.org.  You can set up ddclient or some other service to update your dynamic IP to a static web name.  This needs to be done about once a month as that is the frequency that dyndns.org pesters you for an update.  dyndys.org has free/pester services and paid services.

So if you purchase a fixed exernal IP address from an internet provider and purchase a web name then you shouldn't need to perform any administration to keep your address current--except to renew your web name every few years.

xampp stack is another simpler server stack to install and maintain:

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by doogy2004 on 2008-04-06
do this
```
sudo tasksel
```
select LAMP server
select OK

you have just installed Apache, MySQL, and PHP

---

### Post by ianb72 on 2008-04-07
When I installed the server from the CD I install a LAMP server and all I have installed since is MyPHPAdmin.

I thought it installed everything I needed??

How do I get PHP, MySQL and MyPHPAdmin running at startup??

---

### Post by ianb72 on 2008-04-07
> **doogy2004 said:**
> do this
```
sudo tasksel
```
select LAMP server
select OK

you have just installed Apache, MySQL, and PHP

When I typed in [HTML]sudo tasksel[/HTML]

I got the following error message
[HTML]sudo: tasksel: command not found[/HTML]

---

### Post by BucKao on 2008-04-08
If you already have an existing domain name, try Zoneedit, [www.zonedit.com](www.zonedit.com).   I'm trying to set up a personal web server like you and I stumbled across them yesterday.  Their free dynamic DNS service will work with an existing domain name. :)  With DyDNS or no-ip you have to use their pay service if you want to use your own domain name.  :(

---

