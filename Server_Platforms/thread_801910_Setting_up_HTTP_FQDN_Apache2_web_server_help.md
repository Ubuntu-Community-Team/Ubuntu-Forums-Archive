---
title: "Setting up HTTP FQDN Apache2 web server help"
date: 2008-05-21
forum: Server Platforms
---

### Post by JameoPotato on 2008-05-21
Alright, trying to keep this short...
I got everything installed (MySQL, PHP5, Apache2, bind9) on Hardy Heron
I registered my domain name [www.jameopotato.com](www.jameopotato.com).
and... I started running a couple tutorials and pretty much ran myself over my head. 
I edited many files and finished what I thought was setting up my server as a DNS server and then realized that [www.MyDomain.com](www.MyDomain.com) wants to do all DNS management themselves.

I am running the server on a D LINK router (wireless G... the standard model) and believe I have set that up correctly to allow port 80 through to my server on 192.168.0.103.

What I have done:
Set up virtual server
installed and started mysql and php5
set static ip on both my server and router

Where do I go from now? Could I get a link to a more beginner set-up of apache? I don't expect one person to sit down and write me a essay on how to set one up (although that would be nice :)) but i'm just looking for something even that i could google and look up.
I know I have to login to mydomain.com and set-up something to direct it to my server, but i don't know what ip i need to put onto there. Do i use my DNS ips (which I have 2 of that I saw on my router page) or do i use the physical ip of the router (which I have set to static now).

even if one of you experienced user could just give me a list of the next steps I got to accomplish before I can go to the site and start writing pages and then I can go research them myself.

Thank-you in advance. (srry for the newbie questions)

---

### Post by bluefrog on 2008-05-21
If you do not have a public static IP , you'd better leave your name provider host your DNS servers.
It does not prevent you from running your own DNS on your LAN if you wish.

If you have a public static IP then forward your port 53 on your router to your server and change the dns IP at your name provider config page.

Places to read:
howtoforge.net
tdlp.org

in a terminal, info coreutils

---

### Post by windependence on 2008-05-21
It would be kinda pointless for him to run a DNS server at home unless he has more than 10 or so computers. To be an "official" DNS node he needs permission from his upstream provider also.

I think where he is having problems is with settiung up his nameservers and A record. His hosting provider should be able to help him with that. For hosting, I would recommend either GoDaddy or Gate.com.

-Tim

---

### Post by JameoPotato on 2008-05-21
okay so i don't need to use the server as a DNS server. 
I do however need to set-up what the guy above said about A record and nameserver. I don't know what either of those are.

[www.mydomain.com](www.mydomain.com) said that they provide nameservers:
ns1.mydomain.com
ns2.mydomain.com etc... up to 4.

I have options to edit them but i don't know what that would do.

As far as to my knowledge this is how it works:
someone types "www.jameopotato.com" that is picked up by the MyDomain DNS server
The DNS server turns [www.jameopotato.com](www.jameopotato.com) to my public static IP.
This is where I get stuck. I am running telus highspeed, will i have to call them and ask for a static ip? or can I set my router to keep a static ip?
AND when i talk about editing the mydomain DNS server... what options am I looking for I see A, NS, CNAME record and I also have the option to register nameservers or update nameservers.
The request will then get to my router where I will have opened port 80 and set it to forward those requests to my server 192.168.0.103 (which I know i have set to be static already)

Once I have that set up I need to setup my ubuntu apache2 settings. Virtual Host correct? Which I believe I have done right so far.

---

### Post by freebeer on 2008-05-22
I take it that you currently have a dynamic public IP address from your ISP?  I do, too, and I use dyndns.org for that reason.  However, if you already have a domain name from a provider, you'll probably want to stick with them.  You probably could contact your ISP for a static IP, but either they can't/won't provide you with one, or they'll charge extra for it, I would imagine.

With a dynamic public IP address there are a couple of things you can do.  Some routers have a feature that will report back to your dns provider your new public IP address whenever it changes.  My d-link router has this feature, but the one I had before that didn't.  Alternatively, if you don't have that feature, you can use a script that has the same effect.  I know it worked with dyndns.org, but I don't know if it would work for your provider.

---

### Post by windependence on 2008-05-22
> **freebeer said:**
> I take it that you currently have a dynamic public IP address from your ISP?  I do, too, and I use dyndns.org for that reason.  However, if you already have a domain name from a provider, you'll probably want to stick with them.  You probably could contact your ISP for a static IP, but either they can't/won't provide you with one, or they'll charge extra for it, I would imagine.

With a dynamic public IP address there are a couple of things you can do.  Some routers have a feature that will report back to your dns provider your new public IP address whenever it changes.  My d-link router has this feature, but the one I had before that didn't.  Alternatively, if you don't have that feature, you can use a script that has the same effect.  I know it worked with dyndns.org, but I don't know if it would work for your provider.

If your ISP will do it, the static IP is the way to go. I only pay $5.95 a month for mine. The issue you will have with the dynamic one is even though you can certainly serve pages from it using a redirect, there are many places that filter those and then those people cannot reach your site. I had that problem in the beginning also. Now we have over 12,000 page views per day. People's employer's usually restrict them from viewing redirected pages and let's face it, lost people surf at work. That's where most of my traffic comes from.

-Tim

---

### Post by spiderbatdad on 2008-05-22
> I know I have to login to mydomain.com and set-up something to direct it to my server, but i don't know what ip i need to put onto there. Do i use my DNS ips (which I have 2 of that I saw on my router page) or do i use the physical ip of the router (which I have set to static now).

This is the question I saw. Which i interpret as: You need to register your public ip ( [www.whatismyip.com](www.whatismyip.com)) with the naming service.
As far as nameservers go; that should already be set up if you have internet access. That is how searches are resolved. Your ISP provides them or there are public ones free to use. They are in the folder /etc/resolv.conf

---

### Post by JameoPotato on 2008-05-22
I got it guys thanks.
I had to set up the A record to my Dynamic IP and it works.. but if my router reboots I need to change my Virtual Server to the new IP and my A record.

I contacted my ISP and am waiting to see what they say about a static IP address

---

