---
title: "Configure openssh ftp - Upload to web directory"
date: 2010-07-27
forum: Server Platforms
---

### Post by mortona42 on 2010-07-27
I would like to upload files via ftp or sftp to my web directory at /var/www/...

Originally I had installed openssh-server (through apt-get, before learning about tasksel).  I assumed this only had ssh support and not ftp, so after a quick search, I installed vsftpd.  I would like to learn how to configure openssh, and I mention vsftpd in case there is a conflict.

Right now I am able to log in to my server box through ssh/ftp, but I can only modify my home directory.  I created a directory: /var/www/andrew and set permissions to drwxr-xr-x.  I am unable to upload files to this folder.

What do I have to do to resolve this, and is there anything else I should know about my situation?

---

### Post by Bachstelze on 2010-07-27
Who is the owner of this directory? If it it root, you need to change it to you (with chown).

---

### Post by richardjh on 2010-07-27
Check the ownership of the directory.

Also there is a setting in vsftp that you need to enable to allow any ftp writes:
Check /etc/vsftpd.conf for the lines

```
# Uncomment this to enable any form of FTP write command.
write_enable=YES
```And check write_enable=YES is uncommented.

If you make a change you will need to restart vsftpd for the changes to take effect

```
sudo service vsftpd restart
```

---

### Post by mortona42 on 2010-07-27
Thanks Bachstelze, that was spot on.

richardjh, I am unclear what role vsftp plays in this situation, can you clarify?

---

