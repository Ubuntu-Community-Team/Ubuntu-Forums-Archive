---
title: "Server 10.10 64 hangs on &quot;Configuring language-pack-en-base&quot;"
date: 2011-04-15
forum: Server Platforms
---

### Post by indivision on 2011-04-15
Unless this issue is immediately familiar to someone, my question really is how can I troubleshoot a failed installation attempt?

I built a simple file server. It was running 10.04 with Samba fine for about 6 months. It was a RAID 1 system using LVM and no encryption.

I recently discovered that one of the drives was already failing with a bunch of bad sectors. So, I decided to replace the drives and re-install everything. However, for some reason, it's not finishing the install. It gets to 94% and "Configuring language-pack-en-base" and just hangs. No drive light activity. I've waited hours and it never progresses.

Some details of the server:

Two WD 1.5 TB drives.
RAID 1
Adding encryption this time.
LVM
Partitions: boot, root, swap

I have tried several variations. Putting the boot partition in or out of the LVM. Went back to 10.04. Even tried to re-install on the same old hard drives that I'm replacing. All of these variations result in the exact same issue.

The two differences that I can think of are adding encryption and that the motherboard firmware has been updated since the last install. Other than that, I'm really stumped and pulling my hair out.

If anyone has some insight into how to fix this or at least what steps to take to troubleshoot, I would really appreciate it.

---

