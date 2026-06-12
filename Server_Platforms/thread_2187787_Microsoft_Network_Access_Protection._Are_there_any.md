---
title: "Microsoft Network Access Protection. Are there any Linux alternatives?"
date: 2013-11-13
forum: Server Platforms
---

### Post by Roswebnet on 2013-11-13
Hi everyone

Microsoft in Windows Server 20xx products provides nice security product - the NAP.

> Network Policy and Access Services (NPAS) helps you safeguard the health and security of your network. The NPAS server role includes Network Policy Server (NPS),  [ Health Registration Authority]("http://technet.microsoft.com/library/cc732365.aspx") (HRA), and  [ Host Credential Authorization Protocol]("http://technet.microsoft.com/library/cc732681.aspx") (HCAP).
NPS allows you to provide local and remote network access and to define and enforce policies for network access authentication, authorization, and—when you deploy Network Access Protection (NAP) —client health. HRA is a feature of NPS used when you deploy NAP, and HCAP provides NAP  interoperability with Network Access Control (NAC), the Cisco client health solution.


[http://technet.microsoft.com/en-us/network/bb545879.aspx](http://technet.microsoft.com/en-us/network/bb545879.aspx)

I heard something about Network Admission/Access Control, but it is not the same...
[http://en.wikipedia.org/wiki/Network_Admission_Control](http://en.wikipedia.org/wiki/Network_Admission_Control)
[http://en.wikipedia.org/wiki/Network_Access_Control](http://en.wikipedia.org/wiki/Network_Access_Control)

Any suggestions, packages, tutorials? I prefer that it will run on Ubuntu server.

Thank you.

---

### Post by Lars Noodén on 2013-11-14
What does it do?  I can't parse the marketing speak very well.  :(  In Linux, usually you add components together to get the 
system you need.

If you are interested in routing, look at iptables.  For traffic shaping, look at tc.

For IDS, look at Snort. 

For, vulnerability scanning look at OpenVAS or, more primitively, Zenmap.

For low-level packet analysis look at Wireshark.

Looking up the descriptions of those tools, are those the kind of things you meant?

---

### Post by SeijiSensei on 2013-11-14
If you're asking about a centralized authentication system, Linux can use [LDAP]("http://www.openldap.org/")+[Kerberos]("https://help.ubuntu.com/12.04/serverguide/kerberos-ldap.html") just like Windows does.

Microsoft use to have the "not invented here" mentality until Active Directory.  Then they started incorporating the same protocols that were developed for Unix some decades ago.  They just make sure to hide that fact by using their own names and marketing-speak for things people running Unix networks have used for years.

---

### Post by Roswebnet on 2013-11-15
No

When user PC tries access the network (VPN, WiFi, Ethernet) the NAP asks about the Health status of the PC (Antivirus on, Firewall on, Latest updates or other Policy requirements)

[IMG]http://h17007.www1.hp.com/temp/images/ONE/microsoftDiagram.jpg[/IMG]


It is a very useful feature in Microsoft Networks. More info:

[http://review.techworld.com/security/3227914/microsoft-network-access-protection-review/](http://review.techworld.com/security/3227914/microsoft-network-access-protection-review/)

Therefore, I am interested is it possible to integrate something like this on Linux (Ubuntu)?

---

### Post by Lars Noodén on 2013-11-15
Interesting that they can sell that.  The design looks flawed because it seems to rely on self-reporting by the client. The client could pass any information on to the centralized server, independent of the actual state of things.  So it doesn't look like it protects anything other than market share by locking out other brands of operating system, if that is really being used as a gatekeeper.  

Ubuntu, like most Linuxes, is designed to be secure out of the box.  There are no services listening by default.  So really the best you could do would be poll to see if the system's installed package versions match the latest in the repository for that particular version.  But again that would be relying on self-reporting by the client.  

If you really want to make sure that things are locked down, make sure that the system is partitioned to separate directories that can be written from directories that contain executables.  That means that /home, /var and /tmp get mounted noexec.  And / and /usr get mounted read-only.  That works in a production setting with a known system that will not change, except for patches and updates, but is more of a fiddle on a home desktop and not feasible on a development system.  So the use to which you put your system affects how you might want to set it up.

---

### Post by hawkmage on 2013-11-15
I was part of a project to evaluate some NAC (Network Access Control) products and they were all kludges.  Some required an agent to be loaded on the OS that reported to a policy server that evaluated the client and authorized its access.  Some relied on the VPro Intel chipset for an "agentless" method.  In one way or another they all relied on having the network ports isolate a machine by default and then allow access to the real network once authorized.  Some relied on 802.1x others relied on VLANs and some relied on router ARP table poisoning.  

In the end we did not implement any of them.

---

### Post by koenn on 2013-11-15
I've had a brief look into Microsoft NPS a while back. As I recall, it is indeed (as SeijiSensei hinted at) a mix pretty standard technologies, with the typical microsoft integration, and wrapped in Marketing speak. Think something like RADIUS, Kerberos + LDAP (a.k.a Active Directory Integration), SSL client and server certificates and some other  stuff like PEAP.

IIRC this "NAP" was an optional component in it and  is mostly a framework  that depends on "NAP-capable clients" and manufacturers providing "NAP-agents for their products" ; I haven't heard of anything similar in Linux but all the rest (RADIUS, Kerberos, TLS/SSL, ....) is pretty usual stuff. It's targetted at BYOD/Remote Access scenarios where you 'tolerate' foreign devices on your network if they meet certain requirements (such as "have antivirus installed") but that only makes sense if you only expect Windows systems. In that case, why  bother trying yo emulate this on Linux ?

---

### Post by Roswebnet on 2013-11-15
[B][COLOR=#000000]hawkmage:
   
   [/COLOR][/B][COLOR=#000000][B]> In the end we did not implement any of them.
   
   [/B][/COLOR][COLOR=#000000]Because of an agent?
   
   [B]koenn:
   [/B]
   > IIRC this "NAP" was an optional component in it and  is mostly a framework  that depends on "NAP-capable clients" and manufacturers providing "NAP-agents for their products" ; I haven't heard of anything similar in Linux but all the rest (RADIUS, Kerberos, TLS/SSL, ....) is pretty usual stuff. It's targetted at BYOD/Remote Access scenarios where you 'tolerate' foreign devices on your network if they meet certain requirements (such as "have antivirus installed") but that only makes sense if you only expect Windows systems. In that case, why  bother trying yo emulate this on Linux ? 
   
   The stuff is usual - agreed. Well, the  Linux Server in many cases could replace the Windows Server. However, for end user the Linux client still a problem... Most people do not like to think out of the box ;). Therefore, business/home users will use windows for long time in the future.... (Maybe, once Ubuntu edge/touch, Android due "pc in smartphone philosophy" will replace most of laptops/tablets with constant connection to home/business mainframe/server. Who knows, but today...)
   
   The main Idea of NAP is that if something going wrong (according the Health Policies) with the system, the technology will automatically put the system into quarantined zone with limit or no access to the network resources. I think it is very useful security future.  I tried multiple time NAP in some projects on Windows Networks and it works good. In addition, if admin uses MS Forefront TMG than he can see the isolated clients and take some action. 

According, that many technologies are existed (or were developed firstly on Linux) on the Linux, I got idea maybe such technology is available on Linux too.  What will be great not only on windows clients, but also for Linux, MAC and android clients.
   [/COLOR]

---

### Post by Lars Noodén on 2013-11-16
About you clarification of NAP, it sounds like some kind of IDS.  I suppose OpenVAS and Snort could be set to trigger changes to the network access for certain clients, should certain conditions be triggered by the client.  However, there will very likely be a lot of false positives and those will take staff time to follow up on.  If they are not followed up on, then there is no point in having the systems in place to begin with.   

I don't think setting anything up client side is feasible.  Systems and devices are too varied and anyone with root access can change all that around anyway, whatever you set up.  

It's better to assume a cooperative relationship with the network users.  They can help you help them.

---

### Post by Lars Noodén on 2013-11-16
> **SeijiSensei said:**
> If you're asking about a centralized authentication system, Linux can use [LDAP]("http://www.openldap.org/")+[Kerberos]("https://help.ubuntu.com/12.04/serverguide/kerberos-ldap.html") just like Windows does.

Microsoft use to have the "not invented here" mentality until Active Directory.  Then they started incorporating the same protocols that were developed for Unix some decades ago.  They just make sure to hide that fact by using their own names and marketing-speak for things people running Unix networks have used for years.

Yes, Kerberos V is a classic example of how they treat a standard.  As part of their traditional [EEE](http://www.drdobbs.com/embrace-extend-extinguish-three-strikes/184404225) strategy, they tried breaking the standard by [adding undocumented, proprietary extensions](http://slashdot.org/story/00/03/02/0958226/proprietary-extension-to-kerberos-in-w2k), even going as far as [trying to stifle critique](http://slashdot.org/story/00/05/11/0153247/microsoft-asks-slashdot-to-remove-readers-posts).  Eventually the EC [fought and won](http://www.groklaw.net/article.php?story=20071220124013919) in court to get the documentation for the extensions, but for a fee.  The [Protocol Freedom Information Foundation  paid the fee](http://www.groklaw.net/article.php?story=20071220124013919&mode=nested) and released the documentation so the Samba team could use it.  The standard has continued to be extended and is now overly complex so that some teams are iving up on it.  We'll have to see a re-design in Kerberos VI to simplify it, if the malevolent influences can first be tamed.

That said, Samba4 now has full interoperability with the proprietary extensions after all that work.

---

### Post by Roswebnet on 2013-11-18
Ok, lets finalise it. As I understood there is no possibility to allow server to be part of a NAP technology. However, there is still possibility to use the 802.1x technology...
[https://help.ubuntu.com/community/Network802.1xAuthentication](https://help.ubuntu.com/community/Network802.1xAuthentication)
   That means in my eyes following situation:
   
   [IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Ubuntu%20Network/SAS.png[/IMG]
  
  
  
  [B]If I build up a Linux based security network, there is no possibility for quarantine zone based on capturing the health data (antivirus on, firewall on, updates on).
  
  [/B]Am I right?
  
  Short description:
  SAS - security appliance server (Suricata/IpTables/Squid/DansGuardian/CalmAV/OpenSwan/Webmin)
  Application Server- Samba4, MySQL, OpenERP, OpenChange (dovecot/sogo) and etc.
  Web Server - Apache or Nginx
  Storage Server - NAS/File server
  Clients - Windows7/8, Android or other mobile clients. (wired or wireless clients)
  
  Quarantine Zone is a zone where the clients placed which are not comply to the policies of the SAS.

---

### Post by Bucky Ball on 2013-11-18
I think one of the points you're missing is that Linux client machines don't need these 'health' checks to see if they are infected and then they are consequently quarantined because they don't have the same vulnerabilities as Windows end-user machines in the first instance.

The NAP health check and what-not might be required when you have Win machines dangling off your servers (like buckets with holes), but the same NAP setup isn't required if you have Linux machines hanging off your servers. 

Or something along those lines. Perhaps you're thinking inside the square which is why you are having a problem thinking 'outside the box'. :-k

---

### Post by kurt18947 on 2013-11-18
> 
The NAP health check and what-not might be required when you have Win  machines dangling off your servers (like buckets with holes)

I'm not a pro but wouldn't that be a pretty common scenario?  Linux/*nix servers and Windows clients?  Of course I could also seem some P.O.ed users if they're restricted unnecessarily.

---

### Post by koenn on 2013-11-18
> **kurt18947 said:**
> I'm not a pro but wouldn't that be a pretty common scenario?  Linux/*nix servers and Windows clients? 
Sort of. It's not unusual to see infrastructure services (dns, storage,  web application servers, ...) on Linux, serving windows clients, but to actually manage windows hosts you're better of with Windows servers (think Active Directory services and such)? This NAP thing seems to be on the border.

Still , a couple of years ago you could kinda predict that all the clients would be windows PCs, and disallowing them remote access if they were not configured up to standards (updates installed, firewall on, AV running, ...) to prevent  them being vectors for attacks into your secure network would be rather sensible. 

Today, it's a different picture. In the OP's scenario, who is that NAP going to check if an Apple laptop "has all updates installed" ? how is it going to figure out that a linux laptop is runnng an Antivirus product NAP considers acceptable ? And why stop there : how about iPhones, iPads and Android devices on your wifi network? maybe even Ubuntu phones/tablets ?
So by basing your network security on NAP, you're essentially saying : I want to run a windows only environment. (unless, and that I don't know, Apple, the linux distro's, Google and the android device manufacturers choose to build NAP agents for their stuff).


I think this NAP is the wrong solution, firstly because it's an obvious vendor lock-in mechanism, secondly because it appears to be solving the wrong problem ;

-in a classic managed environment, you don't need those checks : you already have full control of the clients, and you don't allow foreign devices on your network.Or, indeed, you comparimentize (eg "trusted" vs "tolerated" clients) . So NAP is, at best, a safety net to catch the sysadmin's mistakes. Or you could call it an *additional layer* of security.  

-in a more open environment (BYOD  on the wifi network, allowing remote access with private equipment, ...)  NAP doesn't make sense  -- unless your policy is "BYOD as long as it's a Windows device", cfr supra. In this type of environment you have to rethink your security in terms of  authentication, authorization and auditing (focus : users)  where NAP makes security assumptions based on configurations (focus:machines). This most likely also involves tighter security on your servers  (but NAP is more concerned about *clients*)

The idea is roughly the following : if a server serves web applications, nothing else on that server should be accessible to a regular user, and  if  a user is allowed access to a web application, , security-wise  it doesn't really matter if he does it from a a company owned windows PC, his own private Mac, or an android tablet, or does it ?
There's a bit more to it than that, but that's the main idea.

---

