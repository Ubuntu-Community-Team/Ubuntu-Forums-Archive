---
title: "Setting up VPN between Ubuntu Server and OSX"
date: 2008-04-28
forum: Server Platforms
---

### Post by samalex on 2008-04-28
Hi...  

I've just setup Ubuntu Server 8.04 at home to house our data, and I'd like someway to connect in via our broadband connection with my OSX laptop while on the go.  I assume PPTP is the best route with PopTop, but I wanted to see if anyone knew of caveats or other options I should look at.  I've installed pptpd (PopTop) via apt-get, but i'm just now starting to read-up on how to configure it ... so just curious.

Thanks,

Alex

---

### Post by Space-Age on 2008-05-05
I've been trying to do this same thing, but when running 'sudo apt-get install pptpd', it just pauses at Starting PPTP Daemon:  Wait and wait an nothing happens.  Did I miss something?

---

### Post by Space-Age on 2008-05-06
Kind of solved it.  

When the Starting PPTP Daemon was hanging on install, I ended up running 'sudo dpkg -P pptpd' first.  Then ran 'sudo apt-get install pptpd' again, and everything worked fine.  My OS X machine can now establish a connection to the Ubuntu VPN Server!!

---

