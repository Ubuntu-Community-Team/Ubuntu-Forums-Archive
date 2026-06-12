---
title: "Easy vsftpd setup?"
date: 2009-08-04
forum: Server Platforms
---

### Post by adrian-g on 2009-08-04
Hello all,
I would like to set up an FTP server on my extra machine which is used as a web server.

I have tried vsftpd with countless configurations, but in the end it never works out right (it functions, but it allows anonymous logins, and when I log in as root, I can't write or copy files).

Basically, my requirements are the following;
[LIST]
[*]FTP program/daemon must start at log on
[*]No anonymous log ins
[*]Full root access would be nice, but I mainly need /var/www/
[*]SFTP would be nice, aswell
[/LIST]

Could anyone help me out with a config?

Thanks!

---

### Post by cdenley on 2009-08-04
You never want to allow root to authenticate remotely. Bots and scripts will be guessing your password all day. Unless you use SSL encryption (FTPS), your password would be sent in plain text.

If you want easy and secure access to your filesystem, use SSH (SFTP).
```

sudo apt-get install openssh-server

```

Now you can connect securely with many different clients, such as FileZilla.

If you set a root password, I would disable it.
```

sudo usermod -L root

```

---

### Post by adrian-g on 2009-08-04
I understand, but I would prefer to use FTP since I can upload/download files easily using software I already use (such as Dreamweaver on XP).

---

### Post by ibutho on 2009-08-04
To start vsftpd at boot time
```
sudo update-rc.d vsftpd defaults
```
To disable anonymous login edit vsftpd.conf and change
```
anonymous_enable=YES
```
To
```
anonymous_enable=NO
```

---

