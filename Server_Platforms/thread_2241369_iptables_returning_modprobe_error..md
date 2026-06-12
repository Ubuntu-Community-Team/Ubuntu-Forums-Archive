---
title: "iptables returning modprobe error."
date: 2014-08-25
forum: Server Platforms
---

### Post by neltnerb on 2014-08-25
iptables worked fine on 12.04, but upgraded to 14.04 and now running any command gives me:

```
sudo iptables --list
modprobe: ERROR: ../libkmod/libkmod-index.c:821 index_mm_open() magic check fail: b007fa57 instead of b007f457
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/2.6.35.4-rscloud/modules.dep.bin'
iptables v1.4.21: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
```

apt-get update and dist-upgade show no new updates, and rebooting did not fix the issue. Any ideas?

I found [one reference to the problem]("http://serverfault.com/questions/384306/why-is-iptables-command-throwing-errors"), but couldn't find a file libkmod-index.h on my server (and would be nervous changing expected magic checks anyway without understanding).

---

### Post by SeijiSensei on 2014-08-26
Do you actually have a directory called "/lib/modules/2.6.35.4-rscloud/"?  The current kernel for 14.04 is 3.13.0-34-generic or thereabouts.  That entry references kernel version 2.6.35.4 which seems to be part of [this release](http://kernel.slicehost.com/2.6.35.4-rscloud/).

---

### Post by neltnerb on 2014-08-26
Thanks for the question SeijiSensei, I appreciate the reply!

I did some digging, and have found that my rackspace virtual server is a bit funny. It actually loads the kernel from the **host** server rather than the virtual server. So, although I did install kernel 3.13.0-34-generic, through linux-image-generic, it's not loading. Instead, kernel 2.6.35.4-rscloud is loading.

I do have a directory /lib/modules/2.6.35.4-rscloud, which is the correct running kernel.

iptables worked fine on Ubuntu 12.04, so my current guess is that after upgrading to Ubuntu 14.04, the latest version of iptables requires a version of the kernel module which simply doesn't exist on the machine.

Barring a better explanation, I'm going to see what rackspace has to say. I think they can allow me to load my own kernel, but I'm a little worried that there may be a reason that it's not the default (beyond bricking your virtual machine and being unable to manual tell grub to load the old kernel remotely).

If there is a way to get the Ubuntu 14.04 version of iptables to work with the 2.6.35.4 kernel version, that would be ideal. Otherwise, I'll see if I can figure out how to upgrade the kernel. Alternatively, I suppose I could try to regress iptables to the 12.04 version, but I haven't checked to see how that might impact dependencies.

---

### Post by Ian_Darbyshire on 2015-02-24
Hello, just wondering if you managed to get anywhere with Rackspace, and if so what was the outcome? We have exactly the same problem on a VM upgraded from 11.04 to 14.04.

---

### Post by neltnerb on 2015-02-24
No, I gave up and stopped trying to do anything useful with the server.

---

