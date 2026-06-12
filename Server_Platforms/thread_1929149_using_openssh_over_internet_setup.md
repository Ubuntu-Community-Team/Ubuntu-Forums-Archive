---
title: "using openssh over internet setup?"
date: 2012-02-21
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-02-21
I was wondering if someone could supply me with a tutorial on how to remotely connect to my sever using openssh. I have an openssh client on the client computer, can someone help me?:confused:
 
 
Thanks,
      TJ

---

### Post by pricetech on 2012-02-21
A few issues first;

Do you have a fixed IP address ??  If not, do you have some kind of dynamic DNS account that will allow you to point to your IP by name ??

You'll need to configure your router to forward port 22, or whatever port you decide to use for SSH, to the internal IP of your server.  Have you done this yet ??

I suggest installing fail2ban on the server to help protect you from attempts to break in to your server.

Have you completely set up the server and tested it internally ??

What you're wanting to do is pretty common, so you shouldn't have any trouble finding information on the subject, but I suggest starting with the points mentioned above and go from there.

---

### Post by hawkmage on 2012-02-21
First I would suggest not using port 22 on the external NAT/Firewall rule.  When I was using port 22 I got hundreds of bruit force attacks a day.  Select an alternate port.

Also I limit the number of allowed connections with iptables from external.  The easiest way to do this is to have sshd listen on two ports.  This minimizes the how many connections a hacker can make slowing down any bruit force attack.  

Lets say the second port is 23456 in your iptables rules add something like this:
```
-A Firewall-1-INPUT -p tcp --dport 23456 -m recent --set --name ssh2 --rsource
-A Firewall-1-INPUT -p tcp --dport 23456 -m recent ! --rcheck --seconds 60 --hitcount 4 --name ssh2 --rsource -j ACCEPT
```
This allows 4 connections to this alternate port in 60 seconds.

---

