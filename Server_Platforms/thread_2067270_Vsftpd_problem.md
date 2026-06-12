---
title: "Vsftpd problem"
date: 2012-10-06
forum: Server Platforms
---

### Post by msy07 on 2012-10-06
Hi Guys!

I'm currently setting up my ubuntu 10.04 server running on a vps to host a Drupal Site. Now I'm already on the development stage of my drupal site and I also need to update some modules which could be done through FTP. 

Now while searching over the web, I saw that to enable FTP on my ubuntu server, I have to install vsftpd. I installed it and I successfully transferred drupal core files, etc. using sftp in filezilla. 

Now my drupal site is reminding me to update some modules as well as the core files which could be done through ftp. So I obeyed the reminder and clicked to update it. Now it asks for my  FTP server account username, password etc. and I entered all just like how I enter it using filezilla and *POOF* it denies me from logging in.

Now I searched that there are settings on the vsftpd.conf file that should be changed to fix that issue and after it's changed, the vsftpd service should be restarted.

So first I tried

```
sudo /etc/init.d/vsftpd restart
```and it resulted to "**sudo: /etc/init.d/vsftpd: command not found**"

now I tried 

```
service vsftpd restart
```and it resulted to "**exec: 129: restart: not found**".

Now I tried to see what's wrong with /etc/init.d/vsftpd by 

```
ls -l /etc/init.d
```and it results
```

.
.
.
lrwxrwxrwx 1 root root    21 Oct  2 06:29 vsftpd -> /lib/init/upstart-job

```From here I now don't know what to do next to solve my problem.

Any help would be greatly appreaciated! 

Thank You!

---

### Post by Crafty Kisses on 2012-10-08
Try reimaging your VPS

```
dpkg --get-selections | grep php

dpkg --get-selections | grep sql

dpkg --get-selections | grep apache
```

If any arise

```
apt purge package-name
```

---

