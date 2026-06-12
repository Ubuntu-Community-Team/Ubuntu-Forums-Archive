---
title: "SysV Run control scripts not working (older mysql)"
date: 2012-10-03
forum: Server Platforms
---

### Post by FlyboyData on 2012-10-03
Hello,
 
I have to run an older version of mysql (5.0.96) on a new Ubuntu 12.04 installation in order to maintain compatibility via MySQL Master-Master replication with an existing server. I was able to download that from MySQL (in rpm form) and install it using alien. Further, I was able to keep ubuntu from attempting to update it to 5.5 by pinning it in /etc/apt/preferences:guitar:
 
However, it won't start on boot. It did install a start script in /etc/init.d, and I can start mysql via /etc/init.d/mysql start. I tried the traditional SysV method (symbolic link S99mysql in /etc/rc3.d and /etc/rc5.d ) to /etc/init.d/mysql.
 
Am I missing something? This has worked without fail in all linux/unix builds since I was in diapers...

---

