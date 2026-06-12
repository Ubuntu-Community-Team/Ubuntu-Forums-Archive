---
title: "fixed ip address for ubuntu guest OS in vmware"
date: 2017-06-01
forum: Virtualisation
---

### Post by shivashivasiva2 on 2017-06-01
Hi,

I had a guest OS ubuntu12.04 installed in vmware with windows10 as Host PC. 
In windows10, I want to access the files that were created in ubuntu. So the approach that I got on top of my head is to map the network drive in windows10 through samba share in ubuntu and I am successful in doing that. But the problem with this approach is I need to map the dynamic ip address of my virtual machine each time i move from office network to home network. 

BTW, The network connection in the VMware settings is **bridged network** 

So is that possible to configure fixed ip with internet access in vmware ? 

Looking forward for some help...

---

### Post by TheFu on 2017-06-01
Support for 12.04 ended.

Whether you can setup a static IP easily is really dependent on whether the networks at home and work are the same. This is because you've selected a bridged network.  

If you use a NAT'd network, then I think you have more control. Think you'll need to do some port forwarding to make it work. I don't know.

Regardless, #1 task is to move to a supported release.

---

### Post by wildmanne39 on 2017-06-01
*Thread moved to **Virtualisation**.*

---

### Post by sp40140 on 2017-06-02
Aren't you able to find the share using the hostname (of Ubuntu vm)? You should be. Or map the drive using hostname? May be when you connect to work network, you need to tell windows that it's work network. Windows asks you about it when you connect to a network first time.
But the best set-up for you is to use a data partition (NTFS) as you can grant access to both host and guest to that drive and modify the files as you please.

---

