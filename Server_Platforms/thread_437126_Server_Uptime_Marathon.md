---
title: "Server Uptime Marathon"
date: 2007-05-08
forum: Server Platforms
---

### Post by kabronkline on 2007-05-08
I have a coworker who runs Ubuntu 6.06 for remote shell access (for tunneling ect.) and he sent me a screenshot of his console, take a look for yourself:

[http://i11.tinypic.com/4mtrgvq.jpg](http://i11.tinypic.com/4mtrgvq.jpg)

130 days, 57 minutes. I will post an update after a while, hopefully he can make it to a year.

---

### Post by kosmic on 2007-05-08
I have a FreeBsd system that is running for almost 1 year without reboot ;) it's pretty common in the *nix World

---

### Post by mwerlberger on 2007-05-09
Today my servers current uptime: 200 days. So sort or birthday? ----paaarteeiiii---- :popcorn:

But uptimes of > 1 year are quite normal in the *nix world as already mentioned. The only 'problems' that can occur are kernel updates ;-).

Rgds,
 Manuel

---

### Post by StarMonkee on 2007-05-09
My current best is a mail server running debian sarge (i want to update but dont want to lose the uptime)

kris@pingu ~ $ w
 10:00:32 up 488 days, 55 min,  2 users,  load average: 0.38, 0.20, 0.15

---

### Post by kabronkline on 2007-05-09
488 days, impressive. I find it incredibly cool how long *nix boxes can run without a reboot (compared to Windows servers needing rebooted at least once a month).

This very fact alone says a lot in the great Nix Vs. Windows debate IMHO.

---

### Post by rickyjones on 2007-05-09
My monitoring server at my church runs Ubuntu 6.06 I do believe, and it's latest uptime was 90 days before rebooting. I had to shut it down to throw it on a UPS :P. My domain controller can get as much uptime as I want it to - but generally it gets a reboot on patch Tuesday if the patches require it. If they don't... well, then, it'll stay up until the updates ask it to.

-Richard

---

### Post by StarMonkee on 2007-05-09
I'm happy with my 488 days, and all my coworkers are under strict instructions to never reboot that machine :D

It's running 2.6.8 I think, and I'd love to update it to etch, but I don't want to reboot! It was only rebooted to put a UPS in, and I think the uptime was around 100 days before I rebooted it.

---

### Post by MJN on 2007-05-09
How do you manage with kernel security updates?

Mathew

---

### Post by StarMonkee on 2007-05-10
The simple answer is I don't!

Most kernel exploits are things which allow local users to gain root privileges, and I trust all of the local users (they work within 6 feet of me). The server is sitting behind a netscreen firewall and the only open port is 25 (to receive mail, and there are some strict postfix relaying rules). Everything else is done internally to our network (pop/imap/ssh/http/mysql) by users who wouldn't know what linux is, let alone be able to cause problems.

---

### Post by MJN on 2007-05-10
> **StarMonkee said:**
> The simple answer is I don't!

My simple response would be 'then you should'!

> Most kernel exploits are things which allow local users to gain root privilegesMost? Who told you that? Even if this is the case most != all.

The last two updates, for example, were related to NFS and iptables and had nothing to do with local users (or their privileges). DOS was the potential result of both.

Now don't tell me you don't use NFS or iptables - that's besides the point as they were just the two recent examples.

> Everything else is done internally to our network (pop/imap/ssh/http/mysql) by users who wouldn't know what linux is, let alone be able to cause problemsThat is, to put it bluntly, naive beyond belief.

Lagging on security for the purposes of an uptime record is absurd - you'd be marched off the premises where I work!

Mathew

---

### Post by molnarcs on 2007-05-10
> **MJN said:**
> My simple response would be 'then you should'!

Most? Who told you that? Even if this is the case most != all.

The last two updates, for example, were related to NFS and iptables and had nothing to do with local users (or their privileges). DOS was the potential result of both.

Now don't tell me you don't use NFS or iptables - that's besides the point as they were just the two recent examples.

That is, to put it bluntly, naive beyond belief.

Lagging on security for the purposes of an uptime record is absurd - you'd be marched off the premises where I work!

Mathew


I agree with your last statement ("lagging on security fot the purposes of an uptime record is absurd") - but still, if one carefully reviews each security bulletin, and finds them irrelevant, than yes, one can go on without needing to update. I understand that NFS or iptables were just the latest examples, but still, it is possible that none of the security issues affects you for a very long time. I had a FreeBSD server running for a year without reboot, because simply none of the kernel related security issues affected this particular setup (even though it served both as a firewall, and www/ftp server directly connected to the net). 

