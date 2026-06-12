---
title: "Running your own nameservers"
date: 2010-02-11
forum: Server Platforms
---

### Post by pascallj on 2010-02-11
Hello everybody,

I'm running my own webserver at home. I've also bought a domain (it's .nl because I'm Dutch). But now I need to change the nameservers from my domain.

I've read a lot of things about running your own authoritative nameserver and things like that. I also experimented with bind9 but I can't get it.

So, I've got a Webserver running Ubuntu Server. I've bought a domain. Nothing more and nothing less. So is it possible to run a nameserver or something else to get it work in this situation?

I hope you guys can tell me.


Greetz,
Pascal

p.s. Maybe you've noticed that my English isn't very good. That's because I'm Dutch and still learning. I hope I've explained the problem clear enough.

---

### Post by jonrich on 2010-02-11
You want to run a public webserver from home?

You will need DDNS ( dynamic DNS ) or better, a static IP at home
Update your DNS where you purchased the domain name.
* if you have a static IP, change the A record to your home IP
* if you use DDNS update the domain nameservers with your DDNS providers nameservers

I have a public server at home, I use DDNS and it works pretty good.  Wish my DSL was faster.

---

### Post by pascallj on 2010-02-12
Yes of course I've a static IP. But I can't set DNS settings on the place where I bought my domain. Just the nameservers. Not more nothing less.

---

### Post by Porter200el on 2010-02-12
> **pascallj said:**
> Yes of course I've a static IP. But I can't set DNS settings on the place where I bought my domain. Just the nameservers. Not more nothing less.

You want to use a dynamic DNS client, like Zone edit or dyndns, they will host your nameservers for free and it is worth it, running your own nameservers can be a disaster if you don't have redundancy built in. Probably the best senario is for you to do the following:

1.  Register with dynamic dns
2. Set your static IP as your A record host with the dynamic dns service
3. Set your firewall to allow traffic to your ubuntu web server (port 80)
4. Make sure your ubuntu web server has a static ip (locally)
5.  Set up google mail for your domain name, you can set the mx and cname records with your dynamic dns provider as well


This way your site is hosted at your house and google will host your mail for free.  Just my opinion, but I have done this for about a ton of people and it works very well.

---

### Post by pascallj on 2010-02-12
I registrered on DynDNS but it isn't free? It costs 30 dollar for each year? Or do I something wrong?

---

### Post by Porter200el on 2010-02-12
> **pascallj said:**
> I registrered on DynDNS but it isn't free? It costs 30 dollar for each year? Or do I something wrong?

You might have signed up for a premium service, Zone Edit is free as well.

---

### Post by pascallj on 2010-02-12
Thanks, Zone Edit looks great. The site is not proffesional looking, but if does what it needs to do it's fine ;). I configured everything and also the nameservers by my registrar so now let's wait until they will update them.

Thanks for getting me there.

---

### Post by john-boy on 2010-02-12
That's some interesting information there. I have wondered about doing a similar thing myself a few times but have never followed it up. I'd be interested in knowing how things work out and whether DynDNS is any good.

---

### Post by Porter200el on 2010-02-12
> **pascallj said:**
> Thanks, Zone Edit looks great. The site is not proffesional looking, but if does what it needs to do it's fine ;). I configured everything and also the nameservers by my registrar so now let's wait until they will update them.

Thanks for getting me there.

No Problem, Zone Edit is no frills, but it works and works well.  The nice thing is Zone Edit propagation time is only 15 minutes, that is a huge plus!   I am always happy to help.  :)

---

### Post by Porter200el on 2010-02-12
> **john-boy said:**
> That's some interesting information there. I have wondered about doing a similar thing myself a few times but have never followed it up. I'd be interested in knowing how things work out and whether DynDNS is any good.


DynDNS is ok, I prefer Zone Edit, both will work but I prefer ZE for the quick prorogation time and the ease of use.  Let me know if you have any questions I can answer.

---

### Post by jfparis on 2010-02-14
Two things you might want to have a look at

Option 1
I believe xname.org can provide you with the service you are looking for

Option 2 ( it might be overkill)
Run you own DNS on your server (you might want to look at bind)
You might need to register a backup name server (that will mirror your own)
xname.org can also provide the mirror service

For more info on running your own dns server
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

jf

---

