---
title: "OFBiz Install questions"
date: 2007-01-28
forum: Server Platforms
---

### Post by tfunky on 2007-01-28
Hello,

I'm trying to get OFBiz installed on Ubuntu server 6.10.

It requires Java JDK 1.4.2 (not 1.3 or 1.5)

All the documentation I've found on how to install it show how to get 1.5 installed.

Can someone point me in the right direction on how, specifically, to get 1.4.2 installed so I can try to finish getting OFBiz/OpenTaps installed?

also...anyone who has installed OFBiz and can pass along any tips/tricks/gotchas would also be appreciated!

Thanks for your help!!!!!

Tfunk

---

### Post by tim.n9puz on 2007-03-14
I'd be curious to know if you have learned anything further about OFBiz. I'm starting to research ERP systems and would prefer to run one on an Ubuntu server since I already run a couple of these servers and it would be good to keep them in sync.

Tim

---

### Post by carl.davis on 2007-05-07
Here is what I did to get it to work:

sudo aptitude install j2re1.4

export JAVA_HOME=/usr/lib/j2se/1.4/

./startofbiz.sh

Then go to [http://127.0.0.1:8080](http://127.0.0.1:8080)

I still however cannot get the POS system to start.

---

