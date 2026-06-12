---
title: "Advantages of Port Mapper?"
date: 2010-01-20
forum: Server Platforms
---

### Post by ooobooontooo on 2010-01-20
Hi,

I was wondering what exactly are the advantages of a port mapper. Right now, I'm just thinking of it as a dynamic /etc/services daemon. I know it's used extensively in nfs, but why? Doesn't nfs already have a well established port 2049? Thanks in advance.

---

### Post by iponeverything on 2010-01-20
portmapper seems to be used primaryly by NFS and NIS. See the wiki page for it.. It seems to be on the verge of obsolescence with static port assignments listed in /etc/services ... but I could be wrong ;)

---

### Post by ooobooontooo on 2010-01-20
Thanks. That sort of confirmation was exactly what I was looking for. :D

---

