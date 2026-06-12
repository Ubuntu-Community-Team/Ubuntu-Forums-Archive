---
title: "Dovecot maildir rsync backup"
date: 2011-01-12
forum: Server Platforms
---

### Post by Neikius on 2011-01-12
So what I am trying to do is have another mail server with all the backups there. I don't really care for propagating deleted mail and flags.

Setup: dovecot 1.2.9, ubuntu 10.4, maildir

I was thinking like this:

rsync -ayz source target

But will the -y (fuzzy) flag be enough for rsync not to sense maildir flagged files as different? ,S appended means seen etc.

Also I will probably want to exclude uidlist files I guess and let the local dovecot recreate since I will be incrementally adding even deleted mail. I fully expect to have every deleted mail persisting and all moved mail duplicated on the backup end. But that is ok at this point. Did I forget something? Otherwise the time will show I guess.

If anyone knows some better solution for backing up maildir please come forward though.

I know dovecot2 has dsync especially designed for what I want, so when is dovecot2 comming to ubuntu?

---

