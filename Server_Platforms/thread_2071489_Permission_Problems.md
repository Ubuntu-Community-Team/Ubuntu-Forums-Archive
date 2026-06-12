---
title: "Permission Problems"
date: 2012-10-15
forum: Server Platforms
---

### Post by contemp on 2012-10-15
So i've got my vps and installed lamp with virtual hosts.
now i want to install wordpress but it says that wordpress can't write wp-config.php and i have to make it myself.
the problem lies in the permission thing i believe.
Files and Dir.s permissions are  644 & 755 accordingly, but that's for my user not the apache user.
So i have added my user to www-data group and made the permission 664 & 775 .
But it still says the same thing.
What should i do?

---

