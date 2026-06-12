---
title: "SAMBA Shares"
date: 2018-10-14
forum: Server Platforms
---

### Post by Dave_Davis on 2018-10-14
I have two ubuntu servers running and sharing files via SAMBA.  I am confident that the shares are working properly because I can use them fro my windows machines.

I am now trying to get the shares working on a Linux client.  I can mount them with no problem using SUDO but when I do so, the are read-only

I've spent an entire day trying to get the shares to work without sudo.

I've tried an entry in fstab which apparently does nothing and when I try to mount without sudo I'm told

"permission denied: no match for /mnt/www found in /etc/fstab"

As is often with Linux, I'm lost.  The server share is 10.0.0.250/www I want to share it to /mnt/www

Thanks for your help.

---

### Post by howefield on 2018-10-14
Thread moved to the "*Server Platforms*" forum.

---

### Post by TheFu on 2018-10-16
Perhaps if you posted the actual fstab line then someone could help?
Facts are always better than explanations and interpretations.

---

