---
title: "Ubuntu server - database, web, mail"
date: 2009-06-19
forum: Server Platforms
---

### Post by rx7haze on 2009-06-19
I'm sure all of my questions have been answered before, but I'm new to this and not sure where to start or where to look. I want to set up a server that will host a database, web apps, files and email. The first task I want to accomplish is to get the file server up and running. I want my user(s) (maybe 2 or 3) to connect directly to this machine. I do not need to make any or all portions of the server available over the web. I'm sure there is a tutorial out there, I would be most appreciative if someone could point me toward it. I have seen tutorials on getting the individual server components up and running and have been successful getting MySQL up and running. I need to step back and first expose the server to my users.
Thank you.

---

### Post by wojox on 2009-06-19
Check out this site [http://www.howtoforge.com/howtos/linux/ubuntu](http://www.howtoforge.com/howtos/linux/ubuntu) 
It should be a start.

---

### Post by rx7haze on 2009-06-19
I have been to that site. Here's what I have so far. I have set up my server with a static ip address 192.168.0.165 along with the subnet and gateway adresses. I am able to connect to the internet and am able to log into the mysql database from another computer inside my house. My question is how do I now connect to the server from a pc outside my house? I'm planning on using the mysql database for this test. From the other pc within my house i connected to the mysql db using the host name 192.168.0.165 in the connection. Does it have something to do with my ip address? I tried doing a little research on ip addresses but got confused very quickly.

---

### Post by kustomjs on 2009-06-19
if you want to access the information from outside of your network you would have to open the ports on your router.

---

### Post by wojox on 2009-06-19
Yes kustomjs is right on the money

What brand router are you using ?

192.168.1.0 - 255 are assigned to your lan behind the router inside your house.

I have a cisco wireless router. Tell us what your using and we can help figure it out. Like kustomjs said you just need to log into your router config which is probably 192.168.1.1 and set permissions for that specific ip address and port.

---

### Post by rx7haze on 2009-06-19
I am using a D-Link router WBR-2310. I have the choice of setting up a virtual server or port forwarding. Which one should I use?
Thanks.

---

### Post by cariboo on 2009-06-19
Port forwarding is the easiest. Mysql runs on port 3306, so you would have to forward that to your router. 

On my Linksys router you set the sevice - in this case mysql, the port range - 3306 and the ip address of the computer the service is running on - 192.168.0.165.

Then to make sure you have done things correctly check [canyouseeme]("http://www.canyouseeme.org/"), and have it check the ports you have opened.

---

### Post by rx7haze on 2009-06-19
Thank you so much for the help. CanYouSeeMe verified success. I never would have imagined it to be so easy.

---

### Post by rx7haze on 2009-06-23
I have everything in place but I´m still a little confused. How does the outside world find me? From the outside I can´t connect to my db server by typing in 192.168.0.165:3300. When I go to canyouseeme.org it reports back a different ip address. I´m guessing that has to do with my router?

---

### Post by Joeb454 on 2009-06-23
You most likely have a dynamic IP address. This applies to most ISP's.

I would assume you need to look into a service like [DynDNS]("www.dyndns.com") or something similar, so that your IP address isn't of too much importance :)

---

### Post by v3xtra on 2009-06-24
> **rx7haze said:**
> I have everything in place but I´m still a little confused. How does the outside world find me? From the outside I can´t connect to my db server by typing in 192.168.0.165:3300. When I go to canyouseeme.org it reports back a different ip address. I´m guessing that has to do with my router?

Every computer device has its own IP in the world of the Internet.  These are what you call WAN IPs, and they are how the outside world sees your computer.  If you think about it, someone else could easily have the same LAN IP ( or internal IP ) as you, just by using the same router as you and the same default settings.  But how would anyone be able to be different if the IPs were all the same?

Going to a site like whatismyip.com or as stated earlier canyouseeme, the IP that that returns is the WAN IP that allows others NOT on your internal LAN to see you.  For anyone connecting to your router, your internal works just fine, and so should your external.  That is how you will be able to connect to it from the outside world.

Joe hit the nail on the head with dyndns service.  What it does is it gives you a simple "domain" free of charge that links the domain address to your WAN IP address.  This allows you to type in [http://something.dyndns.org](http://something.dyndns.org) instead of [http://176.234.221.35](http://176.234.221.35) , making it easier to remember.  This is also because your WAN IP may renew itself sometimes and you may have a new IP address, but the dyndns will update itself to the new IP allowing flawless changes!

---

