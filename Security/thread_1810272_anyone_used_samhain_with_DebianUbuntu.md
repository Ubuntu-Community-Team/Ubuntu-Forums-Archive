---
title: "anyone used samhain with Debian/Ubuntu?"
date: 2011-07-22
forum: Security
---

### Post by sneakyimp on 2011-07-22
I'm wondering if anyone has any experience with [samhain](http://www.la-samhna.de/samhain/index.html), an intrusion detection system, on Debian and/or Ubuntu.  In particular, I'm interested in the client-server setup where the machine to be monitored acts as a client to a machine doing the monitoring.  Because this process involves multiple machines, I tend to doubt that simply installing it via "apt-get install" is the right approach.  The documentation says to install samhain on the client and "yule" on the server.

On the other hand, manual compilation and configuration looks difficult and will not result on software being updated frequently.

Any advice would be much appreciated.

---

### Post by bodhi.zazen on 2011-07-23
> **sneakyimp said:**
> I'm wondering if anyone has any experience with [samhain](http://www.la-samhna.de/samhain/index.html), an intrusion detection system, on Debian and/or Ubuntu.  In particular, I'm interested in the client-server setup where the machine to be monitored acts as a client to a machine doing the monitoring.  Because this process involves multiple machines, I tend to doubt that simply installing it via "apt-get install" is the right approach.  The documentation says to install samhain on the client and "yule" on the server.

On the other hand, manual compilation and configuration looks difficult and will not result on software being updated frequently.

Any advice would be much appreciated.

I have installed it and had nothing but frustration with it.

Installing the client is easy enough, but getting the rest up (server side) and running was an exercise in frustration. I was eventually able to get it up and running, but found it was not exactly what I wanted.

The samhain documentation was sketchy and I ended up staying with OSSEC.

samhain is a fantastic product, but there is a steep learning curve and it takes time both to learn and maintain.

---

### Post by sneakyimp on 2011-07-24
I appreciate your unvarnished assessment. Do you have any additional detail about the server frustrations you experienced? I hope to take a look at it and would truly appreciate if you could spare me some of the hardship.

Did you install it using apt-get?  If so, did it install both the server (yule?) and the client?

What are the differences between samhain and OSSEC?

---

