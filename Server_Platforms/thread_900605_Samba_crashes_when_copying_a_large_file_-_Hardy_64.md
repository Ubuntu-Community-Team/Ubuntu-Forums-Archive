---
title: "Samba crashes when copying a large file - Hardy 64"
date: 2008-08-25
forum: Server Platforms
---

### Post by robgolding63 on 2008-08-25
Hi,
I have just set up a new server, running Hardy 64-bit, hosting a few VMware Machines. It's got 4GB RAM, so some room to expand in the future - and certainly isn't overworked.

When copying a new VMware image over (about 8GB from a Vista client), the transfer slowed to a crawl, then stopped. Looking at top revealed that the system was swapping like crazy, and the whole thing ground to a halt. I restarted samba to kill the transfer, and had to reboot the Virtual Machines to get their memory out of swap and back into RAM. I ended up just rebooting the whole box, because the swap stayed at about 150MB.

Anyway, is this a known problem? The only thing I have configured with samba is the share definitions, I haven't done any tweaking whatsoever - just left the config file as-is.

Thanks in advance,

Rob

---

### Post by robgolding63 on 2008-08-26
Is there anything I could try tweaking in the config file to try and stop this from happening? Seeing as this is a VM host box I really need to be able to copy new VMs over the network to it - which are obviously all large files.

Rob

---

