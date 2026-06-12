---
title: "clamscan a network folder"
date: 2012-05-25
forum: Security
---

### Post by oyoj on 2012-05-25
Hi Ubuntu

I wanted to share a quick solution i found to clamscan a network folder (i had tried for some time converting my network server with nfs or cifs etc) but found IMHO a quicker solution:

cd ~/.gvfs
clamscan -r --bell

which first locates the network folder in ~/.gvfs and clamscan it.

Please let me know if there is a better solution.

Thanks,
oyoj

---

