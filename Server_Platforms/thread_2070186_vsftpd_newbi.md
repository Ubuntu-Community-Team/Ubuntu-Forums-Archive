---
title: "vsftpd newbi"
date: 2012-10-12
forum: Server Platforms
---

### Post by Mintnacho on 2012-10-12
Hi, I'm having a couple questions that I can't seem to find answers for. 

So far I've been able to finally get vsftpd working. I can login with my server IP address via ssh session to the  box. (I'm currently remote and unable to access router to setup the port forwarding for external access) . 

But here are my questions

I've added the user 'darwin' which is to be the test ftp user and added him to the group 'ftpers'.
However, I can't login with 'darwin' I can however login with one of my other accounts. Specifically my personal account but this account isn't a member of 'ftpers' .

How do I fix this?.. I don't really understand how this is actually working w/o being specified.

Also, If I want to use a free dns (like dyndns) is this something i just need to setup on the router as port forwarding? 

How do I lock users to a specific file or group of files w/o changing permissions?
If I have to change permissions, how do I add the 'ftpers' group into the 'main group'.

I've read a bunch of tutorials and they've gotten' me this far. I'd appreciate any help I can get from the community. 
:guitar:

---

### Post by Mintnacho on 2012-10-21
bump .. 126 people have looked at this and not a single word of advice. But I've come to expect that kind of thing

---

### Post by duesentriebchen on 2012-10-23
Hy there :)
 
please post your ```
/etc/vsftpd.conf
``` or ```
/etc/vsftpd/vsftpd.conf
``` where ever it is located with
```
cat /etc/vsftpd.conf
``` or ```
cat /etc/vsftpd/vsftpd.conf
```
 
please post also the output of ```
vsftpd -v
```
 
 
To evaluate your groups, please do a ```
groups
```
To evaluate in which groups your users are, please do a ```
groups $(whoami)
``` for your personal user, and a ```
groups darwin
``` for your darwin ftp-test user.
 
In case of a DYNDNS account, i would propse the usage of a dnsclient [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)
 
Every user on the system has certain rights like your personal user does. For all other operations like writing you eventaully need sudoers rights.
If you want add users to certain groups, use ```
sudo usermod -a -G GROUP_1,GROUP_2 USER_NAME
```
If you want to withdraw a user from a group, use  ```
sudo deluser USER_NAME GROUP_1
```
If you want to change permissions use ```
chmod
``` and ```
chown
```.
 
Why do you want to use a "ftpers" group? You can add a "normal" user with his HOME directory and allow this user in the vsftpd.conf user_list.
For security reasons, every ftp users shell should be changed from /bin/sh to /bin/false -> this means the ftpuser has no ability to use a shell command.
Also vsftpd gives you the possibility of a chrootjail for every local user!
Please read the vsftpd man page. [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)
If you need more help, i can provide you a vsftpd.conf with an allowed user_list, where every user is "jailed" in his home directory.
 
Kind regards

---

