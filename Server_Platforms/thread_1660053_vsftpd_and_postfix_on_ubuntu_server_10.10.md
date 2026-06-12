---
title: "vsftpd and postfix on ubuntu server 10.10"
date: 2011-01-04
forum: Server Platforms
---

### Post by blejzz on 2011-01-04
hi all, 

i'm new to server administration (and to this forum) and i've managed to setup ubuntu server 10.10 without any problems. The server is running as a gateway for a local network and also runs a webserver + mail(postfix + courier) + ftp (vsftpd)  for multiple sites. And everything works but i've came across some questions google couldnt anwser (or my google skills stink)... so here i am :)

Is it possible to configure vsftpd to allow users that are in a specific group (like ftpusers) to login to the ftp server, and if they aren't they cant login? Just like in the ssh config file the command AllowGroups group1,group2... Or can this be achived somehow different? I know i can allow only specific usernames, but i want to permit a specific group(s).

And my other question is quite similar but for mail. How to achive that if a user is in a group called mailusers he can automaticly recive mail but if he isn't he doesn't get anything? Is it possible or does creating a new user (with home dir set) give the user automaticly the ability to recive email (if the Maildir exists)?

To shorten it up, i would like to have 3 groups: sshusers, mailusers and ftpusers.
if a user called Adam is in group:
    - sshusers - he can ssh into his home dir
    - mailusers - he can login to check/send his email
    - ftpusers - he can login into ftp server into his home dir

And is it possible to configure postfix that if it recives a mail for [EMAIL="someUser@mydomain.com"]someUser@mydomain.com[/EMAIL] and the user someUser doesnt exists that it delivers it to 
[EMAIL="admin@mydomain.com"]admin@mydomain.com[/EMAIL] (which exists) .. i know i can use /etc/aliases but i dont want to do add every user into it, i would just like to use something like (in /etc/aliases): 
```

postmaster:       root
root:            admin
*:               admin

```is something like this possible?

Thanks in advance,
Regards J

---

### Post by blejzz on 2011-01-06
anyone?

---

