---
title: "PhpBB3 &amp; Apache - Can't reach via external access"
date: 2013-03-17
forum: Server Platforms
---

### Post by sergiosanches on 2013-03-17
Hello everybody!


Well, this is my first post on the forum, and after almost a whole weekend searching on Google and here on the forum, I decided to post this here because I could not find an answer.


I would firstly,show the scenario:


I have an ADSL connection.
This connection is being replicated by the router D-LINK DIR-600.
There is a computer with Ubuntu 12.04 LTS Server with XAMPP and phpBB3 running.


The problem is as follows:
The server Apache and phpBB3 are working perfectly.
I access both the server's via internal IP: [http://192.168.0.2:8080/](http://192.168.0.2:8080/) and [http://192.168.0.2:8080/phpbb/](http://192.168.0.2:8080/phpbb/)
Then, when I'm try to access externally, or even from the inside-out - putting my external IP server on the browser ([http://177.180.196.xx:8080](http://177.180.196.xx:8080)), I have no success.


Regarding the issue of port forwarding on the router, I swear, I've done everything you can imagine. Even put the server in the DMZ router.
But the funny thing is that the site [http://canyouseeme.org/](http://canyouseeme.org/) says that my port 8080 is open, but when i'm trying to access it through my external ip, i can not.




I spent the whole weekend trying to put that forum on. Could anyone give me an idea of what to do?
Thank you!

---

### Post by sanderj on 2013-03-17
I scanned the 77.180.196.0/24 range on port 8080, and only one IP address (I won't mention which one) has that port open. When I check that, it shows an O2 DSL router (in German).

So ... is that you? 

General advice: use a different port on the outside than 8080 ... 8080 is a well-known port used by modems itself ...

---

### Post by sergiosanches on 2013-03-17
Thanks for the reply sanderj1!
No,that's not me. I'm from Brazil,and the server is not running right now. But i would like to thank you anyway.
I'm going now running the server again,and apply the tips that you said me.


But,is not really funny that  [http://canyouseeme.org/](http://canyouseeme.org/) saying my port 8080 is open ? Because i'm really configured this on router,but even can not reach from external conection.
What do you say ?


I'll make the changes and already return.
Greetings!

---

### Post by sergiosanches on 2013-03-17
Well, I did what you asked and the result was the same: I can not reach the server from outside.
Just to illustrate it:


I re-configured Apache to listen on port 666 - :twisted:
Restarted the service.
Reconfigured the router port foward.
As expected, i'm able to access the server via internal network without any problem, through port 666 ([http://192.168.0.2:666/phpbb/](http://192.168.0.2:666/phpbb/))
However, through my external IP (177.180.196.xx:666) this is impossible.


And the site [http://canyouseeme.org/](http://canyouseeme.org/) continues saying:


*Success: I can see your service on port 177.180.196.xx on (666)*
*Your ISP is not blocking port 666*


Any idea?
Thanks!

---

### Post by sanderj on 2013-03-18
I did a

nmap -p 666 177.180.196.0/24

a not one open port was detected. I can't tell help you on what [http://canyouseeme.org/](http://canyouseeme.org/) is saying. 

Back to the problem: it could also be a firewall in your modem.

---

