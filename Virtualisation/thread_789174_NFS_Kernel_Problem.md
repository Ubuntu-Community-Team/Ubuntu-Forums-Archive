---
title: "NFS Kernel Problem"
date: 2008-05-10
forum: Virtualisation
---

### Post by igb on 2008-05-10
After running foul of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218126") when upgrading a Gutsy DomU, I re-installed my DomU from scratch and the installed the patched kernel from Hirano. I now have networking working OK with my Feisty guest server. However there is a problem with starting nfs on the guest:

```
root@firewall:~# /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                                    [ OK ]
 * Unexporting directories for NFS kernel daemon...                              [ OK ]
FATAL: Could not load /lib/modules/2.6.24-16-xen/modules.dep: No such file or directory
 * Not starting NFS kernel daemon: no support in current kernel.
```

My guest is now running kernel 2.6.24-16-xen, but in /lib I only have  2.6.22-14-xen. So how do I install the modules for 2.6.24-16-xen on the guest?

Solved by copying the modules from DomU (sledgehammer/nut solution:)

Ian.

---

### Post by jtriedl on 2008-05-23
Thank you very much, Ian.  This problem has been bothering me for a week.  The way I induced the problem was to do an install of xen using xen-tools *while not booted in xen*.  A number of the script variables are configured based on the currently running kernel, apparently including the modules that are installed.

John

---

### Post by Railsbuntu on 2008-06-13
Hi can you give some details on how to achieve this? What are the modules to copy?

---

### Post by igb on 2008-06-13
> **Railsbuntu said:**
> Hi can you give some details on how to achieve this? What are the modules to copy?

They are in /lib/modules. From DOMU something like:

```
sudo scp -r /lib/modules/2.6.24-16-xen root@yourserver:/lib/modules

```

Note that command is off the top of my head and not tested!

Ian.

---

