---
title: "DNS, Apache help"
date: 2009-03-11
forum: Server Platforms
---

### Post by asimons999 on 2009-03-11
Hello Peoples,

We have a domain, lets call it 
```
example.com
```

and want to have client projects to our internal server as subdomains. 
```
client.example.com
```

Thinking I will just pay our hosting company for the external DNS. 

Will a wildcard setup, mean I just add a new apache virtual host for each client.example.com? (Apache ServerName)

Can I then have the ServerAlias as
```
client.local
```

Then just add one zone to bind9 dns, and setup our work stations to have a secondary dns of the local server (or will I need to setup forwards to our ISP's dns, and have it as the only dns)?

I've been playing around with all this, and in my journeys 
[LIST]
[*]restarting bind9 says a denied 127.0.0.1 [fail] message, but forwards were working
[/LIST]

I'm probably being a bit general, I apologise, but will get more specific soon and be using this thread. 

Cheers for any help,

Ash

---

### Post by hyper_ch on 2009-03-11
I don't quite understand (a) what your current setup is with regard to example.com sub.example.com, what your network looks like and (b) where the actual problem is. can you be more specific what the current setup is and what you want to achieve?

---

### Post by internalkernel on 2009-03-11
I agree... with hyper_ch, a little more info on your current situation is needed. At first it sounded like you were running your sub-domains on one machine, and towards the end it sounds like you want the sub-domains to point to individual machines on a local network. 

In either case, you will want bind to point to your main domain.com that is running apache. If your ISP is already doing this for you, then all you have to do is configure virtual hosts in Apache... if this is all running on one machine. 

If you are trying to forward to machines inside a network, then setup your redirects in Apache to the host computer and apply forwarding rules in your firewall to direct traffic to the appropriate machine. I'd have to say that this method is going to be a headache... you might be better off centralizing the data on one machine and sharing it via nfs or even samba. Still not an ideal situation...  

Hope that makes some amount of sense... ;)

---

### Post by asimons999 on 2009-03-11
yeah sorry guys.

It's just one web server on our internal network. 

But I want to let our web hosting company do the external dns (client.example.com) and have an internal dns / domain for the local ip address (client.local) on the same machine.

Do I add a virtual host for both, or just put the ServerName (in the Apache Virtual Host) as client.example.com, and the ServerAlias as client.local?

And was asking whether all I needed to do was add a virtual host for each client (client1.example.com, client2.example.com etc)? (in relation, to the outside world and having our hosting provider do the DNS)

**Our network, is basically just**

router->gigabit switch->all the computers on the network

---

### Post by hyper_ch on 2009-03-12
well, on your ISP just make one entry that goes to your public IP.

Internally use the server as DNS server, then the domain can be local host and then make all clients use that DNS server

---

### Post by asimons999 on 2009-03-12
> **hyper_ch said:**
> well, on your ISP just make one entry that goes to your public IP.

Internally use the server as DNS server, then the domain can be local host and then make all clients use that DNS server

is all I have to do then (for the outside world) to add a virtual host for each project? (with ServerName client.example.com)

---

### Post by BkkBonanza on 2009-03-13
yes, that will work. on your external dns server you can use *.example.com to point all subdomains to your server (public ip) or you can enter each one (more work). If you use * then be aware that any subdomains not configed as a virtual host in httpd.conf will go to the default website for your server. Usually that is the first one in httpd.conf if I recall.

---

### Post by asimons999 on 2009-03-13
> **BkkBonaza said:**
> yes, that will work. on your external dns server you can use *.example.com to point all subdomains to your server (public ip) or you can enter each one (more work). If you use * then be aware that any subdomains not configed as a virtual host in httpd.conf will go to the default website for your server. Usually that is the first one in httpd.conf if I recall.

yeah I think I'll change the root of the Default virtual host to /var/www/default instead of /var/www

---

### Post by asimons999 on 2009-03-19
I soughta got this all working some what, and are writing a bash script to add new projects. 

Except I'm adding two virtual hosts and a dns entry for every website. Can I have on the bind9 side of things, something to point all subdomains of .localdev to our server? So I don't have to add a zone and config for each project?

---

