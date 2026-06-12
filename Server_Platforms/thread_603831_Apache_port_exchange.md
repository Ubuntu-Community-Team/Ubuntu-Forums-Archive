---
title: "Apache port exchange"
date: 2007-11-05
forum: Server Platforms
---

### Post by kroynos on 2007-11-05
Hello All,

I have a little problem maybe somebody can help me, here it is, I have a friend that is on FIOS in florida and i will admin his ubuntu, the problem that has occur is that Verizon has blocked out 80, and i do not want to use 8080 through is routing system, also i have used dyndns.org to set up a bounce back to his server and it just hangs, also i edited /etc/apache2/ports.conf and changed the Listening Port but still no changed, also I have him to do the port forwarding too. any suggestions on what i have missed or is there another conf file that i edit and try to open up more ports so i can use the apache2.

Thanks
William

P.S. you can goto [http://syndog.game-host.org](http://syndog.game-host.org) and see if you can tell me with this error after about 60 secs of hang.

---

### Post by MJN on 2007-11-05
What port have you changed it to?

You need to either get clients specify the port in the URL (e.g. [http://syndog.game-host.org]("http://syndog.game-host.org/"):8080) or use, in your case, the DynDNS 'webhop' service to redirect to your server with a non-standard port number.

Mathew

---

### Post by kroynos on 2007-11-05
> **MJN said:**
> What port have you changed it to?

You need to either get clients specify the port in the URL (e.g. [http://syndog.game-host.org]("http://syndog.game-host.org/"):8080) or use, in your case, the DynDNS 'webhop' service to redirect to your server with a non-standard port number.

Mathew

Good idea i will check that out with dyndns, the port i set it too is 1252 but webhop i will see what i can do there.

---

### Post by kroynos on 2007-11-05
Alright Dyndns.org will not allow me to webhop to point to a certain port number.

I will seekout another dynamic DNS site if they can allow me to adjust the port numbers.


William

---

### Post by MJN on 2007-11-05
DynDNS do support port redirects:

[http://www.dyndns.com/support/kb/webhops_redirections.html#ports](http://www.dyndns.com/support/kb/webhops_redirections.html#ports)

I have tried to connect to [http://syndog.game-host.org:1252/](http://syndog.game-host.org:1252/) but it doesn't work so it sounds like either your port forwarding is not working or Apache is incorrectly. It could even be Verizon blocking based on identifying the HTTP GET request from deep packet inspection (unlikely though - it's rare for them to go this far).

Mathew

---

### Post by kroynos on 2007-11-05
Hey rock on dude thanks.. reading it right now... 

Thanks for your help.

William

---

### Post by kroynos on 2007-11-05
Dang, sometimes i just read everything thoroughly well i got it to work.

Thank you for pointing me to the right directions, i commend you on your knowledge.

Thanks,
William

---

