---
title: "Problem with plymouth hanging during boot"
date: 2012-06-17
forum: Server Platforms
---

### Post by Apewall on 2012-06-17
This is a headless 12.04 server.  Plymouth hangs during loading and will take 2-3 minutes longer to boot into the system if it is not sent a kill message, this only occured after an update from 11.10 to 12.04.

This is a xen server that is not using grub to boot.  Is there any issues with me preventing plymouth from loading?

I'm not sure what the issue with the hang is as I haven't found anything suspicious in the logs as to why init is taking 2-4 minutes to load the init.d scripts.

---

