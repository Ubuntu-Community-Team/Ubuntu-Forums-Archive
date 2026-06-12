---
title: "Trouble with FTP user access with webmin"
date: 2008-07-14
forum: Server Platforms
---

### Post by Swerve1000 on 2008-07-14
Hi,

I have installed Ubuntu Server Ed. followed by webmin.

I am trying to create an FTP user account able to read/write to /var/www but I keep on receiving a permission denied 'error'. The SFTP client I am using is WinSCP.

These are two screen shots of the settings I have:-

[IMG]http://img2.freeimagehosting.net/uploads/cd7595627c.jpg[/IMG]


[IMG]http://img2.freeimagehosting.net/uploads/301fe153fb.jpg[/IMG]

If anyone can advise me on where I may be going wrong, it'll be extremely appreciated.

Many thanks!

Swerve1000

---

### Post by windependence on 2008-07-15
Set your WinSCP for ssh access and use that, it's just as easy and more secure. Also, your user must have access to that directory.

Try:

```
sudo chmod -R 775 /var/www
```

-Tim

---

