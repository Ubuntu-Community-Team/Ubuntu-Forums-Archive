---
title: "Unknown connections to Canonical?"
date: 2010-12-08
forum: Security
---

### Post by wi0 on 2010-12-08
Hello all,

This is a freshly installed 10.10 system. I see two connections from **gvfsd-htt** to sumac.canonical.com:https and papeda.canonical.com:www. Both are in the (CLOSE_WAIT) state. This can be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/571970"), but it's not very important.

I would like to know what these are.

I know they're not synaptic/update manager which show as http and not gvfsd-htt and connect to different servers. Ubuntu One is uninstalled, and no java package is present.

One of them is encrypted too. 

If the host names are dedicated to specific usage, maybe it would be easy to answer this question. In any case, I would appreciate any ideas.

Thanks.

---

### Post by wi0 on 2010-12-10
I now noticed the https connection to sumac is established when running the Ubuntu Software Center. I would still like some info on this functionality.

---

### Post by wi0 on 2010-12-11
Is there a better place for this question?

---

### Post by cariboo on 2010-12-11
I's hard to tell which servers do what, but your installation does check the Ubuntu time server, if you have it enabled, your system sends result for popularity contest, and it usually checks for updates on every restart, even if you have update notifications disabled. You may want to check whether you have landscape-client installed, as that will check the landscape server too.

One other thing, if you have an oem system, it could be calling Canonical, just to say it's still alive.

---

### Post by wi0 on 2010-12-12
These connections appear only when launching the Software Center, so it seems unlikely that they would be associated with time synchronisation (which is set to manual anyway so shouldn't be connecting anywhere anyhow).

Popularity contest is not enabled, no landscape-client, and this a manual install - no oem canonical-census.

Disabling automatic updates in Synaptic should prevent update checking on restart, no?

In any case, this is something done by the Software Center.

> Resolving software-center.ubuntu.com... 91.189.89.105, 91.189.89.106Which are the IPs to which the servers resolve. I'm just not sure why an SSL connection is necessary - regular software installs are not encrypted. I'm now mostly curious.

---

### Post by cariboo on 2010-12-12
An ssl connection may be needed for the music store, or to purchase software. I don't use the software center, as I find it doesn't give me the same experience as synaptic.

---

