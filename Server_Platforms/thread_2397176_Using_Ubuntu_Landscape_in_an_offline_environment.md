---
title: "Using Ubuntu Landscape in an offline environment"
date: 2018-07-26
forum: Server Platforms
---

### Post by psalisbury1871 on 2018-07-26
Hi, 


I have a number of Ubuntu servers that run on an airgapped network with no internet connection. Is there any way to setup an "offline" Landscape server to manage these servers with patching etc? Is it possible to install the software without it having to talk back to Ubuntu? If its not possible is there an alternative?

At the moment i have a Ubuntu pc configured to pull down updates using apt-mirror scheduled to run using cron jobs. Then i copy the folder to a hard disk then import it on to the mirror machine on the network. 

I have setup a similar thing with Microsoft WSUS, exporting from an online wsus box then importing the updates to the offline server.

Many thanks for any help you can give.

---

### Post by TheFu on 2018-07-28
Welcome to the forums.

You will need to contact Canonical for help with this. Nobody here works for them. We are all volunteers here.  I'm not interested in using cloud services, but can understand why that might be attractive to others.

I've worked in air-gapped networks.  Bringing any new code into the environment was part of my job, but at least 3 different humans were involved to ensure the rules were followed. We didn't have any Windows or Linux there (at the time). It was all commercial versions of Unix many with custom realtime kernels built by our kernel team and almost all the application software was custom.

---

