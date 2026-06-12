---
title: "Setting up vsftpd with users?!"
date: 2008-12-31
forum: Server Platforms
---

### Post by spinanicky on 2008-12-31
I have just finished setting up the majority of my NAS - Torrent - Webserver and the only thing left to do is FTP.

I have installed VSFTPD but as far as I can tell by adding users I also give them access to ssh into my machine.. is that right?!
Also it would appear that all ftp directories have to be in the same location and the username then differentiates the root directory for login?

What I would like is to have two folders, FTP and WWW in /var and when I login to www it pushed me into the www directory and if I login with x username it pushes me into the users folder within the FTP folder. On top of it all I want these users to only be able to access ftp, nothing else... ie no ssh login etc.

If anyone is interested in writing a short guide or pointing me in the right direction I would be most grateful!

Thanks
Nicky

---

### Post by spinanicky on 2009-01-02
bump :D

---

### Post by albinootje on 2009-01-02
> **spinanicky said:**
>  I have installed VSFTPD but as far as I can tell by adding users I also give them access to ssh into my machine.. is that right?!
Also it would appear that all ftp directories have to be in the same location and the username then differentiates the root directory for login?


One solution for this is the AllowUsers or AllowGroup option of the openssh-server.
See :
```

man sshd_config

```

For example :
# example bit of /etc/ssh/sshd_config :
Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

AllowUsers henry jane karen@10.1.2.* edward@192.168.1.*
# end example

After that :
```

/etc/init.d/ssh restart

```

By the way, some ftp-server software can let you have virtual ftp users (which are not system users), not sure whether that's the case with vsftpd. 
I'm using vsftpd, but on a local file-server with full down and uploads for the trusted LAN users.

---

### Post by spinanicky on 2009-01-02
yea thats basically what I want however I just dont want them to have access to anything else expcept ftp. 

Will have a look at your SSH example. 

Do you have a link to the website you used for the vsftpd setup?!

Thanks

ps: sftp... im a bit confused now. In the example you gave is that code granting access to ssh connections or to ftp connections?! I realise im editing the sshd file, it's just a bit strange so want to confirm.

---

### Post by albinootje on 2009-01-02
> **spinanicky said:**
> yea thats basically what I want however I just dont want them to have access to anything else expcept ftp. 

Will have a look at your SSH example. 

Exactly, my example with AllowUsers in sshd_config will only give you access to the users that you only want to give access to with ssh.
That means that you can give out normal user accounts for ftp to the users which are not allowed to use ssh.
> 
Do you have a link to the website you used for the vsftpd setup?!

I think I started using vsftpd for the first time when I used FreeBSD on that server, it came with an example config file which was good enough to get started with.

I've just searched for ```
"virtual users" vsftpd
```
This looks pretty good :
[ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=518293](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=518293)
[http://ubuntuforums.org/archive/index.php/t-34292.html](http://ubuntuforums.org/archive/index.php/t-34292.html)
[http://www.vsftpdrocks.org/faq/](http://www.vsftpdrocks.org/faq/)
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)
Have fun reading and configuring ;-)

---

### Post by geforce123 on 2009-01-03
What your looking for is virtual users from any kind of database, instead of system user.

I recommend this howto:

[http://www.howtoforge.com/vsftpd_mysql_debian_etch](http://www.howtoforge.com/vsftpd_mysql_debian_etch)

(also check the comment on page 2, you might have a small change to do to the database scheme)

---

