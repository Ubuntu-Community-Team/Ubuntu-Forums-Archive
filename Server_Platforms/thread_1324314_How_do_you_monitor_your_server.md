---
title: "How do you monitor your server?"
date: 2009-11-12
forum: Server Platforms
---

### Post by hellarough on 2009-11-12
I was looking around in the security discussions forum and I found an awesome sticky about Intrustion Detection/Prevention system (using snort and some other package) that I would love to set up one day. However, until I can set that up I would like to be able to monitor my network/server to make sure that no one is getting through. 

So far I am checking the apache access.log and filtering out any internal IP addresses with grep like this -->

grep -v "192.168.x.x" access.log

I know that this is a really crude way of inspecting the log so I wanted to see the community's ideas. How do you monitor your server, keep it secure, and make sure that all access is authorized access only?

---

### Post by TuckLive on 2009-11-12
Other than BASE/SNORT, I use OSSEC and [IPAudit]("http://ipaudit.sourceforge.net/").

For some screenshots of IPAudit look [HERE]("http://www.securityfocus.com/infocus/1842/2")

---

### Post by noway2 on 2009-11-12
I too use the BASE/SNORT + OSSEC, as described in the sticky.  I too was hesitant to install it and set it up as it looked very complicated.  It turns out that it really wasn't, but it did take a couple of hours to go through everything.

I suggest that you just go ahead and install it.

---

### Post by hellarough on 2009-11-13
> **noway2 said:**
> I too use the BASE/SNORT + OSSEC, as described in the sticky.  I too was hesitant to install it and set it up as it looked very complicated.  It turns out that it really wasn't, but it did take a couple of hours to go through everything.

I suggest that you just go ahead and install it.

Yeah, I am when I get the free time but the problem is that I dont see myself having a few hours like that until next week or so. I just figured that I would see what other people are doing to see if there was some quick easy way of doing it in the mean time plus it almost seems like overkill for my small setup (always a good learning experience though!) 

I do have one question though; say I were to develop a bit of a larger network in the future with a router and say three Linux servers. Would the BASE/SNORT + OSSEC have to be deployed at the machine level or could it be deployed on one master firewall to monitor all servers? I guess what I am really aiming for is eventually learning enough to set up a network with a couple of servers that will suit the needs of a small to medium (like 100 employees in the same office) business. I know servers and networking well enough (probably nothing like I should) but almost nothing about security. 

If you cant tell I cant wait to try out that sticky....I should just quit my job so I can sit at home and tinker around with toys all day.

---

