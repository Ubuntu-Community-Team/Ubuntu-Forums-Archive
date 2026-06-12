---
title: "Untangle versus Dansguardian versus Firewall / Webfilter appliance"
date: 2008-06-11
forum: Security
---

### Post by marianlibrarian on 2008-06-11
I have been looking for over a year for a web filter for our public access computers at our library. I have Dansguardian installed on five of the public access machines but had disable it when an upgrade (the kind that show up when you log into Ubuntu as administrator - I always say yes to all applications that need upgrading) rendered it useless. I admit that I had installed some kind of "gui-interface" to help make tweaking it easier, and really wish now that I had not. I had asked several times about alternatives to Dansguardian (even willing to pay for it) and no one was able to help me. So today I made another search and found mentioned an open source application called "Untangle". 

I went to their website. Very professional. It is free to download and use. But I also saw that they have "professional package" - $25 per month for up to 10 users that includes live support and some other things. The alternative for me is either Dansguardian's application and  support which is a disorganized support forum but free or a Sonicwall NSA Security Appliance which is $3,254.67 (installation not included) firewall and web filter combo. 

Has anyone out there used or are using Untangle?? If so what is your experience?? Do I have to have this application on every computer? Do I install it on a "server" that acts as a stand alone web filter / firewall? Which is recommended? 

If it sounds like I don't know what I am talking about.... I don't. I am a library director of a very small rural library (town size 5K population) who not only is the network administrator but also the toilet cleaner / book buyer / research librarian / well you understand. Currently the disabled version of Dansguardian is on each one of my public access machines. Any help will be appreciated.

Edit: Sorry - OS Dapper Drake Ubuntu 6.06

---

### Post by The Cog on 2008-06-13
I saw your post about Dansguardian last time but couldn't see an alternative. I still find it odd that you can't edit Dansguardian's block list.

This one must be new then. It looks interesting, and you seem to have control over what you block/allow. I certainly think it would be worth a try. Note that you either need a later Ubuntu, or to install their particular version of Linux. To try out, I would probably go with their installer - perhaps use the ex-dansguardian box. Their site is very short on documentation, so you will have to try it to get a good idea of whether it works for you. How you do that without interfering with your customers browsing is an interesting problem.

---

### Post by marianlibrarian on 2008-06-13
A representative of their company called me yesterday. After discussing my network situation, I decided that this is the direction I will go. I currently have 8 desk top and 1 lap top that connect to the internet at our library. I am planning to take another computer and use it for a server that does nothing but firewall and filter and provide other general security to my network. They have prepackaged servers that you can purchase to do this. But since I already have a machine, I will do it from here. They seem to have a solid support system. Time will tell. I also verified that Ubuntu Dapper Drake 6.06 is compatible with their application and they said yes.
 
I will let you know sometime at the end of August because over the next 5 - 6 weeks, I will be immersed in our Children's Summer Reading Program. I am the director / network administrator / toilet cleaner - the network hat is coming off for a little bit. 
 
:)

---

### Post by The Cog on 2008-06-13
Thanks for the reply. Good luck with it. I look forward to hearing how you got on.

---

### Post by TheMiracleMan on 2008-06-24
> **marianlibrarian said:**
> 
Has anyone out there used or are using Untangle?? If so what is your experience?? Do I have to have this application on every computer? Do I install it on a "server" that acts as a stand alone web filter / firewall? Which is recommended?

MarianLibrarian, first off, sorry to hear about your multilateral working arrangements :)  I have been running Untangle for about 2 weeks now, and has been the best Unified Threat Management (UTM) device I've used.  

There are drawbacks and advatanges to all decisions we face in the realm of IT when appliances are involved.  Some of the benefits that Untangle offers: free, open-source (some may dispute open-source as a benefit), ease of use, and the modules which are provided.  

Some of the drawbacks are: must be installed on a fairly hefty system (please refer to their computing requirements), Active Directory (AD) integration requires purchase of "professional" modules, and of course the time required for settings on each module you want added, but this would be required no matter what platform you choose.

For the 2 weeks I've been running this, I haven't had a single issue, failure, lockup, or problem that I didn't cause.  The modules that are available are easy to configure. One feature I really like is the reporting.  It provides detailed reports on every aspect of the system, including graphs and system names/IPs.  

