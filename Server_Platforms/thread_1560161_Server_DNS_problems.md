---
title: "Server DNS problems"
date: 2010-08-24
forum: Server Platforms
---

### Post by gavin100 on 2010-08-24
Hi I hope you can help, Im going slightly mad and running out of coffee.
 
I'm new to linux and Ubuntu server so its a bit of a steep learning curve. I've set up my server (HP Proliant G3) installed all the recomended features eg. phpmyadmin etc and all has gone well until it came to setting up the DNS name, I have set up an account with dyndns as I have a dynamic ip address. installed ddclient and copied the generated settings to the ddclient conf file. restarted the server. made sure port 80 was open on my BT Homehub router and made sure it is open on ufw firewall but all with no luck I still cant access the server away from home.
 
Any help you can give would be ideal, thank you

---

### Post by Bachstelze on 2010-08-24
Maybe the dyndns redirection is wrong, maybe your ISP blocks port 80, maybe.....  Can't give you an answer without more info.  Does the name resolve to the correct IP?  Can you telnet on port 80?  Can you ping?

---

### Post by gordintoronto on 2010-08-24
You say port 80 is open, but is it directed to your server? Most routers have a "port forwarding" option.

---

### Post by sptrsn on 2010-08-24
I think......(disclaimer)
If your ISP is blocking port 80, the idea behind ddns is too use an alternate port, say 8080. Public user hits the ddns website, which converts it to use your "other" port, 8080. 
All traffic between you and the ddns provider happens on port 8080, so your firewall should be config'd to listen on 8080 and be pointed at your server using either virtual server or port forwarding.

---

### Post by arrrghhh on 2010-08-24
Dyndns or other services will NOT redirect traffic based on the port.  If your ISP is blocking the traffic, there's unfortunately not a lot you can do to resolve the issue - most residental connections do not support running any type of services (web, ssh, ftp, etc) - so you're unlikely to get any sympathy from their support dept.

One thing you can do is go to a site like [ShieldsUp!](https://www.grc.com/x/ne.dll?bh0bkyd2) to see which ports it considers open, "stealth", or closed.

---

### Post by BkkBonanza on 2010-08-24
As mentioned above. It's not enough to have port 80 open. It also must be "forwarded" to your server ip inside the network. If you're not sure how to forward ports then either check the router manual, or google "make/model# port forwarding" for info on how to setup your router.

If you do a scan from ShieldsUp and the port 80 is open then the next step is forwarding. If it's closed or dropped/stealth then that means your isp is blocking port 80. That's not unusual on non-business accounts. You would have to use an alternate port - which people often prefer to avoid due to the address being confusing to users (eg. [www.mydomain.com:8080](www.mydomain.com:8080)). You could use a proxy to fix that but that's almost as much hassle as just hosting the site in a data centre. It is possible to use "cloaked/framed redirection" but that also involves some problems and needs to be supported on your dns provider.

Oh, and another thing to check. Make sure that ddclient is actually updating your dyndns account with the correct ip. If dyndns isn't resolving to the correct ip then you'll not get there. In a terminal try, 

nslookup yourname.dyndns.com   (whatever name you set up)

and make sure it returns the current correct ip. It should match whatever you get from an ip address checker site like, [ip-adress.com]("http://ip-adress.com").

---

