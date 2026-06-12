---
title: "DNS public IP resolution?(If I got the term right) IS IT POSSIBLE?"
date: 2007-04-06
forum: Server Platforms
---

### Post by groovdafied on 2007-04-06
I'm wanting to build a family web based server so we can have a personalized family center and what not.

So my question is; is it possible to use linux to host my own dot com? Not a web host for the site files and pictures, I'm talking about the actual dot com like [www.family.com](www.family.com), so when I type that dot com, it'll rout it to my public IP, then to my server.

I know there are DNS services out there like dyndns and no-ip.com. However I'm curious if it's possible to create your own web domain.

I appreciate any information you may have, thanks!

---

### Post by sharke on 2007-04-06
take a look here [http://www.register.com/retail/index.rcmx?SEMGoogle=Google&LID=36004175](http://www.register.com/retail/index.rcmx?SEMGoogle=Google&LID=36004175)

Regards
Sharke

---

### Post by PilotJLR on 2007-04-06
You can absolutely do this, you just need to buy a domain name.

Personally, I buy the domain name only from yahoo (it's something like $20 or less per YEAR). The plan I use obviously doesn't include hosting, which i don't want.
The yahoo controlled domain name point to my free dyndns.org account, since I have a dynamic IP. This is all transparent to the user, and works great!

---

### Post by groovdafied on 2007-04-07
So there's no way to create a web based DNS server without having to pay a registrar?

---

### Post by Nikron on 2007-04-07
> **groovdafied said:**
> So there's no way to create a web based DNS server without having to pay a registrar?

Oh come on, it's like 8-9 bucks per year.  You don't even need to set up a home DNS server, there's plenty of free ones, like zoneedit.com  Or you can you get a dyndns account, but that'll be like family.dyndns.org  It's easy to set up a webserver

---

### Post by groovdafied on 2007-04-07
> **Nikron said:**
> Oh come on, it's like 8-9 bucks per year.  You don't even need to set up a home DNS server, there's plenty of free ones, like zoneedit.com  Or you can you get a dyndns account, but that'll be like family.dyndns.org  It's easy to set up a webserver

I'm not trying to be cheap, I'm doing this out of experience.

---

### Post by MrHorus on 2007-04-08
> **groovdafied said:**
> So there's no way to create a web based DNS server without having to pay a registrar?

What do you mean by that?

If you mean run your own web server and your own DNS then yes, just install and configure BIND and Apache.

---

### Post by r00tintheb0x on 2007-04-08
groovdafied having worked in the past for any hosting providers, the only thing you have to come out of pocket for is your domain name. DNS APACHE MAIL and everything else, you can set up yourself and run from your own server.

---

### Post by jaheds on 2007-04-08
To register a domain with most TLDs (.com, .net, ...) you need to pay the minimal ($10 a year) fee to register that domain.

The rest of the process, however, you can do for free using your Linux.

When you register a domain, it will need to have a DNS entry assigned to it.  This is the IP of the machine that will decide HOW to resolve hits to your domain name (not the same thing as hosting, of course).  So it looks like this:

(1) Domain name --> (2) DNS hosts --> (3) Final host

In summary, you need to pay for (1).

You can make your server do (2), but there is an ICANN registration process involved, and it might cost money... or 

You can do (2) for free, using one of several free DNS services out there that let you do nearly everything you could with your own DNS host.  ZoneEdit ([http://www.zoneedit.com](http://www.zoneedit.com)) is the one I use. Once you tell zoneedit about your domain, it'll provide you with the IP/host-name that your domain needs to point it's DNS entries to.  You set this up in your domain control panel (with the company you registered with)

And you can do (3) without paying using your own Linux box.  That's the easy part.  That'll be the web-server, mail-server, etc. part

So at the end, that process is indeed "hosting your own dot com"

---

### Post by larrybrazos on 2007-04-09
i had all this setup, isp blocks port 80, so i used 8080 and could access the server from WANIP:8080.  i went to godaddy and pointed my domain to my WANIP.  but i got stuck on the very last step.

how can i get my registered domain name hosted at godaddy to resolve to my server that has port 8080 open?  i tried pointing my domain at godaddy to WANIP:8080, but you can only point it to an ip, not an ip and a designated port.

so current status is . . .

1. web server running apache and listening to port 8080.
2. server is running properly and can be accessed from outside the network at WANIP:8080

---

### Post by larrybrazos on 2007-04-09
no-ip.org offers a service to route 80 requests to 8080, so problem solved, now i just have to figure out how to get my godaddy domain to point to the domain i registered at no-ip.org

---

### Post by larrybrazos on 2007-04-09
does a forward from godaddy's control panel to my no-ip.org domain with a mask to keep the godaddy domain name shown in the address bar sound right?

---

### Post by jaheds on 2007-04-11
> **larrybrazos said:**
> does a forward from godaddy's control panel to my no-ip.org domain with a mask to keep the godaddy domain name shown in the address bar sound right?
I think that depends on how no-ip.org and godaddy domain-manager works

I don't know what the term "forward" means.  On a DNS level, forward usually refers to CNAME.  Sometimes, there are other "forwarding" services, such as HTTP redirects, I wouldn't use those.

Let me just explain a few things about how this works:

When you request a web-site from some-domain.com this happens:

First some-domain.com is resolved to an IP (say 1.2.3.4).  Then your web-browser tries to connect to port 80 of that IP.  It's important to note that the IP some-domain.com resolves to is completely independent of the port we're trying to connect to.

So how no-ip.org probably works is that they make a certain domain (say, some-name.no-ip.org) resolve to THEIR OWN IP (not yours) which points to a no-ip.org server which takes requests on port 80 and proxies them based on the HTTP host-name request to your IP.

So, if you're going to use your domain-name for things other than HTTP web-services, and your port 80 is blocked, your best option would be to manage your DNS so that the sub-domain "www" (e.g. [www.your-domain.com](www.your-domain.com)) resolves to the no-ip.org http proxy service (if no-ip.org allows it) and some other subdomain (server.your-domain.com) resolves to YOUR IP.

[www.your-domain.com](www.your-domain.com) --> no-ip.org's proxy IP
server.your-domain.com --> your IP

That way, you can still use your other services (ftp, ssh, pop, etc.) on the domain server.your-domain.com and still use the no-ip.org port 80 service on [www.your-domain.com](www.your-domain.com)

I know this sounds a bit confusing.

---

### Post by shubjero on 2007-04-11
Wow sir it is rather unwise to run all this off your home connection.  First of all it appears that you are running in to a couple issues where your ISP has put measures in place to prevent people such as yourself hosting a domain and servers from home.  I'm pretty sure you are violating your TOS with your ISP but that's up to you to worry about, or not.

Since you said you are doing this for the experience, and not to be cheap, I think you would find that you would gain more experience if you were to have a dedicated server stored in colocation somewhere (in a datacentre) with the appropriate facilities for redundancy and so on.

But whatever, it's up to you.  Best of luck!

---

### Post by larrybrazos on 2007-04-11
thanks for the response man.  yeah, the status now is . . .

my server is accesible at kdoggett.no-ip.com.

at no-ip.com i registered a hostname (kdoggett.no-ip.com) and used "host type" "Port 80 Redirect".  the hostname points to my wanip:8080.  also added a mask so it would show the hostname and not wanip:8080.

i added ServerName kdoggett.no-ip.com to my apache2.conf file.

i tried to use a forward from my godaddy domain "kdoggett.com" with a mask to "kdoggett.no-ip.com" but that didn't work.  but i am not so concerned with that atm.

---

### Post by larrybrazos on 2007-04-11
"thanks for the response" was for jaheds.

to shubjero . . .

it is all for learning purposes.  if anyone is thinking of running a server that people will actually come to, a webhost is probably your best bet

---

