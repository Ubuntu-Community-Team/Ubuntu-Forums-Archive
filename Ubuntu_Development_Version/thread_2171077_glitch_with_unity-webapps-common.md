---
title: "glitch with unity-webapps-common"
date: 2013-08-29
forum: Ubuntu Development Version
---

### Post by zika on 2013-08-29
```
Preparing to replace unity-webapps-common 2.4.16+13.10.20130814-0ubuntu1 (using .../unity-webapps-common_2.4.16+13.10.20130829.1-0ubuntu1_all.deb) ...Unpacking replacement unity-webapps-common ...
dpkg: error processing /var/cache/apt/archives/unity-webapps-common_2.4.16+13.10.20130829.1-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/hicolor/128x128/apps/ubuntuone-music.png', which is also in package unity-asset-pool 0.8.24daily13.06.10-0ubuntu1
```

---

### Post by ventrical on 2013-08-29
same here...

```

Preparing to replace unity-webapps-common 2.4.16+13.10.20130814-0ubuntu1 (using .../unity-webapps-common_2.4.16+13.10.20130829.2-0ubuntu1_all.deb) ...
Unpacking replacement unity-webapps-common ...
dpkg: error processing /var/cache/apt/archives/unity-webapps-common_2.4.16+13.10.20130829.2-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/hicolor/128x128/apps/ubuntuone-music.png', which is also in package unity-asset-pool 0.8.24daily13.06.10-0ubuntu1
No apport report written because MaxReports is reached already
 
```

---

### Post by fooman on 2013-08-29
affects me as well

---

### Post by deadflowr on 2013-08-29
Here's the bug report
[https://bugs.launchpad.net/webapps-applications/+bug/1218490](https://bugs.launchpad.net/webapps-applications/+bug/1218490)

---

### Post by zika on 2013-08-30
Seems like it's been fixed...

---

