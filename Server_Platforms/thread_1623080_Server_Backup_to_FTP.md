---
title: "Server Backup to FTP"
date: 2010-11-16
forum: Server Platforms
---

### Post by trentscott on 2010-11-16
I have a LAMP server and read that you can use Duplicity to backup files in an encrypted archive to an FTP server. Ideally, I'd like to build a second system and mirror them together using Rsync, but would the FTP solution tie me over in the interim (3-6 months)? Does anyone have experience/success doing this? Is Rsync the better solution and can it do FTP?

On the Community Docs at [https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto), Duplicity was used to backup a single directory, is it possible to backup an entire hard disk (approx. 20 GB on my drive) and use incremental backups from then on? The only folders I really need are /var, /etc, and wherever MySQL and Webmin reside. How can I alter the script in the example to do that, if possible:

```

export PASSPHRASE=SomeLongGeneratedHardToCrackKey
export FTP_PASSWORD=WhateverPasswordYouSetUp
duplicity /etc ftp://FtpUserID@ftp.domain.com/etc
unset PASSPHRASE
unset FTP_PASSWORD
```

---

### Post by trentscott on 2010-11-16
Anyone?

---

