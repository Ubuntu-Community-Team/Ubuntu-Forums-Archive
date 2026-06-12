---
title: "Dansguardian"
date: 2009-08-22
forum: Ubuntu Christian Edition
---

### Post by IamWayne on 2009-08-22
I had to uninstall Dansguardian, so I could visit some torrent sites. After uninstalling it, I still can't go to those sites. What gives?? Any help would be appreciated!:confused:

---

### Post by david_kt on 2009-08-23
> **IamWayne said:**
> I had to uninstall Dansguardian, so I could visit some torrent sites. After uninstalling it, I still can't go to those sites. What gives?? Any help would be appreciated!:confused:

Actually what you have to do is just stop dansguardian. But if after removing dansguardian you still could not visit those sites, probably those sites were down or your ISP does some filtering.

DK

---

### Post by IamWayne on 2009-08-23
Then how come I can go to them on my desktop, which is not CE??

---

### Post by david_kt on 2009-08-23
> **IamWayne said:**
> Then how come I can go to them on my desktop, which is not CE??

Not sure why, please remove tinyproxy and firehol

```
sudo apt-get remove --purge tinyproxy firehol
```

, and then restart your computer to see if this help. If firehol is not installed, then remove tinyproxy only:

```
sudo apt-get remove --purge tinyproxy
```

and restart your computer.

DK

---

