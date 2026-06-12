---
title: "Is hexchat and synaptic available for Focal?"
date: 2020-03-25
forum: Ubuntu Development Version
---

### Post by wildmanne39 on 2020-03-25
I have Ubuntu Mate 20.04 installed and I am still setting it up, I am not able to install hexchat or synaptic, I am guessing they are not available yet for 20.04 is that correct?

---

### Post by Irihapeti on 2020-03-25
Iv'e been using synaptic in Xubuntu for quite a while, so, yes, it's available. I've not tried to install hexchat, so I have no idea.

However, I've been having some problems with synaptic with wayland, such as serious lockup. A bug has been reported, but no progress that I can see.

---

### Post by guiverc on 2020-03-25
I'm on 20.04 & `hexchat` is my used IRC client.  I also have `synaptic` installed  (I'm more likely to use `aptitude` though).  Note I don't use wayland  (using LXQt today, but used XFCE yesterday being installed too)

```
guiverc@d960-ubu2:~$   apt-cache policy hexchat
hexchat:
  Installed: 2.14.3-3
  Candidate: 2.14.3-3
  Version table:
 *** 2.14.3-3 500
        500 http://ftp.iinet.net.au/pub/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status
guiverc@d960-ubu2:~$   apt-cache policy synaptic
synaptic:
  Installed: 0.84.6ubuntu5
  Candidate: 0.84.6ubuntu5
  Version table:
 *** 0.84.6ubuntu5 500
        500 http://ftp.iinet.net.au/pub/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status

```
(*I'm using my ISP's mirror; that used to mean upgrades weren't counted on my monthly bandwidth quota, alas they changed policy.. but I haven't switched it yet*)

---

### Post by wildmanne39 on 2020-03-25
I was just able to install both of them, I walked away from my laptop while Ubuntu Mate was installing and did not know that the updates did not install like they  were supposed to during installation and my wifi connection was very slow so the updates took about an hour to download, now that they are I was able to install both programs and I think I have my wifi issue resolved to but it is slow going on getting everything back to the way I like it.

Thanks for the replies.

---

### Post by DuckHook on 2020-03-26
> **wildmanne39 said:**
> …it is slow going on getting everything back to the way I like it…
Wild Man, if you are doing a bare metal install of a new OS, you may want to check out the tutorial I wrote on sandboxing apps with LXD. Link in my sig. I've been migrating a ton of apps into LXD containers and, so far, it's amazing. Hexchat would be a good candidate. Synaptic, you would want on your host OS obviously.

---

### Post by wildmanne39 on 2020-03-26
> **DuckHook said:**
> Wild Man, if you are doing a bare metal install of a new OS, you may want to check out the tutorial I wrote on sandboxing apps with LXD. Link in my sig. I've been migrating a ton of apps into LXD containers and, so far, it's amazing. Hexchat would be a good candidate. Synaptic, you would want on your host OS obviously.

Thanks DH, I will read up on it and see what I can learn.

---

