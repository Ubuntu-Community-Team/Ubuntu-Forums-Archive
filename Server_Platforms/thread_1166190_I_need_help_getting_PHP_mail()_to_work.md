---
title: "I need help getting PHP mail() to work"
date: 2009-05-21
forum: Server Platforms
---

### Post by Ebon Lupus on 2009-05-21
I have a simple development environment set up on Ubuntu 8.04. I have Apache running PHP5 and MySQL and I merely want to work on scripts.

I used to have a simple program (I can't recall what it was) that somehow let me set a variable somewhere that pointed at my ISP's email server so that the mail() function in PHP would work normally, but after a recent re-installation (upgrading to Ubuntu 8.10 hosed my system.) I had to re-invent the wheel again... and I can't remember how I made the mail() function work.

Anyway, does anyone know how to get the mail() function to work, without all the BS of installing mail servers, etc.?

---

### Post by gpredrag on 2009-05-21
There is package called ssmtp. It's not real full-blown email server, nor daemon, nor it listens on any port, but is used to get the mail from server to configured mail hub (like your provider's mail server). It comes with sendmail command which can be used from php

---

### Post by OKKARE on 2009-05-21
I'm having the same problem with 9.04. I've done two installs of it and my websites can't seem to send mail from either. I've tried with Joomla and Magento.

Someone suggested doing "sudo apt-get install dovecot-postfix" but it didn't seem to make a difference.

I also opened port 25 on my router.

And someone suggested switching to GID from UID in php.ini (or was it vise versa) but that didn't work either.

I also installed sendmail. No joy.

Would appreciate a hand.

Edit: my ISP does not block any ports either.

---

### Post by Ebon Lupus on 2009-05-22
> **gpredrag said:**
> There is package called ssmtp. It's not real full-blown email server, nor daemon, nor it listens on any port, but is used to get the mail from server to configured mail hub (like your provider's mail server). It comes with sendmail command which can be used from php
Thanks a LOT for this. I'll let you know how it turns out. This program sounds really familiar, so it's likely the one. It sucks getting old and losing one's wits.

---

### Post by Ebon Lupus on 2009-05-22
This is exactly what I needed... it just sends email to a hub... and it works fine after a little tuning.

Here's what I did for any future seekers info... oh, and make sure sendmail (or any other MTA) is disabled.

```
sudo apt-get install ssmtp
```

Locate/Edit configuration file at /etc/ssmtp/ssmtp.conf
```
#root=postmaster // I left this commented out.
mailhub=mail.yourISP.net
rewriteDomain=YourDomain.org // I think this could be commented out too.
hostname=localhost
FromLineOverride=YES
```

Restart apache:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by Johnsie on 2009-05-22
Postfix does this. However most people need to set it to use their isp smtp because alot of mail providers like Google block emails that originate from home smtp servers (something to do with reverse dns apparently)

---

### Post by Kareeser on 2009-05-23
> **Johnsie said:**
> Postfix does this. However most people need to set it to use their isp smtp because alot of mail providers like Google block emails that originate from home smtp servers (something to do with reverse dns apparently)

That hasn't been my experience. My university mail-exchange server blocked emails coming from my server simply because my server's hostname was "server-3.lan", which isn't correct. Changing it to the domain worked perfectly and the univ forwards my emails. I haven't had problem with Google.

---

### Post by OKKARE on 2009-05-26
Thanks for the suggestions but I am still having problems. I've tried ssmtp and postfix.

Right now I'm not even getting any messgaes in mail.log.

I feel like I am missing something.

---