I have Untangle acting as the firewall/NAT device, with all but smtp spam filter enabled.  I have 2 teenage boys that spawned the necessity of this device (yeah... use your imagination).  As an Information Security Analyst, I have seen a variety of content control devices, and found that that the controls used on Untangle are equivelant, or superior to, commercial products.  In a matter of minutes after installation, I was up and running and succesfully blocking protocols, content, and securing my network.

It does not require any workstation installation.  It resides between your ISP and internal network.  There needs to be 2 NICs, one external, one internal.  If you are using a cable modem which authenticates you by MAC address, there is not a command for cloning your MAC address, you will need to change it using a shell command:

```
ifconfig ethx down hw ether xx:xx:xx:xx:xx:xx
```

x's represent numbers, usually eth0, the other x's are for the new MAC address.

Behing the Untangle server I have a managed switch which houses 3 PCs, then it connects to a wireless access point with switch ports.  I have another workstation connected to the wap switch port, and about 4 laptops connected wirelessly.

I'm sure if you get it installed, you'll enjoy it as much as I have.  Hopefully this wasn't too long. :)

---

### Post by stmurray on 2008-06-24
I have I have created a UTM box for my home, based on Ubuntu (currently Gutsy).  So far, I have installed:
--Shorewall as the firewall
--Dan's Guardian (just rule based-- not using a blacklist feed, yet) using Privoxy as the proxy server
--Snort for Intrusion Detection that feeds a Prelude back-end
--ssh for tunneling into my home network
--clam-av for anti-virus

It sits between my network and my ISP and it seems to all be working fine. I have been working on the documentation on how I have this all configured, and will publish that once I have it tested and completed.  I would like to change the ssh to a VPN and have my home email and web flow through this box for virus checking.  But if anyone has any questions on how I have this working, feel free to ask.

---

### Post by WIGGMPk on 2008-06-24
I have been using Untangle as my UTM for over 4 months now. Starting off from their first release to now, they have come a long way in such a short time. (Makes me think of Ubuntu every time I hear about their team)

As far as the Professional package vs. the Free Open Source package. It all comes down to your needs. Do you need Active Directory Intergration? Is the information your protecting important enough to warrent a second anti-virus? Is the information your portecting vital enough to require off-site config backups? Do you really need 24/7 technical support?

All of those questions can give you a better understanding on what you need. Untangle can do pretty much anything you need, from small home office to a larger enterprise size network.

I personally find it rather easy to put together. There are only small benifiets (for me) to use the Professional package. The community is very nice and helpful. Most issues I ran into, I either figured out myself or got help on their forums. The other thing about the professional package is the Policy Manager is very nice. You can adjust different network settings per groups. But I cant justify paying for it when its only me and some friends on the network hehe.


Give it a shot and see how you like it. You most likely wont be dissapointed. They have a Virtual Machine available as well. I think its very scalable and easy to use.


Hope this helps

---

### Post by firecat53 on 2008-06-25
Probably not the best method, but a quick interim fix could be to sign up for an OpenDNS account, and point your router to the OpenDNS servers. Then set up either a whitelist of acceptable sites, or use the built in filtering groups they've got as a quick way to put something in place.

That'll only take 5 or 10 min to set up :)

Scott

---

### Post by coutts99 on 2008-07-10
> **marianlibrarian said:**
>  **I have Dansguardian installed on five of the public access machines** 

Why install it on 5 machines? Surely you just install it on one and set the proxy settings on the others?

OpenDNS is probably the easiest bet, I use a combination of that and dansguardian to keep my daughters web browsing safe(ish).

---

### Post by hkgonra on 2008-11-18
I would love to hear some more updates on how this program is working out for people. 
I am seriously considering it for my business.

---

### Post by revertex on 2008-11-26
you don't need to install dansguardian in every machine, just put it in your gateway,(i supose you have one).

if you haven't any, try a virtual appliance, there is a ton of vmware appliances around.

there are lots of altenatives.

try safesquid, free up to 20 computers.

smothwall-express, also free

cook your own recipe, mine is shorewall as firewall, squid as proxy cache, squidguard to allow access to certain sites based in ACL and/or time restrains, privoxy as web filter, with my custom action files, to block porn and proxies, sarg and srg to generate nice reports.

you can easily chain dansguardian if you wish, but with my privoxy custom action files it's a bit redundant.

take a look at howtoforge, there is a lots of tutorials.

---

