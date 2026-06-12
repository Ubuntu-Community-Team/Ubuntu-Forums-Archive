---
title: "mkfs breaks when creating ext3 or ext4 filesystem (server 14.04 64-bit)"
date: 2014-07-02
forum: Server Platforms
---

### Post by telepheedian-t on 2014-07-02
Whenever I attempt to create an ext3 or ext4 filesystemusing mkfs with a new volume that I created in KVPM (I have unity installed on top of the server distribution), I get this error: 
mkfs.ext3 (or 4): symbol lookup error: mfks.ext3: undefined symbol: ext2fs_add_journal_inode2

Looking around online, it looks like this could be a package dependency/linker error? I don't see any unfilled dependencies in synaptic.

---

