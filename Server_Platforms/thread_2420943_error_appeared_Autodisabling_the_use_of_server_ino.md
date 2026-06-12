---
title: "error appeared: Autodisabling the use of server inode numbers"
date: 2019-06-13
forum: Server Platforms
---

### Post by NotQuiteSU on 2019-06-13
I had a monitor hooked up to my ubuntu 16.04 LTS while i was attaching a USB drive. A couple days later, I came down and saw the following message:

> Autodisabling the use of server inode numbers on \\192.168.2.10\media. This server doesn't seem to support them properly. Hardlinks will not be recognized on this mount. Consider mounting with the "noserverino" option to silence this message

192.168.2.10 is another Ubuntu 16.04 LTS server. The mounts are done with FSTAB. I understand what hardlinks are, but I'm not sure why this message is occurring and what I should do to resolve it. (besies noserverino)

---

### Post by SeijiSensei on 2019-06-14
That's a UNC address which tells me the machine at 192.168.2.10 is sharing files via Samba.  Windows networking does not support some features of *nix filesystems which likely generates the error you see.

If you want to share files effectively between *nix machines, you should be running NFS.  If you need to share files with both Linux and Windows clients, you can run NFS alongside Samba. (I do that here.)  

See [https://help.ubuntu.com/stable/serverguide/network-file-system.html](https://help.ubuntu.com/stable/serverguide/network-file-system.html)

You'll also need to install the nfs-common package on any client machines.

---

