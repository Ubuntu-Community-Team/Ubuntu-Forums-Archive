---
title: "VPS - 1GB RAM enough for Web Server?"
date: 2013-06-10
forum: Virtualisation
---

### Post by DextrousDave on 2013-06-10
Hi All


I want to buy/rent a very affordable VPS package at my ISP. Now it comes with the following:

[LIST]
[*]1GB RAM
[*]10GB Traffic
[*]10GB Disk Space
[*]1 vCPU
[*]Ubuntu or CentOS
[/LIST]



Now my requirements are:

[LIST]
[*]Surfing internet
[*]Hosting a small to medium website (less than 1GB traffic a month)
[*]DNS server
[*]LAMP - Apache, MySQL and PHP
[*]All have to run concurrently
[/LIST]



Now my question - Is 1GB of RAM sufficient to do all this? Remember this is a Virtual Environment running on either Ubuntu or CentOS.



Also, what do you recommend - Ubuntu or CentOS?

---

### Post by SingingBush on 2013-06-10
If you're not expecting your server to be hammered then that will more than enough.

---

### Post by DextrousDave on 2013-06-10
OK Cool...but no, it will really just be a small website and me playing on it. What is your def of hammering?

---

### Post by CharlesA on 2013-06-11
I don't think you'd need to run a DNS server on your VPS.

How much are you going to be paying for that VPS? You can find some really nice deals on hosting or VPSes at [https://www.webhostingtalk.com/](https://www.webhostingtalk.com/)

I've been running my website on a 256MB VPS with 15GB of disk space and 1TB of bandwidth for 29.99 a year at [http://serverdragon.com](http://serverdragon.com)

---

### Post by DextrousDave on 2013-06-12
@CharlesA - I want to run a DNS server to learn how it works - Educational purposes...What is your recommendation - CentOS or Ubuntu for my needs?

---

### Post by CharlesA on 2013-06-12
> **DextrousDave said:**
> @CharlesA - I want to run a DNS server to learn how it works - Educational purposes...What is your recommendation - CentOS or Ubuntu for my needs?

What do you want to learn about it? It would probably be more secure/easier to just mess with bind on a local virtual machine instead of a publicly accessible VPS. That way if you mess up the configuration, you don't cause the provider any extra load.

As far as which OS, I've used Debian for a few servers, but my advice is to use what you are comfortable with.

---

### Post by sandyd on 2013-06-12
> **DextrousDave said:**
> @CharlesA - I want to run a DNS server to learn how it works - Educational purposes...What is your recommendation - CentOS or Ubuntu for my needs?

Few reccomendations

[LIST=1]
[*]If your going to experiment with a DNS server, make it so that the public cant access it. Its possible to unset the default settings while experimenting, and create an open relay. I dont think you want to be part of a DNS open relay botnet like the one that hit spamhaus earlier this year. Your provider probably wont be pleased either...
[*]Use [SSH keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for authentication instead of a password. Passwords are weak and can be cracked :/
[*]For the OS, it really depends on what you want to use. Ubuntu and Debian-based distros are used, but its not the only thing people use. Fedora, RHEL, and CentOS are also common because they offer SeLinux. Unfortunately,this kind of defeats the purpose if you are using a OpenVZ VPS because OpenVZ doesn't support selinux. Its because it shares the kernel with the host. 

Generally, people go for releases with long term support, where they wont have to upgrade every 6 months, so go for something like Ubuntu 12.04 (LTS), Debian 7, CentOS, or Fedora if you dont want to be reinstalling your OS every once in a while to have the latest version.
[*][http://www.webhostingtalk.com/forumdisplay.php?f=104](http://www.webhostingtalk.com/forumdisplay.php?f=104) has some nice VPS deals and reviews. Check them first unless you want to walk into a minefield that many have walked into and escaped to tell their stories
[*]
[/LIST]
Otherwise, 1G ram is enough for that.
If your thinking of expanding or more traffic, use either Apache Worker MPM + mod_fcgid/mod_fcgi OR Apache Worker/Prefork/Event MPM + Varnish/Squid caching server OR Nginx+php5-fpm. Apache Prefork (the default mpm if your using mod_php for php files) scales horribly, and eats memory like a monster :(

---

### Post by SeijiSensei on 2013-06-12
> What is your recommendation - CentOS or Ubuntu for my needs? 

I use CentOS on servers and Ubuntu on desktops.  I run a couple of applications like [MailScanner](http://www.mailscanner.info) which are better packaged for RedHat-flavored machines.  I also have had issues with the default configurations of some software in Ubuntu like sendmail.  Having built servers since RedHat 4.0 was released in the mid-1990s I'm much more accustomed to the layout of RH-flavored machines like CentOS.

---

### Post by SeijiSensei on 2013-06-12
> What is your recommendation - CentOS or Ubuntu for my needs? 

I use CentOS on servers and Ubuntu on desktops.  I run a couple of applications like [MailScanner](http://www.mailscanner.info) which are better packaged for RedHat-flavored machines.  I also have had issues with the default configurations of some software in Ubuntu like sendmail.  Having built servers since RedHat 4.0 was released in the mid-1990s I'm much more accustomed to the layout of RH-flavored machines like CentOS.  

For simple web service you could run a machine with half that amount of memory and not have problems.  I have a Linode with 512K that accepts inbound mail with SMTP and handles a few websites with PHP and PostgreSQL databases.  I've still got about 128K of memory free, though it has cached about the same amount of code in swap as well.

---

### Post by Cheesemill on 2013-06-12
As well as being an excellent VPS provider Linode also has great documentation for setting up various services. It's worth bookmarking even if your VPS is with someone else.

[https://library.linode.com/](https://library.linode.com/)

---

### Post by CharlesA on 2013-06-12
> **SeijiSensei said:**
> For simple web service you could run a machine with half that amount of memory and not have problems.  I have a Linode with 512K that accepts inbound mail with SMTP and handles a few websites with PHP and PostgreSQL databases.  I've still got about 128K of memory free, though it has cached about the same amount of code in swap as well.

I've been running inbound and outbound mail + http/https but no database on my 256MB VPS. So far the memory usage has been fine. I dunno if it will work if/when i decide to throw a database server on it, though.

> **Cheesemill said:**
> As well as being an excellent VPS provider Linode also has great documentation for setting up various services. It's worth bookmarking even if your VPS is with someone else.

[https://library.linode.com/](https://library.linode.com/)

+1 to the Linode library.

---

