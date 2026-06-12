---
title: "mod-auth-mysql issue"
date: 2010-06-27
forum: Server Platforms
---

### Post by brian_centralpark on 2010-06-27
I am running Ubuntu 9.10 Karmic and am having an issue with mod-auth-mysql authenticating users.  It dies with a segmentation fault.  The problem is fairly well documented and it has been determined that it is a problem with mod-auth-mysql_4.3.9-11 and apparently has been fixed in mod-auth-mysql_4.3.9-12.

The solution seems to be a fix to the auth_mysql.c source file by adding an extra include of apr_strings.h.

While all this is well and good, I never like taking the source and building my own executable from the source.  I prefer to use the package that is provided from the Ubuntu repositories since those are easily upgradeable and don't cause dependency problems when upgrading other packages, etc.

However, the latest mod-auth-mysql_4.3.9 is version 11 and I can't get my Karmic distribution to download version 12.  How can I get this package and get Karmic to download and install it?  It seems to be available for Lucid, but for other compatibility issues, I don't want to upgrade the whole distro.  I just want to get mod-auth-mysql_4.3.9-12 for Karmic.

Can someone tell me how to do this?  

Thanks,
Brian

---

