---
title: "SSH from anywhere?"
date: 2010-09-08
forum: Server Platforms
---

### Post by darms21 on 2010-09-08
Can I SSH from a windows machine out of my LAN network to a Linux Server inside my home LAN network? If so how? Sorry for the basic question, I am new to this Server OS. Thanks!!!

---

### Post by Naitsirhc Hsem on 2010-09-08
you can use your router to forward your ssh port.  I don't know how to do this, but I do know that your router that connects all of your computers to the internet makes them all look like 1 ip address.  if you can make the router tell the outside network that your computer at the ssh port is where it needs to go, you will able to do this.  google port forwarding and ssh

---

### Post by gobbledigook on 2010-09-08
yep! you need to [forward a port]("http://portforward.com/") to 22 of your server at home :) 

you can use any port on the outside as 22 is commonly "scanned" so for instance you could ssh to port 5522 and have you router forward that to port 22 on your server...

only thing is you will need software on the other side like [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") for example to enable you to connect to your server at home, you will need to know the external IP of your internet connection at home. i would love to ssh home from work! think of all the cool "stuff" i could crack on with but just never have the time! but our IT admin won't let us install or run any apps :( damned slave drivers!

---

### Post by endotherm on 2010-09-08
just be careful if you want to expose ssh to the internet. most folks recomend using keys only instead of passwords, and others recommend fail2ban (uses the firewall to block connections that provide too many bad passwords) and DenyHosts to prevent common attacks. 

here is some research material:
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/](http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by DemonBob on 2010-09-08
If you are planning of doing this from work, be wary of the policy and procedure at your company. At some companies it is a firing offense. I have fired people for similar things.

---

### Post by Demented ZA on 2010-09-08
> **DemonBob said:**
> If you are planning of doing this from work, be wary of the policy and procedure at your company. At some companies it is a firing offense. I have fired people for similar things.

Not to hijack the thread, but for what reason? I assume it can be seen as a security breach? Being able to move company information to another pc/server without anyone being able to decern the content being sent or recieved?

---

### Post by DemonBob on 2010-09-08
> **Demented ZA said:**
> Not to hijack the thread, but for what reason? I assume it can be seen as a security breach? Being able to move company information to another pc/server without anyone being able to decern the content being sent or recieved?

Well it's two fold, first reason is security. When you are in charge of the security for a company whom has close to 20,000 records of personal information for your employees. SSHing out can be conceived as someone trying to still that information. The second reason is that if they are not trying to steal data but trying to circumvent security I.E proxies by RDP/VNC/SSH then it's my viewpoint that if they have enough ime to try that then they must not want there job, because they are obviously no doing it at that time.

I've been a Network Admin for 7 years and a manager of IT for two, you learn if you don't put up with it the first few times, words gets around, and others don't try it. Makes me an *** but you need to be to get the point across sometime.

Especially when we are nice enough to set up computers in the break room on separate network for them to use doing thief break. These computers were not governed by a proxy.

Typed from my phone, forgive my spelling. If you want to discuss further, feel free to PM me.

---

### Post by Deniz343 on 2012-06-23
> **gobbledigook said:**
> yep! you need to [forward a port]("http://portforward.com/") to 22 of your server at home :) 

you can use any port on the outside as 22 is commonly "scanned" so for instance you could ssh to port 5522 and have you router forward that to port 22 on your server...

only thing is you will need software on the other side like [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") for example to enable you to connect to your server at home, you will need to know the external IP of your internet connection at home. i would love to ssh home from work! think of all the cool "stuff" i could crack on with but just never have the time! but our IT admin won't let us install or run any apps :( damned slave drivers!

If I change my port number should I need to forward port to my new port number. 
And I found this tutorial for forwarding port on linksys: [http://www.youtube.com/watch?v=GWPUdW1kIJA&feature=youtube_gdata_player](http://www.youtube.com/watch?v=GWPUdW1kIJA&feature=youtube_gdata_player)

---

### Post by dustinmarc on 2012-06-24
I feel so happy I may actually be able to help someone (I'm a newb)!  I just went through the same thing.  Yes, you can absolutely SSH from anywhere into your sever.  What I did was change the port for SSH (both to be SLIGHTLY more secure, and because either my ISP or my router was blocking port 22).  Use something above 1000.  Then forward that new port number in your router to make all information go to your server.    So if you changed to port 2800 in your sshd_config file, then you need to forward all information going to the router on port 2800 to your server's local address.  I believe you have to download putty on the remote PC to use SSH in windows though.  Don't quote me on that.  Let me know if I can help more!

---

### Post by spynappels on 2012-06-25
You could just forward a high port like 22022 on the Internet side to port 22 on the server, you do not need to change the port on the server per se.

Doing what I suggest means you use port 22022 or whatever from outside the LAN and port 22 from inside the LAN.

Having said that, if you use key based authentication, you don't really have to change a port number, as long as you disable password authentication.

---

### Post by markbl on 2012-06-25
> **spynappels said:**
> You could just forward a high port like 22022 on the Internet side to port 22 on the server, you do not need to change the port on the server per se.

I always suggest to keep port 22 on your server, and forward from port 443 on your home router. Using a non-standard external port is better even if you use key authentication merely because 1) it reduces an enormous amount of attacks you otherwise will see hammering your sshd log, and 2) using port 443 is most likely not blocked outbound from your work, internet cafe, etc. Port 22 is usually blocked by most firewalls but since you are unlikely to want to run a https server at home, you may as well use that port 443 for your ssh connection.

---

