---
title: "Upgrade to 11.10 buggy?"
date: 2011-11-15
forum: Server Platforms
---

### Post by Madcamper on 2011-11-15
Ok, so I think the reason none of my services, apache, webmin, ssh/sftp, aren't working is because I can't upgrade to 11.10. When I do-release-upgrade it connects but it has some errors trying to connect to the security.ubuntu.com. While my server is going through this, I can intermittently pull up my apache webserver via my web browser, as well as any of the other services running, but it only works for a split second. Has anyone else had trouble upgrading to 11.10 via command line?

---

### Post by 2F4U on 2011-11-15
How does your /etc/apt/sources.list look like?

---

### Post by Madcamper on 2011-11-15
I got it working now. Not sure why it finally worked. I did the same sudo do-release-upgrade so not sure. my sources.list has oneiric in it now

---

