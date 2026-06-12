---
title: "Migrating Messages Old Server to New"
date: 2009-12-09
forum: Server Platforms
---

### Post by Fooshnik on 2009-12-09
I'm sure I'll feel dumb for asking this, I even googled it and couldn't come up with a straight forward answer. 

Old Server - Ubuntu 7.10, Postfix/Maildirs
New Server - Ubuntu 9.10, Postfix/Maildirs

How do I copy all email messages from the 7.10 server to the 9.10 server so that the permissions to the Maildir folders and emails contained are correct and people can pull up their email properly?

---

### Post by Fooshnik on 2009-12-10
No one knows how to do this?

---

### Post by munky99999 on 2009-12-10
Well you need to basically back up the data and config stuff.

*/etc/passwd
*/etc/shadow
*/etc/group
* /etc/gshadow
* /var/spool/mail
* /home -

Get the new machine up and running with postfix. Dump all these old things into their place. Do a reboot and cross your fingers.

Try to keep the old one functioning the whole time. Then connect to the new one after the reboot to make sure everything is working fine. Then do the dns changes and everything to make sure it's pointed to the new machine. If done correctly. End users might never notice the change.

---

### Post by kewlrichie on 2009-12-11
Once your done copying over the shadow and stuff I would tar -zcvpf /home directory the -p should perserve file permissions or maybe tar keeps the permissions already and maybe you need the -p switch while extracting on the new server hmm now I'm unsure... I believe you can also use the cpio command that keeps file persmissions also I think

---

