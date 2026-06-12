---
title: "Chroot Users"
date: 2009-05-23
forum: Server Platforms
---

### Post by zemon_ on 2009-05-23
Im using vsftpd, I created a user who is directed to there own directory on login.

How do I stop the user from going anywhere else accept his own directory?

```

sudo groupadd user

sudo useradd -c "FTP user" -d /home/user/downloads -g user user
```

What should my vsftpd settings be?

```
sudo nano /etc/vsftpd.conf
```

---

### Post by albinootje on 2009-05-23
> **zemon_ said:**
> 
How do I stop the user from going anywhere else accept his own directory?
[/CODE]

This might help :
[http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html](http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html)

See also the two sections below in this url :
[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)
> 
chroot_list_enable
chroot_local_user


---

### Post by zemon_ on 2009-05-24
This what I have done and does not lock the user out of other directorys.

```
sudo nano /etc/vsftpd.conf
```

Uncomment this line

```
chroot_local_user=YES
```

Restarted

```
/etc/init.d/vsftpd restart
```

Am I right in thinking this does not work for sftp only ftp?

---

### Post by albinootje on 2009-05-24
> **zemon_ said:**
> 
Am I right in thinking this does not work for sftp only ftp?

sftp (and scp) is part of openssh, and has nothing to do with your vsftpd installation.

---

### Post by albinootje on 2009-05-24
Newer versions of Openssh have a build in chroot option, see here :
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

Ssh is also completely encrypted, whereas ftp traffic is completely plain text by default.

---

### Post by zemon_ on 2009-05-24
How is this possible to stop the user going to other folders except there home using ftp or sftp?

---

### Post by albinootje on 2009-05-24
> **zemon_ said:**
> How is this possible to stop the user going to other folders except there home using ftp or sftp?

I gave you a link to a howto for chrooted sftp, read it, (check your ssh version!) and try it.

---

### Post by zemon_ on 2009-05-24
This guide makes absolutely no sense to me can anyone explain this to me.

[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

Is there a way I can disable sftp access and just use ftp?

---

### Post by albinootje on 2009-05-24
> **zemon_ said:**
> This guide makes absolutely no sense to me can anyone explain this to me.

[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)


This might be easier to follow :
[http://ubuntuforums.org/showthread.php?t=1057657](http://ubuntuforums.org/showthread.php?t=1057657)

---

