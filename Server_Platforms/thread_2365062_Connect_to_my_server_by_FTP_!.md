---
title: "Connect to my server by FTP ?!"
date: 2017-07-01
forum: Server Platforms
---

### Post by fairbird on 2017-07-01
Why I can not to connect to my site by ftp in folder ?!
By windows 7 it very easy (just open new windows and type [ftp://IP-addrees-my-site](ftp://IP-addrees-my-site) and then I put my user and password and log in to my files)
But with ubuntu 14.04 I can not, I got this error ?!
[ATTACH=CONFIG]275825[/ATTACH][ATTACH=CONFIG]275827[/ATTACH][ATTACH=CONFIG]275826[/ATTACH]
I don't want to use FTP tools such as gftp or filezilla (I need to browser my files as like folders)

Thank you

---

### Post by wildmanne39 on 2017-07-01
*Thread moved to **Server Platforms**.*

---

### Post by cariboo on 2017-07-02
I'd suggest you install openssh-server on your Ubuntu system, then access it using sftp.

[https://help.ubuntu.com/lts/serverguide/openssh-server.html]("https://help.ubuntu.com/lts/serverguide/openssh-server.html")

---

### Post by fairbird on 2017-07-03
Thank you, Already I have openssh-server on my ubuntu .. And I have read that link but I can not understand how to use it ..
I have typing (sftp://bird.esy.es/) but nothing happens (no prompt me to user and password) ..

So can you to make small tutorial how to use it (Easy way) Just like exactly on windows.

Thank you

---

### Post by cariboo on 2017-07-03
I use aliases in /etc/hosts that map to ip addresses:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	skynet
192.168.0.4	likely
192.168.0.3	willy
192.168.0.5	haven
192.168.0.102	boombox
192.168.0.21 	mcleese
```

then just type in files:

```
sftp://willy
```

---

### Post by fairbird on 2017-07-03
Nothing happens .
This is my Dreambox image feed (can you try to connect it by sftp)
[http://fairbird.esy.es/](http://fairbird.esy.es/)

And here is my server details 

[TABLE="class: table table-striped table-hover table-bordered table-condensed, width: 881"]
[TR="class: even"]
[TD]FTP host[/TD]
[TD][ftp.fairbird.esy.es [FONT=FontAwesome][/FONT]]("ftp://fairbird.esy.es/")[/TD]
[/TR]
[TR]
[TD]FTP IP[/TD]
[TD]31.170.167.221[/TD]
[/TR]
[TR]
[TD]FTP Port[/TD]
[TD]21[/TD]
[/TR]
[TR="class: even"]
[TD]FTP username[/TD]
[TD]u697485723[/TD]
[/TR]
[TR]
[TD]FTP password[/TD]
[TD]&#8226;&#8226;&#8226;&#8226;&#8226;&#8226;&#8226;&#8226;&#8226;&#8226;
[/TD]
[/TR]
[TR="class: even"]
[TD]Folder to upload files to[/TD]
[TD]public_html[/TD]
[/TR]
[/TABLE]

---

### Post by TheFu on 2017-07-04
sftp is not the same as plain FTP. It uses different network ports and is considered secure enough to use over the internet, provided no passwords are used.  Use ssh-keys.  

I scanned your public IP - it isn't running openssh server.  Please fix that. There isn't any way to connect with ssh, scp or sftp without that daemon/service running.

NEVER use plain FTP over the internet.  I find it is easier to just never use plain FTP - ever.  Why leak my passwords for anyone in the middle to see?

Some Linux file managers (nautilus, caja, thunar) don't use the sftp:// at the beginning of the URL. They use ssh:// - don't know why, since that is incorrect.  ssh is a different protocol than sftp or scp, even if the same openssh-server provides all three and uses the same port.  They all honor the same ssh-keys too, if you set them up between the client and server.  That's really easy for Unix-to-Unix systems - just use ssh-copy-id.  I don't think Windows has a similar tool, sorry.

From Windows, use WinSCP as the program or filezilla.  I've never used filezilla.

Please also load fail2ban on any system with a public login of any sort. If you don't change the default ports for ssh/scp/sftp on the server, then fail2ban is already configured correctly.

Please don't use plain FTP over the internet.  That is terrible for system security. Terrible.

---

### Post by fairbird on 2017-07-05
I am using always FTP program such as File filezilla and gftp ..
But some time, Really I need to use FTP manually as like in windows (that way help me some time)..

Thank you

---

