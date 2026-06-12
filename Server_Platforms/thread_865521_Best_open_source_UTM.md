---
title: "Best open source UTM"
date: 2008-07-20
forum: Server Platforms
---

### Post by larynx on 2008-07-20
I'm looking to setup a small business server (less than 10 users) and I want it to be based on Ubuntu server 8.04.

I need the server to be a firewall, attack blocker, LAMP server (for internal web development), and fileserver (SAMBA).

I don't having any problem running the LAMP server or fileserver but regarding the UTM part, I'm currently looking into Untangle Gateway Lite to run on Ubuntu, but I was wondering if there's a better option for a UTM that can run on Ubuntu.

Any suggestions?

---

### Post by gtdaqua on 2008-07-21
Untangle is better and comprehensive. The latest version now supports Qos too. You will find yourself ending up here eventually.

Look at [Vyatta]("http://www.vyatta.com/") too.

---

### Post by cariboo on 2008-07-21
I don't know if I read the documentation right, but it doesn't look like there is any remote administration for this product, which means you're going to need a monitor and keyboard hooked up to your server, which means you're are going to have to keep your server out in the open where anybody can get to it. There are plenty of options available to do what you need. My favourite as far as a fire wall is concerned is arno's iptables firewall. Ufw is installed by default on Hardy so there is another option. Here is a howto for ufw:

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

Once you have the firewall setup, the only thing you have to worry about is your users.

Jim

---

### Post by gtdaqua on 2008-07-21
> **cariboo907 said:**
> I don't know if I read the documentation right, but it doesn't look like there is any remote administration for this product, which means you're ................

Jim

There is a secure web interface to administer Untangle.

---

### Post by larynx on 2008-07-22
I installed Untangle Gateway Lite 5.3 on Ubuntu Server 8.04 and going with that.

Thanks.

---

