---
title: "php 5.2.8 or newer"
date: 2009-06-18
forum: Server Platforms
---

### Post by xkaliburx on 2009-06-18
We have McAfee's hackersafe for PCI compliance, and although some things they are a PITA with, but having CC processing, etc. they merchants require the compliance.

Anyway, a newer threat that came is due to php 5.2.6 and below, and their solution is to upgrade to 5.2.8 or newer.  Everything on the box's are run nicely from binaries so to go download, compile, etc. is really no option.

So, looking in aptitude I only see the 5.2.6 version, anyone know of another way to upgrade?

Thanks

---

### Post by cdenley on 2009-06-18
> **xkaliburx said:**
> We have McAfee's hackersafe for PCI compliance, and although some things they are a PITA with, but having CC processing, etc. they merchants require the compliance.

Anyway, a newer threat that came is due to php 5.2.6 and below, and their solution is to upgrade to 5.2.8 or newer.  Everything on the box's are run nicely from binaries so to go download, compile, etc. is really no option.

So, looking in aptitude I only see the 5.2.6 version, anyone know of another way to upgrade?

Thanks

5.2.9 is available in the karmic repos, but I wouldn't suggest trying to use it. I wouldn't expect 5.2.8 to be released for jaunty. Have the security problems discovered since 5.2.6 that you mentioned been patched in ubuntu's 5.2.6 package, or is that not enough to be compliant?
[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.6.dfsg.1-3ubuntu4.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.6.dfsg.1-3ubuntu4.1/changelog)

---

