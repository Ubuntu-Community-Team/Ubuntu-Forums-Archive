---
title: "Dovecot missing messages after restore"
date: 2017-03-07
forum: Server Platforms
---

### Post by david-whitmarsh on 2017-03-07
Ubuntu 12.04.5 LTS
Dovecot 1:2.0.19-0ubuntu2.2

After successfully restoring user home directories and /var/spool/mail contents onto a backup server, imap clients (thunderbird) on the network are missing all inbox mail messages received since the last time the backup server was primary. Manual examination of /var/spool/mail/<username> files shows that the missing mails are present, and even after deletting the dovecot indexes from /home/<username>/mail/.imap/INBOX, so that dovecot recreates them on restart, the messages are still missing from the client view. Examining the contents of the recreated dovecot.index.cache suggests that the problem lies with dovecot not indexing the missing messages, rather than with thunderbird not retrieving them. Also even creating a brand new thunderbird client account connecting to dovecot, the messages are still missing, again suggesting the issue is server-side rather than client.

I can only surmise that dovecot is maintaining some state elsewhere that tells it what to index, but I am unable to find it.

Any ideas?

---

### Post by SeijiSensei on 2017-03-07
On my server, each user's /home/username/mail directory has a .imap hidden subdirectory with dovecot.index, dovecot.cache, and dovecot.log files for each folder.  Maybe those need to be [deleted and recreated by dovecot]("http://wiki.dovecot.org/IndexFiles")?

It also looks like it's possible to rebuild the indexes with the "[doveadm index]("http://wiki2.dovecot.org/Tools/Doveadm/Index")" command.

---

### Post by david-whitmarsh on 2017-03-08
Tried deleting the index, no difference. I have found a workaround though, by copying the old /var/spool/mail/<username> file into the users $HOME/mail, it picks up all the content as a new folder.

---

