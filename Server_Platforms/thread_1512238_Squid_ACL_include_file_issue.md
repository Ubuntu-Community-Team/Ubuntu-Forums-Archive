---
title: "Squid ACL include file issue"
date: 2010-06-17
forum: Server Platforms
---

### Post by Jerber9264 on 2010-06-17
How's it going everyone?
 
I am currently running squid 2.7 with no real problems. The question I have is about the include file. 
 
I have an acl statement that reads like this : 
[LEFT][COLOR=blue]acl click dstdomain "/home/jeremy/Documents/domainNames.txt"[/COLOR]
[COLOR=blue]http_access deny click[/COLOR][/LEFT]
 
[LEFT][COLOR=black]Now whenever I type the domain names listed in the file (For example, doubleclick.net) into a browser, the sites are blocked and everything works. But when I go to certain sites such as playlist.com, some advertisements that should be blocked are not. But If I make a seperate ACL statement for doubleclick.net and deny it, the advertisements on playlist.com are blocked. [/COLOR][/LEFT]
 
[LEFT]My question is, why does the include file not block the advertisements?
 
Any recommendations are welcome.
 
Thank you for your time[/LEFT]

---

