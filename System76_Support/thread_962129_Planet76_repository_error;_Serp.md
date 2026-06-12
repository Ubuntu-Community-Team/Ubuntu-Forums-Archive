---
title: "Planet76 repository error; Serp"
date: 2008-10-28
forum: System76 Support
---

### Post by thinman1189 on 2008-10-28
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 176A5C84ED67C9ED

W: Failed to fetch [http://planet76.com/repositories/./Release](http://planet76.com/repositories/./Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


Been getting this last week or so now. Any ideas?

---

### Post by drewbenn on 2008-10-29
Just add the System76 repository key.  These details (I think I actually only ran the second command) were included in the recent thread on the updated driver:

> **crichell said:**
> For good measure run the following two commands in your terminal to add the System76 repository and System76 repository signing key:

```
sudo wget http://www.planet76.com/sources.list.d/system76.list -O /etc/apt/sources.list.d/system76.list
```
```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by TheBuzzSaw on 2008-10-29
I ran into this problem as well. I'm running those commands to see if the situation improves.

---

