---
title: "Stopping LAMP from loading at boot"
date: 2008-09-19
forum: Server Platforms
---

### Post by roncrump on 2008-09-19
Hi,

I want to install a LAMP server on a laptop purely for use as a development machine. So I don't want unnecessary stuff running when I'm on battery, and hence would like to configure at least apache, and maybe other components (suggestions?) to not load at boot, only when I fire them up manually to test my code.

Cheers,
Ron.

---

### Post by Pamir on 2008-09-19
I would write a script which stops all the unwanted apps/services and start them munually when needed.

---

### Post by Iowan on 2008-09-19
A similar tact: you could edit the appropriate rcX.d directories (I can't remember proper runlevels at the moment...) and rename the "SXXapache2", etc, files so they don't automatically start. (I generally just change "S" to "s")

---

