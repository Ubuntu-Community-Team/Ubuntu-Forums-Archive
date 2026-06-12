---
title: "Ecryptfs: &quot;keyctl_search: Required key not available&quot;"
date: 2010-06-28
forum: Security
---

### Post by Finog on 2010-06-28
The problem:
I do a terminal login to my account. When I try to logout of the terminal I get the following message:

keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'

I then need to logout again to succeed in doing so.


Ecryptfs-mount-private does indeed work for me and my ecryptfs password is different from my login password. Not sure what the problem is. I can access and unmount the ecryptfs files manually without problems.

Ecryptfs is set to auto unmount.

Any help would be appreciated!

---

