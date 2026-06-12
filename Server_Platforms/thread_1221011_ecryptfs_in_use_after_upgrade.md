---
title: "ecryptfs in use after upgrade?"
date: 2009-07-23
forum: Server Platforms
---

### Post by timefortea on 2009-07-23
Hi all,
I have Ubuntu 9.04 Server installed on my server. I don't think I had performed any updates on it since I did the initial install. Then the other day I performed an update with:
apt-get update
apt-get upgrade
Afterwards I rebooted (just for luck) and when I logged into the machine I got an error about being unable to access my home directory. When I looked in the home dir, there is a readme telling me that I need to use ecryptfs to un-encrypt my home directory. This is odd, I have to supply the utility with my passphrase but I don't have one since I never thought one up in the first place - I have never used ecryptfs. 

Could this be something I have done, a known issue or something more sinister? My server is behind an ADSL router and I don't have any port forwarding to it, so I assume its nothing sinister. I couldn't see anything like this on launchpad. Any help appreciated.

Thanks.

---

### Post by ahh_Jebubs on 2009-08-12
I've just ran into this problem, also on 9.04 server. Did you have any luck getting it sorted?

I had access to my server over ssh this morning, but now there's just two files; Access-Your-Private-Data.desktop and a readme telling me its been unmounted to protect my data. 

Its looking for a passphrase but I've never used ecryptfs so no idea what the passphrase is. wtf?

---

