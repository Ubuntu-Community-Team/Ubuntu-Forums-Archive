---
title: "Sick of Windows!!!"
date: 2016-03-05
forum: Server Platforms
---

### Post by ssmith2 on 2016-03-05
I have been an IT professional for over 30 years now and I am sick of windows. I am so sick of windows its scary.

SO I'm looking for help in the best way to get rid of it.

The server I currently run at home is a windows SBS 2011 but I only really use DNS, DHCP, Exchange email & calendar file server and print server and domain controller.

So I guess thats my question?  Using Ubuntu as a server, can I
1) make a linux "domain controller"
2) enable DNS
3) enable DHCP
4) have a print server
5) have a linux flie server
6) have a linux email & calendar server

And i really want to use gui controls and avoid the CLI as much as possible/

Once I have the server sorted, i can work on the workstations :)

---

### Post by sandyd on 2016-03-05
> **ssmith2 said:**
> I have been an IT professional for over 30 years now and I am sick of windows. I am so sick of windows its scary.

SO I'm looking for help in the best way to get rid of it.

The server I currently run at home is a windows SBS 2011 but I only really use DNS, DHCP, Exchange email & calendar file server and print server and domain controller.

So I guess thats my question?  Using Ubuntu as a server, can I
1) make a linux "domain controller":
2) enable DNS
3) enable DHCP
4) have a print server
5) have a linux flie server
6) have a linux email & calendar server

And i really want to use gui controls and avoid the CLI as much as possible/

Once I have the server sorted, i can work on the workstations :)

Linux can perform all of the things you mentioned. The requirement of a GUI is a bit problematic though. While there are GUIs that can configure all the above, I find that configuring by hand is still the best way to fix issues that the GUI sometimes cannot, and fine-tune settings that the GUI may be missing. If you do not configure it by hand, it is hard to diagnose issues as you do not know what the GUI has done.

Now as for the software...:
1) OpenLDAP + Samba for profiles/etc
2) dnsmasq/unbound/bind, take your pick. Listed in order of what I think is easiest to hardest.
3) dnsmasq/isc-dhcp-server, take your pick. Listed in order of what I think is easiest to hardest.
4) CUPS
5) SAMBA if network contains non-linux clients, NFS4 (+Kerberos?) if pure linux clients
6) Some software supports both, some don't. Zimbra supports calendering for users + mail, but requires 2G+ RAM to run. Axigen Free supports calendering/mail, but only for 10 users. 

Kolab Groupware is free and has calendering but needs a seperate email server. Sogo has the same issue.

For the mailserver, you can probably choose postfix or exim. There are some automatic email setup scripts such as iRedMail or MailInABox which may make it easier to setup a mailserver.

As I mentioned above, there are some GUI software that can configure the software for you. Webmin/Ajenti seem to be popular these days.

There are also entire distributions of Linux that will provide the features, take a look at Zentyal, ClearOS, nethserver

---

### Post by Bucky Ball on 2016-03-05
*Thread moved to **Server Platforms**.*

Even though you're a newcomer, people will take account of that, and you'll have a more fruitful time here (although sandyd has already given you plenty of food for thought in here informative post).

Good luck and hope things work out for you with Ubuntu. :)

---

### Post by DuckHook on 2016-03-06
Welcome to the forums, ssmith2.

sandyd is a guru and has way more technical savvy than I, so her technical recommendations are better informed than mine could ever hope to be, but my observations are of a more "meta" nature:

I ran SBS at home years ago, and discovered much the same as you&#8213;that it was total, absurd overkill. The few pros were completely outweighed by the many cons: outrageous cost, complexity, unreliability, power consumption and excessive maintenance and admin. I'm wondering: are you operating a significant SOHO that requires your own domain? For example, are you serving your own web pages from home? If not, then instead of just duplicating SBS functionality, you may want to radically simplify and offload.

FWIW, here is how I simplified:

1. Switched to Google Gmail, Tasks, Address Book and Calendar. This provides me with all the synchronized functionality that I need, from desktop and laptop (all accessed through Thunderbird) to every Android mobile device that I own. It's not Exchange, but more than sufficient and 1% of the headaches.

2. By offloading all of #1, I don't need DNS.

3. DHCP and VPN is provided by a cheap-as-borscht router ($50) running dd-wrt. It just runs and runs with no complaints for months on end barely sipping any power.

