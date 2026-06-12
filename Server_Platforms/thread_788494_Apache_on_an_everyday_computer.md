---
title: "Apache on an everyday computer?"
date: 2008-05-09
forum: Server Platforms
---

### Post by patrickaupperle on 2008-05-09
I want a server (web server), but can not afford a new computer. Is it ok to run apache on the same computer I use for everyday computing? Is it a security risk? Does it impact usability at all?

---

### Post by Joeb454 on 2008-05-09
I don't see why not, though you would be more open to attacks (because obviously apache would open port 80 on your PC to incoming connections.

And I'm not sure about usability, I have it on a separate PC. Do you not have any spare PC's lying around?

---

### Post by patrickaupperle on 2008-05-09
> **Joeb454 said:**
> I don't see why not, though you would be more open to attacks (because obviously apache would open port 80 on your PC to incoming connections.

And I'm not sure about usability, I have it on a separate PC. Do you not have any spare PC's lying around?

No spare PCs. If it can be used on a normal computer w/o problems, why do people always use a separate computer?

---

### Post by juan@forum on 2008-05-09
you can run apache in the machine you want...

if you need a stable and a production web server you should run it on a different machine

---

### Post by patrickaupperle on 2008-05-09
> **juan@forum said:**
> you can run apache in the machine you want...

if you need a stable and a production web server you should run it on a different machine

So, is apache easily removable? Just apt-get remove apache?

---

### Post by cdtech on 2008-05-10
> **patrickaupperle said:**
> No spare PCs. If it can be used on a normal computer w/o problems, why do people always use a separate computer?

FIREWALL! FIREWALL! FIREWALL!

It's more secure to run a gateway, firewall on a separate computer (server). You have more protection against intruders breaching your local network. You can run a web server from any computer.

To completely remove a package, the correct way would be:
apt-get --purge remove <package>

---

### Post by FakeOutdoorsman on 2008-05-10
I use my desktop with Apache as a development server.  Apache has been configured to ignore any incoming connections other than the host computer.  More info: [Apache, mySQL, PHP]("https://wiki.ubuntu.com/ApacheMySQLPHP") at Ubuntu Wiki.

If this is going to be a production server which will be accessible to anyone to the internet then you should use a dedicated machine and also read the [Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/").

---

### Post by hyper_ch on 2008-05-10
default configuration of apache is pretty secure... when you start messing around with it and alter configuration you risk higher exposure... but I tend to think you can put it on a everyday computer.

---

### Post by Dr Small on 2008-05-10
I ran apache on my desktop computer for the longest time. I saw no security threats with it. And if you are behind a router / firewall, then there is no need for a second firewall on your system, as it really complicates matters.

Xampp is my choice though, as it is pre-configured, easy to use, easy to remove, and comes with all the essentials. But, you would need to run the security script to lock down /xampp, MySQL, PhpMyAdmin and FTP.

Dr Small

---

### Post by patrickaupperle on 2008-05-11
What about setting up OpenSSh? Is it ok to run openssh on the same computer I use for everyday computing? Is it a security risk? Does it impact usability at all?

---

### Post by windependence on 2008-05-11
Just make sure you a) don't give the user a "mormal" name, in other words don't make it a name or a word. b) make sure you use good password security, no dictionary words and put numbers, mix case and even use symbols in it and c) kill root access from the outside. When your root user is enabled access from the outside, you have already given hackers half of the combination to get in.

On my webserver (production) I can see attempts every day to log into the server. First, they try to guess your user name with a file full of regular names, and if they get that they will start trying passowrds until they get it IF your UID and pass are not secure. Also, only open the ports you need like 80 and 443, and run a hardware firewall. That way, if they do try a DDOS attack, they will be using CPU on your firewall and not your machine. If you only have a software firewall, they could still take your box down by saturating your machine's CPU when it's trying to deal with all the incoming packets.

-Tim

---

### Post by windependence on 2008-05-11
> **patrickaupperle said:**
> What about setting up OpenSSh? Is it ok to run openssh on the same computer I use for everyday computing? Is it a security risk? Does it impact usability at all?

OpenSSH is fine and in fact recommended for secure connections to your machine. It's so lite it won't affect performance at all.

-Tim

---

### Post by Dr Small on 2008-05-11
No. Just take the usual security precautions. Setup SSH keys, disable password authentication, disable root login, etc.
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Dr Small

---

### Post by Thirtysixway on 2008-05-11
I used to run Apache/php/mysql on my desktop machine.  It wasn't bad, but when I was doing normal tasks like browing to youtube, it lagged everyone else trying to visit my sites.

I wouldn't call it a security risk, but your visitors will recieve more lag.

---

