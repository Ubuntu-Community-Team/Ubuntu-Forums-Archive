---
title: "full boot partition - dpkg fails error 1"
date: 2009-02-10
forum: Server Platforms
---

### Post by old_salt on 2009-02-10
I have an Ubuntu 8.04 server that the boot partition flled up on. I'm hung with updating kernel 2.6.23 with dpkg error exit status 1.

dpkg --configure -a fails as it tries to complete a kernel update but fails due to lack of disk space. 

Unable to remove previous kernel versions either because of this hung error. 

In the course of all the updates, it appears that the boot partition filled up completely. Aside from the obvious argument of why didn't the system automatically remove the 4th previous kernel like the desktop versions do I'm not sure but in any case, how may I go about clearing this up. It is a production server in a business environment.

Thanks

---

