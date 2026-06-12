---
title: "Being hit by DDoS attacks daily - please help"
date: 2013-05-17
forum: Security
---

### Post by bunglehaze on 2013-05-17
Hi guys, I run a small web business with a private server that is getting hit every day at the moment with timescales ranging from a couple of hours on the first occasion to five minutes yesterday and unsure about today because the server has been removed from the network port so the DC can recover. I have checked for DNS resursion and fixed any issues I found, looked for other obvious security issues, installed and configured UFW, mod evasive and dos deflate in an attempt to mitigate any problems.

SSH is on a non standard port and root user is disabled, essentially I am doing everything my end that I can think of to remove the threat but now I am tearing my hair out - my client sites being down is not good at all and I am hoping one of you can offer some guidance on what, how and perhaps even why these attacks are happening and how to get away from them.

All the sites on the server are Joomla as far as I know, with the xception of one that I am currently upgrading they are all on the latest version and I don't believe that should attract attacks anyway.

Fail2ban is employed also on the server for brute force security

The server is on Ubuntu 12.04, all packages up to date and Virtualmin as the interface, again all up to date. It would seem that on each attack they datacentre is struggling with it and it is affecting their other clients which is the reason why I currently cannot get in to check if how and where they are coming from. Could you suggest which logs I need to be going through or anything in particular to look at to locate either the source of the attack if it is aimed at a particular website or how to view the source on the traffic please - any help here is massively appreciated as I need to get this all under control ASAP otherwise I may be asked to take the server from the datacentre which is problematic.

When I noticed the first slowdown I checked:

netstat -an|grep ESTABLISHED|awk '{print $5}'|awk -F: '{print $1}'|sort|uniq -c|awk '{ printf("%s\t%s\t",$2,$1); for (i = 0; i < $1; i++) {printf("*")}; print ""}'

and there were not masses of connections showing. I checked the IP address for my ESM during the attack and that was operating normally until the DC was swamped so it is obviously going to the main server IP.

regards

---

### Post by miegiel on 2013-05-17
Just to make sure DC means data-center and not domain-controller, right?

In any case it's not reasonable that you are expected to mitigate a ddos attack on your server. In my (not so humble) opinion, that is something your data-center should do for you. Mitigating a real ddos requires specialized dedicated hardware, hardware your data-center should have.

That said, don't use UFW, but write the iptables rules yourself. UFW is just a program that makes it easy to create the rules, writing the rules yourself makes the firewall more efficient and effective (if you do it right). However AFAIK you can't really mitigate ddoses with iptables, just make them a little less severe. Also, if your client only serves national clients, try blocking all traffic coming from abroad _temporarily_. It's very crude, but can drastically diminish the effectiveness of the attack.

On the investigative side, regarding the method, try to figure out how you're getting attacked. There are many different types of ddoses and each needs to be dealt with differently. And regarding the motive, try to find out if it's you that's the target, or (one of) your client(s), or the software you are running.

---

