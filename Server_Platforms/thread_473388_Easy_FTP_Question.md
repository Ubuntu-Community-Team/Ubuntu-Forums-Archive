---
title: "Easy FTP Question"
date: 2007-06-14
forum: Server Platforms
---

### Post by FKi on 2007-06-14
How do you make several accounts on a ftp server running ubuntu server edition?

I need to be able to have multiple people acess ftp without useing my account and password, i need to set up independant accounts for them to use there own password and username.

Im sorry this is a dumb question, but i realy need to get the answer asap so i can go home!

thanks in advance

---

### Post by dominator22 on 2007-06-14
Depends what ftp server you're running.  I'm partial to pureftp.  Search the repositories for it.
```
aptitude search pure-ftp
```

---

### Post by FKi on 2007-06-14
its vsftpd

---

### Post by PaulFr on 2007-06-14
One way of achieving what you want:

1. First set up the local user accounts and passwords, one for each user you wish to give permission (using System -> Administration -> Users and Groups).
2. Then using your favorite editor, edit /etc/vsftpd.conf (for example, sudo nano /etc/vsftpd.conf) to remove the # mark before the following lines
[B]
local_enable=YES
local_umask=022
chroot_local_user=YES[/B]

If these lines do not exist in your vsftpd.conf, please add them. The comments in vsftpd.conf explain what these lines do. A quick summary: First lines allows local users to login, second line allows files created by local users to have rw-r--r-- permissions (readable by group and others), and third line (optional) forces local users to only work with files in their own home directories.

If you have problems with users logging in, see [ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/FAQ](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/FAQ) and specifically, the answer to the sixth question ("Local users cannot log in") for help.

---

### Post by FKi on 2007-06-14
how do you "use system -> administration -> users and groups"?

i try to edit the file but its blank

---

### Post by poisonelegy on 2007-06-14
> **FKi said:**
> how do you "use system -> administration -> users and groups"?

i try to edit the file but its blank

Are you using gnome? If you don't have the desktop try "sudo adduser (name of user)"

---

### Post by PaulFr on 2007-06-14
Hi,

1. Sorry, I assumed you had the X-Windows desktop up (System -> Administration -> Users and Groups is a menu in the desktop). If not, as the comment above, use the following:

**sudo adduser --group users <userlogin>**

where you replace <userlogin> with the values you want (this is the login, no spaces allowed). It will ask you for the password, name and other details.

2. When you say your file (/etc/vsftpd.conf) is an empty file, it may be one of two things:

3. First, vsftpd may not be installed on your server. Check with **aptitude show vsftpd** and see the State: value.

3.1 If the State: is not installed, then install it with **sudo aptitude install vsftpd**
3.2 If it is installed, you can run **sudo aptitude upgrade vsftpd** to update it to the latest version.

4. Now check if /etc/vsftpd.conf exists and is not empty (**wc -l /etc/vsftpd.conf** will show the number of lines in the file) . If yes, then go back to my earlier post and ignore the following.

5. vsftpd.conf may not be in the default position (/etc/vsftpd.conf). To see if this is the case, please tell us the output of
**ls -l /etc/rc2.d/*vsftpd**
**grep vsftpd /etc/inetd.conf**
**ps -eo pid,args | grep vsftpd**

Hope this helps.

---

### Post by FKi on 2007-06-14
i did sudo adduser (username) 

that worked fine.

i would see the output of that but i only have one moniter and 2 computers (one being the server)  soo it would be too much of a hassle, plust im pretty sure its up-to-date

---

