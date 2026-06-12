---
title: "Users can't FTP with WINSCP"
date: 2008-06-19
forum: Security
---

### Post by amai on 2008-06-19
Something strange.

I have a windows PC connected direct to Ubuntu 7.10 Server.
I can't use WINSCP to ftp to the server, with any of the created FTP users.
I have created user1, user2, user3.
I can't ftp with any of these users only when using WINSCP.
BUT
I can ftp using WINSCP when log on using my root username and password.
AND
I can ftp using fireftp with user1,user2,user3 and my root username.
ONLY
change i have done is to change ssh port to 45, so do i need to configure anything to allow these users
to ftp on this port? .

Error message i get is 

"Cannot intialize SFTP porotocol. Is the host running a SFTP server?

which I know it has cause I can ftp using root username

Ta..

---

### Post by hyper_ch on 2008-06-19
for sftp/scp you need to have a ssh server installed and how did you create those users?

---

### Post by amai on 2008-06-19
users where created as follows


cd /var/www
mkdir user1
useradd webuser1 &#8211;p xxxx &#8211;d /var/www/user1 &#8211;s /bin/false
chown user1 user1
passwd user1 and, when asked password, used XXXXXXX as the password.

---

### Post by gaten on 2008-06-19
Try logging in as your regular user (ie the one that was setup on install), as it will have a shell. I'm just wondering if the /bin/false option is messing things up (although it shouldn't).

Also, check your ssh logs and see if something pops up: /var/log/auth.log

Oh, and don't post the password you used, that's a bad idea.

---

### Post by amai on 2008-06-21
Ok I , found whats causing the problem (maybe)

according to the following quote

"when we set up a new user account for our web user, we’ll configure their account so that /bin/false is their command shell. Because there’s no such shell, they won’t be able to log in with telnet."

So since the ftp users dont have a valid shell hence cant use WINCSP.
BUT
What will be another way to disable telnet on these users besides using /bin/false?
(this is for security reasons: FTP users can only FTP but should not TELNET)

---

### Post by fahadsadah on 2008-06-22
You do not need to change their shells from /bin/false. They should still be able to FTP.

---

### Post by kevdog on 2008-06-22
Winscp uses putty type keys.  Are you attempting to connect using openssh keys rather than putty type keys?

---

