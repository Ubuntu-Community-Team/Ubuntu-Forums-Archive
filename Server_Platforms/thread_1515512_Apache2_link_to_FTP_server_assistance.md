---
title: "Apache2 link to FTP server assistance"
date: 2010-06-22
forum: Server Platforms
---

### Post by lioncrazyguy on 2010-06-22
Hello,

I have an apache2 web server running on ubuntu server (Ver 2.6.27-7-server) running just a basic Mediawiki site for our group internally.  It's just a basic info wiki, and it also hosts a bunch of large .iso files for the group to download if they need them.  The latter part is where my latest issue has come up, and I'll try to keep it brief.

We moved all the .iso files to a FTP server that we just got up and running, since the FTP site has goads more space available on it's NAS shared drive than my wiki server whose hard disk is rapidly shrinking with all the .iso files on it.  Now, the FTP server is outward facing unlike the wiki server, so obviously it has to have user/password authentication unlike the wiki, which is only internal.  

I want to be able to link from the wiki server directly to the files on the FTP server without the user being prompted for a password, while still keeping a decent transfer speed.

So far I've tried 2 methods that have "worked".

First, I mounted a local folder on the wiki to the FTP server using CurlFTPfs by adding a line in the /etc/fstab file.

```
curlftpfs#iso:ftpiso@172.17.12.19 /var/www/downloads fuse allow_other,uid=www-data,gid=www-data 0 0
```

This actually works perfectly, I can link to the files and never get prompted for credentials, however the transfer rate is abysmal.  under 100kb/s over a gigabit connection, rather than 10MB/s I can get if using an FTP client directly.

The other method I used was enabling the mod_proxy_ftp and simply redirecting to the FTP using the wiki server as a proxy.  

In the virtual host file:
```

ProxyPass /download ftp://iso:ftpiso@172.17.12.19
ProxyPassReverse /download ftp://iso:ftpiso@172.17.12.19    
```


This speeds things up a little ~230kb/s however I still get prompted for credentials.

Is there any way possible to get it to work like the CurlFTPfs method but still get decent network xfer rates?

any help would be greatly appreciated.

---

### Post by dapperdanny77 on 2010-06-22
sharing your ISOs via nfs could be an option

---

