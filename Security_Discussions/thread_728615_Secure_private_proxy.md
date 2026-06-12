---
title: "Secure private proxy?"
date: 2008-03-19
forum: Security Discussions
---

### Post by thefatmoop on 2008-03-19
How would i have an encrypted tunnel / proxy? i have an ubuntu server that can redirect me. what would i use for a tunnel and how would i redirect firefox to the tunnel? 

my college finds it appropriate to baby sit the students, and it blocks nearly every damn programming site for "security" reasons. 

so far i've been using SSH for a remote terminal login and using lynx/ or vnc (i know very insecure)

---

### Post by pana.corbului on 2008-03-19
You could use putty to tunnel your traffic and use a socks 5 proxy for firefox. 

Watch this: [http://www.irongeek.com/i.php?page=videos/sshdynamicportforwarding](http://www.irongeek.com/i.php?page=videos/sshdynamicportforwarding)

---

### Post by picopir8 on 2008-03-21
If all you want to do is bypass their nanny software to access blocked sites, the easiest solution would be to run tor.  It encrypts and redirects packets so (1) people on your local network can not see what sites you are accessing and (2) the sites you are visiting are unable to determine your ip address.

[http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/](http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/)

For more info see:
[http://www.torproject.org/](http://www.torproject.org/)

---

### Post by hackertarget on 2008-03-21
If you can ssh to an external box, you can setup openvpn over ssh and run anything you want as if you were sitting on the external box. All traffic is encrypted between you and the external host.

Tor is also an option - however it is slow at times and you need to be careful about using unencrypted protocols as bad people and (bad) governments watch the traffic on the exit nodes.

---

### Post by update_manager on 2008-03-21
> **thefatmoop said:**
> How would i have an encrypted tunnel / proxy? i have an ubuntu server that can redirect me. what would i use for a tunnel and how would i redirect firefox to the tunnel? 


You need:

1. SSH Server
2. an HTTP/HTTPs proxy
3. and SSH client


it sounds like you already have #1 and #3, so for #2, you can use polipo, squid, tiny proxy, etc.

I'd stick to one of the smaller ones, probably polipo.

In the /etc/polipo/config file, set
proxyAddress = "127.0.0.1"
localDocumentRoot = ""

On the client side, use  this setting in Putty. Its easiest if you stick with the defaults (8123 127.0.0.1:8123, etc).

In your browser, set your proxy to 127.0.0.1 and port 8123 (or whichever port your proxy is running on).

Once you start putty, all connections to 127.0.0.1 8123 will get sent down your SSH tunnel and be routed via the proxy server.

---

### Post by kevdog on 2008-03-21
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=723025&highlight=ssh](http://ubuntuforums.org/showthread.php?t=723025&highlight=ssh)

---

### Post by bhavi on 2008-03-22
This could also provide some info:

[http://ubuntuforums.org/showthread.php?t=632346](http://ubuntuforums.org/showthread.php?t=632346)

[http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

---

