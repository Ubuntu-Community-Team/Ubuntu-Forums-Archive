---
title: "a little help with mysqldump &amp; rsync"
date: 2006-02-05
forum: Server Platforms
---

### Post by Zelut on 2006-02-05
Hopefully someone with a little more experience with mysql can give me some tips here.  This is what I'm looking to do:

Right now I have a cronjob rsyncing my /var/www/ to a backup machine but many of my sites also use php/mysql and I need the Dbs to be synced as well.  Can someone tell me a good way to do this?  So far I've only come up with mysqldump -all > output.file & syncing the differences in that, but how can I then dump back INTO the mirror Dbs?

If there is a good way to use mysqldump, rsync & then update changes into the mirrors Dbs I would appreciate the tips.

Thanks.

---

