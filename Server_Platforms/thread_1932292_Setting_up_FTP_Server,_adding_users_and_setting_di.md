---
title: "Setting up FTP Server, adding users and setting directory"
date: 2012-02-27
forum: Server Platforms
---

### Post by ludatha on 2012-02-27
Hello

I'm very new to ubuntu server, I've set up lamp on this ip: *Removed*

Now I'm trying to set up FTP so I can upload files to the www directory. But I have no idea what I'm doing, I've followed many tutorials but I can't find anywhere that says how to add a user and set the directory to www.

I've installed vsftpd (and various others).

I'm very new to the command line to be gentle ;)

---

### Post by Lars Noodén on 2012-02-27
Unless there is a specific reason that you must have FTP and nothing else, I would recommend using SFTP instead.

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[/list]

If you have the package OpenSSH-Server already installed, then you already have SFTP configured (it works over SSH) and you can then connect to it using FileZilla or Nautilus.

---

### Post by ludatha on 2012-02-27
> **Lars Noodén said:**
> Unless there is a specific reason that you must have FTP and nothing else, I would recommend using SFTP instead.

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[/list]

If you have the package OpenSSH-Server already installed, then you already have SFTP configured (it works over SSH) and you can then connect to it using FileZilla or Nautilus.

Oh, that worked, I was already controlling the server using SSH, thanks! 

Now how can I get to www?

---

### Post by Lars Noodén on 2012-02-27
> **ludatha said:**
> Now how can I get to www?

If you mean the web pages that your web server is using, then the default is in /var/www  To write to it, you need permission to do so.

If you are going to be the only user of the directory, then you can simply take ownership of it and that will be that:
```

sudo chown -R ludatha /var/www

```

If you are going to be sharing access to the folder with a bunch of people, then you can set up group access.

```

sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add ludatha  webmasters


```

---

### Post by ludatha on 2012-02-27
> **Lars Noodén said:**
> If you mean the web pages that your web server is using, then the default is in /var/www  To write to it, you need permission to do so.

If you are going to be the only user of the directory, then you can simply take ownership of it and that will be that:
```

sudo chown -R ludatha /var/www

```

If you are going to be sharing access to the folder with a bunch of people, then you can set up group access.

```

sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add ludatha  webmasters


```

Thanks it all working now :)

---

