---
title: "SMB-Copy to LVM timed out"
date: 2012-11-14
forum: Server Platforms
---

### Post by rodpott on 2012-11-14
Hello,

I have the following problem. When I start to copy a file from my ubuntu 12.04 client to an ubuntu 10.04 server with samba, the copy job gets a timeout within the first 30 seconds. When I restart the job everything works fine till I restart the server or wait a couple of hours.

After searching the internet and debugging by myself i figured out, that it only happend when I try to write to an LVM- Disk- Group on the server. A copy to a single disk is working fine.

When I copy files from my windows system to the server there is no delay or timeout, too.

Any suggestions how to fix it?

Thank you!

---

### Post by rodpott on 2012-11-22
Hello,

the problem was caused by the file-system ext4. After I made a new logical-volume with xfs as file-system the problem has gone.

I hope this helps if somebody runs into similar issues.

rod

---

