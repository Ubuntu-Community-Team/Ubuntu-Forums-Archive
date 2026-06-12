---
title: "2 questions about VSFTPD"
date: 2009-04-02
forum: Server Platforms
---

### Post by artheus on 2009-04-02
Hey! I've got two questions about VSFTPD..

1. I am experiencing some trouble with connecting to my VSFTPD server, with the Dreamweaver FTP. Many of the times I try to connect I get a connection error. Something like "Not able to connect". And the same thing if I try to connect with the windows built-in FTP in explorer. (I don't mean Internet Explorer).
Have anyone else experienced this too? Is there a solution for this? Or should I change FTP server?

2. My second question is maby more simple. I have a domain, let's call it mydomain.org. And it is redirected to my server, by IP.
And to connect to my ftp-server from a non-local machine. I can do that by writing "mydomain.org" as a host. I don't want that to be possible. I want it to be "ftp.mydomain.org" and no other domain, and no other url works.
And.. I've got several domains. So I wan't "ftp.myotherdomain.org" to also point to the same ftp server. But NOT "myotherdomain.org".
I know that in apache2 I can write in
```

Listen 80
NameVirtualHost *:80

<VirtualHost *:80>
    ServerAdmin myname@localhost
    ServerName mydomain.org
    ServerAlias mydomain.org *.mydomain.org

    DocumentRoot /mnt/sdb1/websites/mydomain
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin myname@localhost
    ServerName myotherdomain.org
    ServerAlias myotherdomain.org *.myotherdomain.org

    DocumentRoot /mnt/sdb1/websites/myotherdomain
</VirtualHost>

```

So I wonder If there is some way to do the same thing in VSFTPD.
Something like
```

Listen 21
NameVirtualHost *:21

<VirtualHost *:21>
    ServerAdmin myname@localhost
    ServerName ftp.mydomain.org
    ServerAlias ftp.mydomain.org
</VirtualHost>

<VirtualHost *:21>
    ServerAdmin myname@localhost
    ServerName ftp.myotherdomain.org
    ServerAlias ftp.myotherdomain.org
</VirtualHost>

```


Cheers,
Artheus

---

### Post by artheus on 2009-04-02
Well.. That was not a good example.. but something like
```

UsedURL ftp.mydomain.org, ftp.myotherdomain.org, ftp.somedomain.com

```
or something would be really nice!

Cheers

---

