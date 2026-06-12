---
title: "Server Advice Needed"
date: 2011-04-30
forum: Server Platforms
---

### Post by dfgilbert on 2011-04-30
**So, here's the deal:**

I'm running win 7 64 as my host OS.  I've installed Virtual Box, with Ubuntu 11.04 64-bit server.  I have a basic-intermediate understanding of networking, but I need some help and advice.

So incase you wonder why I want to do this, I want to create my own web-based job scheduler.  Since my netbook can't crunch the numbers for me without freaking out and taking forever.  So I can upload, code, scripts, and lists of parameters and pass a command to execute/compile, whatever and return my results in a document via dropbox or ubuntu one, or some other cloud service.  

Also, the reason that I want to develop in a client-server setting is so when I go to deploy, I know what to do and how to maintain it, instead of learning server administration after the fact.

The server is going to run tomcat and my java services.

**Where I need advice:**
Eventually I'm going to want to put the server online.  So I can access it remotely.  I'll probably use a service like dyndns.

What kind of advice can you give me for protecting my server?  I've never admined a server before outside of a controlled environment.

Lets say, I have my virtual server running.  And it doesn't have any shared folder access.  Is my host OS secure?  Or does putting a virtual server online put my host OS at risk of intrusion?  The reason I ask this is because I notice, as I expected, that my virtual box registers its network card on the same IP as my host OS.  So will opening my virtual server up expose my host machine?

I'm going to assume, for at least "better safe than sorry", that I should just go ahead and purchase a second network card and put my server on that card when I get ready to go live.  Right?

I'd post more information, if I knew which information would be helpful.

Also, I'd really appreciate any server admin blog links or websites or even good book recommendations.

---

### Post by Lars Noodén on 2011-04-30
> **dfgilbert said:**
> 
What kind of advice can you give me for protecting my server?  I've never admined a server before outside of a controlled environment.

Ubuntu itself is secure out of the box.  Weak points on the server will be your application.  Be sure to validate all input, always.  If you use a database, then use the API for it and use Prepare and Execute statements and placeholders.  Use taint mode to manage variable taint.

---

### Post by falko on 2011-04-30
You might want to install fail2ban to block break-in attempts: [http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)

---

### Post by dfgilbert on 2011-04-30
> **Lars Noodén said:**
> Ubuntu itself is secure out of the box.  Weak points on the server will be your application.  Be sure to validate all input, always.  If you use a database, then use the API for it and use Prepare and Execute statements and placeholders.  Use taint mode to manage variable taint.

Thank you for that advice.  It's been so long since I did any web programming I forgot all about breaking applications with bad input, like injection attacks.

---

### Post by dfgilbert on 2011-04-30
> **falko said:**
> You might want to install fail2ban to block break-in attempts: [http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)

Thank you, this looks like a very good tool.

---

