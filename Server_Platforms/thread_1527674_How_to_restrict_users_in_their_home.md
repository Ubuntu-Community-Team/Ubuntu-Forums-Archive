---
title: "How to restrict users in their home"
date: 2010-07-09
forum: Server Platforms
---

### Post by naminem on 2010-07-09
How do I restrict users from going outside their home directory when connecting to the server via FTP or SSH?

---

### Post by arrrghhh on 2010-07-09
I think the term is called a "chroot jail".  I am by no means an expert in the field however, so I'd just be googling like you :P

Here's the official Ubuntu doc - [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by cdenley on 2010-07-09
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

FTP servers usually have an option in the configuration file for chroot'ing users. Which FTP server are you using?

Chroot environments for SSH servers where you need to provide shell access is rather difficult, since they basically need their own OS within their chroot directory in order for their shell to run. If you only need SFTP access, see the link above.

---

### Post by naminem on 2010-07-09
I am using pureftpd

---

### Post by naminem on 2010-07-10
Any help would be appreciated!

---

### Post by Vegan on 2010-07-10
I use vsftp and it works like a charm on my system

---

### Post by cdenley on 2010-07-12
> **naminem said:**
> I am using pureftpd

Sorry, not familiar with that FTP software. Is it even in the repos?

---

