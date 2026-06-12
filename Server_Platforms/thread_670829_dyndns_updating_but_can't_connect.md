---
title: "dyndns updating but can't connect"
date: 2008-01-17
forum: Server Platforms
---

### Post by fizban9 on 2008-01-17
I'm trying to connect to my computer remotely using the service provided by dyndns.  My home network is a dsl modem plugged into a Linksys router.  I'm connected directly to the router.  My ip address is updated correctly with dyndns (it gets the ip address of the dsl modem) but I can't ping or traceroute or connect to my computer in anyway.  

Any ideas?  If I can just get the ping to work I'd be happy.  My domain is redmage.doesntexist.com

Thanks for the help.

---

### Post by ecrissman on 2008-01-17
Are you trying to connect from another computer in your network or from the outside? What service does DynDNS provide to connect to connect remotely?

---

### Post by freymann on 2008-01-18
> **fizban9 said:**
> I'm trying to connect to my computer remotely using the service provided by dyndns.  My home network is a dsl modem plugged into a Linksys router.  I'm connected directly to the router.  My ip address is updated correctly with dyndns (it gets the ip address of the dsl modem) but I can't ping or traceroute or connect to my computer in anyway.

 I would think there's a setting in your router's configuration that determines if it will respond to a PING command.

 Log into your LinkSys router and click on 'Security'

 See if Block Anonymous Internet Requests is checked. Linksys describes this option as:

> 
By enabling the Block WAN Request feature, you can prevent your network from being "pinged," or detected, by other Internet users. The Block WAN Request feature also reinforces your network security by hiding your network ports. Both functions of the Block WAN Request feature make it more difficult for outside users to work their way into your network. This feature is enabled by default. Uncheck to disable this feature.


 Since it's enabled by default, that may explain why you can't ping your domain.

 As far as 'reaching' your computer behind the router, you'd have to set up some port forwarding for that to happen.

 Under "Applications and Gaming" you will find a table where you can direct ports to internal IP addresses. The only thing you have to do differently here is to assign your internal computer a static IP address so the port forwarding works all the time even after you reboot your computer.

 Have fun!

---

### Post by fizban9 on 2008-01-18
> **freymann said:**
>  See if Block Anonymous Internet Requests is checked.


I'll try that when i get home.  I think I remember seeing that option when I was poking around in it.

>  As far as 'reaching' your computer behind the router, you'd have to set up some port forwarding for that to happen.

 Under "Applications and Gaming" you will find a table where you can direct ports to internal IP addresses. The only thing you have to do differently here is to assign your internal computer a static IP address so the port forwarding works all the time even after you reboot your computer.

Right now I do have my PC on a static IP address within my own home network and I set up port forwarding to send port 22 to my IP.  I think thats the port that ssh/telnet goes over.  

Thanks for the advice.  I wish I could work on it right now, but I'm at work.  I'll let you know if that fixes the problem.

---

