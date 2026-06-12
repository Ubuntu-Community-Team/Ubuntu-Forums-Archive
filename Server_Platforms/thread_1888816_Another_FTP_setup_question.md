---
title: "Another FTP setup question"
date: 2011-11-30
forum: Server Platforms
---

### Post by PD24 on 2011-11-30
Hi,

I have an Ubuntu server (11.04) running and would like to give the end user FTP access to there website which is located in:

/var/www/website1

the problem is I have many other sites but the user can only have read/write permissions to there folder ie website1.

Any ideas?

Thanks (sorry new to Linux :()

---

### Post by PD24 on 2012-01-06
I would like to learn how to do this via vsftpd. Ive tried successfully using a GUI (gadmin-proftpd) but that got magically removed from the server by somebody/something.

---

### Post by Lars Noodén on 2012-01-06
Out of curiosity what got you steered towards FTP?  I get the feeling that there is some outdated documentation out there that needs fixing.  I'd like to track it down and get it fixed.

If you can connect to the machine with SSH then you already have SFTP available and configured.  You can connect to it via Nautilus, Dolphin and FileZilla.  Unlike FTP, which is insecure and cannot be secured, SFTP is designed from the ground up to provide a secure connection.

Here is some background reading on the issue, if that helps:

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[/list]

---

### Post by PD24 on 2012-01-06
> **Lars Noodén said:**
> Out of curiosity what got you steered towards FTP?  I get the feeling that there is some outdated documentation out there that needs fixing.  I'd like to track it down and get it fixed.

If you can connect to the machine with SSH then you already have SFTP available and configured.  You can connect to it via Nautilus, Dolphin and FileZilla.  Unlike FTP, which is insecure and cannot be secured, SFTP is designed from the ground up to provide a secure connection.

Here is some background reading on the issue, if that helps:

[LIST]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[/LIST]


I searched Google, "FTP using Ubuntu".  This wasnt really that helpful: [https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html)

Thanks, hopefully its an easy read! :D

The end user just wants to upload there new website to the folder. Therefore i need to give FTP access to the folder. I dont think the end user knows how to use SSH or anything like that. So it needs to be simple.

---

### Post by Lars Noodén on 2012-01-06
> **PD24 said:**
> Therefore i need to give FTP access to the folder. I dont think the end user knows how to use SSH or anything like that. So it needs to be simple.

Then you can use SFTP it is related to SSH only in that it is part of SSH.  You can connect to an SFTP server using regular clients like Nautilus, Dolphin and FileZilla.  Even some regular editors, like Kate, can accept an SFTP address.  The SFTP option is *secure*, the FTP option is neither secure nor securable.  FTP is complicated to set up.  SFTP works out of the box already if you have an SSH server running, it's part of the server.

It's hard to get simpler than SFTP.  :)

---

### Post by PD24 on 2012-01-06
> **Lars Noodén said:**
> Then you can use SFTP it is related to SSH only in that it is part of SSH.  You can connect to an SFTP server using regular clients like Nautilus, Dolphin and FileZilla.  Even some regular editors, like Kate, can accept an SFTP address.  The SFTP option is *secure*, the FTP option is neither secure nor securable.  FTP is complicated to set up.  SFTP works out of the box already if you have an SSH server running, it's part of the server.

It's hard to get simpler than SFTP.  :)

Yes.. thank you. but i cannot find instructions or a guide to set this up..

if i want to give SFTP access to a specific folder with upload and dowload rights also with a specific username and password how do i?

In Windows i just install FileZilla Server and then set up the permissions to the folder and set up the access for the users. 

I need to learn how to do this on Linux without the GUI.

---

### Post by Lars Noodén on 2012-01-06
It should be just a matter of regular file/folder permissions.  If that folder is being used by only that one account, then you can change ownership of that folder.

```

sudo chown pd24 /path/to/some/folder

```

If you are sharing access among a group of accounts then it means that you have to work with the group permissions instead.

```

sudo addgroup webmasters

sudo gpasswd --add pd24  webmasters

sudo chgrp -R webmasters /path/to/some/folder

sudo find /path/to/some/folder -type d -exec chmod g=rwxs "{}" \;

sudo find /path/to/some/folder -type f -exec chmod g=rws  "{}" \;

```

Here are some more details:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by PD24 on 2012-01-06
> **Lars Noodén said:**
> It should be just a matter of regular file/folder permissions.  If that folder is being used by only that one account, then you can change ownership of that folder.

```

sudo chown pd24 /path/to/some/folder

```If you are sharing access among a group of accounts then it means that you have to work with the group permissions instead.

```

sudo addgroup webmasters

sudo gpasswd --add pd24  webmasters

sudo chgrp -R webmasters /path/to/some/folder

sudo find /path/to/some/folder -type d -exec chmod g=rwxs "{}" \;

sudo find /path/to/some/folder -type f -exec chmod g=rws  "{}" \;

```Here are some more details:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thanks but is this using the sftp?

---

### Post by Lars Noodén on 2012-01-06
It will be used by SFTP.  SFTP is just the connection to the remote machine.  Once the connection is made, it will obey the file systems permissions just like any other process.

---

### Post by PD24 on 2012-01-20
i did this and the existing ftp accounts now have access to the root folder!!!! this is badddd
how can i change this?

---

### Post by TFroehlich3 on 2012-01-20
Thank you!

---

### Post by TFroehlich3 on 2012-01-20
> **PD24 said:**
> i did this and the existing ftp accounts now have access to the root folder!!!! this is badddd
how can i change this?
 Thank you!

---

### Post by PD24 on 2012-01-20
> **TFroehlich3 said:**
> Thank you!


Thank You? I didnt realise this would happen!!!!! I thought the idea was setting the /var/www/ folder up so that the "webmaster" group could have access.

---

### Post by SeijiSensei on 2012-01-20
I set the DocumentRoot in Apache to $HOME/web for each virtual site.  You need to make sure that /home/username has 711 permissions, and that /home/username/web has 755 permissions.  That way when users connect with FTP or any other method, they end up in their home directories and far away from /var/www.

If you want to increase the level of security between users, put the www-data user in each website user's group, then set /home/username to 710 and /home/username/web to 750.  Now the Apache user can read the files, but no one else can.

---

