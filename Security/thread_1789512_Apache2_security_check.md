---
title: "Apache2 security check"
date: 2011-06-23
forum: Security
---

### Post by chomlee on 2011-06-23
I have created a web server to use for media files with my roku box and I dont have any need for outside access and want to cut it off so no one could get in and steal files from outside of the home network.

I put in the ports.conf file  "Listen 127.0.0.1:80" which replaced the "Listen 80".  Is this all I need to restrict outside access or do I need something else?  Is apache by default closed to the outside?  How can I check to see if I can get access from the outside or not?


Thanks,
Tom

---

### Post by Dangertux on 2011-06-23
> **chomlee said:**
> I have created a web server to use for media files with my roku box and I dont have any need for outside access and want to cut it off so no one could get in and steal files from outside of the home network.

I put in the ports.conf file  "Listen 127.0.0.1:80" which replaced the "Listen 80".  Is this all I need to restrict outside access or do I need something else?  Is apache by default closed to the outside?  How can I check to see if I can get access from the outside or not?


Thanks,
Tom

Well the way you have it set right now will allow it to listen on all interfaces for a connection. Which is not necessarily bad since you will still need to access it from a remote machine on the network. 

You can additionally block outside access to it from ufw by adding something like this 

sudo ufw allow from 192.168.0.0/24 to 192.168.0.x  port 80

that will allow traffic from the 192.168.0.0 network (assuming that is the ip range for your network) to your server where 192.168.0.x is the IP of your server on port 80.You can also change the subnet /24 to a specific IP address if you'd only like to allow one IP. In addition to deny all in ufw you should be covered. Also if you're using a router just make sure you don't forward the ports unless you want it accessible from the internet.

---

### Post by crispy_420 on 2011-06-24
Other than mentioned previously just make sure your router is locked down and not forwarding anything to box.

---

### Post by chomlee on 2011-06-24
Thanks for the help, how to I check to see if it works?

---

### Post by Dangertux on 2011-06-24
You can use an online port scanning application or have a third party (not within your LAN) scan your external IP address. This should indicate that port 80 is not open to them. If it does not you either didn't configure your firewall properly or forgot to enable ufw.

---

