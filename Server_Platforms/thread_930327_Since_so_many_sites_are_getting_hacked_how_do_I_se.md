---
title: "Since so many sites are getting hacked how do I secure my server and sites?"
date: 2008-09-25
forum: Server Platforms
---

### Post by kustomjs on 2008-09-25
Alright Guys,

I need to know how to secure my server and sites from hackers since Bill O'Reilly's site and Palin's email was hacked over few weeks and I want to know how to protect my server and customers information and pages safe from hackers?

---

### Post by cariboo on 2008-09-25
You are never going to be able to set up a totally secure server, Have a look here for a server administration guide:

[http://www.tldp.org/LDP/sag/html/index.html](http://www.tldp.org/LDP/sag/html/index.html)

and here:

[http://www.tldp.org/LDP/nag/node1.html#SECTION001000000](http://www.tldp.org/LDP/nag/node1.html#SECTION001000000)

Jim

---

### Post by Robstarusa on 2008-09-26
The basics always apply>

VERY good passwords, or even better -- certificates/keyfiles.
Turn off all unused services.
Keep up to date with security patches.
Audit any custom code (such as php scripts, etc) to make sure it is secure to the best of your knowledge.
Install an IDS and/or read the logs daily.

---

