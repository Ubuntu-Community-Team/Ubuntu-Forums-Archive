---
title: "Ubuntu 10.10 on Hyper-V Failover cluster"
date: 2012-11-02
forum: Server Platforms
---

### Post by sentinelace on 2012-11-02
I have hyper-v running on 2008 R2 datacenter. It is working and failing over. The issue is, when this server fails over the Ubuntu guest nic doesn't work until I restart the server. I have the hyper-v drivers installed. Is there something else that needs adjusted for this to work properly? All windows VM's work fine.  When it fails over the nic seems to change from Eth0 for example to Eth2.  How can this be prevented?

---

### Post by sentinelace on 2012-11-06
no one?  :(

---

### Post by angryfirelord on 2012-11-06
There was this post make on the Technet forums: [http://social.technet.microsoft.com/Forums/en-US/winserverhyperv/thread/3b277224-ab02-4d48-b413-9bbcea9e724e]("http://social.technet.microsoft.com/Forums/en-US/winserverhyperv/thread/3b277224-ab02-4d48-b413-9bbcea9e724e")

I'd also make sure Hyper-V is updated, as I'm sure Microsoft has released hoxfixes for it.

---

### Post by sentinelace on 2012-11-07
Setting the static mac fixed it.  Thanks for the pointer!!!

---

