---
title: "SSH Refused Connection (I've Tried Everything!)"
date: 2008-10-10
forum: Server Platforms
---

### Post by Lul2x on 2008-10-10
Hey All,

I've installed ssh on my server and can connect locally to it from other computers on my network. However, I cannot connect from anywhere else!

I have:
-installed ssh
-port forwarded my router to port 22 on my server's static IP
-am using the default config settings
    -have tried ListenAddress * and AllowUsers *
-ran iptables -L  and nothing seemed to be running
-ran ufw status and ufw is not running

It doesn't look like anything is blocking it and ssh was working on my Gentoo setup (which I just switched to ubuntu) just last week with the same port and IP.

Any help is welcomed. Thank you!

---

### Post by lykwydchykyn on 2008-10-10
If it works locally but not remotely, I see four possibilities:
 - Your server is limiting connections to the local network somehow
 - Your router is not forwarding the port correctly somehow
 - There is some difference between the client on your local network and clients outside
 - The outside network you're connecting from is somehow firewalled against outgoing ssh connections

Are you using /etc/hosts-allow or /etc/hosts-deny at all?
Are you using key authentication or just password?
Do you have a way to confirm that you are in fact hitting the router and that it is in fact forwarding the port?
What client are you using outside the network?  Is the remote network filtering outgoing ssh?

---

### Post by Lul2x on 2008-10-10
You saved me again. It ended up being that my workplace blocks outgoing ssh connections. I tried from a different location and it worked. Thank you!!

---

### Post by HermanAB on 2008-10-10
I'm running a SSH daemon that listens on port 80 on one of my servers, in order to get around dumb-*** port blocking.

---

### Post by PilotJLR on 2008-10-10
If you want to open up ssh to the internet, I highly recommend you pick a random port to do it. Even a port like 12345 would work well.

Anything well known, like 80, 25, 443, etc etc are all easy targets. Basic scanners and script kiddies are less likely to stumble upon your server if you use a non conspicuous port.

---

### Post by lykwydchykyn on 2008-10-10
Any open port is going to be conspicuous to someone doing a scan.  I would think the weirder the port #, the more likely they are to want to poke around and find out what you're running.

In any case, I believe the point of using port 80 in this case is because the ISP/corparate firewall is filtering connections out to port 22, and would likely not be filtering out connections to port 80 (unless they filter all web traffic, in which case there's probably not much they would let out).

---

