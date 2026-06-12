---
title: "Very strange but suspected easy Postfix problem"
date: 2011-07-30
forum: Server Platforms
---

### Post by Aquachip on 2011-07-30
Postfix logs state its unable to create .lock file in '/var/mail/vmail/domain1'.
For testing purposes, I have set permissions on this directory from 775 to 777. Now Postfix is able to write to it.

Allowing 'everyone' to read/write to the directory tells me Postfix is not apart of the mail group on my computer, when it should be. How can I check or change this? ... or is there another problem at hand perhaps?


Also, how can I set virtual_uid_maps and virtual_gid_maps so that generated mail files are owned by root and allow mail group read/write access?

---

