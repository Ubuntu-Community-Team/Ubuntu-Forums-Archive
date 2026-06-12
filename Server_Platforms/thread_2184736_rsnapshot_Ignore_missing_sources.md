---
title: "rsnapshot: Ignore missing sources"
date: 2013-10-30
forum: Server Platforms
---

### Post by gdi2k on 2013-10-30
I'm using rsnapshot for backup. Things are working, but the machine I am backing up from has removable media, which I also backup when available. The problem is that if this removable media is missing, the backup fails ("missing source"), and nothing gets backed up. 

I would like it to backup as normal, skipping the missing media, instead of failing completely. Is there some way to tell rsnapshot to ignore a missing source?

---

