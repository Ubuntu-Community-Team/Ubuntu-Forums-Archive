---
title: "Ubuntu vs. W2k3 Server"
date: 2005-11-01
forum: Server Platforms
---

### Post by ezahariev on 2005-11-01
Hello,
Can you explain me, why i have choose Ubuntu platform instead of MS W2k3?
I mean what are advantegies of Ubuntu.

---

### Post by Glut on 2005-11-01
It very much depends on your purpose for the server. You may be well served by googleing for windows vs linux comparisons.

---

### Post by blu.gecko on 2005-11-11
by choosing linux you will cut back on cost for microsoft licence agreements.
by choosing linux you will cut back on cost for antivirus 1 year or corp agreements.
by choosing linux, your machine will not be prone to spyware/ and ads sent via port protocols. 

just so you know I have a small ubuntu server running in my garage, samba, ftp and I use 8% of my processor and 65mb of my ram

650mhz processor
512mb  ram

80 gig hd.

much to think about. wouldnt take me long to install linux.........

---

### Post by N8MAN1068 on 2005-11-11
Depends on what you're trying to do.
I use Ubuntu on one of my laptops at work, and also for my home system.
My other(main) laptop is XP Pro. This week I rolled out a Win2k3 SBS server for my company.

Benefits of Ubuntu? Free, don't have to worry as much about virus/malware breakouts, secure by default since users can't install software (search bars, etc), KDE is close enough to the familiar Windows interface, great support community.

Benefits of Windows? Better integration w/ the rest of the world, more/better? COTS applications, better/more support for hardware, a GUI more people are used to, when something breaks, there's almost guaranteed to be someone within 20 minutes who can come help without having to wait for your question to be answered online.

All boils down to what you want to do and how critical support it.
 Small LAN for your home/home office? Ubuntu should suffice. For a corporate environment? Windows.
I've been trying to awhile to incorporate a Debian box to serve Samba+DNS..no joy yet.

---

### Post by JogerNaut on 2005-11-11
[QUOTE=N8MAN1068]
All boils down to what you want to do and how critical support it.[/quote]
I agree. And this is probabl the most important question.

[QUOTE=N8MAN1068]
Small LAN for your home/home office? Ubuntu should suffice. For a corporate environment? Windows.[/QUOTE]
Not necessarily, I know of a lot of corporations that rely on Linux.

---

### Post by irv on 2005-11-11
I heard or read somewhere that 'Burlington Coat Factory' has gone Linux. Desktops and servers. They did this for cost saving reasons I believe.

---

### Post by N8MAN1068 on 2005-11-11
Companies that have Linux servers don't use distros that upgrade every six months.
Not knocking Ubuntu because I love this distro; but I'd be willing to bet that any company that does go to Linux Production will do so buy using IBM+RH4, or Novell+Suse. It's all about the support. Being able to pick up a phone at 0345 and know someone competent is going to be able to help you out w/ some off the wall issue that magically appeared, is priceless.

I know that even though my wife thinks it, I'm just not smart enough to know 'everything' on all platforms.;)

---

### Post by jstrubberg on 2005-11-11
Win2K3 gives you better control over the client machines in your domain.

Linux is much more secure out of the box, less likely to throw problems and cheaper.

Smart corporations make use of both.  If you do a google search, you just used a linux server.  mail a letter, all the sorting was done by a linux box as well.

In my year and a half of working with linux and eight years as a Windows administrator, it has come down to a simple question.  Will the end user need to mainipulate the software on the machine?  If so, it's windows.  If the server is transparent to the end user, Linux.

---

### Post by LordHunter317 on 2005-11-11
[QUOTE=blu.gecko]by choosing linux, your machine will not be prone to spyware/ and ads sent via port protocols. [/quote]Nope, not in the least.


[quote=jstrubberg]Win2K3 gives you better control over the client machines in your domain.

