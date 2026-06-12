---
title: "Stateless node upgrade grub-pc error"
date: 2015-11-04
forum: Server Platforms
---

### Post by extremis11 on 2015-11-04
I have created an Ubuntu server 14.04.2 image for PXE booting from a central NFS server. I tried to upgrade to 14.04.3 issuing the command

```
sudo apt-get upgrade
```

to the node running the image; upgrade has completed with the following error

Setting up grub-pc (2.02~beta2-9ubuntu1.3) ...
/usr/sbin/grub-probe: error: failed to get canonical path of `192.168.1.1:/nfsroot'.
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have commented the 'exec update-grub' line in

/etc/kernel/postinst.d/zz-update-grub

file as suggested in

[http://jeffwelling.github.io//2011/08/29/Diskless-Upgrade-Problem.html](http://jeffwelling.github.io//2011/08/29/Diskless-Upgrade-Problem.html)

but that does not work. I also tried to put grup-pc installation on hold using

```
echo 'grub-pc hold' | sudo dpkg --set-selections
```

but it doesn't work as well. Is it safe to remove grub-pc since it is no longer needed for booting?
Is there anything else i could try to avoid getting this error?


Thanks in advance for any suggestions,
                                                          Kostas

---

### Post by extremis11 on 2016-02-02
Just in case anyone else has the same problem, i have found some kind of solution: i put "exit 0" in the 3rd line of "/var/lib/dpkg/info/grub-pc.postinst" file. Now, i can install/upgrade programs without any errors. Then, i put grup-pc on hold and changed back the above file. I hope that when i will upgrade again there will be no problem.

---

### Post by Bucky Ball on 2016-02-02
*Thread moved to **Server Platforms**.*

---

