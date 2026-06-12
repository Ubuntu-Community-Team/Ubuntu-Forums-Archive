---
title: "Server Help!"
date: 2010-09-01
forum: Server Platforms
---

### Post by Nix1794 on 2010-09-01
I have Ubuntu 10.04 LTS and I installed the apache web server but, the problem is I can't figure out how to set it up for the Internet. It only works for my local network :(
Can anyone help? 
P.S I'm new to Linux Operating Systems.
Thanks!

---

### Post by spynappels on 2010-09-01
If it works fine on the LAN, you need to set up port forwarding on your router to allow connections from the WAN (Internet) to be forwarded to your server on it's LAN IP.

---

### Post by thegaffney on 2010-09-02
Yep, you need to tell your router that connections coming from your external IP on port 80 will be sent to your servers internal ip on port 80

If that's already done, then i would check your DNS settings for your domain name, are you using a external place for that like godaddy.com? if so you need to tell them that when people type in your web site, then that needs  to go to your external ip address, ( and hopefully it is a static ip ?)

So basically it should be (ill use our setup for an example)

-Someone types in [www.midfifty.com]("http://www.midfifty.com")
-A name server knows that that website name belongs the the IP 24.156.50.242 based on godaddy's DNS settings we set up
-Our router connected to that IP address knows that internet requests (port 80) get sent to our server on our internal network (192.168.1.222) 
-And then finally apache knows to listen to port 80 and shows the page


How are your accessing it on your LAN? Typing the actuall website name? or the servers IP address or something just like localhost?

---

