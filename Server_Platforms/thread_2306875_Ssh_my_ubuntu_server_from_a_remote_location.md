---
title: "Ssh my ubuntu server from a remote location"
date: 2015-12-19
forum: Server Platforms
---

### Post by biggyk on 2015-12-19
Having a bit of trouble getting connected to my home server externally.

My server is currently my only linux system I have atm. Everything is else is Windows and android. I figured I can just open the port on my router and it would work fine but it doesn't seem to want to connect. I have it set to tcp forwarding using port 21 as my router will not allow 22 to be used. Is there anything else on the server side that im missing. On my lan, it works wonders.

---

### Post by gtozzi on 2015-12-19
If you want to use 21 instead of 22, you'll have to also change the port on your server.
I would suggest tu use something like 2222 instead, because 21 si supposed to be reserved for FTP.

See this for how to change the port:
[http://ubuntuforums.org/showthread.php?t=1591681](http://ubuntuforums.org/showthread.php?t=1591681)

---

### Post by biggyk on 2015-12-19
Yes, I did that. sorry for not mentioning that. I use webmin also and set it through there. I tested it on port 21 internally and it works.

---

### Post by darkod on 2015-12-19
Then it seems like port 21 is blocked. If you are sure you set the port forwarding correctly.

I also suggest to use some port above 1000. Configure the sshd_config with the correct port, test internally, and then set port forwarding and test externally.

Your ISP might be blocking many of the ports. In such case change ISP (if others don't do the same).

Usually you can check on this page if a server behind a specific public IP is listening on a specific port: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by gtozzi on 2015-12-19
If it works internally, then most probably there something wrong with your router configuration.

---

### Post by darkod on 2015-12-19
Also take a look at the firewall settings. Configuring a port forwarding rule does not open the firewall for that port on all routers. On some you would need a separate firewall rule too.

And why do you say it doesn't allow to forward port 22? Are you sure? After all, you can see your router interface, we can't... :)

---

### Post by SeijiSensei on 2015-12-20
You should only use ports between 1024 and 65535.  Ports 0-1023 are reserved for defined services and should only be accessible to the root user.  See /etc/services for a list.

Choose an arbitrary high port like 22222 externally and forward it back to 22 on the server.  I sometimes choose ports using the mnemonic of spelling out a word on a telephone dial.  For instance, "linux" would be "54689".

---

### Post by biggyk on 2015-12-20
I just changed it to 2222 and it works fine now.  Thank you. 

My router just told me I couldn't use 22 for ssh management.

---

### Post by darkod on 2015-12-20
Great. You can mark the thread as Solved in Thread Tools above the first post.

---

