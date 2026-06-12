---
title: "slow to access website through domain name while on same connection as server"
date: 2007-07-03
forum: Server Platforms
---

### Post by robk86 on 2007-07-03
When I access my server using the fully qualified domain name (ex. site.dyndns.org); It is very slow to load web pages, but more specifically php apps like zencart, wordpress.  If I use the server IP address when using these apps, then I have to change the settings for the server location in the admin panel and change it back if I want it usable outside my network.  Is there any way to speed this up with the FQDN?

---

### Post by nitro_n2o on 2007-07-03
It's slow because it is performing a DNS name resolution/translation i forgot the accurate name.. anyways check you dns settings

---

### Post by nitro_n2o on 2007-07-03
Try out this it might help [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/) 
It helped in my case

---

### Post by robk86 on 2007-07-03
OK I am in the middle of the tutorial you posted. It says:

```
Now open the file /etc/resolv.conf in your text editor. It probably looks like:

search yourisp.com
nameserver 217.54.170.023
nameserver 217.54.170.024
nameserver 217.54.170.026
```

The one on my server looks like this:

```
nameserver 192.168.1.1
```

^ That is the IP address of my router.  What should I put in the file?

---

### Post by robk86 on 2007-07-03
In the resolv.conf file I just put in the following:

```

search sbcglobal.net
nameserver 127.0.0.1
nameserver 68.94.156.1
nameserver 68.94.157.1

```

I ran the command "dig google.com".  The first time it said 16ms then the next two times it was 2ms.  However loading the shopping cart is still very slow.  I went to a few web pages first.  Then I went to the cart homepage followed by the admin.  It all seems slower than 56k dialup.

I have DSL by the way and there is a section in the tutorial for DSL users only.  Maybe I will try that.

***Just to make things clear; I am having this problem when using my desktop compute  to access my website which is located on a server connected to the same router as my desktop.  My server is wired to a wireless to ethernet converter which is connected wirelessly to my Netgear wifi router.  The desktop is connected to the router by cable, and the wan port of the router is connected to my SpeedStream 5100 DSL modem.  I would greatly appreciate any more suggestions.

---

