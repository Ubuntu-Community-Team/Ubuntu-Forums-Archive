---
title: "Automatic Synaptic"
date: 2006-07-19
forum: Server Platforms
---

### Post by Spleenie on 2006-07-19
Is it possible to have synaptic download, install and reboot if necessary when updated without user intervention? I have a fileserver that is just a box with an ethernet connection, and I only have to log into it to update it.

I have the packages downloading and the security packages installing automatically, but I want to go a little further with it.

Cheers

---

### Post by Randomskk on 2006-07-19
Putting something like this in a root-owned file in /etc/cron.daily might work:
```

#!/bin/bash
apt-get update
apt-get -y upgrade

```

Name it, say, update.sh and make sure it's owned by root (sudo chown root update.sh).

Then, run it with sudo /etc/cron.daily/update.sh and check it works fine, and if so it'l get run daily.

Not sure on rebooting if updates are needed though...

---

### Post by cptnapalm on 2006-07-20
wouldn't the "apt-get -y upgrade" overwrite customized configuration files if the package has a new version of said file?

---