Linux is much more secure out of the box, less likely to throw problems and cheaper.[/quote]Neither of these are true and it's easy to prove both are quite nieve points of view.

---

### Post by N8MAN1068 on 2005-11-11
I don't think it can be dis-proven.
For example, I'd like to find a linux server/app that competes with the WSUS/SMS capabilities of Win2k3.

Security wise, the 2k3 server I just put up...as soon as i turned it on I needed 35+ security updates, a reboot, more update, another reboot, 4 2k3 service packs+reboots.
This ubuntu machine i've got going over here to run DNS needed 7, and those were application updates, not security related. Also, the vast majority of linux updates don't require constant rebooting to apply 'service packs'.

As far as problems w/ hardware..those can be negated w/ linux by supporting companies that put out source for drivers(nividia), and sticking to what is known good. Sure, a SATA raid5 array may be nifty for a MS server, but will that same config work for your linux box?

In reality, you'll never get your straight answer from us. We can give you our views on the pro's and cons. I'm a Sys.Admin/MCP for the past 7 years working w/ NT-2k3, small LANS to large data-centers. Best thing you can do, is get two identical computers, get a 180trail of 2k3, setup both server to do what you need, and test them out.

---

### Post by LordHunter317 on 2005-11-11
[QUOTE=N8MAN1068]For example, I'd like to find a linux server/app that competes with the WSUS/SMS capabilities of Win2k3.[/quote]RHN does, if you pay RedHat enough money.

There are other commerical applications out there, some cross platform.

I'm not aware of any true F/OSS applications that are at feature-parity with SMS or WSUS in terms of OOB functionality, but it is possible to create such things if you desire.

> Security wise, the 2k3 server I just put up...as soon as i turned it on I needed 35+ security updates, a reboot, more update, another reboot, 4 2k3 service packs+reboots.And?  Look at the CERT list for relevant Linux vulnerabilites this year on any distribution of choice.  

The number of patches is reasonably comparable, not that it matters, as that's a terrible metric to measure by anyway.  I care less about number, I care far more about how quickly they're released and how easy they're to apply.  Which is harder to measure but comparable in my experience.  Certainly, NIST has given ALC_FLR.3 to both RHEL and Win2K server, so they feel the experience is comparable when dealing with patches after install.

> Also, the vast majority of linux updates don't require constant rebooting to apply 'service packs'.Yes, but the service affected still has to be stopped, meaning for 100% uptime you still have to have a second box.  It's not relevant.  In a properly setup redundant environment, having to reboot a single box means nothing.

In fact, there are a host of OpenVMS clusters still in operation with 100% uptime, and many common tasks on OpenVMS require a reboot.

Reboots are a terrible red-herring.

> As far as problems w/ hardware..those can be negated w/ linux by supporting companies that put out source for drivers(nividia),NVIDIA hasn't released source, never has, and never will.  They cannnot, and AFAIK, they have no intention of ever changing the IP-sharing relationships they have that forbid them.

> Sure, a SATA raid5 array may be nifty for a MS server, but will that same config work for your linux box?Yes, LSI makes several products that work perfectly, with every feature you could want out of a RAID controller.

---

### Post by jstrubberg on 2005-11-12
Gee, I am pretty sure the original poster asked for the difference between Win2k3 and Ubuntu, not Win2K3 and an expensive Red Hat app.

Lord, are you going to chase me from thread to thread now?  I answered the mans question.  Running a Win2K3 server, you can look forward to spending time chasing down and securing all of the buggy code that Microsoft chose to carry to their server platform from what was originally a home user oriented OS.  The fact that 90% or better of the computer world runs some version of a Windows OS means that you will deal with an order of magnitude more attacks than you will on a Linux server.

Number of patches means nothing in any practical sense.  There are less than a tenth as many people that have any notion how to exploit those vulnerabilities.

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=jstrubberg]Gee, I am pretty sure the original poster asked for the difference between Win2k3 and Ubuntu, not Win2K3 and an expensive Red Hat app.[/quote]And that's not the question I was answering,  was it?  How does the fact the discussion has turned tangential matter in the least?  Someone asked a legtimiate question and I gave them a legetimate, honest response.


