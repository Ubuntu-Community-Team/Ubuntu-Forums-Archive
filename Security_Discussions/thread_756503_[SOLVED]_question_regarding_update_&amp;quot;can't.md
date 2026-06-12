---
title: "[SOLVED] question regarding update: &amp;quot;can't be authenticated."
date: 2008-04-15
forum: Security Discussions
---

### Post by ducttapemasterJ on 2008-04-15
So I am running a wifi network in my apartment and am having a problem with a hacker somewhere in my complex.  I've now got my wifi network protected with a very strong WPA security and MAC address filtering, which seems to have stopped him for the moment.  I don't know if this is a coincidence or not, but now the latest update in my update manager, called update-manager and update-manager-core just came up, and when I went to install it the update manager warned me that it couldn't be authenticated and that it may be a malicious attack.  I've never had that warning before on any package updates and I thought the timing to be odd.  
Any thoughts regarding how to keep this guy off my computer and/or if Im just being over-paranoid?
thanks!

---

### Post by Shazaam on 2008-04-16
You need to reload the package list. Either do it via Synaptic or run this in terminal.....
```
sudo apt-get update.
```

---

