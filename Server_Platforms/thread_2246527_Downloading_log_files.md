---
title: "Downloading log files"
date: 2014-10-01
forum: Server Platforms
---

### Post by as2000 on 2014-10-01
I am searching for instructions how to download my log files from my remote server so I can view them offline. I have disabled ssh access and don't use an rsa key. I manage this server through Linode which I can log in using their access methods.

---

### Post by SeijiSensei on 2014-10-01
Do you have an SSH server somewhere else you can ship the logs to from the remote?  If so, you can log in with Linode's virtual console, zip up the logs, and copy them to the other server with scp or rsync.  Or you could email them using either the "mail" command or a plain-text email client like Alpine.

If you plan to do this on a permanent basis, you'll want to run a script from crontab.

---

### Post by as2000 on 2014-10-01
*slaps self on forhead*

Pretty simple using Filezilla....

Thanks for the suggestion SeijiSensei. I will also keep that in mind when I am at a computer without Filezilla.

---

