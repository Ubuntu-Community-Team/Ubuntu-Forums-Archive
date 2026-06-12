---
title: "xdmcp security issues"
date: 2009-03-07
forum: Security
---

### Post by shahin on 2009-03-07
Greetings-
    I am looking at procedures at: [https://help.ubuntu.com/community/HowToCygwinX](https://help.ubuntu.com/community/HowToCygwinX) to setup cygwin access to my server, and it says xdmcp has some inherent security issues.  I am not sure how old these procedures are, and wonder if these security issues are addressed or they still hold?  
Also are there updated procedures?  
In short what is the best way to remote desktop to my ubuntu server in a secure way?

---

### Post by Nxion on 2009-03-10
Are you going to be connection for your internal network or from somewhere offsite like school or work? If you are just connecting from your local network, then xdmcp or VNC is fine. If you will be connecting from somewhere off site, then you can tunnel vnc and rdp over SSH so it is all encrypted,

---

### Post by shahin on 2009-03-10
Well I want to have both options.  I tested VNC, and it is really slow even when I access it from home.  Also, maybe I am not using it right, but I found that I could not switch from one desktop to the next withing the linux environment.  Is there a better solution?  I tried nomachine's NX.  But for some reason the connection timeout rightaway. I posted my logs in the general news group but I have not received a reply.

---

