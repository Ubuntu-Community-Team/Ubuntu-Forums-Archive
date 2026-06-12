---
title: "all-in-one server??? can it exist"
date: 2005-09-27
forum: Server Platforms
---

### Post by dbrine on 2005-09-27
I have a crazy, maybe, question. I have a server that I want to use as a file server, webserver, ftp server, mail (maybe) and act as a firewall/router. Can all this exist on 1 pc??? I don't want mess of pc's in the house. I am using 2 wifi routers (using WDS) and a cable modem. what i sthe best way tosetup everything up? I have 2 nics already.

---

### Post by deuce868 on 2005-09-27
You CAN, but it's never recommended to put anything else on a box acting as a firewall/router. 

As to how to set it all up, going to have to start one things at a time. I would start with the router/firewall portion, get your iptables rules in place. Then go from there.

---

### Post by ben2005uk on 2005-09-27
you shouldn't have anything else on a firewall/router - technically.  heard it causes security risks - loop hole in webserver leads to whole network being open and stuff like that.  Never done it personnally but is something I wouldnt recommend.

Depending on how beefy your box is,  you could run a firewall/router as the base and then a vmware session ontop of that running all the webserver and mail etc.  

BUT!! There could be problems with doing that, guess it depends on how much support u have

---

### Post by dguitar on 2005-09-27
A lot of secruity issues in doing that. It would be very simple to over load that system too, even on bleeding edge technology. 

Also, if you were doing anything big, you should probably go with 3 machines or even 4. 

I won't even touch wifi in a mission critical situation :razz: 

If you are just goofying around trying to teach yourself stuff, you *MIGHT* be able to get away with 1 machine but I would definetly suggest 2. I have a 486 Packard Bell running as a router for my network, and I run a webserver behind it that gets 100k hits+ a week. So even an old dusty PC can be a router ;)

---

### Post by ben2005uk on 2005-09-27
Personally at home (don't live there any more,  at uni now) I had a off the shelf router + P120 box for webserver, mysql, mail, ftp and any other linux services i wanted to find out how to install :)

I also have a P166 which i could use as a router, but it means buying a ethernet modem and its a bit noisy.....i like my off the shelf one - it just works :)

if you want like VPN or something you could have a router which supports pass though (wrt54g like mine) and set that up on your web server box.........

just a thought.

---

### Post by dbrine on 2005-09-27
I have 2 linksys 54g's with modified firmware now. But wanted to keep as much as possible, securely and smartly, on a single box. I could run shorewall on each box.  But wasn't sure about running everything else, like ftp, web, etc from the same box. I am pretty new and want to dump windows. does anyone have any really good how to's as far as setting up everything I need? I am running multiple HDD's if it matters.

---