4. File service is provided by a cheap Western Digital MyBook Live ($120) that is capable of servicing Linux and Windows machines. Again, uses barely any power.

5. I don't need a print server because I buy only network-capable printers that are assigned addresses by the router.

Since simplifying, I have cut my software bill to nothing, cut my "server" power consumption to almost nothing, cut my HW costs to practically nothing, and cut my maintenance and admin headaches to what seems like less than nothing.

You won't have to deal with any CLI&#8213;or even a GUI for that matter&#8213;because every element is so simple it is managed through a web browser.

It was like being let out of jail.

---

### Post by MAFoElffen on 2016-03-06
Welcome to Linux.

For server GUI, think Win Server Core... Where they no leverage no GUI as being more secure. Linux Server 

If you are stuck on GUI, look into webmin for admin of you Console based Linux Server. 

... Or as sandyd recommended "Zentyal". Zentyal is an Ubuntu Server core topped off with a GUI and some very good scripting. It can be administered remotedly with a web interface. It has everything you are looking for. It's said to be a small business server, but I feel that is an understatement. It does have compatibility of exchange server, "modules" for kerberos, ldap, domain controllers, dns, dhcp, smb shares, etc ... so if you are still supporting Windows clients... or not ... The modules are more a "if you have experience with Win Server... You would find that role as this." The scripting I described makes ties the GUI to installation, configuration, and administration of roles very intuitive and easy. 

You have lots of options. You don't need a GUI, and you are not locked into you have to do it this way. Linux give you lots of choices to do things how you want to. You can tweak things how you want to. But then again, a GUI might help you in the interim to learn what you can quickly... (ease the transition).

---

### Post by mastablasta on 2016-03-07
Zentyal aims to be an Ubuntu based SBS replacement, so I would start there. by default it installs a desktop of sorts (I guess windows server does it that way too !?!). with "expert" install mode you can opt out of that and have only a WebGUI installed.

---

### Post by houstonbofh on 2016-03-08
> **ssmith2 said:**
> I have been an IT professional for over 30 years now and I am sick of windows. I am so sick of windows its scary.
Welcome to the club!  I am reminded every time I work on a clients Windows system. :)

First, there are a LOT of "right ways" to do this.  Many will have a different take, and you can use what you like.  My personal take is more segmented.  I do not like all-in-one kitchen sink style applications.  I go with best of breed stuff, and use the best tool for each job.  And that is how my recommendations will go. Speciffically, my recomendations will require a few different servers, or some type of virtualization to segment the jobs.
> **ssmith2 said:**
> 1) make a linux "domain controller"
Yes.  SAMBA can do this.  Mostly by command line, however.  There are some GUI web apps for it, however.
So can a app called nas4free.  It is a BSD based appliance for stoarge, and will do SAMBA for file sharing, as well as NSF and rsync, and snapshots, and deduplication and...  I am getting ahead of myself. :) But it works well enough that I have 12 at different client locations.  And the other file sharing methods are handy if you ever move off Windows clients.
> **ssmith2 said:**
> 2) enable DNSThis is usually best taken car of on the firewall / gateway.  I like SmallWall for this, but pfSense works too.  Best of all, it can go on small hardware that needs very little power.  And you will still have a network while rebooting your file server. :)
> **ssmith2 said:**
> 3) enable DHCPSmae as above...  SmallWall.
> **ssmith2 said:**
> 4) have a print serverSamba can do this as well.  I have never tried it on nas4free, however.  But are you sure you really need this?
> **ssmith2 said:**
> 5) have a linux flie serverLinux can support most file sharing methods.  Bot configuing NFS can be a chalange from the CLI without nas4free.
> **ssmith2 said:**
> 6) have a linux email & calendar serverThis can be more of a headache then you want.  Between spam management, and other BS, it may be worth it to use gmail, or ZoHo if you do not trust Google.  (I do not trust Google)  Otherwise, Look at iRedmail.  It is an easier setup then most, and supports a lot of the features you need.  Support is also available.

> **ssmith2 said:**
> And i really want to use gui controls and avoid the CLI as much as possible/
This can be hard.  Unix like OSs run very well from CLI.  But Unix based appliances often have very good Web GUIs.  This is why I recomended nas4free and SmallWall.  They are mature, and VERY easy, in spite of having full enterprise class features.

