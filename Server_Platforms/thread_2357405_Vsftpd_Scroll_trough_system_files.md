---
title: "Vsftpd Scroll trough system files"
date: 2017-04-01
forum: Server Platforms
---

### Post by lecethimon on 2017-04-01
Greetings,

I am running Ubuntu server 16.04.2

I installed vsftpd and followed a guide made by Digital Ocean.

Everything works fine but there is one thing that is bothering me. When I log in with an account all the permissions are fine. I cant upload or download outside my own home folder. But I can scroll and look through all the sytem files and other people's files.

Is there a way that when I log in I cant look into any other folders from other people or system files?
I'm fairly new to linux. I added my vsftpd config file just in case someone wants to see it.

Thnx!

[ATTACH]274398[/ATTACH]

---

### Post by cariboo on 2017-04-02
Moved to Server Platforms.

---

### Post by darkod on 2017-04-02
I am not too familiar with vsftpd, but there should be some option to limit you to the home folder only. By default if you don't limit it, it is normal to allow you to see many system files that are read-only too. You shouldn't be able to change them, but you can see them.
Another option for ftp is to use something like chroot jail. That is limiting the user only to specific location.

But having said all that, ftp is very uncommon to be used. Most people stick with ssh/scp that is way more secure. And you definitely shouldn't use plain ftp especially if the server is public on the internet, you are looking for trouble.

Bottom line, reconsider your needs and see if ssh/scp can work out for you. If yes, remove vsftpd and forget any ftp... :)

PS. Quick vsftpd limit users search:
[http://serverfault.com/questions/544850/create-new-vsftpd-user-and-lock-to-specify-home-login-directory](http://serverfault.com/questions/544850/create-new-vsftpd-user-and-lock-to-specify-home-login-directory)
[https://access.redhat.com/articles/6292](https://access.redhat.com/articles/6292)
[http://askubuntu.com/questions/656901/vsftpd-restrict-users-to-home-directory](http://askubuntu.com/questions/656901/vsftpd-restrict-users-to-home-directory)

PPS. The above links do not mean I recommend you to continue using ftp. :) As I said, if possible stick to more secure protocols like ssh/scp.

---

