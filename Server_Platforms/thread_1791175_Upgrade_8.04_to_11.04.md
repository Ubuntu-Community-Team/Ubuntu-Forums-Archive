---
title: "Upgrade 8.04 to 11.04?"
date: 2011-06-26
forum: Server Platforms
---

### Post by sentinelace on 2011-06-26
Is this possible?  I know some things changed with init and I don't want to break anything.  I do a sudo apt-get dist-upgrade and I get nothing.

---

### Post by Enigmapond on 2011-06-26
It is possible however, with all the changes to 11.04 and in general, you would be better to just do a fresh install. This I think will preserve your sanity. Backup the important home files first.

Cheers!

---

### Post by snowpine on 2011-06-26
"apt-get dist-upgrade" doesn't do what you think it does (type "man apt-get" for the details).

You can upgrade from 8.04 to 10.04 in one step. If you choose then you could go to 10.10 and then to 11.04. Personally for a server I would stick to the Long Term Support releases (10.04) and wait for 12.04 next year. But it is your choice.

Instructions here:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by arrrghhh on 2011-06-26
+1 to snowpine's comments.

Stick to LTS on server edition.  Upgrade to 10.04 and leave it until 12.04.

Fresh install is probably safer, but upgrading will be easier.  Either way, as always have backups - whether you upgrade or fresh install.

---

