---
title: "Restricting Users SFTP"
date: 2009-05-08
forum: Server Platforms
---

### Post by zemon_ on 2009-05-08
Im running ubuntu server 8.10 with vsftpd.
I want to restrict users to there home directory.
This is what I tried 

```
nano /etc/vsftpd.conf
```

Then uncommented this line

chroot_local_user=YES

```
/etc/init.d/vsftpd restart

```

Any ideas what im doing wrong?

---

### Post by Alekz_ on 2009-05-08
> **zemon_ said:**
> Im running ubuntu server 8.10 with vsftpd.
I want to restrict users to there home directory.
This is what I tried 

```
nano /etc/vsftpd.conf
```

Then uncommented this line

chroot_local_user=YES

```
/etc/init.d/vsftpd restart

```

Any ideas what im doing wrong?
Hi zemon_

Try this:

Edit the /etc/vsftpd.conf file with these lines:
```
chroot_list_enable=yes
chroot_list_file=/etc/vsftpd.chroot_list
```

You have to create the /etc/vsftpd.chroot_list file with the users you want to restrict access.

---

### Post by zemon_ on 2009-05-08
Yes I tried that also , but does not work I can still login as restricted user and view all the other files

---

### Post by Alekz_ on 2009-05-08
Oh! I forgot to mension...

If you're are using the 

```
chroot_list_enable=yes
chroot_list_file=/etc/vsftpd.chroot_list
```

then you must set 

```
chroot_local_user=no
```

They have opposite effect! :)

---

