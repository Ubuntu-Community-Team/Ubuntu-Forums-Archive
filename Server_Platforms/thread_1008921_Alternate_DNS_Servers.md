---
title: "Alternate DNS Servers"
date: 2008-12-12
forum: Server Platforms
---

### Post by kooseefoo on 2008-12-12
Hi all!

Quick question here: my ISP's DNS servers don't always work, and actually cut out pretty often. Are there any good DNS's (secure, reliable, etc) available that I could point my stuff to to avoid this problem?


Thanks,
Chris

---

### Post by falconed7 on 2008-12-12
Check out [www.opendns.com](www.opendns.com)

I use them and have had absolutely no problems.

---

### Post by madverb on 2008-12-12
Or you could set up your own DNS on your server!

---

### Post by Dr Small on 2008-12-12
> **falconed7 said:**
> Check out [www.opendns.com](www.opendns.com)

I use them and have had absolutely no problems.
+1 for OpenDNS

---

### Post by MystaMax on 2008-12-12
+1 here for OpenDNS as well. They offer a very good service.

---

### Post by CrucifiedEgo on 2008-12-12
if for some reason you can't use opendns (or you can't remember their IPs) there's always the trusty 4.2.2.2 and 4.2.2.3.

---

### Post by hictio on 2008-12-12
You should be aware that there are some privacy concerns regarding OpenDNS:

[Why opendns is evil](http://fr.pastebin.ca/689242)
[Privacy issues and covert redirection](http://en.wikipedia.org/wiki/OpenDNS#Privacy_issues_and_covert_redirection)

That being said, I have been a long time user, even registered one, os their service... Right now I feel a bit orphan.

---

### Post by martien on 2008-12-13
The best way is to run your own dns server and set forwarders 
First of all: to your isp dns servers
And second: to opendns or whatever dns severs you like.
There is a possibility to write perl/python/shell script to check your activity with your ISP dns and if its down then to reconfigure your dns server with the alternative dns severs. Put all this into cron job script and it will work just fine.

---

### Post by kooseefoo on 2008-12-14
DHCP is handled by my router, so couldn't I just specify the opendns as an alternate DNS server in the router settings?

If I chose to set up my server as a DNS, then I would be able to just point the router to my DNS server, and specify the alternate as my ISP servers (in case my DNS goes down), correct?

---

### Post by adaptr on 2008-12-14
> If I chose to set up my server as a DNS, then I would be able to just point the router to my DNS server, and specify the alternate as my ISP servers (in case my DNS goes down), correct?
That depends on how your router works, and whether you can enter static nameservers at all with whatever access method you are using.
If the device allows you to specify internal nameservers (which would be kind of silly) then yes, you can - but then it would also be trivial to set up DHCP on your own server, and not use the router.

---

### Post by lswb on 2008-12-14
There's a bunch of alternatives but 2 that I find easy to remember are 4.2.2.1 and 4.2.2.3

---

### Post by hictio on 2008-12-14
> 
There's a bunch of alternatives but 2 that I find easy to remember are 4.2.2.1 and 4.2.2.3


I moved myself from OpenDNS to those two myself, but, and maybe that has something to do with my location, name resolution is way slower than with OpenDNS.

---

### Post by kooseefoo on 2008-12-14
The router is a Linksys WRT54G with DD-WRT installed.


For my server to run DHCP, I would need dual LAN cards in there, correct?

---

### Post by martien on 2008-12-15
The request method of the dns calls is randomized - the computer gets one of the dns records in your configuration or the other, no matter which is first. The second dns is usually set by the ISPs for server load optimization. My opinion is that you should use other dns servers but your ISP only when its necessary (when your ISP dns servers are down), cause the connection between you and your ISP is different than you and Opendns for example. (the idea for changing router options is bad at this stage) => so the best way for you is to make caching server and reconfigure it to opendns/some free dns providers/etc. when your ISP's dns-es are down. And dont forget to set manual configuration of your pc, so you can point the dns to your own dns server. The routers give the given to them dns server to the clients. There are a few models that have their own dns server. Good luck.

---

### Post by MystaMax on 2008-12-15
I use to run DD-WRT, but found out about the [Tomato Firmware]("http://bit.ly/nTxhh"), and now run it on my WRT54g router. I find its interface much more pleasing to look at and manage. The only downside I see with Tomato compared to DD-WRT, is that DD-WRT has addons for OpenVPN servers and VOIP services. Other than that, their pretty much the same (someone correct me if I'm wrong here).

I think OpenDNS is perfect if you're ok w/ the privacy concerns [hictio]("http://ubuntuforums.org/showpost.php?p=6358644&postcount=7") mentioned earlier in the thread.

Attached is a screenshot of my DNS settings on my WRT54g. You'll see that the third Static DNS server is 4.2.2.2, which I used in the past, before OpenDNS. Its now there for backup purposes.

---

### Post by Ferret-Simpson on 2008-12-16
OpenNIC is an open source "Alternate TLD"

Basically, we have Open Source OS's, Open source applications, Open Source networking technologies and open source hardware.... Why exactly is our Domain Name system still under direct control of the US Government and corporations (Rhetorical Question, I know it's money.)

So OpenNIC is a comminuty based DNS that gives access to traditional ICANN domains (.com .net .org etc) but also allows the creation of community hosted Top Level Domains as well: (.bbs, .geek, .null, .parody, .ing, .s, .fur, couple others) And it's lightning fast.

So....[www.opennic.org](www.opennic.org) and [www.opennic.org.uk](www.opennic.org.uk) are my votes.

---

### Post by Dr Small on 2008-12-16
> **Ferret-Simpson said:**
> OpenNIC is an open source "Alternate TLD"

Basically, we have Open Source OS's, Open source applications, Open Source networking technologies and open source hardware.... Why exactly is our Domain Name system still under direct control of the US Government and corporations (Rhetorical Question, I know it's money.)

So OpenNIC is a comminuty based DNS that gives access to traditional ICANN domains (.com .net .org etc) but also allows the creation of community hosted Top Level Domains as well: (.bbs, .geek, .null, .parody, .ing, .s, .fur, couple others) And it's lightning fast.

So....[www.opennic.org](www.opennic.org) and [www.opennic.org.uk](www.opennic.org.uk) are my votes.
Hey, that is absolutely cool. Now I am browsing .glue websites :)

---

### Post by Ferret-Simpson on 2008-12-16
Ridiculously fast too, isn't it?

---

