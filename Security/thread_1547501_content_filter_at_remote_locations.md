---
title: "content filter at remote locations"
date: 2010-08-06
forum: Security
---

### Post by bcdudley on 2010-08-06
I just got this project dumped into my lap a couple days ago and it has now become urgent as other projects are on the line.

We have approximately 100 retail locations that will have split vpn tunneling. Intranet traffic will flow over the vpn to the corporate headquarters, voip traffic will tunnel to a regional hub and internet bound traffic will go over the local isp. The retail locations are small with 1-8 users and no enterprise grade equipment (servers, etc). This setup in effect will render our current content filtering solution  useless. 

The locations will be equipped with Cisco ASA 5505 Firewalls. The original plan was to use a Websense server and the url filtering feature to act as a content filter. I just found out that pricing for Websense was not included in the budget and will be a show stopper. There may also be some performance issues with this method. 

Putting a proxy server at each location is not really an option. We do not have the resources to place a server at each location, plus the users could simply unplug an inline device or go around it. There is minimal supervision at most of these locations. 

Ideally, I would like to find a way to use something like Dansguardian with an ldap interface and the url filtering feature of the ASA firewalls. I found a program called n2h2p, but I can find 0 documentation for it. It is also 2 years old with no updates. I also need to be able to centrally manage this as trying to keep up with 100 different configurations for 400 users would be virtually impossible for the amount of time I will have available.

I would appreciate any suggestions.

Thank you,

---

### Post by bodhi.zazen on 2010-08-06
> **bcdudley said:**
> I just got this project dumped into my lap a couple days ago and it has now become urgent as other projects are on the line.

We have approximately 100 retail locations that will have split vpn tunneling. Intranet traffic will flow over the vpn to the corporate headquarters, voip traffic will tunnel to a regional hub and internet bound traffic will go over the local isp. The retail locations are small with 1-8 users and no enterprise grade equipment (servers, etc). This setup in effect will render our current content filtering solution  useless. 

The locations will be equipped with Cisco ASA 5505 Firewalls. The original plan was to use a Websense server and the url filtering feature to act as a content filter. I just found out that pricing for Websense was not included in the budget and will be a show stopper. There may also be some performance issues with this method. 

Putting a proxy server at each location is not really an option. We do not have the resources to place a server at each location, plus the users could simply unplug an inline device or go around it. There is minimal supervision at most of these locations. 

Ideally, I would like to find a way to use something like Dansguardian with an ldap interface and the url filtering feature of the ASA firewalls. I found a program called n2h2p, but I can find 0 documentation for it. It is also 2 years old with no updates. I also need to be able to centrally manage this as trying to keep up with 100 different configurations for 400 users would be virtually impossible for the amount of time I will have available.

I would appreciate any suggestions.

Thank you,

See if these blogs give you any ideas :

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

You can restrict your users either with rules in iptables or tunneling http traffic through your VPN.

If you are going to filter content, you need at least one proxy server somewhere. You then tunnel or configure iptables to enforce the proxy.

---

### Post by bcdudley on 2010-08-06
Thank you for the response. A proxy server would work, but we do not want to route all of the internet traffic through our corporate office. We also cannot put a proxy server at each location. We do not have the budget, nor the manpower to do that.

We need to find a method to control internet traffic that is not routing through our datacenter.

---

### Post by bodhi.zazen on 2010-08-07
As far as I know, either you can do this with your router, but then you will need to maintain a blacklist on your router, or you need a proxy server.

A proxy server does not need to be expensive, any old box will do. You need 2 NIC. Then look at any of the router specific distros and install squid + dansguardian + dhcp.

I suppose a third option would be to try to maintain a host file on each box. Again you will need a blacklist and point restricted ip addresses at 127.0.0.1. I would imagine any per box solution would be more expensive then a proxy server.

---

