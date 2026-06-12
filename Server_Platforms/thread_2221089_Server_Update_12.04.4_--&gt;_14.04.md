---
title: "Server Update 12.04.4 --&gt; 14.04"
date: 2014-04-30
forum: Server Platforms
---

### Post by TheFu on 2014-04-30
```
$ sudo do-release-upgrade 
Checking for a new Ubuntu release
No new release found

$ more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"

```
Ran this today on a 12.04 x64 server.  Do I manually need to modify the /etc/apt/ stuff to get the 14.04 server updates?
Or is there a policy of not advertising server updates until the .1 release?
Or something else?

---

### Post by CharlesA on 2014-05-01
Nono, do this:

```
sudo do-release-upgrade -d
```

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

LTS to LTS will be enabled once 14.04.1 hits, but the above command should let you upgrade to 14.04 now.

---

### Post by TheFu on 2014-05-01
```
$ sudo do-release-upgrade -d | tee log
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                            
Get:2 Upgrade tool [1,148 kB]                                                   
100% [Working]                                                                  
Reading cache

Checking package manager

```

Left it for 30 minutes. Nothing more.  

I'm about to load up a new virtual machine server and wanted to start out with 14.04. It has 12.04 on it with a few VMs now that cannot be moved (hardware and networking reasons). If it doesn't get 14.04 soon, it will likely run 12.04 until 2017.

I did review this: [https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes) ... since it is a pure VM server today (just the bridging and NIC assignments are complicated) most of the things inside that link do not apply.  I should mention that nominal patching works fine and we use apt-cacherng internally.

---

### Post by CharlesA on 2014-05-01
Huh. I just did that yesterday and it ran fine. Maybe you have to change it so it doesn't hit the apt-cache server?

---

### Post by TheFu on 2014-05-29
Finally got back home and removed the apt-cacherng from the config, temporarily.

Worked fine over ssh to my headless server (no VGA output, but I only have VGA on the KVM switch).  So far, everything has been seamless in the upgrade - samba, nfs client, bridge configuration, KVM server - all working.

Thanks Charles.

---

### Post by CharlesA on 2014-05-29
Awesome. Glad it worked!

---

