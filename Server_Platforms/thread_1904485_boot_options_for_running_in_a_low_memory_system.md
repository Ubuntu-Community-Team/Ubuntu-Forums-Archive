---
title: "boot options for running in a low memory system"
date: 2012-01-04
forum: Server Platforms
---

### Post by boondocks on 2012-01-04
Just installed (the base) Ubuntu 10.04 Minimal CD on an old cheap lowend PC.

openssh-server is the only package that was installed after the minimal base.
This PC is only being used to provide occasional ssh access to other systems upstream.

Even with just 48 Mb of RAM it has been working without any problems.

Wondering ...
Are there any options that can be appended to the GRUB_CMDLINE_LINUX_DEFAULT to tweak it for such a low memory environment?

---

### Post by bluexrider on 2012-01-04
what are you trying to accomplish?

---

### Post by boondocks on 2012-01-04
This old PC has 4 memory slots. Each slot has 12 Mb memory module.

One of the 12 Mb modules was bad and had to be replaced.
But it took a while to find a replacement for such a dinosaur.

If another module gives memory errors, for the time being the system will be down to 36 Mb.

So I was wondering if the system could still run with some boot options.

---

### Post by bluexrider on 2012-01-05
> **boondocks said:**
> This old PC has 4 memory slots. Each slot has 12 Mb memory module.

One of the 12 Mb modules was bad and had to be replaced.
But it took a while to find a replacement for such a dinosaur.

If another module gives memory errors, for the time being the system will be down to 36 Mb.

So I was wondering if the system could still run with some boot options.

you might try zRam for low memory systems 
[http://en.wikipedia.org/wiki/ZRam](http://en.wikipedia.org/wiki/ZRam)

---

