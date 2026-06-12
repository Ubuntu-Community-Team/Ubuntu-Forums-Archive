---
title: "Windows file share and Apache"
date: 2005-12-07
forum: Server Platforms
---

### Post by mangus580 on 2005-12-07
Ok, so the problem goes deeper..... I cant seem to get apache to be able to write to any directory I make.  I have made sure that the directory owner is the www-data user/group.  I am not having any luck with any of this.

Hope I am posting in the right spot....

I am running Breezy as an Apache server, in a windows world.  I need to allow apache to write to a windows share directory.  I have mounted the dir using fstab, and can read/write to the dir with Nautilus.  However, if I plug the dir into my web config (Postnuke/pagesetter) it tells me that it is unable to write to the directory.  I assume that there is some sort of permissions violation.  My mounted dir is /var/www/docusys and if I check the permissions on this dir, they show up as 777.  I am confused, as everything I read says this should work, but yet I cant make it so.

Thanks,
Mike

---

