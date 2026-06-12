---
title: "mysqldump"
date: 2009-05-17
forum: Server Platforms
---

### Post by tomazo on 2009-05-17
Hello,

I'm using mysqldump to take backups as follows:

mysqldump -R -q –single-transaction --user=root --password=pass database db | gzip >  file.gz

But there is a problem that on servers with new kernel, Apache is very slow after execusting that command [loading of a forum takes 20s]. On an older debian everything worked fine. This problem could be solved by setting up a priority of mysqldump, but I don't know how to do it. Another solution could be copying of mysql directly from /var/lib/mysql, but that's not the best solution.

Any ideas?

Thanks

---

### Post by Gremmie on 2009-05-17
So you are having Apache run that command somehow?

Personally I run something like that on all my databases via a cronjob every night and have not seen any performance issues. My databases aren't that big though.

---

