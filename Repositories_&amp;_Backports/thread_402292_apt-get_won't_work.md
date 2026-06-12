---
title: "apt-get won't work"
date: 2007-04-05
forum: Repositories &amp; Backports
---

### Post by cris on 2007-04-05
i just finished installing ubuntu 7.04 and want to install the video drivers (nvidia) . the problem is that when I use the apt-get to install the driver , it won't work , no matter what package i want to install , it says "Couldn't find package..." . The internet works fine , I use another computer (on Windows) as a gateway . Please help me out! Thanks

---

### Post by spin2cool on 2007-04-05
Have you run "apt-get update"?  checked your /etc/apt/sources.list to make sure it's set up correctly?

---

### Post by johnc4510 on 2007-04-05
You probably need to enable the extra repositories not enabled after default install. Here is the how to page:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by tom56 on 2007-04-08
> **cris said:**
> i just finished installing ubuntu 7.04 and want to install the video drivers (nvidia) . the problem is that when I use the apt-get to install the driver , it won't work , no matter what package i want to install , it says "Couldn't find package..." . The internet works fine , I use another computer (on Windows) as a gateway . Please help me out! Thanks

Go to System->Administration->Restricted Drivers Manager

---

