---
title: "broadband static ip &amp; apache not working"
date: 2010-03-17
forum: Server Platforms
---

### Post by j6904 on 2010-03-17
For some strange reason, I cannot access web pages served from our LAMP server through our broadband static IP address.

The LAMP server is running Ubuntu 9.10, and it was mostly just a standard install. The machine is configured with a static IP address. It will show web pages when I navigate to the local IP address of the server, and I did verify that it is working on port 80. However, it does not work when I use the IP address assigned to us from our Internet provider.

The gateway modem that we are using is an SMC SMCD3G-BIZ. Without port forwarding turned on, the admin page for the gateway modem is displayed when navigating to our broadband static IP. When port forwarding is configured to send port 80 traffic to the static IP of the LAMP server, nothing is displayed when navigating to our broadband IP address (it times out).

I did try turning on DMZ for the IP of our LAMP server, but that did not fix the problem. I do get a reply when I ping our broadband IP, and [http://www.canyouseeme.org](http://www.canyouseeme.org) reports that they can see my service on port 80, and that port 80 is not being blocked.

It seems like it should be working - any ideas on how to fix this would be greatly appreciated.

---

### Post by volkswagner on 2010-03-17
Have you tried from a PC outside your LAN?  

It may be NAT blocking the request from inside your LAN.  

You will certainly need the port 80 forwarded to your servers ip address.

Verify you don't have software firewall running like UFW.

---

### Post by mikemelen on 2010-03-17
check is there any default firewall block the service and setup NAT in modem to froward port 80

---

### Post by j6904 on 2010-03-17
Hi, thanks for the replies. I've been working at it all day, and I'm just grasping at straws right now.

The modem is forwarding traffic to port 80. The firewall was turned on. I turned it off completely, but it still doesn't work.

Maybe an interesting thing was when I called somebody to try it from outside of my LAN. At first, they experienced the same thing I was seeing - nothing, like it will time out. Then just as I was getting ready to hang up the phone with them, they said it displayed some text from the webpage, but no graphics, no style sheet, etc.

---

### Post by volkswagner on 2010-03-19
The lack of graphics/css is most likely file permission issues.

```
ls -alt /path/to/webroot
```

Verify group or owner set for www-data, or www-data is included in the group files are set to.

---

