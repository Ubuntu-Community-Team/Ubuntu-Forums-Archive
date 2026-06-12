---
title: "What kind of address is this !"
date: 2009-04-25
forum: Security
---

### Post by kibster on 2009-04-25
Today I noticed that my firewall (firestarter) got a hit (one of many that scan my ports sniffing around) And the address it showed was

ns5.alisp.co.uk  on port 25  TCIP  SMTP

The address does not resolve.. What kind of address is it. 

Is it some sort of mask ?

Russ

---

### Post by lovinglinux on 2009-04-25
First of all, it was an outgoing or incoming connection?

SMTP means it is a mail server. But wouldn't trust Firestarter, since it will tell you it's an SMTP connection whenever the port 25 is used. For example if you use a p2p client and it tries to connect to a peer accepting connections on port 25, then Firestarter will tell you is a SMTP connection, while it is in fact a p2p connection.

Addresses starting with ns# are usually provided by web site hosts to configure the DNS of the site.

Check this [http://en.wikipedia.org/wiki/Name_server](http://en.wikipedia.org/wiki/Name_server)

BTW, you shouldn't use Firestarter for monitoring connections. It can be used safely for configuring the firewall and then should be closed. Firestarter is not actually the firewall, it is just a firewall manager that allows you to create rules for iptables (the real firewall) without knowing the commands. Leaving it open it's not necessary, since iptables runs in the background, and could introduce security risks due to the root requirement to run the GUI.

---

### Post by kibster on 2009-04-25
Sounds like good advice.... What FIREWALL should I use then . Or how should I configure it too.

It was incoming.

Thanks for your help...


Russ

---

### Post by lisati on 2009-04-25
> **kibster said:**
> Sounds like good advice.... What FIREWALL should I use then . Or how should I configure it too.

It was incoming.

Thanks for your help...


Russ
Ubuntu comes with its own firewall, iptables. Tinkering with the settings can be a bit fiddly, which is why programs like firestarter exist.

I've never had occasion to change the default settings (my machines sit behind two routers, both of which have their own firewall-like features), so I shall bow to the recommendations of others.

---

### Post by lovinglinux on 2009-04-25
Since it was incoming, then the port you specified was the source or the destination?

If it was the source, then it's probably the mail server replying to a connection request. Try sending an e-mail and check the logs to see what happens and if you get another blocked connection.

If it was the destination port, then is someone trying to connect to a mail server on your machine.

The recommended firewall manager is ufw. I guess it comes installed by default, but you can add the GUI using this command:

```
sudo apt-get install gufw
```

Don't use two firewall mangers at the same time, because you will probably mess with the iptables rules.

Info about  [gufw](http://gufw.tuxfamily.org/index.html) and [ufw](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by kibster on 2009-04-25
Ok I'll get it that one then.. I'm doing the update 9.04 now...Ill wait and maybe tomorrow i'll get it..

Russ

---

### Post by kibster on 2009-04-26
I went and got the UFW  and am using it now..

Russ

---

