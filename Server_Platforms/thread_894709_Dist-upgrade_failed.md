---
title: "Dist-upgrade failed"
date: 2008-08-19
forum: Server Platforms
---

### Post by chrislynch8 on 2008-08-19
HI,

I was upgrade from kernel2.6.15-51 to 2.6.15-52 and the sudo apt-get dist-upgrade didn't complete. I then had issues booting the server but I'm in and its running on the older kernel.

In the boot folder the files for kernel 52 are there and when I run apt-get dist-upgrade it tells me that 2 packages are not fully installed, I press Y

setting up linux-image-2.6.15-52-amd64-server (2.6.15-52.69)...
There was a problem running depmod. This may be benign, or this could be an error
depmod exited with return value 0
depmod got a signal 11

Then I get a message saying that "since this images uses initrd, I am not deleting the file /lib/modules/2.6.15-52-amd64-server/modules.dep. However there is no guarantee that the file is valid. I would strongly advice you to either abort and fix the errors in depmod, or regenerate the initrd image with a known good module.dep file. I repeat, an initrd kernel image with a bad modules.dep shall fail to boot"

I get the option to abort and I do.

Any one have any advice on how to resolve me issue.

Rgds
Chris

---

