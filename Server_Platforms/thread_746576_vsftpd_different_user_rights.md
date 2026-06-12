---
title: "vsftpd different user rights"
date: 2008-04-05
forum: Server Platforms
---

### Post by durus on 2008-04-05
Hi, I am want to set up my ftp server something like this:

1. User type 1 -> access /home/$USER
2. User type 2 -> access /home/ftp_common

Is this possible in vsftpd and if so, how can I do that ? I have managed to do only 1 or only 2 (2 with virtual users) but I have not managed to make them both working at the same time.

Thank you
Payam

---

### Post by netlogic on 2008-04-05
> **durus said:**
> Hi, I am want to set up my ftp server something like this:

1. User type 1 -> access /home/$USER


adduser and chroot to their homedir

```
chroot_list_enable=YES
```

> 
2. User type 2 -> access /home/ftp_common
add the user1 to userxxx and change their user home dirs to


let's assume this is a group ftp share /home/share1
add a new user
edit passwd manually and move the location to /home/share1

(this mean their ssh session will break. i am going to assume you are not giving them ssh accounts)

---

### Post by durus on 2008-04-06
Thank you it worked. But is it possible to let user type 2 be virtual. So that I don't need to have so many user on my computer. I do not know, but for me it seems like a security issue to have them as local users. Even if I don't let them use ssh.  I may maybe install some other application like ftp that will use my users, and then I need to change every thing.

---

### Post by netlogic on 2008-04-06
It depends how you look at it. It isn't really a security risk. First of all, they only have a ftp access. You can even limit the FTP command functions in your config file. They can't browse anywhere besides chroot directory. Also, PAM is a lot stronger authentication and easier to manage. If you are worried about having a tougher user management, change your pam for vsftpd to allow from disallow. 

modify the file in /etc/pam.d/vsftpd

now, you only add ftp users in
/etc/ftpusers

default is disallow. i think it is easier to mange if it is set to allow.
also, ssh should be only used by people who need to interact with the system.
ssh users should just use ssh.

Let's say the user falls for the man in the middle attack on his/her DNS and he/she accidentally logon to a wrong FTP server.  The person enters his/her username and password and the wrong ftp server happens to be logging the password. This doesn't jeopardize your system at all. ONly thing they can do  with your system is download that users files.  Also, with pam you will have more control over the user. It is up to you how you want to handle it.

---

### Post by durus on 2008-04-06
"First of all, they only have a ftp access."
This is the thing I can't understand, how do I know that they only have ftp access ?

If I for some reason install vnc or some other application. The application will then maybe also use my local users, exactly as ftp does. Or can I set some permissions so that they only are ftp users ?

---

### Post by netlogic on 2008-04-06
1. your sshd config should only allow certain groups of users to use ssh.
2. like i mentioned before set your pam to allow for vsftpd and list only the users who need ftp in /etc/ftpusers
3. every server based application permission should be based around "groups."
4. never do FREE for all permission on any system.

---

