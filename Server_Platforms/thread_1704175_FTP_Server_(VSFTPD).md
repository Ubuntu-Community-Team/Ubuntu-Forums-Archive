---
title: "FTP Server (VSFTPD)"
date: 2011-03-10
forum: Server Platforms
---

### Post by PhoeniX_NL on 2011-03-10
Hello Guys,

I am new to ubuntu and just installed the vsftpd service by this tutorial: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

Now my question is how can i give users rights to one specific folder?

useradd username -d /home/folder/new

Thats the command id used but when i login to the ftp the user is able to see all other folders as well ..

How can i fix this guys?

Greetings PhoeniX

---

### Post by btindie on 2011-03-10
You're not running Ubuntu 6.06 are you?

Try following the more up to date guide: [https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html)

---

### Post by mciverza on 2011-03-10
> **btindie said:**
> [https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html)

From that page, the solution is under the "Securing FTP" section

> There are options in /etc/vsftpd.conf to help make vsftpd more secure. For example users can be limited to their home directories by uncommenting:

chroot_local_user=YES

---

### Post by PhoeniX_NL on 2011-03-10
> **btindie said:**
> You're not running Ubuntu 6.06 are you?

Try following the more up to date guide: [https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html)

Hello,

I am running Ubuntu 10.04 (64bit).

---

### Post by PhoeniX_NL on 2011-03-10
> **mciverza said:**
> From that page, the solution is under the "Securing FTP" section

Thank you :)!

That solved my problem m8.

---

### Post by mciverza on 2011-03-10
> **PhoeniX_NL said:**
> Thank you :)!

That solved my problem m8.

Please mark this thread as solved.

---

### Post by Return Privacy on 2012-06-22
This doesn't solve the problem at all. The link he says to find the answer, is a bad link. 
I have the same exact question, and can't figure this out.
1. How to create a new user and pw 
2. How to assign and limit the new user to 1 specific folder
Ubuntu 11.10 and vsftpd

---

### Post by Elfy on 2012-06-23
> **Return Privacy said:**
> This doesn't solve the problem at all. The link he says to find the answer, is a bad link. 
I have the same exact question, and can't figure this out.
1. How to create a new user and pw 
2. How to assign and limit the new user to 1 specific folder
Ubuntu 11.10 and vsftpd

It probably wasn't last year.

Try looking here [https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

But you need to start a new thread if you have further issues.

Closed.

---

