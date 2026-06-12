---
title: "[SOLVED] VSFTPD chroot jail to /var/www"
date: 2008-10-25
forum: Server Platforms
---

### Post by rubenverweij on 2008-10-25
Hello everyone!
I have succesfully set up an Ubuntu LAMP server and I want to use VSFTPD to allow users to acces the server via FTP. (not anonymous acces, just users who can login)
So, I succesfully configured the VSFTPD server and I can login remotely. My problem is: I have set it to lock the users in their home directory, but the websites are in /var/www or /var/www/[user]. Is it possible to lock the users to the /var/www directory instead?
Thanks in advance!
Ruben

---

### Post by baudday on 2008-10-25
What I did is I installed Webmin. Downloaded to vsftpd module for Webmin. And configured it that way. Then also, in Webmin, there is a place where you can add/delete/modify users. All you have to do is click on the user and set their home directory to whatever you want. Then I believe there is a place where you can jail the user to his home folder. I suggest getting Webmin.

---

### Post by rubenverweij on 2008-10-25
Ok, thanks! But I would rather not use webmin, I would prefer something command-line... :) I am looking for a web control panel, but only for vsftpd and mail server management, I don't need all the fancy features webmin offers me.

---

### Post by rubenverweij on 2008-10-25
The issue is solved!
I found this on [http://www.ducea.com/2006/07/27/allowing-ftp-access-to-files-outside-the-home-directory-chroot/](http://www.ducea.com/2006/07/27/allowing-ftp-access-to-files-outside-the-home-directory-chroot/):

> The solution to this little problem is to mount the needed directory using the –bind parameter… from the man page of mount: “–bind Remount a subtree somewhere else (so that its contents are available in both places)“.

So we might do something like:

```
mkdir /home/ftp_user/www_dev
mount --bind /var/www/dev/ /home/ftp_user/www_dev
```

After this the ftp user will be able to see the needed files in his home directory and use them in his ftp client as if they were local files.

If you need to make this configuration permanent you can either add the mount command in some startup script or you can just include a line in /etc/fstab:

```
/var/www/dev  /home/ftp_user/www_dev    none    bind    0       0
```

---

