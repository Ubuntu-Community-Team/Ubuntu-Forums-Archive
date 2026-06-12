---
title: "Using rSync to mirror data"
date: 2006-07-29
forum: Server Platforms
---

### Post by catfox on 2006-07-29
Hi All,
I'm trying to mirror one cyrus mailstore from serverA to serverB - however, even when the user's data (mails in their mailstore) show up on serverB, i still can't see this user on serverB via cyradm.

So, I think I'm using rSync incorrectly, and it isn't grabbing all the files I need (not overwriting the old imap database?).

I'm running this: 
rsync -avz -e "ssh -p 1111" root@cyrus_server:/var/mailstore /var/ --delete

Which grabs the latest files, but doesn't seem to overwrite (thats what I'm assuming).

Does anyone have any suggestions?

---

