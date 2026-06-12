---
title: "iptables without gui"
date: 2006-10-16
forum: Server Platforms
---

### Post by aliyanage on 2006-10-16
Hi all,

I've seen quite a few posts on how to install firestarter to get a gui to configure the iptables. I would rather be interested in getting to know how to configuring and playing around with it over the terminal without a gui. Could someone tell me where I can find the iptables file or config file?

regards
aliyanage

---

### Post by rklauco on 2006-10-16
I used this howto:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Using step by step tests I get a working firewall.
And, I advice to get a knockd package and read documentation too.

---

### Post by OmegaBLK on 2006-10-16
You could also use firehol if you don't want to deal with IPTable syntax.  Firehol's syntax is pretty simple.  [http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)

---

### Post by Ride Jib on 2006-10-16
[http://www.netfilter.org/](http://www.netfilter.org/)

---

### Post by aliyanage on 2006-10-17
thank you very much for the hints and help, appreciate it!!!  :-D

---

### Post by autosuggested on 2006-10-17
Hi aliyanage,

If you're lazy (like me), you can generate a firewall at [http://easyfwgen.morizot.net/gen/index.php](http://easyfwgen.morizot.net/gen/index.php)

Once you have the iptables commands on file, you can start messing with them. The learning curve is a bit less steep than going about building a firewall from scratch.

// autosuggested

---

