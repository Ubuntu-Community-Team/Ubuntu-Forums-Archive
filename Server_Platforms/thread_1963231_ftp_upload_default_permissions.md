---
title: "ftp upload: default permissions"
date: 2012-04-22
forum: Server Platforms
---

### Post by sowdust on 2012-04-22
Hello everyone : )

I have recently set up my first home server (ubuntu of course).
Whenever I upload a file via ftp, the permission is set to 600 not regarding the file type, its original permission etc...

Is there a way I can set up default permission for certain kind of files, so I don't have to manually change them each time? For instance if i upload a .jpg, .doc. htm file it will have 644 and if it's a folder or a .php file 755, as it happens with most web hosting providers?

Thanks in advance!

---

### Post by Jonathan L on 2012-04-22
Hi sowdust

> **sowdust said:**
> Whenever I upload a file via ftp, the permission is set to 600 not regarding the file type, its original permission etc...

Is there a way I can set up default permission for certain kind of files, so I don't have to manually change them each time? For instance if i upload a .jpg, .doc. htm file it will have 644 and if it's a folder or a .php file 755, as it happens with most web hosting providers?

Thanks in advance!

What you're looking for is essentially the umask behaviour, and each process has its own setting for the umask.

When a file is created, you get the permission the program asks for (normally 666 for files and 777 for directories), masked by the current umask.  Your current umask is apparently 077 ("nothing for group, nothing for other".)  What you describe wants a umask of 022 ("no writing for group, no writing for other".)

The umask is set in a number of places for a shell (usually /etc/profile, overrides in ~/.profile).

What your FTP server does varies by server, but typically will have its own settings.  The FTP server I have to hand is vsftpd, which has settings for both the mask and the open mode.  Depending on the server and its configuration you may well also be able to set the umask as an ftp command (if you can't change the defaults) and also chmod the files.

Some FTP clients therefore try to set the mode to be the same as the original; and you'll therefore get whatever you have on the source computer.  I don't actually know of any FTP servers which will give you different modes for different file types.

If your php scripts are being run from a web server, note that they don't need to have execute permission (depends on the web server configuration: I believe this is the default with Apache.)

Nonetheless, if you want to get 755 for *.php: the solution you often see -- admittedly very ugly -- is to give all files execute permissions even if they are images and so on.  With vsftpd, you could therefore use:
```
local_umask=022
file_open_mode=0777
```Some tidy people then like to have a cron job which removes the silly execute permission from the .jpg and so on.

Hope that helps.

Kind regards,
Jonathan.

---

