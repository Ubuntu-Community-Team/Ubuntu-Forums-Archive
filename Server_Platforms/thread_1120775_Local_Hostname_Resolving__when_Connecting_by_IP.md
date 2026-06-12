---
title: "Local Hostname Resolving  when Connecting by IP"
date: 2009-04-09
forum: Server Platforms
---

### Post by Cretin_Yes on 2009-04-09
Hi all,

I have a LAMP server running, and everything is working on the local network.  Unfortunately, when I try to access the site from a remote location, I only receive the html for the index page, no working links, no images.  When I check the links, they are linking by the local machine's name, and not the IP.  I'm trying to set up wordpress so I imagine the links should already be relative.  How can I fix this?  

Some useful info:
The system is behind a NAT router, on a private addressing scheme.  I have port forwarding enabled, which is what is getting me access to the index page, if not all the references and links.  

Is this a network problem?  Apache?

Thanks

---

### Post by BkkBonanza on 2009-04-09
This sounds like a page content issue, not networking. Your links need to all be relative. If using an IP to access then you don't want any absolute references to content, ie. no local host name, just relative paths.

---

### Post by Cretin_Yes on 2009-04-09
The thing is, I don't see why wordpress would hardcode static links when to my understanding its meant to be portable - and why choose the local hostname?  I certainly didn't tell it to.  It is possible its a wordpress issue - I'll look into it more.

---

