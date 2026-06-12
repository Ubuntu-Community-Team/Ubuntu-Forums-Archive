---
title: "suggestion for secure web server"
date: 2016-12-26
forum: Server Platforms
---

### Post by marchello_lippi2 on 2016-12-26
Hi all, 

I would need your suggestion for secure web server. 
Thanks ahead.

---

### Post by cariboo on 2016-12-26
Moved to server platforms.

Have a look [here]("https://ubuntuforums.org/showthread.php?t=1046738").

---

### Post by marchello_lippi2 on 2016-12-27
Did not really get it. Is it suggestion for apache2 web server? Is it really secure?

---

### Post by TheFu on 2016-12-27
> **marchello_lippi2 said:**
> Did not really get it. Is it suggestion for apache2 web server? Is it really secure?

There isn't anything that is "secure."  It comes down to how the server is setup, then apache, then the content, then the web-app running, then the network security, and firewall, and IDS/IPS, and, and, and ... it is a moving target that can easily be completely non-secure by running a poorly written theme on a wordpress instance or allowing plain FTP use.

So the "secure web server" question doesn't really make sense.  No server is secure, unless you make it so. Every server is a little different with slightly different risks. Mitigation strategies are different based on background, skills, knowledge.  For example, I always run a reverse proxy which filters by source IP and requested URL.  Some parts of the world have no business even accessing certain servers that I run, so they are blocked.  Some of that blocking happens multiple places - the router, the firewall, the server-firewall, the reverse proxy, and the web-app config.  

"Secure Server" is not a check box. Sorry.

Why not?  Because many people don't actually need a secure web server.  They are serving pgs inside a company to 100K intranet users, so the risks are significantly less and performance is more important than mitigating nasty internet visitors.

---