### Post by HermanAB on 2010-08-07
Probably the easiest solution is to use DynDNS:
[http://www.dyndns.com/](http://www.dyndns.com/)

Amongst other things, they run a filtered DNS service.  You then configure the DHCP server at your remote locations to hand out the DynDNS filtered DNS server address to all and sundry.

---

### Post by OpSecShellshock on 2010-08-07
This is a retail location? I assume that means it processes credit cards. With over 100 physical stores, it's not much of a stretch to suppose that it does over $80k per year. So you can maybe start by printing off the PCI-DSS specifications, then go the management and/or the general counsel and explain to them that they're going to find the budget to do it right (perhaps suggest to them that they run "tjx albert gonzalez" through a google search) . If they're going to come back to you and say no anyway, then make sure they do it in writing and that you have it on file.

OK, so once the tedious part is over, there are other things to figure out. If you've got the company intranet set up, and the VoIP network is also set up, then what's the purpose for having internet access at all? It seems to me that content filtering is only necessary when you're standing up desktop systems that have browsers on them, but I can't figure out why retail employees would need access to something like that. In any case, it seems this starts with administrative things like training, codes of conduct that they sign off on, whatever. Then restrict their permissions on the computer systems to only being able to do the things they need to do in order to get their work done. I don't imagine this involves accessing the web in the same way people do at home. If there must be access, I'd consider flipping the plan around and going with whitelists rather than blacklists. Load a standard image on all of those systems with the whitelist configured as part of it (I'd think it can be done with iptables). Ensure that any changes made (sites added) require a formal tech support request ticket.

It seems like in such a distributed network environment, whitelists would be cheaper. Employees would probably complain about it, but the important thing is that they aren't complaining to you.

---

### Post by bcdudley on 2010-08-07
Thank you for all the responses. Our retail locations income can vary depending on many factors. I do not know numbers as financial's are not part of my job. I leave that up to the bean counters. They do process credit cards at every location. 

We are an insurance company so we do not have a typical retail store with cash registers and such. We have employee desks setup and each employee has their own computer. We do not restrict internet access except to objectionable content and harmful malware sites. Internet access is used for researching cases, vehicles, checking status of whatever. 

 We do not actually keep customer data on our sql servers. We have a contract with another company to store sensitive data for us. The data is transmitted securely directly to their servers.

A whitelist setup would meet with a great deal of pushback from everyone at the company, including myself. It would not be a good fit for us. I currently have a Sonicwall CSM filter at our corporate headquarters. All internet traffic flows through our location via vpn tunnels, mpls or isdn connections. It does work very wells for us, but that is a huge bottlenecks and wastes a great deal of bandwidth. Doing split tunnel vpn's at each location will speed up internet access for everyone, if we can get it to work.

Is there no way to emulate the connection for a Websense or Secure Computing Webfilter. I also read that Dansguardian is not licensed for corporate use, so I will need to check more into that.

---

### Post by OpSecShellshock on 2010-08-07
Oh, OK, so this is for limited personal use and basic research in an office. That's actually a relief. I was initially picturing a retail store with teenage salespeople. However, it does open up some other things. Are the office desktops using Ubuntu, or are do the actual desks have Windows machines? The reason I'm asking is to try and help assess the risks.

Thing is, appropriateness of the content/sites is at this point in the game a secondary concern to malware. Frankly, the cost of incident response is going to be way higher than the cost of using a service like Websense. Heck, even using them doesn't stop everything, but they are pretty good in enterprise environments when it comes to filtering because in addition to the content filtering they block some amount of known malicious stuff that gets delivered through the web. Anti-virus software alone just isn't good enough. I spend a good deal of every day with the AV database on one side of my display and the NIDS logs on the other, trying to line up matches for when I know something bad is going on, and when I actually can get both of them to agree it's still rare enough for a happy dance. It's just the lay of the land now, and it's not going to get any better.

Also, the same workstation connected to the Internet and the company's intranet is still a weak point because of user habits. Anything that can be accessed by a legitimate user can be accessed by malware, provided it can get on the machine (most of the time this is where the user comes in). I guess what I'm saying is that, given the potential catastrophe of a data breach at an insurance company and the current state of the web as a platform for the delivery of cheap yet robust malicious content, it's almost certainly worth the money to pay for a third party filtering service unless you can switch the workstations over to a non-Windows platform (a nightmare for workplace morale if the users aren't trained for it). Does your central office have a dedicated information security staff, or is this stuff being put on the general IT staff?

If you are dealing with Windows workstations, then it might be worth looking into content filtering via Group Policy Objects. I don't know much about those, unfortunately, but they seem useful enough and can be managed centrally in the same way that patch management is usually done in enterprise environments.

---

### Post by bcdudley on 2010-08-08
It is more of an office type of environment, but we do have customers coming in and out all day. We typically have a few desks for new policies, renewals, stuff like that. Then we have a front counter for taking payments and such. All of the pcs are unfortunately windows. For the moment, linux machines are restricted to the datacenter and my office. One of my upcoming projects is looking at a thin client setup. The clients will be based on a linux core, so that will be an improvement security wise.

Malware is the primary concern, but at the same time, I do not want to get reports from a customer walking into a branch and seeing the employees perusing through their daily porno fix. I do run the full Symantec security suite. I have managed endpoint protection on every workstation, mail security on the mail servers, hosted mail security as well. It is all centrally managed and I get alerts the second something shows up. I also run Nagios and Cacti to monitor everything.

I know what you mean about having to pour over logs all day. I have 6 monitors setup in my office. Four for my Windows box and 2 more for my Linux box. When people walk in my office, they always joke that I am trying to take over NASA.

I do keep the workstations locked down fairly tight already with group policies. No user has administrative, or even power user privileges. I lock out usb drives and have Windows installer disabled. I manage all the windows updates from a wsus server and I have several other security mechanisms in place.

 We do not have a dedicated It Security staff. We have 4 people on the day shift IT staff to handle all the issues. I handle pretty much everything server related, switches & routers, security and everythign that goes along with it.

I am determined to find a solutions to this. I know that I cannot be the first person to have this need.

---

### Post by HermanAB on 2010-08-08
So, while you are figuring out how to install Squid-cache and Squidguard, configure the sites with DynDNS as I suggested above.  DynDNS will solve 90% of your problem immediately for very little effort.

---

### Post by bcdudley on 2010-08-08
That may work, except, all of the workstations point to my AD server in the datacenter for dns. It is a requirement for M$ Active Directory. Are you talking about doing something else?  Looking at the dyndns website, I do not see anything on their about filtered dns. I could theoretically set my forwarders on the AD server to point to dyndns, but I would like to see more information about it. All I have ever known dyndns to do is dns hosting, primarily for dhcp web addresses.  Thank you.

---

### Post by bodhi.zazen on 2010-08-08
You can point your workstations to the Windows DNS server for internal DNS, and then point the Windows server to DYNDNS or Opendns for external DNS.

See:

[http://www.opendns.com/solutions/business/filtering/](http://www.opendns.com/solutions/business/filtering/)

[http://www.linuxjournal.com/content/web-content-filtering-opendns](http://www.linuxjournal.com/content/web-content-filtering-opendns)

[http://www.dyndns.com/services/dynguide/](http://www.dyndns.com/services/dynguide/)

[http://www.liberiangeek.net/2010/05/how-to-protect-your-computers-with-dyndns-web-content-filtering-system/](http://www.liberiangeek.net/2010/05/how-to-protect-your-computers-with-dyndns-web-content-filtering-system/)

You will have to decide the most cost effective route.

---

### Post by bcdudley on 2010-08-09
Thank you. The links helped me to understand what you were talking about. I will look into the dyndns option. I think it may work as an interim solution, but not a long term solution.

---

### Post by kewlrichie on 2010-08-09
As other people are saying DNS filtering would work.

But why are you so against having a proxy at each location? The proxy wouldn't take much CPU power at all just a tiny bit of HD space if your going to cache sites with squid. You don't have any old PCs laying around that you can use and install ubuntu server on? and if even if HAD to buy something you can use something like the Acer Aspire Revo which is $199 a piece and you might be able to find stuff even cheaper.

I built a Ubuntu server with squid and Dansguardian which also has ClamAV for virus scanning huge blacklists if you want, phrase weighting, block file types, auto virus scanning and I have to say it worked great. I set squid up as a transparent proxy server so everyone who I want to go through the proxy for web filter there gateway would be the proxy server IP handed out by DHCP of course and they would have to be filtered whether they liked it or not. There are also linux based distros that have all this pre-configured with an interface and all

---

### Post by bcdudley on 2010-08-10
I am against using a proxy server at each location primarily for cost reasons. Another reason is management of all of the servers. Even at $199 each, that will still cost over $20,000. I do not think the Revo would work because it only has a sinlge nic. If I were to put in a proxy, it would have to be inline to keep people from bypassing it. I priced together what might have been a workable computer and the cheapest I could find was around $250 before tax. That means that to put a small proxy server at every location would cost close to $30,000 just for materials. We do not have 100 extra machines laying around. We have maybe 5-10 at the most for replacing broken computers.

Setting up and managing 100 new servers would be whole other project involving more manpower than we have.

I have found something that may work that I am looking into. If it works out, I will report back.

---

### Post by divya101101 on 2010-08-11
Thanks for showing a useful information. I think applying proxy server can definitely work.

---

### Post by bodhi.zazen on 2010-08-11
> **bcdudley said:**
> I am against using a proxy server at each location primarily for cost reasons. Another reason is management of all of the servers. Even at $199 each, that will still cost over $20,000. I do not think the Revo would work because it only has a sinlge nic. If I were to put in a proxy, it would have to be inline to keep people from bypassing it. I priced together what might have been a workable computer and the cheapest I could find was around $250 before tax. That means that to put a small proxy server at every location would cost close to $30,000 just for materials. We do not have 100 extra machines laying around. We have maybe 5-10 at the most for replacing broken computers.

Setting up and managing 100 new servers would be whole other project involving more manpower than we have.

I have found something that may work that I am looking into. If it works out, I will report back.

Managing 100 locations is a big project.

Best of luck to you.

---

### Post by bodhi.zazen on 2010-08-11
> **divya101101 said:**
> Thanks for showing a useful information. I think applying proxy server can definitely work.

Proxy servers are fun. IMO squid is nice at what it does and it has a lot of features. But with features also comes complexity.

You could consider alternate proxies, privoxy or polipo, depending on your needs, are both nice.

privoxy is feature rich as well in terms of content management and I llike it because it performs ad blocks as well. Privox has a web interface if you wish.

polipo is fast and performs well, but dos not give much content management.

---

### Post by bcdudley on 2010-08-11
After speaking this over in depth with management, we have decided that we do not want to put servers at locations that do not staff it people. That means no servers at the retail locations, or any locations other than our HQ really. After looking at all the options, we have decided to not do the split tunnel vpn connection and route all traffic through our HQ like we are currently doing. It is not the ideal, but it seems to be the only reasonable choice. 

If we only had 20 locations or so, the proxy servers would have been a great solution. Trying to manage that number or extra servers with the staff level we have would prove to be impossible for us. Likewise, the Dyndns would be a great solution, but it does not filter our protocol stuff such as torrent files and streaming media. It also does not have any type of anti-virus built in. We have had experience with users bringing torrent clients in on jump drives in the past and trying to run them. we have also had experience with users bringing in personal laptops and putting them on the network without authorization. One of them started spewing spam at a rate of over 1000 messages per minute. In both instances, the content filter detected the intrusion. In the case of the torrents, it actually blocked it. Something that only an in-line device could do.

Thank you for all the feedback and suggestions. It was very helpful and informative at helping me to correctly analyze all the available alternatives..

Regards.

---

### Post by bodhi.zazen on 2010-08-11
If you are tunneling over VPN, perhaps adding additional (central) VPN servers would be best.

---

### Post by bcdudley on 2010-08-11
Our VPN actually works great. We have a Cisco VPN Concentrator 3000 with a redundant backup. I was just trying to find a faster/cheaper solution than what we are currently using.

Thank you.

---