### Post by linuxtechguy on 2013-05-17
If you cannot afford real ddos protection, I would suggest trying a more advanced firewall like [http://configserver.com/cp/csf.html](http://configserver.com/cp/csf.html)

If you have the money to spend there are alot of companies that provide good ddos filtering.

Not all datacenters have the proper equipment or bandwidth to deal with attacks.

---

### Post by miegiel on 2013-05-17
> **linuxtechguy said:**
> If you cannot afford real ddos protection, I would suggest trying a more advanced firewall like [http://configserver.com/cp/csf.html](http://configserver.com/cp/csf.html)

If you have the money to spend there are alot of companies that provide good ddos filtering.
On first glance it looks like they just use iptables with extras. Besides, packet inspection is illegal in some jurisdictions.
> Not all datacenters have the proper equipment or bandwidth to deal with attacks.
That would be a valid reason to migrate to a different data-center.

---

### Post by bunglehaze on 2013-05-17
Hi guys, thanks for the replies.

Firstly, yes DC was just my abbreviation for DataCentre.

miegiel, I agree that I should not have to mitigate a DDoS attack as much as I feel like I should be doing, I did think that the DC would be able to filter this kind of thing a little bit better but obviously I am trying everything I can to make sure I am no OPEN to attack as such. This is the reason I installed UFW as actually iptables was in use anyway but I wanted something a little easier to put into place initially, also with mod evasive and dos deflate in place with fail2ban i would have thought that my end was about as protected as it could be without going over the top and locking out everything.

Unfortunately being small means I cannot afford the prices of big company ddos protection and the size of my clients are similar too.

What logs should I look into when i first get the server back up again that will give me an indication of the scale and type of attack and perhaps give me an angle to look at and discuss with the guys at the DC to help filter out traffic. Could something as simple as website spam be attracting this kind of attack too? I have noticed that on one of the client sites they were getting a lot of spam user registrations in the days leading up to the first attack but this is quite normal for a site that is at the top of Google and I thought little of it other than to tighten up the registration process which stopped them.

I am just spitballing here too as I don't think this will be anything but I have a virtual IP interface on my server that has not been linked up to the client virtual server as yet. Something like this wouldn't attract attention would it?

Finally, any good tools you could recommend to assist in finding the target on the server?

regards

---

### Post by CharlesA on 2013-05-17
> **miegiel said:**
> In any case it's not reasonable that you are expected to mitigate a ddos attack on your server. In my (not so humble) opinion, that is something your data-center should do for you. Mitigating a real ddos requires specialized dedicated hardware, hardware your data-center should have.

Agreed. My VPS provider has specfic DDoS protection, but it is pricy. I just use iptables to keep my logs clear of SSH attacks, but so far the only thing I've noticed in the logs on my box is port scans and attempts to use exploits.

> That said, don't use UFW, but write the iptables rules yourself. UFW is just a program that makes it easy to create the rules, writing the rules yourself makes the firewall more efficient and effective (if you do it right). However AFAIK you can't really mitigate ddoses with iptables, just make them a little less severe. Also, if your client only serves national clients, try blocking all traffic coming from abroad _temporarily_. It's very crude, but can drastically diminish the effectiveness of the attack.

I don't think you can totally mitigate a DDoS with iptables because it can still overload the machine (depends on the severity of the attack), but it can help to see how you are being attacked, especially if logging in enabled. If you are getting hit by a DDoS attack, it is a good idea to let to provider know so they can take action against it.


> **miegiel said:**
> That would be a valid reason to migrate to a different data-center.

I would tend to agree. @OP: Who is your provider, if you don't mind me asking?

---

### Post by sandyd on 2013-05-17
Packet filtering at the OS level is easily made useless these days
All the attacker has to do is to fill up your network port (most servers are 100mbps, while some are 1Gib/s while others are 10+Gib/s), and your done for. Its why most filtering is done upstream.

The best way (with the least work) is to get a DDOS protection proxy such as JavaPipe, Gigenet. Otherwise, you probaby want to get a server from a datacenter that specializes in DDOS migration such as Staminus (there are some cheaper plans at WebHostingTalk starting at ~$60, just search Staminus), or Black Lotus.
Cloudflare also migrates DDOS attacks, but I dont trust them.

I would probably try enabling cloudflare first, let them hammer cloudflare for a while and see if the situation improves

Of course, if they already know your public server ip, cloudflare is useless...

---

### Post by sandyd on 2013-05-17
Packet filtering at the OS level is easily made useless these days
All the attacker has to do is to fill up your network port (most servers are 100mbps, while some are 1Gib/s while others are 10+Gib/s), and your done for. Its why most filtering is done upstream.

The best way (with the least work) is to get a DDOS protection proxy such as JavaPipe, Gigenet. Otherwise, you probaby want to get a server from a datacenter that specializes in DDOS migration such as Staminus (there are some cheaper plans at WebHostingTalk, just search Staminus), or Black Lotus.

Cloudflare also migrates DDOS attacks, but I dont trust them.

---

### Post by bunglehaze on 2013-05-17
> I would tend to agree. @OP: Who is your provider, if you don't mind me asking?

It is a local Tier2 Datacentre - Sheffield Data Centre

>  I don't think you can totally mitigate a DDoS with iptables because it can still overload the machine (depends on the severity of the attack), but it can help to see how you are being attacked, especially if logging in enabled. If you are getting hit by a DDoS attack, it is a good idea to let to provider know so they can take action against it.

Fortunately I have logging enabled so hopefully it may shed some light on things when I get access again.

With the size of my company only being small and the size of the websites only being similar I cannot see any benefit or huge target for a large scale attack, it is confusing me how big a ddos attack would have to be to be affecting the datacentres other clients and network as it currently is doing. They have not been able to tell me much about the attacks in general either so far.

---

### Post by bunglehaze on 2013-05-18
Well it would appear that I am going to be asked to remove the server from the datacentre, I partially understand it from the standpoint of protecting their other clients but i really do not understand how a small server with no noxious or contentious content on any of the small local businesses I host would attract an attack big enough to cause an issue to affect the whole subnet.

So the options available to me currently seem to be diminishing fast. What is the normal procedure in this situation? I do not have another datacentre nearby in which to transfer the server and I guess the only option is to move my clients all of to another provider.

Really, really unhappy today.

---

### Post by CharlesA on 2013-05-18
Have you talked to the provider? It could be that someone is attacking them instead of you. They should know how to deal with a DDoS attack if that is what you are experiencing. If it is this bad, I would definitely look into switching providers, but it would be a good idea to talk to the current provider first to see what their thoughts are.

Are you hosting a dedicated server, or VPS there?

EDIT: Have a read of [this article]("http://www.networkworld.com/newsletters/techexec/2013/101113bestpractices.html"), it might not be the best one, but you will definitely need to handle this if it is a DDoS attack.

---

### Post by sandyd on 2013-05-18
> **bunglehaze said:**
> Well it would appear that I am going to be asked to remove the server from the datacentre, I partially understand it from the standpoint of protecting their other clients but i really do not understand how a small server with no noxious or contentious content on any of the small local businesses I host would attract an attack big enough to cause an issue to affect the whole subnet.

So the options available to me currently seem to be diminishing fast. What is the normal procedure in this situation? I do not have another datacentre nearby in which to transfer the server and I guess the only option is to move my clients all of to another provider.

Really, really unhappy today.

Right now, start with adding the free version of cloudflare to your site. Cloudflare will at least block the DDOS attacks.

---

### Post by bunglehaze on 2013-05-20
Hi guys, a quick update:

The datacentre sent the information upstream and had the server IP blocked and have said they are going to move me to another subnet away from other clients which will make it easier for them to traffic manage if it restarts so in the meantime although I have had a weekend of downtime I am not totally dead in the water as yet. The server is my own box housed in their facility and not a rented unit or VPS, I don't rent racks worth, just a single 1u rack so in terms of financial gain for them vs risk I can see this has caused a lot of work - perhaps though it has highlighted to them where their own network could be susceptible though as an attack could be directed at any of their clients.

I had been looking at the likes of Cloudflare free but was under the impression that the free service sisnt do anything to mitigate DDoS, however if it is the case that it does I will set each client site up with the free service once I am back online and obviously my main priority is to see if I can find the target on the server or if it was directed at the server IP in general. If there is a specific target or application it will need to be dealt with to stop the same happening again.

Over the weekend I did a lot more reading and saw that older versions of Joomla have been targeted by people, I know of at least one client still using an outdated version so will need to keep that one offline in the first instance while I see if it could be the cause - would mod security help in this type of instance though? I do not want to be adding tons of modules if they are just going to be eating resources although the server is vastly overpowered for the resources I need anyway (ironically to try and keep a good service level and uptime)

regards

---

### Post by CharlesA on 2013-05-20
Why not suggest they update Joomla to the latest version? Running outdated software on a server exposed to the internet is a very bad idea.

I don't know if the free version of cloudflare handles DDoS, but you can always contact them and ask.
[https://www.cloudflare.com/plans](https://www.cloudflare.com/plans)

EDIT: Here you go:
[https://support.cloudflare.com/entries/23664767-Does-CloudFlare-offer-DDoS-protection-to-free-and-Pro-plans-](https://support.cloudflare.com/entries/23664767-Does-CloudFlare-offer-DDoS-protection-to-free-and-Pro-plans-)

---

### Post by bunglehaze on 2013-05-20
Charles, one of the sites running and old joomla is actually mid process of being migrated anyway, I was working on it as the DDoS occured, although the site is not 100% finished it is in a position where I can switch off the old site and work on it live so that is fine, the other that is possibly out of date is just going to be left offline unless they want me to upgrade it as I have warned them twice that they are using out of date software.

The datacentre got back to me just now and confirmed that they tested a new approach yesterday in a lab environment and are happy with how it works in theory so they will push me on to it this afternoon or tomorrow so we can see how it goes full time. They have actually been quite reassuring that the idea may help them mitigate DDoS attacks in future and it would seem it may help them for other customers if something similar happens, it is an approach they wanted to put in place in the past but never had a need so I guess my attack has helped in some way to realise their action needed looking at.

So now it is a case of waiting for them to call and let me know I have to ride over and change the IP address on the physical machine and with any luck it will work and stay up.

regards

Leigh

---

### Post by CharlesA on 2013-05-20
Well, that's good news then. Hopefully whatever they are working on will help mitigate the attack.

---

