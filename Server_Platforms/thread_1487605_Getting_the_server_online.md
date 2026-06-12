---
title: "Getting the server online"
date: 2010-05-19
forum: Server Platforms
---

### Post by Yizi on 2010-05-19
Hi, It's my first time setting a local server up and getting everything to go smoothly, at the moment I have the server running LAMP and I control it using SSH. I like to know how I can get the server online and actually connect a domain to it? 

I have the ISPConfig setup and it runs perfectly fine, what I like to know is:

[LIST]
[*]How do I attached a IP to the server? (or can I just access it using the IP i have now?)
[/LIST]

I have my domains with Namecheap and they provide FreeDNS.

---

### Post by volkswagner on 2010-05-19
You first need to open port 80 on your router and forward it to your servers internal FIXED ip address.  This will allow you to access your server using your external ip address.  To easily find your external ip address go to canyouseeme.org.  While at the site, you can also see if your isp blocks any important ports such as port 80.

If all is ok up to this point you just need to point your DNS servers to your external ip address.

Most likely your residential Internet connection is a dynamic (changing) ip address.  If this is the case you will need to set up a dynamic ip service such as from noip.com or dyndns.com.  Check your router to see if it has built in service for any of these providers.

---

### Post by Yizi on 2010-05-19
The information was very useful! I managed to the the port 80 open in my router, I can access the server via external IP as well, now I just can't figure out how to connect it to my domain ..

I'm using the domain control panel @ namecheap (Nameserver Registeration) and I connected my IP to ns1. and ns2. ... Am I doing it right because it's not showing when I go to the domain

---

### Post by volkswagner on 2010-05-19
You need to check the TTL (time to live) setting at your DNS provider.  It needs time to propagate.  The amount of time depends on this setting.

---

