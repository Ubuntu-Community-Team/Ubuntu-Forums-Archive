---
title: "How do you set DNS for home-based server?"
date: 2009-02-21
forum: Server Platforms
---

### Post by clay7 on 2009-02-21
Hello,

I am running server 8.04. The domain name I would like is parked at godaddy and I want to point the DNS to my home-based server. Here's my problem: 

Right now my desktop (Win XP / Ub. 8.10) and server (8.04) are connected to a netgear router, which is connected to the internet. The only way I've accessed my server so far is by [http://192.168.1.3](http://192.168.1.3) from my desktop. So what address would I tell godaddy to point to?

Other info: I know my IP address from ifconfig, and right now it's dynamic, so I'll be using DynDNS. The server is running Webmin also.

Thank you,
Clay

---

### Post by adramalech on 2009-02-22
well have you thought of running a static network settings, and turn dynamic off?  


the [http://192.168.1.3](http://192.168.1.3) is your lan...so of course you will be able to connect to your network through the computer, but i don't think that it is your ip address that everyone else sees...so maybe run a whois or traceroute

because what your router does is allow you to connect to up to what 100-200 different sub numbers.... 192.168.1.xxx you would never know what one you are running...unless you go through ifconfig etc...  

so what i am saying it would be good to configure your router to do static numbers but assigning ip addresses...that way you can keep things organized....furthermore make sure to keep a good firewall up to keep your server from becoming pirated...so as you go along create a good complex iptable settings...

EDIT:
is it a ddns (i.e. a dynamic dns) ?????  because if soo i saw that in my linksys 330n router that dyndns.org has some settings to point to your router from the host site... using your username password etc... i think this is what you where looking for...

also you can do a dynamic static or a custom system....

the good thing about dynamic is that it is hard for hackers to pirate your system....but static is more secure if you know what you are doing...i am sure there are many guides for you to utilize in setting up and securing a good static network...

---

### Post by clay7 on 2009-02-22
right...I know my IP address (ifconfig), which I didn't publish here.

Here's what I'm asking:

Let's say I have a domain called "mydomain.com" and it's parked at GoDaddy. I want to tell the DNS at GoDaddy to point that domain to my server at home, which is behind a router. How do I do that? (I'm using DynDNS because it's a dynamic IP)

I'm asking this because if I just tell GoDaddy my IP, then how will "mydomain.com" know whether to go to my server or my desktop, because they are both on the same router.

---

### Post by adramalech on 2009-02-22
well i don't know what you can do besides make the network static....have your server on one ip address and have your desktop on the other...to not confuse it....i don't think that it could get confused...

i take it your server isn't running 24/7?? like dedicated...because if that is the case just leave it as is...

---

### Post by Hobgoblin on 2009-02-22
> **clay7 said:**
> right...I know my IP address (ifconfig), which I didn't publish here.


That doesn't give you your WAN IP address, which is what you need to point the domain name to.

If that is dynamic then you won't be able to, you can use dyndns but are then limited to their domain names.

You need to get a static IP from your ISP, point your domain name at that, then (on your router) set up port forwarding for port 80 and 443 TCP to your webserver (actually the netgear has predefined settings for a webserver so you just need to point that at the correct internal IP address).

---

### Post by clay7 on 2009-02-22
hmmm... I'll have to get a static IP. But since i have my desktop and the server behind the router, how will the "mydomain.com" know to go to the server instead of to the desktop?

---

### Post by jasonsjunk on 2009-02-22
Let me take a crack at this....  
1) Setup a dyndns account that will allow you to use your domain name with thier dynamic dns services.  The service you need is called custom dns [http://www.dyndns.com/services/dns/custom/](http://www.dyndns.com/services/dns/custom/) 

2) Point your domain name that you have registered with GoDaddy to the dns servers at dyndns.  Dyndns will give you the ip addresses for thier servers when you sign up.  You will have to create an A record and change the DNS server associated with your domain name.  GoDaddy has lots of information on how to do this, everything you need is located in your account settings. 

3) Once everything propagates in about 4 hours or so your domain name should be pointing to your ip address.  

4) You will need to forward port 80 in your router's configuration to the internal ip address of your server.  I would also set a static ip address for the server just to make things easier and keep them stable.

5)Netgear routers have a built in update client for DynDNS.  Just find the DynDNS setup in your routers configuration and enter your user name and password I believe.  It might ask for your domain name as well.

---

### Post by clay7 on 2009-02-22
Thanks! I'll give it a shot and see how it goes!

---

### Post by evilGUI on 2009-02-22
You might also want to try, everydns they have a perl script that you can setup in cron so your IP updates every few hours.

---

### Post by cariboo on 2009-02-22
You need to tell godaddy's dns server what your external ip address is. to find what your exteranl ip address is go the the mangement page of your router and check the status page. 

The above will only work if you have a static ip address provided by your isp. If you want to use a service like noip or dyndns you will probably have to have to pay to use your registered domain name.

Jim

---

### Post by E_K on 2009-02-22
go to whatismyip.com 
write down ip
fill in relavent dns records at godaddy
Go to your router config
forward port 80 to the local ip of the server (ifconfig)
taaaadaaaa

This will work until your friendly ISP decideds to update your ip

else sign up for free domain at no-ip.com
point free domain to your server
install script from no-ip that sends your ip to them at intervals you decide
point godaddy dns to no-ip domain

taadaaaa hassel free method (also free, but a little more work)

---

### Post by clay7 on 2009-02-22
sweet! Thanks everyone!

---

