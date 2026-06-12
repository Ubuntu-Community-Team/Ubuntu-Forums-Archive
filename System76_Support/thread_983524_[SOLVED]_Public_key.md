---
title: "[SOLVED] Public key?"
date: 2008-11-15
forum: System76 Support
---

### Post by VOLKOV9 on 2008-11-15
I followed the knowledge76 directions to update to 8.10 and everything so far seems to be working, except any time I update, use Synaptic, etc, it has this problem checking the system76 repo:

```
W: GPG error: http://planet76.com ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 176A5C84ED67C9ED
```

What can I do to correct this?

Thanks in advance.

---

### Post by drewbenn on 2008-11-16
Just add the System76 repository key.  These details (I think I actually only ran the second command) were included in a thread on the updated driver:

> **crichell said:**
> For good measure run the following two commands in your terminal to add the System76 repository and System76 repository signing key:

```
sudo wget http://www.planet76.com/sources.list.d/system76.list -O /etc/apt/sources.list.d/system76.list
```
```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

---

