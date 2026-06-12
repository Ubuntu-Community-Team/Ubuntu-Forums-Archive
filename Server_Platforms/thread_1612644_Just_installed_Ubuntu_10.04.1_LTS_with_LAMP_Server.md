---
title: "Just installed Ubuntu 10.04.1 LTS with LAMP Server... Now what?"
date: 2010-11-03
forum: Server Platforms
---

### Post by mj44 on 2010-11-03
I'm making this server to learn how to use/run a web server. (I'm "Learning by Doing".)

I:
* Know _some/allot_ about websites, and how to make them.
* Know _some_ about Linux desktop's, and command's.
* Don't know anything about servers.



I read somewhere, that i can't see the web server on other networks, unless i have made some kind of configuration/permission in my router?

What about "PHPMyAdmin" and "FTP"? - How do i start using those on my server?

---

### Post by CharlesA on 2010-11-03
You'd need to install phpmyadmin.

```
sudo apt-get install phpmyadmin
```

As for FTP, I'd suggest using SFTP instead, as it's easier to configure (and it's a part of SSH)

---

### Post by abix_adam_pl on 2010-11-03
You can read some manuals, the good one is 

[http://www.howtoforge.com/perfect-server-debian-lenny-ispconfig2](http://www.howtoforge.com/perfect-server-debian-lenny-ispconfig2)
and
[http://howtoforge.net/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp](http://howtoforge.net/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp)

There are based on Debian and Ubuntu, and can shows to you the WAY, how to configure Very good serwer for Hosting - I hope you will learn a lot from these manuals.

Adam

---

### Post by mj44 on 2010-11-04
I have read those manuals, and the LAMP server is running perfectly.

What i like to know now is:
* How do i make the server visible to other people around the world?
* Is there anything else i need to use to start host my own website? (security and stuff.)

My server is behind a firewall, wich is in the router.

---

### Post by mj44 on 2010-11-04
> **CharlesA said:**
> As for FTP, I'd suggest using SFTP instead, as it's easier to configure (and it's a part of SSH)
Do i need to install anything, or is it some configurations on the server? (basicy - How?)
> **CharlesA said:**
> You'd need to install phpmyadmin.

```
sudo apt-get install phpmyadmin
```

Okay nice and easy.

---

### Post by CharlesA on 2010-11-04
> **mj44 said:**
> I have read those manuals, and the LAMP server is running perfectly.

What i like to know now is:
* How do i make the server visible to other people around the world?
* Is there anything else i need to use to start host my own website? (security and stuff.)

My server is behind a firewall, wich is in the router.

You'd need to forward that port on the router. Check here: [http://www.portforward.com](http://www.portforward.com)

> **mj44 said:**
> Do i need to install anything, or is it some configurations on the server? (basicy - How?)

Check here: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by mj44 on 2010-11-06
Okay, i got some stuff to look at.. 

I will write when i'm done..

---

### Post by listerdl on 2010-11-06
Seeing how you are learning as you are doing - how do you get a domain to point to your server or vica versa? (sorry dont want to hijack your thread)

---

### Post by abix_adam_pl on 2010-11-06
He just can try some DynamicDNS if his connection is ADSL with dynamic IP, or buy some domain and configure DNS on his own server if it's static, public IP.

Adam

---

### Post by cracker89 on 2010-11-13
is there a simple solution available? like wamp for winders?

---

