---
title: "NFS or sshfs?"
date: 2008-11-26
forum: Server Platforms
---

### Post by roundhay on 2008-11-26
I would like to be able to mount (preferably automount) folders on my server to 2 PC's I have at home over my LAN. I had planned to use NFS but sshfs seems like another option.

Any suggestions over which way is the best way to go?

I would like to have the folders on the server mounted on both PC's at the same time.

---

### Post by cariboo on 2008-11-26
Depending on what the two computers you want to mount the shares on  are running. If they are windows computers you will need a third party addon to be able to read either NFS or SSHFS. Samba is the easiest to use as Windows computers can mount shares without any addons. 

If your computers are running Linux distributions NFS is the easiest for a local network.

Jim

---

### Post by Dr Small on 2008-11-26
I have never used NFS, but SSHFS has always served my purposes.

---

