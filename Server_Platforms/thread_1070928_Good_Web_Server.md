---
title: "Good Web Server?"
date: 2009-02-15
forum: Server Platforms
---

### Post by psychx on 2009-02-15
I am looking for a good web server that will be used to stream video and audio, and will be running a small "website" with a control panel and user access across a local network or across the internet. 

Any ideas? I have been looking around, but wanted to know if anyone had experience with a stable and fast webserver. There won't be a huge amount of load (only 1-2 active connections at any given time), so something that can run while I still use the computer would be preferable. Thanks!

---

### Post by psychx on 2009-02-15
Actually, a buddy of mine just told me about L.A.M.P - which he says is good. Any experience with this? I will go ahead and try this in the meantime.

---

### Post by bgates on 2009-02-15
LAMP is pretty much the way to go, and you already have the L, I take it.  :)

The control panel and website, has it already been coded?  In which language?

---

### Post by rmockler on 2009-02-15
Apache2 should be the answer you're looking for.

---

### Post by psychx on 2009-02-15
Awesome! I am loving this site more and more with each post. I really appreciate it.

And by the way, I am using a pre-coded content management system as my backend. Flash, PHP, and an SQL database will also be used for streaming and controlling users.

---

### Post by bgates on 2009-02-17
Linux, Apache, MySql, PHP will run from your computer and do almost everything you want.  If you were streaming Flash to a whole bunch of users then Apache might need to be tweaked some, but for this it should go fine as is.

---

