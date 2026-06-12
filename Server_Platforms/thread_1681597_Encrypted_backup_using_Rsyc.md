---
title: "Encrypted backup using Rsyc"
date: 2011-02-04
forum: Server Platforms
---

### Post by damo12 on 2011-02-04
[FONT="Comic Sans MS"]I support a small business which has an Ubuntu server running as a file server.  The server is running Ubuntu 10.4.

There is one hard drive which is mounted as /media/hdd.  Each night this is backed up to an  external USB hard drive mounted as /media/backup.  The backup is carried out using the command:

```
rsync -av /media/hdd/ /media/backup/
```

Is there a way to encrypt this back-up so that if the USB hard drive is plugged into another machine it cannot be read?

Thanks in advice for your help with what I'm sure is a stupid question.[/FONT]

---

### Post by CharlesA on 2011-02-04
You'd have to use something like Truecrypt or LUKS to encrypt it. I'm not sure if you can mount an encrypted drive automatically tho.

---

### Post by SeijiSensei on 2011-02-05
This looks like a good tutorial for Truecrypt on Ubuntu:
[http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/](http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/)

As Charles say, you'll have to enter a password when you mount the encrypted volume on the external drive.  It sounds to me like you leave this connected all the time, so I don't see that as a problem.  It will protect you against someone walking off with the external drive.

---

### Post by damo12 on 2011-02-05
[FONT="Comic Sans MS"]Thanks for the advice, forgot to mention it's a headless server accessed through Putty and Webmin so the guide is out but it gives me a few pointers.

Thanks again.[/FONT]

---

### Post by CharlesA on 2011-02-05
You can always forward X over SSH if you want to set it up via GUI.

---

### Post by disabledaccount on 2011-02-05
eCryptFS: filesystem level, incremental backups, separate keys for files.
Disk-based encryption can be considered as "additional" security level, because it's relatively easy to gain access to data when "ecrypted" volume is mounted.

---

