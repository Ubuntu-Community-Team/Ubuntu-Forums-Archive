---
title: "[SOLVED] Internet access to my Apache server"
date: 2008-08-31
forum: Server Platforms
---

### Post by llothos on 2008-08-31
ok i have been searching around in the forums and online in general and can't quite find the answer to my problem, I know the answer is out there but I thought I would start this with hopes someone can quickly answer my question.

At the moement i'm using vmware and playing around with server setup (8.04). I want to get this going so when I go to put it on one of my desktops I can just get it going with little fuss.

I installed lamp without a hitch no problems and I have installed mediawiki as well. Everything is up and running but I only have access locally. I have tried opening port 80 access to machine running virtual machine but that did not work. I will try to add the virtual machines ip to router list to see if that works or not!!

I am relatively new to linux, i've only dabbled in it a little and want to learn more.

I have read about host files and changing servername, etc. I tried setting up mediawiki on my whs and got it running but then the latest pp1 update broke the connections so I'm looking at migrating it to ubuntu server. So far as i have said it works, i've imported the wiki and everything I just need to gain access to it from outside my home!

Any help would be apreciated!

---

### Post by schettj on 2008-08-31
Well, its a vm problem, not an ubuntu problem.

What's the IP address inside the vm in ubuntu? I am assuming it is a local non-routable address like 192... 10.... etc.

Which means, from the outside, you need to be able to talk to that address. I would think the HOST machine could talk to it - if it can't then you'll need to look at firewalls. The ubuntu machine could have a firewall - if so, open port 80. The host machine might have a firewall but that seems unlikely (assuming you can surf on the host to the rest of the web...)

So, when you made the VM, what kind of networking did you pick? Bridged? NAT?

---

### Post by llothos on 2008-08-31
my host machine can use the internal ip address which is a 192.168... address but if I punch in my actualy ip address that is where i can't access it. I will try to forward that ip in my router when i get home from work. I am hopeing it's that easy, i just thought i'd start the thread to see if there was any other ideas out there before I got home to try this one!

---

### Post by schettj on 2008-08-31
Oh ok. So you'll need to port forward from your external IP to the local ip. Or from your router, if it's also on the local IP space and acts as your firewall/router.

---

### Post by llothos on 2008-09-01
well i attempted to forward the vm's machine but as I was kind of wondering, it didn't work. the address wasn't the typical 192.168.0.(whatever) it was 192.168.173.(whatever) so it wasn't considered part of the "domain" of the router. Didn't want to play around with changeing the ip address of the server.

So I installed it on my empty box and withing an hour or so I had everything up, running and configured (for the most part). I have access outside my network and everything! (well once I forwarded the correct port to my server). 

The only problem I'm having now is I can't seem to get my logo to show up on the wiki. but that can be for another thread!

Next I'm going to play with using file server (samba)

---

