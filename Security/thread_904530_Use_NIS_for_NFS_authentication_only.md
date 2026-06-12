---
title: "Use NIS for NFS authentication only"
date: 2008-08-29
forum: Security
---

### Post by rangans on 2008-08-29
Hi guys,
       I have setup an NIS server following the how-to in the community documentation. But the users/clients are going to be mobile laptops. They want to be able to login and work offline on code that they checkout. But when they are on campus they have to transfer files to and from NFS with NIS authentication. I can get them to use the same username and even password if need be. Can somone help me to make NIS just authenticate NFS and the rest is done by the local system level authentication. Also these laptops wont have a static IP address even they are on campus as they will be connected through a wireless network at times so is it possible to avoid the list of static client IP address to the server. I dont think this would be a problem since the server is behind a proxying firewall/gateway of the IT department anyway. Thanks.

---

