---
title: "CIS benchmark implementation issues with editing /etc/fstab"
date: 2018-06-26
forum: Security
---

### Post by dontron64 on 2018-06-26
Hello
I'm currently trying to stand up a new Ubuntu 16.04 server and secure it using the CIS benchmark guide.
While I was performing the installation wizard I created serveral partitions that the benchmark calls for, /tmp, /var, /var/log, /var/log/audit, etc.
The benchmarch shows it should be type tmpfs but that option wasn't available in the partitioning wizard so I selected the default ext4.

While working my way though the CIS benchmark, I need to change the defaults and set noexec, nosuid, nodev .

original:
UUID=<......> /tmp ext4 defaults 0 0

I edited the line for the tmp partition as such.

UUID=<.......> /tmp ext4 (rw,nosuid,nodev,noexec,relatime)


When I saved the change and tried to perform a remount it didn't fail, but obviously it didn't succeed either.

$ sudo mount -a
<nothing is returned after this command is executed>.

When I tried to reboot the server I get a message that indicates it can't mount /tmp partition.

systemctl status tmp.mount gave me the following information

loaded: loaded 9/etc/fstag; generated)
Active: failed (Result:exit-code) since <date>
Where: /tmp
What: /dev/disk/by-uuid/<uuid #>
Docs: man:fstab(5)
         man:systemd-fstab-generator(8)
Process: 805 ExecMount=/bin/mount /dev/disk/by-uuid/<uuid #> /tmp/ -t ext4 -o (rw,nosuid,nodev,noexec,relatime)  (co....   [unreadable] 

Mounting /tmp....
Mount: /tmp: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program

tmp.mount: mount process exited, code=existed status =32
tmp.mount: failed with result 'exit-code'.
Failed to mount /tmp



If I comment out this line and put back in the default line for /tmp, the the partition mounts fine. 
I have also tried to specify the type as tmpfs, but it didn't like that either?


Can someone please assist me and tell me why changing the default options to these correctly spelled arguments are being rejected?

Thanks

---