> **ssmith2 said:**
> Once I have the server sorted, i can work on the workstations :)
The users may not like you much. :)  Don't ask me how I know... :)

---

### Post by 1clue on 2016-03-08
> **sandyd said:**
> Linux can perform all of the things you mentioned. The requirement of a GUI is a bit problematic though. While there are GUIs that can configure all the above, I find that configuring by hand is still the best way to fix issues that the GUI sometimes cannot, and fine-tune settings that the GUI may be missing. If you do not configure it by hand, it is hard to diagnose issues as you do not know what the GUI has done.

Now as for the software...:
1) OpenLDAP + Samba for profiles/etc
2) dnsmasq/unbound/bind, take your pick. Listed in order of what I think is easiest to hardest.
3) dnsmasq/isc-dhcp-server, take your pick. Listed in order of what I think is easiest to hardest.
4) CUPS
5) SAMBA if network contains non-linux clients, NFS4 (+Kerberos?) if pure linux clients
6) Some software supports both, some don't. Zimbra supports calendering for users + mail, but requires 2G+ RAM to run. Axigen Free supports calendering/mail, but only for 10 users. 

Kolab Groupware is free and has calendering but needs a seperate email server. Sogo has the same issue.

For the mailserver, you can probably choose postfix or exim. There are some automatic email setup scripts such as iRedMail or MailInABox which may make it easier to setup a mailserver.

As I mentioned above, there are some GUI software that can configure the software for you. Webmin/Ajenti seem to be popular these days.

There are also entire distributions of Linux that will provide the features, take a look at Zentyal, ClearOS, nethserver

This, only I might mention that for 2 and 3 the last options are the most capable options. They are the reference implementations by the Internet Systems Consortium. They take a little bit of time and effort to learn, but IMO it's worth it.

A note on CLI: Pretty much every GUI tool is an unnecessary wrapper around core functionality which has a more-capable command line interface. Contrary to popular belief, the GUI tool usually doesn't call the CLI version, rather they both call a binary library (DLL in Windows-speak) but since testing is easier to implement on command-line code (Purely my opinion) I think the command line tool is usually more complete.

It's up to you to decide on CLI vs GUI. Certainly most of the software you've mentioned has some sort of GUI configuration tool. The thing that you need to keep in mind is that a non-gui environment removes a lot of software from the server, with no real loss of functionality.

The thing you need to ask yourself is this:  Do you want to be a hobbyist or do you want to do the same things you've been doing on Windows, being an IT professional? There is a level of commitment involved, and a real cost to doing things always with a GUI.

---

### Post by rob-bosch on 2016-04-26
> **mastablasta said:**
> Zentyal aims to be an Ubuntu based SBS replacement, so I would start there. by default it installs a desktop of sorts (I guess windows server does it that way too !?!). with "expert" install mode you can opt out of that and have only a WebGUI installed.

This is not correct. Since v4.0 Zentyal has switched from a SBS replacement to an Active Directory/Exchange replacement. A LOT (like 80%) of the SBS features have been dropped. If you want an Ubuntu based distro that can do SBS features, I suggest to try Karoshi Linux Currently V 11 is being beta tested based on Ubuntu 16.04. As soon the last bugs are ironed out, the images will be released featuring a home server version wich includes a DLNA service for streaming multimedia.
Current version is V 10, based on Ubuntu 14.04. There is an education version and an SBS version. The main difference is the provisioning of Samba4. The only thing that lacks is an UTM/Gateway service. But if you run a router on your network, this shouldn't be that big of a problem.
If you need an SBS server _with_ UTM/Gateway, I recommend NethServer. Based on CentOS, a fork of SME-server and shipped with a very intuitive webinterface. Besides a great and stable distro, there is a super active and friendly community around NethServer. NethServer 6.7 comes with Samba3 so it is 'NT-domain' compatible.
Currently NethServer v7 is in beta. It will be based on CentOS 7 and as soon it is released, development of the next big thing will be happening: Samba4 integration, so true AD replacement can be achieved.

---

### Post by mastablasta on 2016-04-28
Zentyal's company dropped plenty of the apps and they wanted the community to pick up their development. I am not sure where they are standing now and how mcuh of the apps was then maintained by community.

---

