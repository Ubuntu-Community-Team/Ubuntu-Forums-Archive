---
title: "Gateway Server Help!"
date: 2006-06-24
forum: Server Platforms
---

### Post by Flashstar on 2006-06-24
We have two offices and several workstations at each office. We are also migrating to a Windows 2003 server at office 1. This server happens to be located at office 1 and there are no servers at office 2. For now, the clients at office 2 have to logon through the internet and authenticate that way also, so it takes much time every time data is sent or recieved over the internet. I am going to build a server at office 2 to handle this authenticating so that it won't take so long to send or recieve data. I also don't want to spend a fortune on another Windows 2003 liscense so I am planning on going with Ubuntu 6.06. This linux server would have to create a permanent gateway between it and the one at the first office. I would like to find out how to accomplish this. Note that all of the clients are running Windows XP professional. Thanks

---

### Post by Flashstar on 2006-06-25
Does anyone have any ideas?

---

### Post by alamba on 2006-06-26
Are the clients in office 2 authenticating via VPN? You're probably looking at a LAN-to-LAN VPN tunnel rather than a roadwarrior configuration. OpenSWAN might be your answer.

A

---

### Post by Flashstar on 2006-06-26
Yeah, the clients in Microsoft Office 2003 are authenticating via VPN. 
I think it's probably a lan to lan tunnel also.
Thanks for the help.

BTW: How do you install Openswan?

---

### Post by LordHunter317 on 2006-06-26
You umm, want to spend the money on a Windows 2003 server.  You could build a FDS box with an AD bridge, but it will be suboptimal.

Put a second DC in the second office, join all the machines to it and make it in charge.  This solves the problem.

---

### Post by herald on 2006-06-26
I would say this all depends on many factors.  First of all, what kind of pipeline does the "remote" office have to the internet?  If it's something like 128K DSL, you're going to see slow communications regardless...Second, How is the VPN handled?  Do you have a hardware VPN router?  Is the VPN really configured as a site to site VPN?  It sounds more like each client is configured to authenticate via VPN which would almost certainly have to indicate a "road warrior" configuration.  If this is the case, no wonder it's slow!  Site to Site VPN should create a transparent tunnel and the machine should just be configured to authenticate as though they were on the same subnet as the domain controller (because technically they would be via the site to site tunnel).  I would be careful when using VPN through a Linux gateway to a windows client.  Windows requires the L2TP protocol in addition to the standard IPSec, and this can be extremely frustrating to set up, not to mention terribly insecure if done improperly.  I would try to use hardware based VPN to simplify things as much as possible.  This will also give you improved performance, depending on what level of routers you use.

As LordHunter mentioned, you could very well buy another Windows server and implement a Backup Domain controller to speed up authentication, but you're still left with the problem of slow throughput to the primary server, which I assume is also serving as a file server.

My advice is to be very certain of your current site to site communications setup, and to make sure you set up your VPN carefully.  As long as you've got the bandwidth, your speed problems should clear up dramatically once this is done.  Unfortunately, without more information on what you're networking with, and how it is all set up, I can't give any more specific advice.

---

### Post by Flashstar on 2006-06-26
I'm sorry about not being clear, but I don't even really know most of the stuff about how the network it set up. I know that we don't have a dedicated vpn router, we just login to the server remotely. Also, the line is 384kbps dsl, but we are planning on speeding that up. The main thing that we want is to be able to make it appear like the second office is in the network so the entire thing just looks like 1 network rather than 2 separate ones. 

Unfortunatley as well, I am not sure about what I am doing or what I want, but Openvpn seems like a good option.

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=herald]I would say this all depends on many factors.[/quote]Not really.  Authentication needs to be done locally.  You compromise your ability to get work done if it's not.

> As LordHunter mentioned, you could very well buy another Windows server and implement a Backup Domain controller to speed up authentication,No, it would not be A BDC.  That would be probabyl even worse.  You want to make a second domain and run a second AD controller that's local for that office.  It should be a child of the forest setup at the main office, but it should be the master for everything in the remote office.

---

### Post by ShaneScott on 2006-06-29
Putting a DC in a remote office with a group of users described as "several" is like killing ants with a sledgehammer.  It'll definitely work, but it's probably more than you need and apparently more than you want to spend.

     Get more bandwidth and a static IP at the remote office.  You'll want that anyway. Buy 2 matching VPN routers and configure a tunnel.  Make sure the subnets are different at each location.  You should be able to log in with no problems whether the tunnel is up or not assuming you can log in at least once to get cacheable domain credentials.

     If you don't have a pressing need to have the clients be members of the domain you can use the "Manage my network passwords" heading in the user configuration in XP Professional to save a password for the server (which will count for the domain) so it won't prompt you for user credentials and you can authenticate the workstation to a local SAM.
  
     If you have significant slow downs with name resolution you can opt to hit the server by it's IP or if you want to get nasty you could set up a BIND server with a replicating copy of the forward lookup zone for your domain in office A.  

     What i would do is probably just set up the tunnel as stated above with 150 bucks worth of VPN endpoints and see how it goes. It doesn't sound like your networking environment is too complex and that's something you want to hold on to if possible.  If you want to add entries to the PCs hosts file to speed name resolution up go for it, but i'd hesitate to get into a situation where you might be troubleshooting replication for DNS or AD over a user group that's smaller than 10 folks.  
     
     Let me know if i misunderstood what you were trying to do.  

SS

---

### Post by LordHunter317 on 2006-06-29
[QUOTE=ShaneScott]Putting a DC in a remote office with a group of users described as "several" is like killing ants with a sledgehammer.[/quote]Except it's not.  If the VPN link drops for any reason, users can't login.  THey probaly can't access their work (it should be moved on the DC and it made a fileserver).   They won't be able to change their passwords, either.

