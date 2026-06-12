---
title: "How can I prevent Desktop Users from accessing any online website?"
date: 2010-12-17
forum: Security
---

### Post by emurad on 2010-12-17
Hello,

How can I prevent Desktop Users from accessing any online website? I tried 127.0.0.1 * in /etc/hosts but it didn't do the trick.

Please note that I need to keep [http://localhost](http://localhost) fully functional.

Thanks.

---

### Post by gn0m3boy on 2010-12-17
If I understand correctly, you don't want anyone accessing the internet, just the intranet or local host only?
Try this:
Set up Firestarter.  This is a great tool that is basically a frontend for Ubuntu's firewall.  Real easy to configure and has white list / black list so you can add or remove places in the future.  You can set it up to block internet access and this will not disable the *[http://localhost*](http://localhost*) function.  :D

---

### Post by bodhi.zazen on 2010-12-18
> **emurad said:**
> Hello,

How can I prevent Desktop Users from accessing any online website? I tried 127.0.0.1 * in /etc/hosts but it didn't do the trick.

Please note that I need to keep [http://localhost](http://localhost) fully functional.

Thanks.

1. Unplug the network card.

2. Disable the wireless card.

3. As root, disable network cards , eth0 / wlan0 etc.

4. Use your firewall. You can configure it with ufw or gufw if you want a graphical interface.

ufw:
```

sudo ufw enable
sudo ufw default deny
sudo ufw allow out to 127.0.0.0/8
sudo ufw deny out to any
```

iptables:

```
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -j DROP
sudo iptalbles -A OUTPUT -o lo -j ACCEPT
sudo iptables -A OUTPUT -j DROP
```

5. Configure your router.

6. Build a router and deny access.

7. Install a (transparent) proxy server, such as squid, and configure access to the internet.

[http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

---

### Post by HermanAB on 2010-12-19
Howdy,

Make an iptables rule to drop port 80 or block port 80 in your router.

---

### Post by kevdog on 2010-12-19
> **HermanAB said:**
> Howdy,

Make an iptables rule to drop port 80 or block port 80 in your router.

Hopefully they aren't planning on using google ssl?!! :p

---

### Post by CharlesA on 2010-12-19
> **kevdog said:**
> Hopefully they aren't planning on using google ssl?!! :p

In that case, block port 80 and port 443.

---

### Post by bodhi.zazen on 2010-12-19
Well, you would need to probably add a few additional ports for stragglers (8080, 8118, 8123, and 8443). That would cover most variations on the theme.

---

### Post by HermanAB on 2010-12-19
No, no, you should leave at least one backdoor for knowledgeable geeks on the LAN...

---

