---
title: "Can't create valid initramfs in Server 8.04"
date: 2009-02-06
forum: Server Platforms
---

### Post by orgler on 2009-02-06
Hi,

I recently updated my Ubuntu 8.04 server and since then it didn't start any longer. It gives me an error message:
Could not load /lib/modules/2.6.24-23-generic/modules.dep

(I've attached a screenshot, this is Virtual server btw. but this shouldn't be the problem I guess)

When reusing my old kernel and (!!) my old initrd everything works fine. I then tried to generate new initramfs using the following command:
 sudo update-initramfs -k 2.6.24-23-generic -c
This didn't help. When I created a new Initramfs for the exising and working old kernel, this initrd doesn't work either.

So I think my initramfs tools or some config is messed up. Doing a dpkg-reconfigure initramfs didn't help. When returing to the original initrd for the old kernel, everything is fine again. But this prevents me from doing any kernel-updates :-(

Does anyone have an idea what went wrong?

Any help would  be highly appreciated.

EDIT: I added a full bootlog, but the first error seems to be the "modules.dep not found"
Best regards,

Johannes

---

### Post by orgler on 2009-02-16
are there really no ideas on this problem? This would mean I'd have to reinstall my whole maschine :-(

best regards,

Johannes

---

