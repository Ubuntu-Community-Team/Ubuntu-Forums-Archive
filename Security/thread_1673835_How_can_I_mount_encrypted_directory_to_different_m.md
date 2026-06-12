---
title: "How can I mount encrypted directory to different mount point?"
date: 2011-01-23
forum: Security
---

### Post by 3rods on 2011-01-23
I'm running 10.04 as a VM on top of ESXi v4. I'm using VMWare Data Recovery 1.2 (VDR); one of it's features is the ability to mount a recovery point within the running system to recover individual files. 

How can I mount an encrypted home folder that is inside the recovery point and decrypt it? 

I know how to set the passphrase and actually decrypt the folder, but how do I tell ecryptfs-mount-private to mount somewhere other than /home/user?

---

