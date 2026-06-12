---
title: "[SOLVED] vsftpd permissions of files being uploaded"
date: 2008-07-03
forum: Server Platforms
---

### Post by kerryhall on 2008-07-03
How can I change the default permissions of files that are uploaded via ftp with vsftpd?

Right now when files get uploaded, they default to -rw-------
I want them to default to something like -rw-r--r--

Thanks!

---

### Post by nix4me on 2008-07-03
easy.  change local_umask=077 to local_umask=022.  That will set 755 permissions.

Read the docs here:
[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

---

### Post by RealPSL on 2008-07-03
Good security practice for your web server says the files should have permissions rw-r----- (umask 027). However if you want it to have umask 022 like you describe you need to change the local_umask from 077 (default) to 027. More information is available in the man pages for vsftpd.conf. The change needs to be made in the vsftpd.conf file and the ftp server restarted with 

```
sudo /etc/init.d/vsftpd restart
```

---

### Post by kerryhall on 2008-07-07
Thanks to both of you for your help! :)

---

### Post by possumator on 2008-07-22
I am not very experienced with Linux, but have an 8.04 server running a LAMP + SVN + FTP configuration on an old P2 366mhz laptop. This is my web development testing rig and it runs fine. 

Naturally, I would like to FTP directly into the /var/www directory. So hoping the above posts will help me. Up to now I have been moving the content manually to /var/www. 

That said, what are the appropriate permissions for content living in /var/www? This is just a bunch of static xhtml pages. I couldn't seem to get apache 2.2 to load them short of giving them full permissions. I even tried CHOWN to www-data:www-data as after upload everything had root:root.

thanks for any help.

---

