---
title: "Multiple applications on Tomcat"
date: 2019-08-25
forum: Server Platforms
---

### Post by ScorpioTiger on 2019-08-25
I'm currently managing a number of VPS running applications under Tomcat; specifically Alfresco, Jira, and Pentaho. I'd like to see if I can save on hosting (and probably maintenance) by moving these applications to a single server. Research to date tells me that I can run multiple applications under a single Tomcat instance. I am however left with a number of questions;

How do I go about determining RAM and CPU requirements? Storage is easy as it's simply an aggregate of our current storage usage, but RAM will surely depend on how much overhead there is in having each application running when there's zero load and concurrency. We have very few concurrent users, so most of the time the applications are sitting dormant and the current server resources are not being hit.

What would be best practise for isolating these applications, but still getting the advantages of running a single RDBMS, Tomcat instance etc (if this is even a good idea)?

Whilst I have found myself acting as a sysadmin, I'm certainly not knowledgeable enough to be able to make informed architectural decisions such as this. Any advice on how to go about this or even if it's a good idea would be most appreciated.

---

### Post by TheFu on 2019-08-25
I only know Alfresco, not the others.

Keep Alfresco in either its own VM or own Container. Don't attempt to mix it with others.  Alfresco is a complex enterprise application that is picky about all the dependencies.  If the other two are similar, keep them separate too.  You'll thank me at patch and upgrade time.

As for RAM and CPU requirements, your current monitoring should provide educated guesses.  You should test the estimated TPS so you know what it can handle before any serious load happens.

As for the DBMS, check how specific on the version each of those tools is about the DBMS version. Hopefully, they aren't, but you never know until you look.

---

### Post by ScorpioTiger on 2019-08-30
Thank you for your input. I'll look closer at dependencies.

---