Granted, I don't know how linux fares in this department, but I assume that is not that different from FreeBSD, and if you have exactly what you need without any cruft (yes, no NFS if you don't use it - not even kernel support for NFS, no IPv6 if you don't use it, nothing that you don't actually need) - than I'd say that it is even better practice NOT to apply completely unrelated security updates without thinking if you have a setup that works. What matters is to subcribe to the security mailing list (or whatever gives you prompt notifications about security issues) - and read each bulletin.

---

### Post by MJN on 2007-05-10
Agreed, but I'd be willing to bet a copy of Windows Vista that Starmonkee isn't reviewing the bulletins and determining whether or not his/her kernel is indeed vulnerable - this is based on the assumption that this would've been given as the fundamental, if not sole, reason for keeping it at the same version.

Mathew

---

### Post by StarMonkee on 2007-05-10
I'm not completely up to date on all possible kernel vulnerabilities, but I do check up on major ones. I don't recompile kernels every time a new one is out - I usually wait until my distro releases an update.

No, I'm not using NFS or iptables.

As I said, the server is behind a very good (netscreen 25) firewall, and only one port is accessible from outside. I'm not too worried about internal access because there's no way into the office network without me knowing (I have a private IPSEC VPN). Postfix is configured pretty aggressively, and there have been attack attempts against the server in the past (mainly dodgy teardrop attacks which get stopped by the firewall, and would be useless even if the firewall let them through), nothing has got close to compromising it.

Lucky I don't work for you :) I'm head of IT for one of the top 20 busiest travel websites in the UK (according to hitwise). Even small amounts of downtime would cost thousands, so I do need to make sure things are secure.

But, this is the only server I have (out of around 20) which isn't fully up to date, and yes, it's mainly because I like the uptime - but it's still as up to date as debian sarge ever got, and that was their 'stable' release until last month.

Feel free to prove me wrong by pointing out a vulnerability I've missed, and I'd be happy to see if it affects my server.

Anyway, 489 days now :D

---

### Post by StarMonkee on 2007-05-10
Sorry if that last post is aggressive, that wasn't my intention.

The quick answer is that I don't know of any vulnerabilities in my server which are capable of getting through on the only open port, the hardware firewall keeps everything else tightly locked.

If anyone can point anything out which is serious then I would upgrade it. I know that nothing is 100% secure.

---

### Post by MJN on 2007-05-10
That's alright, no aggression taken.

The bottom line, from my perspective at least, is that security comes before uptime figures - indeed uptime figures don't appear anywhere on my priority list. In the context of service availability, yes, but not simply a figure to impress your mates with. ;)

I fully appreciate that *you*r setup may not necessarily susceptible to every vulnerability that might be found, and as Molnarcs mentioned it's all about applicability and if none of the fixes are required then it can prove wise to not install them out of habit. But this has to be an educated decision and not driven by uptime games.

That said, if this machine cannot be taken down to apply a well tested kernel patch due to your reliance on it then that, if nothing else, shows you *do* have a vulnerability and it's one which no patch is going to solve. As for what other vulnerabilities you might have due to the kernel itself - I don't know the answer to that and unless you're going to pay consultancy fees I'm not going to start searching! ;) Whilst I accept I don't know, do you?

Seriously, the question of vulnerabilities is wider than simply firewalling off the machine - if you're opening access to it through even genuine services then it runs at risk. Managing that risk is more than simply stopping access to the wider world - it's the machines on the *inside* that I'd be concerned about. After all, particularly given the users are unknowledgeable, who knows what vulnerability they might inadvertently exploit? Inside attack is already big enough, and is on the increase given the tightening of exterior gateways.

Horses for courses, but I'm pretty sure the course your travel firm is on is not one looking to top the 'uptime' charts. What would your Head of IT say? Oh... don't answer that one... ;)

Mathew

---

### Post by StarMonkee on 2007-05-10
I agree with all of your points. Our mission critical servers uptimes are a lot lower because of planned updates - I'm not going to risk the company for the sake of uptime.

I admit that there are going to be vulnerabilities - nothing is 100% secure and I dont know all of the possible vulnerabilities in the kernel and services.

I'm not worried at all about local users causing problems. Our IT department is relatively small, and we're all working on the same goals - it wont help any of us to break one of our own servers (the only possible problem I can see is disgruntled ex employees), plus we all have physical access to the server anyway. I'm also confident that there is no way into our network from outside without me being aware of it. The only other users are call centre staff who connect to it through http or imap - I know that none of them have the skills to do anything dangerous.

As the setup on this server is fairly tricky, I do have a clone (updated) server ready to take over the role if anything happens.

Basically, this server has turned into a bit of a "dont reboot it" scenario. As it's not mission critical to the business I'm happy to leave it as is until there's a need to update it. But seriously, if anyone does know of an exploitable flaw then I would be happy to sacrifice the uptime.

---