I've been in situations before like this.  I worked in an office of 10 people with HQ on hte other side of the city, with the DC and fileserver there.  Everytime the DC went down there was little to but go home.  All of my work was inaccessible.

>   If you don't have a pressing need to have the clients be members of the domainYou do, because otherwise this is pointless.  You might as well pretend the two offices are full seperate at this point.

---

### Post by ShaneScott on 2006-06-29
So you're saying that if there is no VPN tunnel to the main office no one can log in? That's just not true.  Like I said in my previous post you will need to log in once, and after that if the domain isn't immediately available you will log in with cached credentials.  I do it almost every night with my notebook.  I turn the notebook on, log in with my domain credentials, connect to the internet over my WAP and finally i connect to the VPN.  It is true that you won't be able to change your password for the domain with the tunnel down, but if the tunnel is down that isn't going to be your biggest problem.  I'm going to just assume they'll have connectivity often enough to refresh policies if they use them and reset passwords.  If you're saying your DC went down regularly, well that's a different story, and it still doesn't mean he needs a DC with a child domain in his remote office to get some work done.  

      My point is this:  Ubuntu or any other *nix will work in this situation.  You can absolutely hit your needs with something that won't cost you as much as a Server 2003 license.  You can very easily use a linux box to store files and could configure it to sync with the main file server in the evenings before the main backup runs in the office. That is preferable to working with your files stored on a remote server, no doubt.  You could also configure the linux box to keep versioning info on the files just like Shadow Copy in Server 2003, that way if someone deletes or overwrites a file they won't have to request a tape restore from the main office.  

     I would like to hear why remote workstations not being on the domain is pointless if you have the time.  I access file servers at our office almost every day from machines that aren't members of the domain.  Our IDS boxes aren't members of the domain and they get the job done.  Domain membership is just one tool in the tool belt.  

     The network i'm on now has 5 major sites in a single domain with no child domains.  In addition to that we've got around 375 small acquired and affiliate offices that connect to this network in a variety of ways.  Some VPN, some with webapps, and a fair number of point to point links.  We currently have no issues with logins.  We don't have DCs in every location.  You don't need DCs in every office.   I'd put a second DC in the first office before i put a DC with a child domain in a satellite with only a few users. 

    Anyway, i was hoping there would be info about setting up a gateway in Ubuntu in this thread.   I will look elsewhere.

SS

---

### Post by LordHunter317 on 2006-06-29
[QUOTE=ShaneScott]Like I said in my previous post you will need to log in once, and after that if the domain isn't immediately available you will log in with cached credentials. [/quote]which is great, if hte the same people use the computers every day and you're willing to take the security risks.

But if their work is stored on the other of the link, being able to login in is rather worthless.

> If you're saying your DC went down regularly,No, our T1 dropped out about every 8 hours.

> I would like to hear why remote workstations not being on the domain is pointless if you have the time.They're a massive security liability.  Endlessly massive, in fact.  They shouldn't even be allowed on the network, as you have no control over them.

---

### Post by herald on 2006-06-30
[QUOTE=Flashstar]I'm sorry about not being clear, but I don't even really know most of the stuff about how the network it set up.[/QUOTE]

Please don't take this as an attack, because it's certainly not meant as such, but if you can't figure out how the network is set up, OpenVPN is definately not going to make your life easier.  Earlier, someone recommended that you buy 2 matching VPN routers.  I heartily agree.  While DSL connections are not the single most reliable pipe to connect to, the reliable options are expensive and hard to maintain (I.E. frame relay over a T1).  If the pipe does go down, then the problem isn't with your network, nor a domain controller, it's with the ISP, in which case you should be jumping all over your service provider.  If you can't trust that, then switch.  That's the first thing to consider.

Once you've got the two matching VPN routers, it is quite simple to set up a site-to-site tunnel.  The encryption will require a little bit of bandwidth overhead, but overall it shouldn't be too bad.  This will get you connectivity with the home site, and the possibility of link dropouts can be can be mitigated with locally cached credentials, synchronized (aka offline) files, and other Windows features.

Laptops are generally configured to take advantage of most of these features because they are often used "on the road" and cannot connect to the domain controller.  Especially considering offline files, the user won't even notice the dropout, unless they try to access the internet or a specialized service offered by the homesite (I.E. a centralized database).

Non-windows clients would not be quite so happy, however, as they don't come with an integrated caching system for files or authentication tokens.  Even the Windows machines will be somewhat limited (time synchronization, password changes, Group Policy updates, etc.) but all of these services should transparently reconnect again once the homesite link is back up.

No offense to the other posting members, but I must agree that buying another windows server and setting up an entirely separate domain for anything less than 20 clients is borderline overkill.

I understand your desire to set up another Linux server as a gateway, but another network hop is not what you need here.  A more functional existing hop is what you need.  When you can combine the existing router's functionality with a VPN gateway all in one package, you're working smarter, not harder.  Buying a new computer (at least $1K, I estimate) The license for Windows Server 2K3 ($300+) and the 4 hours devoted to setting up a separate domain, would seem excessive compared with $700 for two Cisco routers and a 2 hour set up time to get the site-to-site VPN tunnel working.  It's a snap-in solution virtually guaranteed to work with your existing assets.  An additional Linux gateway would add to the complexity of your network (not to mention the cost of the server it would embody). A separate Windows domain would add to not only complexity, but heavily to cost as well.

While adding servers makes me drool just as much as the next guy, having to manage more complexity (be it a Linux gateway or a whole new Windows Domain) without getting a raise makes me grumble.:grin: 
My humble two cents.

---

