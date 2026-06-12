---
title: "DNS issues? New to setting up servers"
date: 2007-09-17
forum: Server Platforms
---

### Post by reddeth on 2007-09-17
Ok, I"m not sure exactly how to describe whats happening and I'm a bit new to setting up servers so I'll do my best. I'm following a guide ([www.linuxhomenetworking.com](www.linuxhomenetworking.com)) and in all honesty doing pretty good setting up the software side, however I keep running into one issue, I cannot for the life of me figure out how/what I'm to do to get my domain name to point to the webserver.

My networking: Internet goes into a DSL modem, modem goes into a netgear switch, Ubuntu server is located behind the switch

My domain setup: I purchased a domain through godaddy, and set DNS to point to my routers external address.

My problem is if I type in the domain into Firefox I keep getting my routers webpage! I setup port forwarding to forward all traffic incoming from port 80 to forward to the linux box, but even when I type in "<domain>.com:80" it still takes me to my routers web config page.

From reading various guides (and the one I linked to), they all mention that I need to install a DNS server on my box, however I was under the impression that if the web traffic can't even get to my box a DNS server won't do any good...? If a DNS server is what I need to install can anyone please give me a semi-noob-freindly guide to setting one up? I've been trying to wrap my brain around the entire DNS process and doing a poor job.

Thanks very much!

---

### Post by gombadi on 2007-09-17
At a guess if you are using another machine connected to the netgear switch.

When you type in the domain name firefox will do a dns lookup and be given your public ip address. Lets say it is 1.2.3.4

It will then send packets to 1.2.3.4. They will leave your machine go via the netgear switch and arrive at the router heading for the Internet. The router will say that "Hey 1.2.3.4 is one of my addresses" so will connect you to its web page.

Lets say that your linux server has an ip of 9.8.7.6

What you need to do is set your view of the domain name to point to 9.8.7.6 (not the worlds view)

On the machine you are running firefox you need to tell it that your domain is at 9.8.7.6
If it is linux then as root add this to /etc/hosts
9.8.7.6 [www.mydomainname.com](www.mydomainname.com)

That will tell your machine and only your machine that it needs to go to 9.8.7.6 for your domain while the rest of the world will be told to go to 1.2.3.4 (your public ip address)

or I could be completely wrong :)

Now I must run off to work...

---

### Post by reddeth on 2007-09-17
Well, I understand what you are saying about trying to talk to the webserver running off the same switch. I am now sitting at home (the server is at work) and can access the site (although I keep getting Apaches placeholder page even though I edited the httpd.conf file...), so my assumption is that it works haha.

Thanks much for your help, there may not have been a problem to begin with but at least I understand what was going on.

<edit>
Ok, rather than start a new thread I figured I'd just ask real quick in here:
The website pages are stored in "/home/www/reddeth" (so the index page is /home/www/reddeth/index.html)

In the httpd.conf file I have:
<VirtualHost (server ip)>
        DocumentRoot /home/www/reddeth
        servername [www.reddeth.com](www.reddeth.com)
</VirtualHost>

But I still get a "404 page not found" error, I'm assume I didn't type something in right on the httpd.conf file?

---

