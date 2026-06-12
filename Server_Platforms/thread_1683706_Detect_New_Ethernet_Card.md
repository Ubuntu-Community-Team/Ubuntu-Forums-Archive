---
title: "Detect New Ethernet Card"
date: 2011-02-07
forum: Server Platforms
---

### Post by CheezItMan on 2011-02-07
I've added another ethernet card to my VMWare Ubuntu installation.  How can I detect the new card via the command-line?

---

### Post by trundlenut on 2011-02-08
Has it already detected it?  What does ifconfig output?

If not what is the output from: ```
lshw -C network
```

---

