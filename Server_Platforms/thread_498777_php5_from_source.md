---
title: "php5 from source"
date: 2007-07-11
forum: Server Platforms
---

### Post by Daveyboy on 2007-07-11
I uninstalled the php5 package with apt-get remove --purge php5 and downloaded php5 source (as it was recommended for troubleshooting a cacti install ) It still shows the old php version 5.2.1 build May22 instead of php 5.2.3 with current build date  in the phpinfo function page in apache2. Please advise.

---

### Post by jtc on 2007-07-12
Actually, the package PHP5 is simply a meta-package, helping you to install other packages. Removing it won't remove the other (real) packages.

```
dpkg --list |grep php
```

If nothing else, you probably still have at least libapache2-mod-php5 and php5-common.

---