> Lord, are you going to chase me from thread to thread now?No, I've done nothing of the sort and the forum history clearly shows that.  However, you're bordering on a personal attack, which I kindly ask you to refrain from.

> I answered the mans question.Poorly and incorrectly.  Your answer is so vauge as to be meaningless, nevermind the fact your second statement is nievely incorrect.

If you're talking about setting up and managing a corporate domain with workstations, then yes, you'll probably have an easier time doing so with Win2K3 and Active Directory.

If you're talking about a cluster of webservers, I'm not sure that holds true.  If you're talking about a singe fileserver, I'm not sure that holds true.  If you're talking about a network that must be heterogenous for whatever reason, then it obviously doesn't hold true.

So no, your statements weren't correct.  This is why generalizations about such matters are terrible things, and why I try to avoid making them.

The correct choice is of course, whatever best fits your situations and your own needs, which are always unique and different.  If you feel Windows is the best pick, choose it.  If you feel Ubuntu is, choose that.  And if you need help picking, then you need to describe an explicit, focused situation.

 > Running a Win2K3 server, you can look forward to spending time chasing downNo, you don't, as you don't generally have access to the source and as such, really can't do any chasing down.

> and securing all of the buggy code that Microsoft chose to carry to their server platformWhich, if you look at CERT advisories for any distribution of Linux, is not significantly more than that of any Linux distribution.  And for certain portions of Win2K3 (i.e., IIS) it's significantly less.

> from what was originally a home user oriented OS.Windows NT was never meant to be used on the home desktop until 2K/XP Home, really.  It's certainly wasn't that originally. 

> The fact that 90% or better of the computer world runs some version of a Windows OS means that you will deal with an order of magnitude more attacks than you will on a Linux server.No, that's not necessarily true.  Apache Slammer was a pretty terrible worm, all things considered.

There's a new Apache worm out there, even though Linux boxes aren't the majority of the world's hardware out there.

---

### Post by jstrubberg on 2005-11-12
If all the original poster is wanting to do is run a web server, I agree.  IIS may indeed be a better option than Apache **today**.

His question was much more generic, though.  That's why he got a generic answer.  Web services are the only area I can think of where Microsoft security has done well.  

For pretty much everything else, the question comes down to 1. Easy, or 2. Secure?


If you need a server to authenticate logins for a group of windows clients and want control of the user experience on those clients, Win2K3 and Active Directory works well.  If you want a task-specific server with few security problems, Ubuntu is a better choice.

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=jstrubberg]Web services are the only area I can think of where Microsoft security has done well.[/quote]See, that's not true.  SQL Server 2K5 has gone through lots of work to limit privilege of the various services.

> For pretty much everything else, the question comes down to 1. Easy, or 2. Secure?No, it doesn't.  There are a host of other factors to consider including (not limited to):[list][*]License cost[*]Reoccuring cost[*]Staff familarity[*]Network makeup[/list]In fact, "easy" and "security" are both almost total red herrings as neither platform is particular hard to use in the face of competent staff, and the security is comparable.


> If you need a server to authenticate logins for a group of windows clients and want control of the user experience on those clients, Win2K3 and Active Directory works well.Which is a specific, not general case.  Which is my whole point: your statements were inductive fallacies.

> If you want a task-specific server with few security problems, Ubuntu is a better choice.:rolleyes:  Sure, if you know, believe people who can't provide any substantiation for your claims.  You've yet to provide a single technical reason as to why Ubuntu is more secure.

---

### Post by N8MAN1068 on 2005-11-13
I think what we can all probably agree on, is that we need more information from the original poster; if he's still around.

One might be better, but if you're not familiar w/ it, it's not easier.

Personally, I'd deploy Suse before RedHat.

---

