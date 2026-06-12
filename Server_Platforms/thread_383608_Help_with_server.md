---
title: "Help with server"
date: 2007-03-13
forum: Server Platforms
---

### Post by Numbah51 on 2007-03-13
I have recently installed ubuntu 6.06 server with LAMP.  Everything has been working good so far, except, when i upload files to the /var/www directory (using vsftpd on the linux machine), i have to chmod them myself otherwise i can't view them in my web browser.  i am using one of my created users "mike" to upload files.  Also one other quick question, is there any easy way to create new users and only allow them to upload in say /var/www/user2.  And that just reminded me, when i log in as "mike" i can view the whole filesystem, and if i let other people use my server, i don't want them to be able to.  Thanks so much in advance for any help.

-Numbah51 a.k.a. Mike

---

### Post by Nikron on 2007-03-13
Umm, have you tried creating a specific upload directory, and then chmoding that whole directory?  Also, I don't know if this a good/bad idea but look into the possibility of a chroot jail for people who upload things.

---

### Post by Mr. C. on 2007-03-13
You need to change the local_umask parameter in /etc/vsftpd.conf

I assume you have set local_enable set to yes.

```
man vsftpd.conf
```

and search for local_umask

You need a umask of 022 to have files created such that apache will be able to read them after you've uploaded.

MrC

---

### Post by Numbah51 on 2007-03-14
ah yes that helps with that one problem.  Thanks so much.  Any help with the other questions (About ftp users and seeing the whole filesystem) would be great :)

---

### Post by Mr. C. on 2007-03-14
Sorry, I don't do well with long running sentences and paragraphs.  Use more paragraphs and punctuation for clarity to get the best chances of help.

You can use the chroot_local_user setting to lock your users into their own home directories.  This comes with its own security risk if you allow uploads, unless you understand what you are doing, and how security may be breached in chroot environments.

MrC.

---

