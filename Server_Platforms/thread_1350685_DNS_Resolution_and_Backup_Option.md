---
title: "DNS Resolution and Backup Option"
date: 2009-12-09
forum: Server Platforms
---

### Post by fiveironfrnzy08 on 2009-12-09
[LEFT][/LEFT]I'm working on hosting a website from home without a static ip address. I've registered my domain through godaddy.com and will be re-setting up my ubuntu server with ISPconfig 2, or in other words apache, bind, etc...

I set up godaddy.com's DNS to point to my external ip address (which I'm aware will be changing now and then, since it's dynamic) which I've done by altering the A record to my current external ip. 

Since my external ip will be changing, I will do my best to catch when it does so that I can correct it in the A record and get it back up.

Now here's what I need help with...
I'd like to set it up so that when my external ip changes, the DNS knows to redirect to a dynamic DNS service where I will also have my domain set up (but that, being a dynamic DNS, will always have my external ip address current).

So in a short diagram, this is what I'm looking for

mydomain.com -> 
godaddy's DNS -> 
external ip of my home server ->
**mydomain.com** (if external ip is same)

**IF NOT ->**

direct to dynamicDNS ->
_current_ external ip ->
**mydomain.dyndns.com**

---

### Post by munky99999 on 2009-12-09
Ya godaddy actually doesnt support dynamic dns for your names. As they want to sell you their hosting.

My question might be; what is your isp? You might actually get better performance out of getting a cheap vps. zazeen or uk2.net or whatever is closer to your potential viewers.


Anyway. The thing you want is this.

[http://www.everydns.com/](http://www.everydns.com/)

They give you name servers that you can put in for godaddy entry under your nameservers. Then use their dynamic clients to keep them uptodate.

[http://www.everydns.com/dynamic.php](http://www.everydns.com/dynamic.php)


The perl client for ubuntu is needed. Edit the script with your info.

sudo apt-get install libwww-perl libnet-smtpauth-perl libnet-ip-perl libnet-dns-perl

sudo apt-get install gnome-schedule

That schedules how often you want that script to run. That's kinda bleh.


The best option is grab a router capable of doing DDWRT then do this. Cisco ones generally?
[http://www.dd-wrt.com/wiki/index.php/Dynamic_DNS](http://www.dd-wrt.com/wiki/index.php/Dynamic_DNS)

---

### Post by fiveironfrnzy08 on 2009-12-09
Thank you very much for your response!

I'm not quite sure that this is exactly what I'm looking for unfortunately... Maybe it is and I'm just not seeing it yet...

Let me just clarify exactly what I'm looking to accomplish:
1. Host a website from home as independently as possible
2. Primarily, I'd like GoDaddy.com's nameserver to point to my external ip address, though I'm aware that it will change and my website will go down. I want to do it this way so that I can use mydomain.com **instead** of mydomain._[dynamicservice]_.com

Now here is what I'm really looking for how to do.
3. Secondarily, once my external ip changes and GoDaddy.com's name servers can no longer locate my external ip address, and thus my server, I want it at THAT point to redirect to a dynamic DNS service where the website will then be mydomain.[dynamicservice].com.

Does that make it any clearer? Or did you get that already and I'm just misunderstand what the solution is or steps are to achieving this?

Thank you very much for your time and help, it is GREATLY appreciated. I've spent many, many hours trying to get to understand how web servers, domains, and DNSs work...

---

### Post by munky99999 on 2009-12-09
personally I'm perfectly happy with the dyndns free one I use. So never used an actual pay domain.

The setup I suggested I'm pretty sure is actually one that allows you to dynamically update the godaddy one essentially. So it will look to the end-user that you have that domain you purchased.

So basically when they goto your domain. They goto godaddy and godaddy doesnt know so they send the request to the dns servers you specify. Which is the ones that you can dynamically update. So the end result is that you still have that domain working. It's just using that other set of dns servers so you can dynamically update.

I say give it a shot.

---

### Post by fiveironfrnzy08 on 2009-12-09
> **munky99999 said:**
>  So the end result is that you still have that domain working. It's just using that other set of dns servers so you can dynamically update.

I say give it a shot.

So wait, are you saying that this will work without having the dynamic service's domain added to my websites name (mydomain.*ddns*.com)?


UPDATE

Okay, so I got a profile with everyDNS.net. I set up a client to automatically update my ip address.

So on the GoDaddy.com side of things...
The ns records _were_:

Host	Points To	TTL	Actions	
@	ns61.domaincontrol.com	 1 Hour	Informational
@	ns62.domaincontrol.com   1 Hour	Informational

Now, I have changed them to the following, adding the name servers from everyDNS:

Host	Points To	TTL	Actions
@	ns1.everydns.net	 1 Hour	
@	ns2.everydns.net	 1 Hour	
@	ns3.everydns.net	 1 Hour	
@	ns4.everydns.net	 1 Hour	
@	ns61.domaincontrol.com	 1 Hour	Informational
@	ns62.domaincontrol.com   1 Hour	Informational

Is this correct?
Will this setup always end up at mydomain.com?

---

